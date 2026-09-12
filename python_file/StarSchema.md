# Threat Incident Analytics & Security Visualization


```python
!pip install pandas matplotlib seaborn plotly
```

    Requirement already satisfied: pandas in c:\users\dkraz\anaconda3\lib\site-packages (2.3.3)
    Requirement already satisfied: matplotlib in c:\users\dkraz\anaconda3\lib\site-packages (3.10.6)
    Requirement already satisfied: seaborn in c:\users\dkraz\anaconda3\lib\site-packages (0.13.2)
    Requirement already satisfied: plotly in c:\users\dkraz\anaconda3\lib\site-packages (6.3.0)
    Requirement already satisfied: numpy>=1.26.0 in c:\users\dkraz\anaconda3\lib\site-packages (from pandas) (2.3.5)
    Requirement already satisfied: python-dateutil>=2.8.2 in c:\users\dkraz\anaconda3\lib\site-packages (from pandas) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in c:\users\dkraz\anaconda3\lib\site-packages (from pandas) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in c:\users\dkraz\anaconda3\lib\site-packages (from pandas) (2025.2)
    Requirement already satisfied: contourpy>=1.0.1 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (1.3.3)
    Requirement already satisfied: cycler>=0.10 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: fonttools>=4.22.0 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (4.60.1)
    Requirement already satisfied: kiwisolver>=1.3.1 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (1.4.9)
    Requirement already satisfied: packaging>=20.0 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (25.0)
    Requirement already satisfied: pillow>=8 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (12.0.0)
    Requirement already satisfied: pyparsing>=2.3.1 in c:\users\dkraz\anaconda3\lib\site-packages (from matplotlib) (3.2.5)
    Requirement already satisfied: narwhals>=1.15.1 in c:\users\dkraz\anaconda3\lib\site-packages (from plotly) (2.7.0)
    Requirement already satisfied: six>=1.5 in c:\users\dkraz\anaconda3\lib\site-packages (from python-dateutil>=2.8.2->pandas) (1.17.0)
    


```python
import pandas as pd

# Dataset load 
df = pd.read_csv('cybersecurity synthesized data.csv')
df['timestamp'] = pd.to_datetime(df['timestamp'])

# Check karo
print("✅ Dataset Loaded Successfully!")
print("Total Rows & Columns:", df.shape)
print()
print(df.head(3))
```

    ✅ Dataset Loaded Successfully!
    Total Rows & Columns: (100000, 15)
    
            attack_type  target_system  outcome                  timestamp  \
    0          Phishing  Cloud Service  Failure 2024-04-03 11:13:15.083419   
    1              DDoS   Email Server  Success 2024-02-03 20:51:56.083463   
    2  Zero-Day Exploit  Cloud Service  Success 2024-07-19 18:40:05.083472   
    
           attacker_ip        target_ip  data_compromised_GB  attack_duration_min  \
    0      21.166.79.4      23.20.50.78                15.31                  300   
    1  187.180.150.169    34.160.58.218                65.05                  242   
    2   57.161.159.140  213.142.125.206                48.99                  120   
    
      security_tools_used      user_role   location  attack_severity industry  \
    0            Firewall       Employee  Australia                2   Energy   
    1  Endpoint Detection          Admin     Brazil               10   Retail   
    2            Firewall  External User    Germany                7  Finance   
    
       response_time_min  mitigation_method  
    0                164        Containment  
    1                 64  Reset Credentials  
    2                 87         Quarantine  
    


```python
# ── WHY DIM_TIME? ──────────────────────
# 1. Timestamp se Time information alag ki
# 2. Hour - kis time attack hua
# 3. Day  - kis din attack hua  
# 4. Month - monthly trend analysis ke liye
# 5. Quarter - quarterly report ke liye
# 6. Year - yearly comparison ke liye
# 7. Power BI mein time based filtering easy hogi
# Result: 1,00,000 rows x 7 columns ✅

# ── DIM_TIME ──────────────────────────
dim_time = pd.DataFrame({
    'time_key': range(1, len(df)+1),
    'timestamp': df['timestamp'],
    'hour': df['timestamp'].dt.hour,
    'day': df['timestamp'].dt.day_name(),
    'month': df['timestamp'].dt.month_name(),
    'quarter': df['timestamp'].dt.quarter,
    'year': df['timestamp'].dt.year
})

print("✅ DIM_TIME created:", dim_time.shape)
print(dim_time.head(3))
```

    ✅ DIM_TIME created: (100000, 7)
       time_key                  timestamp  hour        day     month  quarter  \
    0         1 2024-04-03 11:13:15.083419    11  Wednesday     April        2   
    1         2 2024-02-03 20:51:56.083463    20   Saturday  February        1   
    2         3 2024-07-19 18:40:05.083472    18     Friday      July        3   
    
       year  
    0  2024  
    1  2024  
    2  2024  
    


```python
# ── DIM_THREAT ─────────────────────────
# We created DIM_THREAT because:
# - It stores all attack type information separately
# - Helps us classify threats as Critical/High/Medium/Low
# - Makes filtering by attack type easy in Power BI

dim_threat = pd.DataFrame({
    'threat_key': range(1, df['attack_type'].nunique()+1),
    'attack_type': df['attack_type'].unique(),
    'severity_category': ['Critical' if s >= 9
                          else 'High' if s >= 7
                          else 'Medium' if s >= 4
                          else 'Low'
                          for s in df.groupby('attack_type')
                          ['attack_severity'].mean()]
})

print("✅ DIM_THREAT created:", dim_threat.shape)
print(dim_threat.head(8))
```

    ✅ DIM_THREAT created: (8, 3)
       threat_key           attack_type severity_category
    0           1              Phishing            Medium
    1           2                  DDoS            Medium
    2           3      Zero-Day Exploit            Medium
    3           4         SQL Injection            Medium
    4           5               Malware            Medium
    5           6            Ransomware            Medium
    6           7           Brute Force            Medium
    7           8  Cross-Site Scripting            Medium
    


```python
# ── DIM_LOCATION ───────────────────────
# Why DIM_LOCATION?
# - Stores country/region information separately
# - Helps us create Geospatial Threat Maps in Power BI
# - We can see which country has most attacks
# - Makes location based filtering easy

dim_location = pd.DataFrame({
    'location_key': range(1, df['location'].nunique()+1),
    'location': df['location'].unique()
})

print("✅ DIM_LOCATION created:", dim_location.shape)
print(dim_location)

```

    ✅ DIM_LOCATION created: (10, 2)
       location_key   location
    0             1  Australia
    1             2     Brazil
    2             3    Germany
    3             4     Russia
    4             5         UK
    5             6     France
    6             7        USA
    7             8     Canada
    8             9      China
    9            10      India
    


```python
# ── DIM_INDUSTRY ───────────────────────
# Why DIM_INDUSTRY?
# - Stores industry and target system info separately
# - Helps us see which industry is most attacked
# - Finance, Energy, Retail etc. ka analysis easy hoga
# - Power BI mein industry based filtering milegi

dim_industry = pd.DataFrame({
    'industry_key': range(1, df['industry'].nunique()+1),
    'industry': df['industry'].unique(),
    'target_system': df.groupby('industry')
                    ['target_system'].first().values
})

print("✅ DIM_INDUSTRY created:", dim_industry.shape)
print(dim_industry)
```

    ✅ DIM_INDUSTRY created: (8, 3)
       industry_key       industry   target_system
    0             1         Energy      IoT Device
    1             2         Retail   Cloud Service
    2             3        Finance   Cloud Service
    3             4     Healthcare        Database
    4             5     Technology    Email Server
    5             6      Education  Network Switch
    6             7  Manufacturing    Email Server
    7             8     Government    Email Server
    


```python
# ── DIM_RESPONSE ───────────────────────
# Why DIM_RESPONSE?
# - Stores how each attack was handled
# - Response time kitna laga ye track karta hai
# - Which mitigation method used - Patch/Quarantine etc.
# - Attack outcome - Success ya Failure
# - Helps build Response Analytics dashboard in Power BI

dim_response = pd.DataFrame({
    'response_key': range(1, len(df)+1),
    'response_time_min': df['response_time_min'],
    'mitigation_method': df['mitigation_method'],
    'outcome': df['outcome'],
    'security_tools_used': df['security_tools_used']
})

print("✅ DIM_RESPONSE created:", dim_response.shape)
print(dim_response.head(3))
```

    ✅ DIM_RESPONSE created: (100000, 5)
       response_key  response_time_min  mitigation_method  outcome  \
    0             1                164        Containment  Failure   
    1             2                 64  Reset Credentials  Success   
    2             3                 87         Quarantine  Success   
    
      security_tools_used  
    0            Firewall  
    1  Endpoint Detection  
    2            Firewall  
    


```python

```
