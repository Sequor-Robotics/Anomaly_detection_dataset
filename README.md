# Anomaly detection dataset

This repository consists of processed dataset for anomaly detection for robots in warehouse environments.

Training/Evaluation pipeline is available at this [repository](https://github.com/Sequor-Robotics/Anomaly_detection.git).


### Dataset structure / Scenario Taxonomy

Generally, the dataset consists of two types: Expert and Negative.

Expert data, which starts with prefix 'E', includes three scenarios: safe straight/curve driving, escaping dynamic obstacle approaching straight, and escaping crossing dynamic obstacle.

Negative data, which starts with prefix 'N', includes six scenarios: straight/curve driving near static obstacles, jerky driving, crashing to wall, crashing to dynamic obstacle approaching straight, crashing to crossing dynamic obstacle, and dangerous escape from crossing dynamic obstacle.

Table below describes the structure and the composition of this dataset.

|Type|Scenario|Scenario ID|# trials|distance [m]|
|:---:|:---:|:---:|:---:|:---:|
|Expert|straight/curve|E1|30|7019.5465|
|Expert|safe escape straight|E2|20|53.2734|
|Expert|safe escape cross|E3|40|139.1526|
|Negative|straight/curve near static obstacles|N1|15|3003.0405|
|Negative|jerky driving|N2|6|126.2155|
|Negative|crash wall|N3|38|38.7153|
|Negative|crash straight|N4|40|53.2434|
|Negative|crash cross|N5|40|58.3411|
|Negative|unsafe escape cross|N6|36|193.5397|


Expert 1, 2, 3

<img src="./assets/E1_clip.gif" height="200">
<img src="./assets/E2_clip.gif" height="200">
<img src="./assets/E3_clip.gif" height="200"> <br>

Negative 1, 4, 5, 6

<img src="./assets/N1_clip.gif" height="207">
<img src="./assets/N4_clip.gif" height="207">
<img src="./assets/N5_clip.gif" height="207">
<img src="./assets/N6_clip.gif" height="207">



### Definition of state-action

`(scenario ID)_(trian no.).json` data file contains processed data at each time $t$. Sampling rate during collection was 10Hz. Action must be defined for MDN (Mixture Density Network) training, and it is specified as below. $v, a, \omega, p^{\mathrm{obj}}$, and $d$ denote linear velocity, linear acceleration, angular velocity, position of dynamic obstacle, and lidar 2D laser scan points, respectively. During training, $k$ frame data is concatenated to construct input vector, thereby $k$ refers to the length of time window.

$$
\mathbf{s}_t :=
\begin{bmatrix}
v_t \\
a_t \\
\omega_t \\
p_t^{\mathrm{obj}} \\
d_t
\end{bmatrix} \in \mathbb{R}^{135}
\qquad
\mathbf{a}_t :=
\begin{bmatrix}
a_t \\
\omega_t
\end{bmatrix} \in \mathbb{R}^{3}
$$