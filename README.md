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
### 1.3 ​​Visual Results Comparison​


<!-- 固定宽度（高度自适应） -->
<img src="https://github.com/user-attachments/assets/1fdb86bd-1249-4bc2-9d89-2f3907ca9641" width="300px">

<!--  固定宽度（高度自适应 -->
<img src="https://github.com/user-attachments/assets/19f9ebca-fccf-4bc5-89ef-a10bd51e9af3" width="300px">


​​Visual Comparison Results:​​

Under identical speech input, the two models show only subtle differences. During prolonged speech sequences, ​​our trained model demonstrates more natural eye-blinking frequencies​​ that better approximate human behavior.

For more detailed visual comparisons, please refer to the test videos included in this project.


## 2. UE5 Interactive Project Synthesis Based on MHC-Talker

This project integrates MHC-Talker and MetaHuman technologies. Below is the implementation workflow.

### 2.1 ​Download and Installation of MHC_Talker

(1) Apply for Usage Permission

Go to [Bilibili](https://space.bilibili.com/XXXXXX), find YX-Interact's official account, send an application to obtain the download link and Token code.

(2) Installation

- After downloading the plugin, unzip it and place the MHC_Talker folder into the Plugins directory of your project (if the folder does not exist, manually create a Plugins folder).
- Copy the following code and paste it at the bottom of the DefaultEngine.ini file in the Config directory of your UE project:
```
  [Voice]  
bEnabled=true  

[SystemSettings]  
voice.SilenceDetectionThreshold=0.01  
voice.MicNoiseGateThreshold=0.01  

[/Script/Engine.GarbageCollectionSettings]  
gc.MaxObjectsInGame=25165824  
```
(3) Enable the Plugin

- Open the plugin panel, check whether the MHC_Talker plugin is ticked.
- Find MHC_Talker in the plugin bar and enter the Token code to complete the activation.

Note: For detailed installation steps, please refer to the [MHC-Talker Installation Guide](https://yx-interact.yuque.com/org-wiki-yx-interact-pfv67o/mhc/tv9zrfpl16nzk61v).

### 2.2 Creating a MetaHuman Digital Human

(1) Create a New Project and Material

- Start a new project and create a folder. Import a facial photo into this folder.
- Create a material, double-click to open it, drag the photo into the material editor, link it to the Self-Illumination node, and save the material.

<img src="https://github.com/user-attachments/assets/991b9da3-63ec-4b2e-9ba1-a997c5cbe8fb" width="300px">  
(2) Apply Material to a Cube

- Create a cube and drag it into the folder.
- Open the cube's settings, drag the material created in Step 1 into the cube's material slot to apply it.

<img src="https://github.com/user-attachments/assets/991b9da3-63ec-4b2e-9ba1-a997c5cbe8fb" width="300px">  

(3) Use MetaHuman Plugin for Tracking

- Activate the MetaHuman plugin and create a MetaHuman instance.
- Click on the Components in the mesh settings and select the cube created in Step 2.
- Align one front face of the cube with the screen. First, click Advance Frame at the top, then enable Auto-Track in the lower Frame window.

<img src="https://github.com/user-attachments/assets/1d9c3b11-5fac-4227-a4fd-463e29cc9b5f" width="300px">  

(4) Solve and Preview the Model

- After correctly identifying the mouth and eyes, click Solve on the MetaHuman instance.
- Switch the viewport to preview the generated model.

<img src="https://github.com/user-attachments/assets/519b6660-3fcb-4e8a-bbf0-ce56c716bd81" width="300px">  

(5) Convert Mesh to MetaHuman

- Once the model is confirmed to be correct, select a body model.
- Convert the mesh to a MetaHuman model through the plugin.

<img src="https://github.com/user-attachments/assets/7b8bf52f-5cb1-4bef-969d-098342102632" width="300px">

(6) Add Details on MetaHuman Website

- After the mesh conversion is complete, log in to the MetaHuman Official Website.
- Select the newly generated character model and use the website’s features to add clothing and details.

<img src="https://github.com/user-attachments/assets/9965764d-1bb2-4969-914d-1459fb2e86a1" width="300px">

### 2.3 Project Integration

After opening UE5 and importing the MetaHuman model, select the MetaHuman-standard character blueprint, right-click → Scripted Asset Actions → Spawn MHC Talker.

<img src="https://github.com/user-attachments/assets/7de78277-e404-482b-871c-fc26d55071ca" width="300px">

<img src="https://github.com/user-attachments/assets/ef13a9d2-be6f-413d-b4c6-f913ec600fc9" width="300px">

## refs

@article{huang2024midi,
title={MIDI: Multi-Instance Diffusion for Single Image to 3D Scene Generation},
author={Huang, Zehuan and Guo, Yuanchen and An, Xingqiao and Yang, Yunhan and Li, Yangguang and Zou, Zixin and Liang, Ding and Liu, Xihui and Cao, Yanpei and Sheng, Lu},
journal={arXiv preprint arXiv:2412.03558},
year={2024}
}























