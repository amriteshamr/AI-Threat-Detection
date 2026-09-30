### A machine learning project for detecting Distributed Denial-of-Service (DDoS) network traffic using a Random Forest classifier.

The model classifies network flows into two categories:

BENIGN — legitimate network traffic

DDoS — Distributed Denial-of-Service traffic

##Dataset - Network Intrusion dataset(CIC-IDS- 2017)

Source - Kaggle
The dataset contains network-flow statistics extracted from network traffic.

After loading the dataset:

Rows: 225,745

Columns: 79

Input features: 78

Target: Label

Problem type: Binary classification

Example features include:

Destination Port
Flow Duration
Total Fwd Packets
Total Backward Packets
Flow Bytes/s
Flow Packets/s
Fwd Packet Length Max
Fwd Packet Length Mean
Packet Length Mean
Init_Win_bytes_forward
Init_Win_bytes_backward
Subflow Fwd Bytes
Average Packet Size
