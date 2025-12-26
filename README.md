# Anomaly detection dataset

This repository consists of processed dataset for anomaly detection for robots in warehouse environments.

Training/Evaluation pipeline is available at this [repository]().


### Dataset structure / Scenario Taxonomy

Generally, the dataset consists of two types: Expert and Negative.

Expert data, which starts with prefix 'E', includes three scenarios: safe straight/curve driving, escaping dynamic obstacle approaching straight, and escaping crossing dynamic obstacle.

Negative data, which starts with prefix 'N', includes six scenarios: straight/curve driving near static obstacles, jerky driving, crashing to wall, crashing to dynamic obstacle approaching straight, crashing to crossing dynamic obstacle, and dangerous escape from crossing dynamic obstacle.

Table below describes the structure and the composition of this dataset.
