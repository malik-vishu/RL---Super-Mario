# 🍄 Mario Bros Atari — Double DQN Agent (Extended Documentation)

## 📘 Overview
This repository contains a complete, production-ready **Double Deep Q-Network (DDQN)** agent trained to play **Mario Bros (Atari 2600)** from raw pixels.  
It includes:
- Atari preprocessing  
- Double DQN update logic  
- Replay buffer  
- Warmup phase  
- Checkpointing + auto resume  
- Logging  
- Evaluation loops  

---

## ✨ Features (Detailed)

### 🧠 Double DQN
Solves overestimation bias by:
- Using *online network* to select action (argmax)
- Using *target network* to evaluate that action

### 🖼 Atari Preprocessing
- Convert to grayscale  
- Resize to 84×84  
- Stack 4 frames (velocity awareness)

### 🧩 Nature CNN Architecture
```
Conv2d → ReLU  
Conv2d → ReLU  
Conv2d → ReLU  
Flatten  
FC 512 → ReLU  
FC → Q-values
```

### 🎮 Action Space
```
[0, 2, 3, 4, 7]
NOOP, UP, RIGHT, LEFT, JUMP
```

---

## 🚀 Quick Start

### Install dependencies
```bash
pip install torch torchvision numpy gymnasium "gymnasium[accept-rom-license]" ale-py opencv-python

OR

pip install -r requirements.txt
```


### Resume training
Start it again — it auto-loads latest checkpoint.

---

## 📊 Evaluation
The script automatically evaluates every N episodes and logs:
- mean steps
- per-episode performance

---

## 🔧 Troubleshooting

### ❗ “ROM Missing”
Install using:
```
pip install "gymnasium[accept-rom-license]"
```