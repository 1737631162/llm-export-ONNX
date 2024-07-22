[下载TensorRT](https://developer.nvidia.com/nvidia-tensorrt-8x-download)  

将 ONNX 文件转换为 TensorRT 引擎有两种主要方法，第一种是通过安装的windows平台上tensorRT安装包下的trtexec.exe转换，另一种是通过tensorRT的C++或者python的API转换：  

1.用trtexec.exe  
2.使用 TensorRT API  

**windows端使用trtexec.exe转换的方式：**  
安装步骤：  

1. 解压到你自己的路径  

  这一步不做介绍，后面我提到的路径需要参考自己路径。  

2. 添加环境变量  

  E:\TensorRT\TensorRT-8.6.1.6\lib  

3. 将bin和include文件移动到cuda安装目录下  
  ```text
  TensorRT-8.6.1.6\lib下的lib文件拷贝到CUDA路径下的lib/64路径下
   
  TensorRT-8.6.1.6\lib下的dll文件拷贝到CUDA路径下的bin路径下
   
  提示：cuda路径参考：我的路径：E:\moreSoftWare\CUDA121\NVIDIA GPU Computing Toolkit\
  ```

4. 安装tensorrt依赖  

  安装E:\TensorRT\TensorRT-8.6.1.6\python路径下的tensorrt库文件，注意自己的python版本选择合适的版本安装。  (tensorrt-8.6.1-cp310-none-win_amd64.whl)

5. 转换onnx to engine  
输入：xxx.onnx   输出：xxx.trt文件  
5.1 anaconda终端切换到trtexec.exe路径下(示例 E:\TensorRT\TensorRT-8.6.1.6\bin)  
5.2 xxx.onnx放在该路径下
操作命令：trtexec --onnx=xxx.onnx --saveEngine=xxx_engine.trt  
**Note：由于每台设备的参数不同，而onnx转trt的过程是与设备参数高度匹配的，所以绝大多数情况下，trt文件必须得从自己要推理的设备上生成，没法复用。**



