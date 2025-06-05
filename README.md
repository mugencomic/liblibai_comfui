# liblibai_comfui
目前liblib客户端的pytorch和cuda版本都是比较旧的，这导致很多加速类插件、wan视频插件无法安装

1.升级torch版本
于https://pytorch.org/ 查看目前支持的cuda版本，目前选择2.7正式版，对应cuda12.8。与此同时将xformers一同编译。
在comfyui的python文件夹（LiblibAI-workspace\comfyui-deploy-win\python_embeded）下，右键“在终端中打开”或在资源管理器地址栏中输入“cmd”呼出终端。
复制黏贴代码 
python.exe -m pip install -U xformers torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
跑完代码后，打开客户端启动发现已经成功启动xformers模块

2.安装triton-windows与SageAttention
要用KJ工作流的wan节点，需要在虚拟环境中安装这两个包
同样在comfyui的python环境文件夹中呼出终端，依序安装triton-windows与SageAttention
python.exe -m pip install -U triton-windows
git clone https://github.com/thu-ml/SageAttention
python.exe -m pip install sageattention
“-m”参数保证在该虚拟环境内安装，否则是会用系统的python（如果你有安装）安装。
我在完成上述操作后，还遇到了bitsandbytes报错，这是因为刚才编译xformers和torch时，编译的是非GPU版本，不带GPU加速。单纯重装bitsandbytes无效。
权宜之计，找别的环境包（我会上传我用的到此项目中）里的bitsandbytes文件夹，放到我们的lib客户端内（LiblibAI-workspace/comfyui-deploy-win/python_embeded/Lib/site-packages/），不再报错。

3.在客户端内添加加速选项
客户端默认只有3种加速选项而没有SageAttention选项，打开（LiblibAI-workspace\comfyui-deploy-win）内的

