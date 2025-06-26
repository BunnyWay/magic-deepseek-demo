# Magic DeepSeek Demo

Deploy **DeepSeek R1** on [Magic Containers](https://bunny.net/) with a single Docker image.

This repository provides a **ready-to-deploy** setup for running the **DeepSeek R1 1.5B** model using [Ollama](https://ollama.ai/) inside **Magic Containers**. With this, you can run AI inference at the edge without the need for complex infrastructure.

🚀 **Read the full blog post** for a detailed guide: **[Link to the blog post](https://bunny.net/blog/deploying-deepseek-r1-on-magic-containers-ai-inference-at-the-edge/)**

---

## 📦 What's Inside?

This repository contains:

- **Dockerfile** – Defines a lightweight container with Ollama and DeepSeek R1.
- **pull.sh** – A startup script that pulls the DeepSeek model and launches the Ollama server.
- **GitHub Actions Workflow** – Automates the build and push process to **GitHub Container Registry (GHCR)**.

---

## 🔧 How to Use

### 1️⃣ Clone the Repository

```sh
git clone https://github.com/BunnyWay/magic-deepseek-demo.git
cd magic-deepseek-demo
```

### 2️⃣ Build the Docker Image Locally

```sh
docker build -t magic-deepseek-demo .
```

### 3️⃣ Run the Container

```sh
docker run -d --restart=always -p 11434:11434 --name magic-deepseek-demo magic-deepseek-demo
```

This will start the **DeepSeek R1 model** inside a container and expose the API on port **11434**.

The first start might take around 10 minutes because we need to download the DeepSeek model before Ollama can query it.

### 4️⃣ Test the API

Once running, you can query the model using **cURL**:

```sh
curl -X POST http://localhost:11434/v1/completions \
     -H "Content-Type: application/json" \
     -d '{"model": "deepseek-r1:1.5b", "prompt": "How many carrots is enough to eat daily?", "temperature": 0.8}'
```

---

## 🌍 Deploying to Magic Containers

1. **Push the Docker Image to GHCR**
   
   The repository includes a **GitHub Actions workflow** (`.github/workflows/build.yaml`) that automatically builds and pushes the Docker image to **GitHub Container Registry** when you push to the repo.

2. **Use Magic Containers to Deploy**
   
   Go to the **[bunny.net dashboard](https://dash.bunny.net/)**, create a **Magic Container**, and use the image:

   ```
   ghcr.io/bunnyway/magic-deepseek-demo:latest
   ```

3. **Start AI inference at the edge!** 🎉

---

## 🔄 GitHub Actions: Automated Builds

The repository includes a **CI/CD pipeline** that automatically builds and pushes the Docker image whenever changes are made.

### ✅ Features:
- Automated **Docker image build and push** to **GitHub Container Registry (GHCR)**.
- Supports **multi-architecture builds** using QEMU.
- Uses **GitHub Actions** for seamless deployment.

---

## 📝 Related Resources

- 📖 **Blog Post**: [Read the full guide on deploying DeepSeek R1 on Magic Containers](https://bunny.net/blog/deploying-deepseek-r1-on-magic-containers-ai-inference-at-the-edge/)
- 🐰 **Magic Containers**: [Learn more about bunny.net's Magic Containers](https://bunny.net/magic-containers/)
- 🤖 **DeepSeek R1**: [Check out the DeepSeek AI model](https://deepseek.com/)
- 🐳 **Ollama**: [Lightweight framework for AI inference](https://ollama.ai/)

---

## 🛠 Contributing

We welcome contributions! If you find any issues or improvements, feel free to submit a **pull request** or open an **issue**.

---

## 📜 License

This project is licensed under the **Apache 2.0 License**.

---

🚀 **Deploy AI at the Edge with Magic Containers!**
