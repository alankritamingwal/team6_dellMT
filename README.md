Quick Start
⚙️ Install
Our repo mainly constructed based on FastChat. Please follow the install instructions. Or you can install from source by

git clone https://github.com/alankritamingwal/team6_dellMT
cd ChatPsychiatrist
pip3 install -r requirements.txt
⏬ Model Download
We provide the weights hold on Huggingface. You can download the model weights using Huggingface Client Library. Or use the following wget script:

mkdir -P PATH_TO_WEIGHTS_DIR && cd PATH_TO_WEIGHTS_DIR
user='EmoCareAI'
repo='ChatPsychiatrist'
curl "https://huggingface.co/${user}/${repo}/tree/main" | grep -o 'href="[^"]*"' | cut -d'"' -f2 | grep "^/${user}/${repo}/blob/main/" | sed "s|^|https://huggingface.co|; s|/blob/|/resolve/|g" > files.txt && wget -nc -i files.txt && rm files.txt
cd ..
🚀 Inference
Inference with CLI
See details refer to FastChat CLI Inference. In short, you can run the following command below around 14GB of GPU memory.

# Single GPU inference
python3 -m fastchat.serve.cli --model-path PATH_TO_WEIGHTS_DIR
# Multi GPUs inference
python3 -m fastchat.serve.cli --model-path PATH_TO_WEIGHTS_DIR --num-gpus N
Serving with Web GUI
Launch the controller, which manages the distributed workers
python3 -m fastchat.serve.controller
Launch the model worker.
python3 -m fastchat.serve.model_worker --model-path PATH_TO_WEIGHTS_DIR
Launch the Gradio web server
python3 -m fastchat.serve.gradio_web_server
See details refer to FastChat Web GUI Serving
