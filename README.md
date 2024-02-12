# Machine Learning Plugin for Snort3 Intrusion Detection System

## [CICFlowMeter](https://www.unb.ca/cic/research/applications.html#CICFlowMeter) 

A tool used to generate the CIC-IDS2017 dataset. Takes an input pcap or network interface and outputs csv containing 80 features related to network flow statistics.

Depends on a depricated jnetpcap java app, need to build in an environment with correct dependencies.

## [Dataset CIC-IDS2017](https://www.unb.ca/cic/datasets/ids-2017.html)

PCAPs as well as CSVs containing labeled data (CICFlowMeter output)

5 seperate days of network traffic, contains a mix of known exploits and benign. Orginal dataset is about ~10GB of pcap per day, use a reduced sample for training

|Label||
|---|---|
|BENIGN|22731|
|DoS|19035|
|PortScan|7946|
|BruteForce|2767|
|WebAttack|2180|
|Bot|1966|
|Infiltration |36|

## Machine Learning Model

Forked from [Western-OC2-Lab/Intrusion-Detection-System-Using-Machine-Learning](https://github.com/Western-OC2-Lab/Intrusion-Detection-System-Using-Machine-Learning)

### Signiture Detection
| | |
|-|-|
|Accuracy of XGBoost|0.9955555555555555|
|Precision of XGBoost|0.9957643745143745|
|Recall of XGBoost|0.9955555555555555|
|F1-score of XGBoost|0.9954610536001841|

| |precision|recall|f1-score|support|
|---|---|---|---|---|
|0|0.95|0.88|0.91|24|
|1|1.00|1.00|1.00|394|
|2|1.00|0.75|0.86|4|
|3|0.92|1.00|0.96|24|
|4|0.88|1.00|0.93|7|
|5|1.00|1.00|1.00|11|
|6|1.00|1.00|1.00|436|
| | | | |
|accuracy|    |    |1.00|900|
|macro avg|0.96|0.95|0.95|900|
|weighted avg|1.00|1.00|1.00|900|

![Signiture Confusion Matrix](https://github.com/AlexPerrin/snort3_ml/blob/main/figures/sig.png?raw=true)

### Anomoly Detection

| |precision|recall|f1-score|support|
|---|---|---|---|---|
|0|0.00|0.00|0.00|8|
|1|0.88|1.00|0.93|56|
| | | | |
|accuracy| | |0.88|64|
|macro avg|0.44|0.50|0.47|64|
|weighted avg|0.77|0.88|0.82|64|

0.875

[0, 8]

[0, 56]

## Snort Plugin

Snort defines a plugins API
https://www.snort.org/downloads/snortplus/snort_devel.html