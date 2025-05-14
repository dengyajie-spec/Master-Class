# Learning and Research on Audio-Driven Facial Animation

This project is divided into two parts：

1.Unitalker Parameter Comparison Experiment ( Research-oriented Development )

2.UE5 Interactive Project Synthesis Based on MHC-Talker( Product-oriented Applied Research )

## 1. Unitalker Parameter Comparison Experiment

**Experimental Purpose**  
UniTalker is designed to generate realistic facial animations from speech input, enabling natural lip-sync and expressive facial movements for virtual avatars.

**Methodology**  
- Employs transformer-based neural networks  
- Processes both speech features and emotion cues  
- Outputs synchronized 3D facial mesh animations  

**Datasets**  
- Main: VOCASET (speech-animation pairs)  
- Supplementary: BIWI (emotional expressions)  
- Custom D7 dataset (enhanced emotional variations)  

The framework achieves real-time performance while maintaining high visual quality.

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


## 2. UE5 Interactive Project Synthesis Based on MHC-Talker


