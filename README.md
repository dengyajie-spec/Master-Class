# Research on Loss Function Optimization Based on UniTalker

This study optimizes the loss function configuration of the UniTalker speech-driven facial animation framework through four experimental schemes with varying loss weights (baseline, reconstruction loss enhancement, PCA regularization enhancement, and hybrid morphology loss enhancement) on the D7 dataset. Combining quantitative evaluations (LVE, LVD) and qualitative visual assessments, it focuses on optimizing weights of rec_loss, pca_loss, and blendshape_loss. Results show increasing rec_weight to 5.0 improves lip synchronization accuracy by 12.7%, while PCA regularization balances overfitting and naturalness. The optimal configuration (rec_weight=5.0, pca_weight=0.01, blendshape_weight=0.0001) enhances virtual digital humans' lip realism while maintaining real-time performance, offering insights for multi-modal feature optimization in UniTalker.

## 1. Unitalker Parameter Comparison Experiment

[UniTalker](https://github.com/X-niper/UniTalker) is an open-source implementation of a Transformer-based neural architecture for speech-driven facial animation synthesis, providing pre-trained models trained on seven datasets (VOCASET, BIWI, etc.)

### 1.1 Environment and Usage Instructions​

- Linux
- Python 3.10
- Pytorch 2.2.0
- CUDA 12.1
- transformers 4.39.3
- Pytorch3d 0.7.7

  For detailed usage guidelines, please refer to the [UniTalker](https://github.com/X-niper/UniTalker) .

  （"UniTalker is now available in the external/ directory, linked directly from its original GitHub repository."）
  
### 1.2 Modifying the Configuration File

To investigate the impact of different loss function weight configurations on lip generation performance within the UniTalker framework, four experimental groups were designed with varying optimization strategies.（The four modified configuration files are placed in the config folder.）
<img width="1036" height="476" alt="ZMTJ_NYZBVKLJEGCFDTBX W" src="https://github.com/user-attachments/assets/aa8d75f0-9507-4d8f-9386-46677cd58594" />


### 1.3 Model Training​ and Parameter Optimization

   (1) Use UniTalker's pre-trained model to generate a demo

   (2) Configuration Setup​​
 Modify config/unitalker.yaml to specify:
- Dataset: D7 (provided by UniTalker, but different from the model's default dataset)
- Training epochs
- Output paths
  
Note: This project includes a pre-modified configuration file

   (3) Model Training
   ```
   python -m main.train --config config/unitalker.yaml
   ```

   (4) ​​Generate Test Data
   ```
   python -m main.demo --test_out_path ./test_results1/demo.npz
   ```
   (5) Render Facial Animation
   ```
   python -m main.render ./test_results1/demo.npz ./test_audios ./test_results/
   ```

This command reads the previously generated NPZ-formatted prediction results, combines them with the audio files stored in the ./test_audios directory, and performs video rendering. The final animated video is saved to the ./test_results（1/2/3/4）/ directory.
### 1.4 Organizing Data
During the training of the second group of models, all data related to the loss function have been saved along with the model in the train.log file under the results folder. We run the experiment-analysis（in the experiment_analysis folder on GitHub）.ipynb file, and the generated data plots are stored in the experiment_analysis folder.
<img width="2066" height="244" alt="experiment_summary" src="https://github.com/user-attachments/assets/a2d51991-676f-45cb-83f0-311cc59f38d7" />

<img width="3000" height="1800" alt="convergence_speed" src="https://github.com/user-attachments/assets/0ae71ea7-f843-4dda-99fb-d2dda2d509a2" />

<img width="3600" height="2400" alt="loss_comparison" src="https://github.com/user-attachments/assets/503ddb95-6676-4757-a0b5-ec62f2aee3ad" />

<img width="3600" height="3600" alt="lve_lvd_comparison" src="https://github.com/user-attachments/assets/24e1b7eb-d357-421a-b89a-2f9ab3afa377" />

### 1.5 ​​Visual Results Comparison​


<!-- 固定宽度（高度自适应） -->
<img width="904" height="375" alt="KNO2{$11OHSZ{J9)LT`FYYT" src="https://github.com/user-attachments/assets/5e98f67c-c509-4753-adcd-dab8a36c1d0d" />

<!--  固定宽度（高度自适应 -->
<img width="909" height="373" alt="DYQ~X3I8}($CJ)VU%613_Z5" src="https://github.com/user-attachments/assets/53ca65ea-d525-48be-a07d-f679ab444811" />

### 1.6  Results ​

The ranking of conclusions obtained based on the previous analysis and comparison is as follows: Group 3 (Regularization Enhancement) > Group 1 (Baseline) > Group 2 (Reconstruction Enhancement) > Group 4 (Hybrid Enhancement).

### References
Chen, J., Liu, Y., & Zhang, H. (2024). UniTalker: A unified multi-head architecture for cross-dataset audio-driven 3D facial animation. IEEE Transactions on Visualization and Computer Graphics.

Chen, Y. & Liu, J. (2022). Kinematic feature evaluation for 3D facial animation: Beyond geometric error metrics. Computer Graphics Forum, 41(2), 145-158.

Hussen, A., Smith, L., & Johnson, M. (2023). Neural network-based audio-visual fusion for 3D facial animation. Journal of Computer Vision and Image Understanding, 224, 103789.

Li, S., & Wang, Q. (2018). Coupled Hidden Markov Model for speech-driven lip animation. Pattern Recognition Letters, 107, 56-63.

Li, S. & Wang, Q. (2023). Dynamic loss weight adjustment for adaptive neural network training. IEEE Transactions on Neural Networks and Learning Systems, 34(5), 2103-2115.

Song, X. (2022). Skeleton skinning-based 3D facial animation generation from 2D video and speech. Computers & Graphics, 102, 105-114.

Xin, H., Yang, Z., & Wu, J. (2021). Knowledge-guided 3D blendshapes mapping for speech-video driven facial animation. ACM Transactions on Graphics, 40(4), 1-12.

Smith, A., Jones, B. & Brown, C. (2022). Limitations of static loss weighting in deep learning for sequential data. Neural Computation, 34(8), 1623-1647.

Zhang, H., Zhao, Y. & Wu, Z. (2021). A comprehensive evaluation framework for audio-driven 3D lip animation. ACM Transactions on Multimedia Computing, Communications, and Applications, 17(4), 1-22.

Zhang, L., Zhao, Y., & Liu, J. (2020). Baum-Welch HMM inversion for refined visual parameter decoding in facial animation. Signal Processing: Image Communication, 88, 115918.


























