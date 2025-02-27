Deploying Wan2.1 Text-to-Video Model on Spheron Network
Welcome to this repository! Here, you'll find a step-by-step guide to deploy the Wan2.1 text-to-video (T2V) model—specifically the lightweight T2V-1.3B variant—on Spheron Network, a decentralized GPU computing platform. Wan2.1, developed by Alibaba, generates high-quality videos from text prompts, and Spheron’s scalable infrastructure makes it an ideal environment for running such AI workloads. This guide uses a Jupyter notebook with GPU support to streamline the process.
What’s This About?
Wan2.1 T2V Models: Open-source video generation models with two key variants:
T2V-1.3B: Lightweight, needs only 8.19 GB VRAM, generates 5-second 480P videos in ~4 minutes on consumer GPUs like the RTX 4090.

T2V-14B: Higher quality (480P/720P), requires ~24-26 GB VRAM for larger-scale deployments.

Spheron Network: A decentralized platform offering on-demand GPU compute (e.g., RTX 4090, RTX 6000 Ada), perfect for AI tasks like video generation.

This setup combines Wan2.1’s accessibility with Spheron’s robust, censorship-resistant infrastructure, enabling you to create videos from text prompts efficiently.
Prerequisites
Before diving in, ensure you have:
Spheron Account: Sign up at Spheron Network and purchase credits to access compute resources.

GPU Requirements: At least 1 GPU with 24 GB VRAM (e.g., RTX 4090) for T2V-1.3B. For T2V-14B, aim for ~24-26 GB total VRAM across multiple GPUs.

Software: Python 3.11, PyTorch >= 2.4.0, CUDA 12.6+ (pre-installed in Spheron’s Jupyter image).

Deployment Tools: Choose between:
Spheron Console (web UI), or

Spheron CLI with this sample YAML.

Setup Instructions
Step 1: Deploy the Jupyter Notebook on Spheron
Via Spheron Console:
Log in to console.spheron.network.

Create a new instance, select the jupyter/minimal-notebook image, and configure:
Port: Expose 8888 globally.

GPU: 1 RTX 4090 (24 GB VRAM).

Storage: At least 15 GB (for model weights).

Deploy and note the URL (e.g., https://<your-id>.spheron.app:8888) and access token.

Via Spheron CLI:
Install the CLI: npm install -g @spheron/cli.

Use the sample YAML, adjusting GPU and storage as needed:
yaml

version: "1.0"
services:
  web:
    image: jupyter/minimal-notebook
    expose:
      - port: 8888
        to: world
profiles:
  compute:
    web:
      cpu:
        units: 2.0
      memory:
        size: 8Gi
      storage:
        size: 20Gi
      gpu:
        units: 1
        attributes:
          vendor:
            nvidia:
              - model: rtx4090
                ram: 24Gi

Run sphnctl deploy -f deploy.yaml and note the URL/token.

Step 2: Import and Configure the Notebook
Open your Jupyter instance (e.g., https://<your-id>.spheron.app:8888) and log in with the token.

Go to File > Open from URL and paste this notebook URL: [TBD - Insert link to your notebook here].

The notebook includes scripts to:
Clone the Wan2.1 repo.

Install dependencies.

Download T2V-1.3B weights from Hugging Face.

Step 3: Run the Model
Execute each notebook cell step-by-step:
Installs dependencies (pip install -r requirements.txt).

Downloads the T2V-1.3B model (~8 GB).

Loads the model onto the GPU.

In the final cell, enter your text prompt, e.g., "A futuristic cityscape at sunset with flying cars.".

Run the cell to generate a 5-second 480P video (expect ~4 minutes processing time).

For T2V-14B, adjust the notebook to download from Hugging Face T2V-14B and ensure sufficient VRAM.
Example Output
Prompt: "Two anthropomorphic cats in boxing gear fighting on a stage."
Result: A 5-second 480P video showing animated cats sparring, rendered in ~4 minutes on an RTX 4090.

