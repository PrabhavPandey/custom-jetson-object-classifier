
![banner](https://i.postimg.cc/h43rKzPC/banner.png)
## 💡About The Project

![working demo]()

Real-time defect detection system for bottle manufacturing quality control implemented on NVIDIA Jetson Nano. Uses MobileNet-SSD model custom trained on 172 images.

Built as our final year B.Tech project.

[Project Presentation Link](https://www.canva.com/design/DAGXYtXBucs/t_LgQQETgELRulF6xo6lvw/edit?utm_content=DAGXYtXBucs&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

### 📚Resources Used

- [Jetson Inference Repo](https://github.com/dusty-nv/jetson-inference)
- [Jetson AI Fundamentals YouTube Playlist](https://www.youtube.com/watch?v=QXIwdsyK7Rw&t=840s)

### 🏃‍♂️Usage

1. Clone the `jetson-inference` repo from the link above onto your Jetson Nano.

2. Train the mobilenet model using camera capture. Good practice to manually take ~100 pictures of each classification type.

![working demo](https://i.postimg.cc/cL5hLvm1/training.png)

Save it to the `models/bottles` directory.

3. Run the model.

```bash
python3 train.ssd.py --dataset-type=voc --data=data/bottles --model-dir=models/bottles --batch-size=2 --workers=1 --epochs=20
```

4. Export the custom model created.

```bash
python3 onnx_export.py --model-dir=models/bottles
```

5. Run the model on the video input `video0`.

```bash
detectnet --model=models/bottles/ssd-mobilenet.onnx --labels=models/bottles/labels.txt --input-blob=input_® --output-cvg=scores --output-bbox=boxes /dev/video0
```

6. No more defects passing through!


## ✒️Authors

- [Mehardeep Singh](https://github.com/PurpleBooth)
- [Prabhav Pandey](https://github.com/PrabhavPandey)

- [Prof. Aakash Sinha (Mentor)](https://www.linkedin.com/in/aakashsinha/)
