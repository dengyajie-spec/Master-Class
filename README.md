# Learning and Research on Audio-Driven Facial Animation

This project is divided into two parts：

1.Unitalker Parameter Comparison Experiment ( Research-oriented Development )

2.UE5 Interactive Project Synthesis Based on MHC-Talker( Product-oriented Applied Research )

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

   python -m main.train --config config/unitalker.yaml

   (4) ​​Generate Test Data

   python -m main.demo --test_out_path ./test_results1/demo.npz

   (5) Render Facial Animation

   python -m main.render ./test_results1/demo.npz ./test_audios ./test_results/

### 1.3 ​​Visual Results Comparison​


<!-- 固定宽度（高度自适应） -->
<img src="https://github.com/user-attachments/assets/1fdb86bd-1249-4bc2-9d89-2f3907ca9641" width="300px">

<!--  固定宽度（高度自适应 -->
<img src="https://github.com/user-attachments/assets/19f9ebca-fccf-4bc5-89ef-a10bd51e9af3" width="300px">


## 2. UE5 Interactive Project Synthesis Based on MHC-Talker


