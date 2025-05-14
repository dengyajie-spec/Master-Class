# Learning and Research on Audio-Driven Facial Animation

This project is divided into two parts：

1.Unitalker Parameter Comparison Experiment ( Research-oriented Development )

2.UE5 Interactive Project Synthesis Based on MHC-Talker( Product-oriented Applied Research )

## 1. Unitalker Parameter Comparison Experiment

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

   (3)


## 2. UE5 Interactive Project Synthesis Based on MHC-Talker


