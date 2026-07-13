# Craters-Exploration 1: Autonomous Crater Detection Using YOLOv8

Hey everyone! This is a project I built to solve a specific problem for space exploration companies: how can we automatically, quickly, and accurately identify and map impact craters from satellite images? While I trained this version using Martian surface imagery, the underlying logic can be adapted to pretty much any planetary or lunar surface. 

---

## The Big Picture: Why This Project Matters

If you look at traditional space exploration or planetary mapping, scientists have historically relied on basic geometry tricks (like Hough Transforms) to detect craters. Those algorithms basically hunt for perfect geometric circles. 

But out in the real world—especially on Mars—craters are rarely perfect circles. They are eroded by wind, partially buried under dust, warped by terrain slopes, or overlapping on top of each other. Traditional math-based tools completely fail here. 

That is why I wanted to build an AI-driven approach. By using a convolutional neural network, the system doesn't just look for circles; it learns to recognize actual geological textures, depth shadows, and the subtle, weathered rims of ancient craters. 

---

## What Did I Use? (The Tech Stack)

I wanted this pipeline to be robust but efficient, so I put together a workflow using tools that complement each other:

* **Roboflow:** I used Roboflow to host, organize, and manage my dataset of 148 high-resolution Martian surface tiles. It made it seamless to feed clean, formatted data directly into my training loop.
* **YOLOv8-Medium Architecture (`yolov8m.pt`):** When picking an AI model, you usually have to choose between tiny/fast models or massive/slow ones. I intentionally chose the **Medium** variant of YOLOv8. It strikes a perfect balance: it’s deep enough to catch complex surface variations and shadows, but lightweight enough that it doesn't require a supercomputer to run.
* **Ultralytics & Python:** The entire training script was built in Python using the Ultralytics framework, running for 50 epochs at a standard `imgsz=640` resolution.

---

## How Is This Better Than Other Models?

If you search online, you'll find plenty of crater detection projects, but this implementation has a few distinct advantages:

### 1. Optimized for Edge Deployment (Rover-Ready)
Many research papers use massive, heavy neural networks that take seconds to process a single image. That is useless if you want to put the AI on a physical rover or an autonomous lander. Because this project utilizes YOLOv8m, it processes high-resolution satellite frames in just milliseconds. It proves that real-time hazard avoidance and live mapping are completely possible on low-power, onboard spacecraft computers.

### 2. High Efficiency with a Compact Dataset
Training an object detection model usually requires thousands of images to get decent results. By using a pre-trained YOLOv8 architecture and fine-tuning it specifically for planetary geology, this model achieved a solid **Precision of 64.0%** and an **mAP@50 of 65.8%** using a compact dataset of just 148 training images. It proves you don't need millions of data points to get a smart, functional computer vision system up and running.

### 3. Texture over Geometry
Unlike standard circle-finding algorithms, this model doesn't get confused by irregular shapes or broken crater walls. Because it looks at shadow depth and landscape textures, it can successfully flag ancient, heavily eroded craters that traditional software completely misses.

---

## Future Updates & Optimization Plans

This is officially version 1.0! It’s an active project, and I plan to keep tweaking it over time. My immediate goals for the next version are:
* Expanding the dataset with more diverse surface imagery (including lunar data) to help the model generalize even better.
* Fine-tuning the confidence thresholds to completely eliminate minor false positives from random sand dunes or surface ripples.

---

## Contact & Live Demo

Feel free to check out the code, fork the repository, or reach out if you want to chat about computer vision or space tech!

* **Developed by:** Sadhvik Kamal Y.
* **Email:** ysadhvik555@gmail.com
* **Live Sandbox:** [Test my model interactively on Roboflow Universe](https://universe.roboflow.com/sadhviks-workspace/craters-exploration/model/1)
