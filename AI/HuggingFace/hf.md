Step 1: 登录
hf auth login --token {你的access token}
可以从这个地址获取https://huggingface.co/settings/tokens


Step 2: 下载文件
hf download Comfy-Org/z_image_turbo split_files/text_encoders/qwen_3_4b.safetensors --local-dir ./models
hf download Comfy-Org/z_image_turbo split_files/diffusion_models/z_image_turbo_bf16.safetensors --local-dir ./models