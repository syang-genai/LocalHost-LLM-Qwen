Setup Enviroment
---
* sudo apt update
* sudo apt install python3-pip
* pip install uv
* uv init --python 3.10 LLM
* cd project_name
* uv venv
* source .venv/bin/activate
* uv add huggingface_hub
* uv add accelerate
* uv add vllm

Serve LLM Model
---
uv run vllm serve /root/Qwen/Qwen3-0.6B --port 8000 --enable-auto-tool-choice --tool-call-parser hermes --reasoning-parser qwen3 

Test LLM Model Server
---
curl -X POST "http://0.0.0.0:8000/v1/chat/completions" \
        -H "Content-Type: application/json" \
        --data '{
                "model": "/root/Qwen/Qwen3-0.6B",
                "messages": [
                        {
                                "role": "user",
                                "content": "What is the capital of France?"
                        }
                ]
        }'
