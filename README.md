# Ravindu Somawansa

**Staff AI Engineer** building at the intersection of AI, robotics, and edge computing.

Based in Paris. Currently at Air Liquide. Focused on making AI systems that run locally, respect privacy, and work on consumer hardware.

## What I'm Working On

### Robotics & Edge AI

**[Baby Reachy-Mini Companion](https://github.com/ravediamond/baby-reachy-mini-companion)** — An autonomous AI nursery companion built on the Reachy Mini robot. 7 AI models (VAD, STT, TTS, YAMNet, YOLO, LLM, VLM) orchestrated on-device with zero cloud dependency. The robot listens, sees, reasons via tool-calling SLMs, detects baby cries, spots dangerous objects, and alerts parents — all running locally on a Mac or a $700 NVIDIA Jetson Orin NX.

- Fully local pipeline: Silero VAD → Faster-Whisper → Ollama/vLLM (3B-4B SLMs with tool calling) → Kokoro TTS
- Autonomous safety: YAMNet cry detection + YOLO danger scanning with deterministic alerts (never gated on LLM behavior)
- Deployed on NVIDIA Jetson Orin NX via vLLM and llama.cpp with quantized models (~3s end-to-end latency)
- Built for the **NVIDIA GTC x Hugging Face Golden Ticket Contest** — ranked #2 in community rankings

### Products

**[MCPH](https://github.com/ravediamond/MCPH)** — MCP Hub ([mcph.io](https://mcph.io)). AI artifact storage and sharing platform built on the Model Context Protocol. Upload, organize, and share AI-generated content across Claude, ChatGPT, and any MCP-compatible tool. Features semantic search, poll collection, embeddable badges, and a full MCP server. TypeScript / Next.js / Firebase.

**[EvalNow](https://github.com/ravediamond/simple-eval)** — A lightweight AI evaluation tool ([evalnow.xyz](https://evalnow.xyz/)). Upload a dataset (CSV/JSONL/Excel), get instant AI-powered scoring with detailed reasoning. Privacy-first: no data storage, in-memory processing only. Python / FastAPI.

### Open Source Contributions

- **[huggingface/lerobot](https://github.com/huggingface/lerobot)** — Contributing Reachy Mini robot integration: teleoperation interface, motor control, sensor support, and tests
- **[langchain-ai/langchain-aws](https://github.com/langchain-ai/langchain-aws)** — Added `llms.txt` documentation for AI coding tool support

### Technical Writing

I write about deploying AI in production on **[Medium](https://medium.com/@ravindu.somawansa)** — covering RAG pipelines, LLM serving on AWS SageMaker, edge deployment, and agentic architectures.

## Technical Interests

- **Agentic AI** — Tool-calling agents, multi-step reasoning, MCP integrations, autonomous decision loops
- **Local/edge AI** — Running multi-model pipelines on consumer hardware without cloud dependencies
- **Robotics** — Autonomous companion robots, assistive robotics, teleoperation, LeRobot ecosystem
- **SLM engineering** — Tool calling with 3B-4B models, working around reliability limits, quantization for edge deployment
- **NVIDIA Jetson** — vLLM / llama.cpp deployment, memory optimization, DLA core utilization

## Stack

`Python` `TypeScript` `PyTorch` `ONNX` `Ollama` `vLLM` `llama.cpp` `FastAPI` `Next.js` `YOLO` `Whisper` `LangChain` `AWS` `GCP` `Docker` `NVIDIA Jetson`

## Links

- [Medium](https://medium.com/@ravindu.somawansa)
- [Twitter/X](https://twitter.com/RSomaw)
- [HuggingFace Space](https://huggingface.co/spaces/ravediamond/baby-reachy-mini-companion)
