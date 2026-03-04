But anyways day one to two is all about setting up and understanding what I'm here for. Also, I am writing this with the help of AI, but generally all the unwitty quips that you read (literally only me) are written by me. Also, there's something about AI generated documentations that ick me so much. As a reader, some are far to verbose n sht, don't do that. Also after this, I'll be writing some thesis sht lmao. 

# The Title
"Threat Hunting in ICS environments with Sysmon and Modbus simulation with MITRE ATT&CK ICS Mapping". TLDR: Just the keywords pls. 
    Keyword Breakdown
    1. Threat Hunting 
        Security analysts actively search to detect, isolate, and neutralize advanced threats 
    2. Industrial Control Systems environments 
        Environments that are integrated hardware and software systems used for industrial processes.
    3. Sysmon and Modbus 
        * Sysmon - advanced monitoring tool from Microsoft's Sysinternals suite designed to provide in-depth visibility into Windows system activity
        * Modbus - is an application-layer messaging protocol used for client/server communication between devices in industrial automation systems. 
    4. MITRE ATT&CK ICS Mapping 
        4.1. MITRE ATT&CK® - (Adversarial Tactics, Techniques, and Common Knowledge) is a comprehensive, globally accessible knowledge base of  adversary behaviors based on real-world observations. 
        4.2. Mapping - MITRE ATT&CK Mapping is a process of aligning observed threat data, security controls, and defensive tools with the MITRE ATT&CK framework 

        **Thus**
             MITRE ATT&CK for ICS is a specialized, open-source framework mapping adversary behaviors specifically to Industrial Control Systems (ICS) and Operational Technology (OT) environments.

# What's the heck is that about, dfk? 
    Now, per keyword, actively searching for threats within Industrial Control Systems using Sysmon and Modbus and then aligning it to the MITRE ATT&CK Matrix for da "real-world" thing or something. 

# Timeline and Computing Power
    I am not smart, things will take time. 
    
    ## First Part: Environment Provisioning (Purdue Setup)
        Tasks
            [1] Deploy the ELK Stack, preferably with Docker 
            [2] Set Up a Windows VM to act as the Engineering Workstation (EWS)
            [3] Use ModbusPal to simulate a Programmable Logic Controller
            [4] With Sysmon on the EWS, configure Winlogbeat to ship the logs to ELK
    ## Second Part: Sysmon and Modbus Baseline 
        Tasks 
            [1] Use a security-hardened config and add specific inclusions for Modbus Related Tools and Ports 
            [2] Run your Modbus simulator and a legitimate Human Machine Interface. Make sure that I can see the Network Connection logs in Kibana 
            [3] Identify which MITRE ATT&CK ICS techniques correspond to your normal operations
    ## Third Part: Simulation 
        Tasks 
            [1] Use a python script to send a Force Single Coil Modbus command to the simulated PLC to shutdown a virtual something 
            [2] Map this to T0821 AND T0836
            [3] Confirm that Sysmon captured the Pythin execution and the network connection to port 502
    ## Fourth Part : Simulation 
        Tasks
            [1] Simulate an attacker moving from a compromised IT asset to the EWS. Use PowerShell to download a "malicious" script.
            [2] Map to T0812 (Default Credentials) or T0866 (Lateral Tool Transfer).
            [3] Create a Kibana dashboard showing Process Trees (Parent-Child relationships) to spot unusual PowerShell activity.
    ## Fifth Part: Threat Hunting
        Tasks
            [1] Write an EQL (Event Query Language) query in Kibana to find any process not in your "known good" list that is initiating connections on Port 502.
            [2] Pivot from the Network Log (ID 3) to the Process Creation log (ID 1) to find the file hash of the "attacker" script.
    ## Sixth Part : Advanced Mapping & Dashboarding
        Tasks 
            [1]: Use the Elastic Common Schema (ECS) to map your Sysmon logs directly to MITRE ATT&CK ICS IDs.
            [2] Build a "Heat Map" in Kibana. Every time a specific Sysmon Event ID triggers a match for a MITRE technique (e.g., unauthorized Registry modification ID 13 → T0851 Rootkit), it should light up your dashboard.
    ## Seventh Part : 
        Tasks 
            [1] Build a "Heat Map" in Kibana. Every time a specific Sysmon Event ID triggers a match for a MITRE technique (e.g., unauthorized Registry modification ID 13 → T0851 Rootkit), it should light up your dashboard.
            [2] Adjust your Sysmon config to automatically alert on the specific telemetry you used to catch the attack.

# Some Notes on the Tools 

