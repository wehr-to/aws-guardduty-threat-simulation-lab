🛡️ AWS GuardDuty Threat Simulation Lab
Simulated cloud security incidents to evaluate AWS GuardDuty's threat detection and alerting pipeline — using best practices, mock architecture diagrams, and documented steps to recreate unauthorized API access and abnormal user activity. Built to strengthen cloud security skills and validate automated detection and response workflows.

📌 Overview
This project explores the real-world effectiveness of AWS GuardDuty in detecting suspicious activity in a controlled AWS environment. By simulating unauthorized API calls, privilege escalation attempts, and abnormal behavior, the goal was to test how GuardDuty responds, triggers alerts, and integrates with automated workflows (SNS, Lambda, Slack).

This lab is fully mocked, sanitized, and intended for educational purposes only.

🧠 Objectives
Understand how AWS GuardDuty detects real-time threats
Simulate unauthorized API calls and IAM misuse
Configure automated alerting via SNS, Lambda, and Slack
Document the detection and response process
Evaluate GuardDuty's limitations and behavior

                +------------------------+
                |    Simulated IAM User  |
                |   (Unauthorized Role)  |
                +----------+-------------+
                           |
            +--------------v----------------+
            |    AWS CloudTrail + Config     |
            | (Logs API calls, role changes) |
            +--------------+-----------------+
                           |
                +----------v-----------+
                |     AWS GuardDuty    |
                | (Detects abnormal    |
                |  API activity)       |
                +----------+-----------+
                           |
                     +-----v-----+
                     |   SNS     |
                     | Topic     |
                     +-----+-----+
                           |
                    +------v------+
                    |   Lambda     |
                    | Alert Logic  |
                    +------+-------+
                           |
                     +-----v-----+
                     |   Slack   |
                     | Webhook   |
                     +-----------+
🔬 Simulated Threat Scenarios
Unauthorized API calls using limited IAM user
Attempted deactivation of logging
Role escalation attempt
Login attempts from unfamiliar geolocations (via scripted credentials)

🧪 Detection & Response Pipeline
GuardDuty Findings triggered by simulated behavior
SNS Topic receives finding notification
Lambda Function parses finding, formats alert
Slack Webhook sends alert to a security channel
Validation Check confirms log source and timestamp match

⚠️ Challenges & Lessons Learned
Not all simulated behavior triggers GuardDuty — must align with known detection patterns
IAM simulation required careful permission tuning to avoid false positives
Timing and region specificity mattered for geo-based detections
SNS > Lambda > Slack works, but parsing findings for clarity is crucial

📚 Future Enhancements
Integrate with AWS Security Hub for aggregation
Add Athena + CloudTrail query tooling for enrichment
Expand to simulate malicious EC2 behavior
Build a custom detection engine using Python + Lambda

📝 Disclaimer
This lab is for educational and portfolio-building purposes only.
No real AWS credentials, users, or sensitive resources were used or exposed.
