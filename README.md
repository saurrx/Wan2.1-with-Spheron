# Deploying Wan2.1 Text-to-Video Model on Spheron Network

Welcome to this repository! Here, you'll find a step-by-step guide to deploy the **Wan2.1 text-to-video (T2V)** model—specifically the lightweight **T2V-1.3B** variant—on **Spheron Network**, a decentralized GPU computing platform. Wan2.1, developed by Alibaba, generates high-quality videos from text prompts, and Spheron’s scalable infrastructure makes it an ideal environment for running such AI workloads. This guide uses a Jupyter notebook with GPU support to streamline the process.

## What’s This About?

### Wan2.1 Models: Open-source Video Generation Models
- **T2V-1.3B (Lightweight)**: Requires only 8.19 GB VRAM, generates 5-second 480P videos in ~4 minutes on consumer GPUs like the RTX 4090.
- **T2V-14B (Higher Quality)**: Requires ~24-26 GB VRAM for larger-scale deployments, supporting 480P/720P videos.

### Spheron Network
A decentralized platform offering on-demand GPU compute (e.g., RTX 4090, RTX 6000 Ada), perfect for AI tasks like video generation.

This setup combines Wan2.1’s accessibility with Spheron’s robust, censorship-resistant infrastructure, enabling you to create videos from text prompts efficiently.

## Prerequisites
Before diving in, ensure you have:

- **Spheron Account**: Sign up at [Spheron Network](https://www.spheron.network/) and purchase credits to access compute resources.
- **GPU Requirements**: 
  - At least 1 GPU with 24 GB VRAM (e.g., RTX 4090) for T2V-1.3B.
  - For T2V-14B, aim for ~24-26 GB total VRAM across multiple GPUs.
- **Software**: Python 3.11, PyTorch >= 2.4.0, CUDA 12.6+ (pre-installed in Spheron’s Jupyter image).

## Setup Instructions

### Step 1: Deploy the Jupyter Notebook on Spheron

#### Via Spheron Console
1. Log in to [console.spheron.network](http://console.spheron.network).
2. Create a new instance, select the `jupyter/notebook` image:
3. Deploy and note the URL (e.g., `https://<your-id>.spheron.app:8888`) and access token.

#### Via Spheron CLI
1. Install the CLI: `npm install -g @spheron/cli`.(detailed guide here : [https://docs.spheron.network/user-guide/protocol-cli](https://docs.spheron.network/user-guide/protocol-cli)
3. Use the following ([jupyter.yml](jupyter.yml)) adjusting GPU and storage as needed:
4. Run sphnctl deploy deploy.yaml and note the URL/token.

### Step 2: Import and Configure the Notebook
1. Open your Jupyter instance (e.g., https://<your-id>.spheron.app:8888) and log in with the token.
2. Go to File > Open from URL and paste this notebook URL: [[https://raw.githubusercontent.com/saurrx/Wan2.1-with-Spheron/refs/heads/main/main.ipynb]([url](https://raw.githubusercontent.com/saurrx/Wan2.1-with-Spheron/refs/heads/main/main.ipynb))].
3. The notebook includes scripts to:
   Clone the Wan2.1 repo.
   Install dependencies.
   Download T2V-1.3B weights from Hugging Face.

### Step 3: Run the Model
1. Execute each notebook cell step-by-step.
2. In the final cell, enter your text prompt.
3. Run the cell to generate a 5-second 480P video (expect ~4 minutes processing time).

### Example Output
Prompt: "Two anthropomorphic cats in boxing gear fighting on a stage."
Result: A 5-second 480P video showing animated cats sparring, rendered in ~4 minutes on an RTX 4090.

## Why Use This?
1. Wan2.1: Outperforms many closed-source models and runs on consumer hardware.
2. Spheron: Decentralized, scalable, and cost-effective GPU access without local setup hassle.









