# splunk-ssh-bruteforce-detection
A Splunk SIEM project where I ingested Linux authentication logs using Splunk Universal Forwarder and built detection logic for SSH brute-force attacks using Event Types, risk-based classifications, and visual dashboards.

🛡️ Splunk SSH Brute Force Detection – Mini SIEM Project
📌 Project Overview

This project demonstrates how to use Splunk Enterprise and Splunk Universal Forwarder to detect and classify SSH brute-force attempts on a Linux system.
It covers log collection, normalization, event filtering, and threat classification.

🔥 Features
✔️ 1. Linux Log Forwarding (Universal Forwarder)

Configured Splunk Universal Forwarder on Kali Linux

Enabled persistent journald logging

Forwarded /var/log/auth.log to Splunk Enterprise running on Windows

Verified ingestion using:

index=* host="kali"

✔️ 2. SSH Failed Login Classification

Created two custom Event Types to separate low-risk vs. high-risk SSH brute-force attempts.

🔵 Event Type 1 – Less Risky (Priority 8)

Name: less_risky_invalid_user
Search:

"Failed password for invalid user"


Meaning: Automated bots guessing random usernames.

🔴 Event Type 2 – High Risky (Priority 3)

Name: high_risk_valid_user
Search:

"Failed password" NOT "invalid user"


Meaning: Real attack attempts against existing Linux accounts.

✔️ 3. Splunk Searches Used
index=* "Failed password" host="kali"


Low-risk only:

"Failed password for invalid user"


High-risk only:

"Failed password" NOT "invalid user"

🖼️ Screenshots

Log ingestion

Splunk search results

Event type configuration

Priority tags (3 & 8)


📁 Project Structure
/screenshots
/README.md
/SPLUNK_EVENT_TYPE_PROJECT_REPORT.pdf

🎓 What I Learned

How SIEM ingestion works end-to-end

How to parse Linux SSH authentication logs

How event types and priorities help reduce alert fatigue

Distinguishing bot noise vs. real attack attempts

Why SOC analysts rely heavily on Splunk for rapid triage

🛠️ Tools Used

Splunk Enterprise

Splunk Universal Forwarder

Kali Linux

Journalctl / rsyslog

SSH client

⭐ Conclusion

This project helped me understand real-world SIEM workflows and how to transform raw system logs into actionable threat intelligence.

If you’re learning Splunk or Blue Team skills — this is a great starting point!
