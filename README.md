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

### 1.2 Model Training​ and Parameter Optimization

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
### 1.3 Organizing Data
During the training of the second group of models, all data related to the loss function have been saved along with the model in the train.log file under the results folder. We run the experiment-analysis（in the experiment_analysis folder on GitHub）.ipynb file, and the generated data plots are stored in the experiment_analysis folder.
<img width="2066" height="244" alt="experiment_summary" src="https://github.com/user-attachments/assets/a2d51991-676f-45cb-83f0-311cc59f38d7" />

<img width="3000" height="1800" alt="convergence_speed" src="https://github.com/user-attachments/assets/0ae71ea7-f843-4dda-99fb-d2dda2d509a2" />

<img width="3600" height="2400" alt="loss_comparison" src="https://github.com/user-attachments/assets/503ddb95-6676-4757-a0b5-ec62f2aee3ad" />

<img width="3600" height="3600" alt="lve_lvd_comparison" src="https://github.com/user-attachments/assets/24e1b7eb-d357-421a-b89a-2f9ab3afa377" />

### 1.4 ​​Visual Results Comparison​


<!-- 固定宽度（高度自适应） -->
<img width="904" height="375" alt="KNO2{$11OHSZ{J9)LT`FYYT" src="https://github.com/user-attachments/assets/5e98f67c-c509-4753-adcd-dab8a36c1d0d" />

<!--  固定宽度（高度自适应 -->
<img width="909" height="373" alt="DYQ~X3I8}($CJ)VU%613_Z5" src="https://github.com/user-attachments/assets/53ca65ea-d525-48be-a07d-f679ab444811" />


​​Visual Comparison Results:​​

Under identical speech input, the two models show only subtle differences. During prolonged speech sequences, ​​our trained model demonstrates more natural eye-blinking frequencies​​ that better approximate human behavior.

For more detailed visual comparisons, please refer to the test videos included in this project.


























