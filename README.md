# liblibai_comfui
目前liblib客户端的pytorch和cuda版本都是比较旧的，这导致很多加速类插件、wan视频插件无法安装

1.升级torch版本
于https://pytorch.org/ 查看目前支持的cuda版本，目前选择2.7正式版，对应cuda12.8。与此同时安装xformers一同编译。
在comfyui的python文件夹（LiblibAI-workspace\comfyui-deploy-win\python_embeded）下，右键“在终端中打开”。
复制黏贴代码 python.exe -m pip install -U xformers torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
