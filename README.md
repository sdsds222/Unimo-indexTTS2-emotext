# Unimo IndexTTS2情绪描述文本解析优化模型
Unimo 是一个专门为优化IndexTTS2而训练的自然语言情绪向量转换模型，基于Qwen3-0.6B和Qwen2.5-0.5B模型微调。

目的是为了优化原版IndexTTS2内置的情感文本描述解析模型，提升解析情绪文本的准确度。

本模型加强了对情绪描述文本的程度词的理解，将其精准解析为 8 维情感特征向量，以供IndexTTS2生成情绪准确的音频。

这个模型是为了解决IndexTTS2官方源码内置的Qwen情绪文本解析模型识别情绪不精确的问题而训练的，对情绪描述文本的程度词等方面进行了优化。

模型产生的情绪向量可直接给IndexTTS2生成的时候使用。IndexTTS2配合本模型使用，产生的音频能够更加符合情绪描述。

（后续可能会继续训练一个情绪上下文模型，能够根据情绪的上下文（如上一句话的情绪向量）以及当前的情绪描述，综合信息后生成更加自然的情绪，使情绪的变化更加丝滑流畅）

输入情绪描述文本，模型即可输出情绪向量，向量可直接给IndexTTS2使用。
目前只做了控制台交互界面和对比测试界面，有需要的可以根据py文件自己编写api调用逻辑。

Huggingface仓库: https://huggingface.co/sdsds222moyu/Unimo-indexTTS2-emotext

## 部署方法：
安装依赖：
```
python -m venv venv
source venv/bin/activate  # Linux
.\venv\Scripts\activate   # Windows
pip install -r requirements.txt
```
有两种模型可选（Qwen3 0.6B、 Qwen2.5 0.5B），请根据情况自行选择。

启动交互界面：
```
python Unimo_interactive_qwen2.5
```
```
python Unimo_interactive_qwen3.py
```
![image](image/2.png)

启动对比测试界面（和原版内置的情绪文本解析模型进行对比）：
```
python Unimo_test_qwen2.5.py
```
```
python Unimo_test_qwen3.py
```

![image](image/1.png)

