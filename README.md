# 🎓 Workshop: Getting Started with Ollama & Running LLaMA Models

Welcome to our hands-on workshop! This guide walks you through installing **Ollama**, running **LLaMA models**, customizing behavior, and backing up results — all beginner-friendly!

---

## 🎤 Self Introduction

### 👨‍💻 SK. Muneer – *Tech Guide*

Hello everyone! I’m SK. Muneer, a passionate technology educator and AI enthusiast.
I specialize in making complex technologies approachable and hands-on.
Today, I’ll guide you through using **Ollama** and **LLaMA** models to build powerful AI applications.

### 👩‍💻 Aishwarya – *Clarity Coach*

Hi there! I’m Aishwarya — a software engineer and advocate for open-source learning.
I focus on simplifying technical concepts so anyone can explore and innovate with AI.
We’re here to ensure you get real results with practical demos, not just theory.

---

## 🧽 Table of Contents

1. [What is Ollama?](#what-is-ollama)
2. [Why Use Ollama?](#why-use-ollama)
3. [What You’ll Need](#what-youll-need)
4. [Installing Ollama](#installing-ollama)
5. [Running LLaMA Models](#running-llama-models)
6. [Customizing Model Behavior](#customizing-model-behavior)
7. [Understanding Responses](#understanding-responses)
8. [Backing Up Outputs to Google Drive](#backing-up-outputs-to-google-drive)
9. [Troubleshooting](#troubleshooting)
10. [Contributing to Ollama](#contributing-to-ollama)
11. [License](#license)
12. [Contact](#contact)
13. [Appendix: Full Install Script](#appendix-full-install-script)

---

## 🧠 What is Ollama?

**Ollama** is an open-source tool that lets you run LLMs (like LLaMA3) locally — no internet required post-setup.

* 🔐 Private by default
* ⚡ Fast & efficient
* 🧠 Supports popular models
* 💽 Works on macOS, Linux & Windows (via WSL2)

---

## 💡 Why Use Ollama?

| Feature          | Benefit                                  |
| ---------------- | ---------------------------------------- |
| ✅ Runs Locally   | Full offline capabilities after download |
| 🔐 Private       | No data leaves your device               |
| 🚀 Simple Setup  | Works across platforms                   |
| 🧠 Model Variety | LLaMA, Mistral, and more supported       |
| ↺ Dev Friendly   | Python integration and automation ready  |

---

## 🧰 What You’ll Need

* 💻 macOS / Linux / Windows (WSL2)
* 📀 Minimum 8GB RAM (16GB+ recommended)
* 🌐 Internet for downloading models
* 🧑‍💼 Basic Terminal skills

---

## ⚙️ Installing Ollama

### 🗅 macOS

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### 🐧 Linux (Debian/Ubuntu-based)

```bash
sudo apt update
sudo apt install -y curl
curl -fsSL https://ollama.com/install.sh | sh
```

### 🪠 Windows (via WSL2)

1. Install **Ubuntu from the Microsoft Store**
2. Launch Ubuntu and run:

```bash
sudo apt update
sudo apt install -y curl
curl -fsSL https://ollama.com/install.sh | sh
```

### ✅ Verify Installation

```bash
ollama --version
```

---

## 🧪 Running LLaMA Models

### Step 1: Pull the model

```bash
ollama pull llama3
```

### Step 2: Run the model

```bash
ollama run llama3
```

Try:

```text
Tell me a joke.
Explain black holes in simple terms.
```

---

## 🎛️ Customizing Model Behavior

Use the Python API to fine-tune how the model responds:

```python
import ollama

response = ollama.generate(
    model="llama3",
    prompt="Write a poem about cats.",
    temperature=0.8
)

print(response["response"])
```

| Parameter           | Description                |
| ------------------- | -------------------------- |
| `temperature`       | Higher = more creative     |
| `max_tokens`        | Limits response length     |
| `top_p`             | Controls diversity         |
| `frequency_penalty` | Reduces repetitive outputs |

---

## 📖 Understanding Responses

Ollama can:

* 🧠 Answer questions
* 💻 Generate and explain code
* 📚 Summarize documents
* ✍️ Write creative stories or poems
* 📊 Explain data and concepts clearly

> ⚠️ Always verify important info — it may occasionally hallucinate or guess.

---

## ☁️ Backing Up Outputs to Google Drive

### Step 1: Install rclone

```bash
sudo apt install rclone
rclone config
```

Configure it with your **Google Drive** account.

### Step 2: Create a local folder

```bash
mkdir ~/ollama_output
```

### Step 3: Save responses and upload

```bash
ollama generate llama3 "Your question" > ~/ollama_output/response.txt
rclone copy ~/ollama_output remote_drive:/ollama_backup
```

---

## 🛠️ Troubleshooting

| Problem                | Solution                                      |
| ---------------------- | --------------------------------------------- |
| ❌ Can't download model | Check internet connection                     |
| 🧠 Out of memory error | Try a smaller model: `llama3:8b`              |
| ⚠️ Command not found   | Reinstall Ollama or add it to your PATH       |
| 🚫 GPU not used        | Ensure your CUDA/NVIDIA drivers are installed |

---

## 🤝 Contributing to Ollama

Ollama is fully **open-source**. You can:

* 🐞 Report issues
* 💡 Suggest features
* 📙 Improve docs
* 💻 Submit PRs

🔗 [GitHub – ollama/ollama](https://github.com/ollama/ollama)

---

## 📄 License

* Ollama uses the **MIT License** — use, modify, and share freely.
* Each model (e.g., LLaMA3) may have its own license — review before redistribution.

---

## 📬 Contact

| Name      | Email                                                 | GitHub Handle                                  |
| --------- | ----------------------------------------------------- | ---------------------------------------------- |
| Muneer    | [muneer@example.com](mailto:muneer@example.com)       | [@muneerai](https://github.com/muneerai)       |
| Aishwarya | [aishwarya@example.com](mailto:aishwarya@example.com) | [@aishwaryaml](https://github.com/aishwaryaml) |

---

## 📦 Appendix: Full Install Script

Below is the actual install script used by Ollama (as of June 2025):

```bash
#!/bin/sh
set -e

ARCH=$(uname -m)
OS=$(uname -s | tr '[:upper:]' '[:lower:]')
VERSION="latest"

if [ "$ARCH" = "x86_64" ]; then
  ARCH="amd64"
elif [ "$ARCH" = "aarch64" ]; then
  ARCH="arm64"
fi

echo "Detected architecture: $ARCH"
echo "Detected OS: $OS"

curl -L "https://ollama.com/download/$OS/$ARCH" -o ollama.tar.gz
mkdir -p ~/.ollama
tar -xzf ollama.tar.gz -C ~/.ollama
sudo mv ~/.ollama/ollama /usr/local/bin/ollama
rm -rf ~/.ollama ollama.tar.gz

echo "✅ Ollama installed successfully!"
```

---

## 🎉 Final Words

Thank you for attending the workshop!

> 🧠 AI is no longer just for experts — it's for *everyone* who’s curious, creative, and ready to build.

Go ahead, experiment with LLaMA, build something cool — and have fun! 🚀
