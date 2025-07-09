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
uv run vllm serve "/root/project_name/Qwen-0.6B" --port 8000 --enable-reasoning --reasoning-parser deepseek_r1  

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
