# How-to-install-tensorflow-gpu
I struggled quite a bit when installing TensorFlow for training on GPU and I found that there are a lot of people who are finding it a little bit difficult like me. Therefore, I want to help you go step by step on installing TensorFlow for training on GPU.
- If you want to check your [GPU spec information](https://developer.nvidia.com/cuda-gpus)
- Fristly, we need to download and install [Microsoft Studio community](https://visualstudio.microsoft.com/downloads/)
- Uninstall all the NVIDIA in "Apps & Features" and remove "NVIDIA Corporation" and "NVIDIA GPU Computing Toolkit" folder in C:\ProgramFile and C:\ProgramFilex84 if this exist. Don't worry we will install all of it later. This is for compatibility.
- Choose your GPU devices and [Install GPU driver](https://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/Windows/512.15/512.15-notebook-win10-win11-64bit-international-dch-whql.exe&lang=us&type=geforcem)
- **Important**: You must choose the version of cuDNN and CUDA compatibility. Go to and download cuDNN first and see what CUDA version is compatible.
    - [Install cuDNN](https://developer.nvidia.com/rdp/cudnn-archive)
    - [Install CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit-archive)
- After that copy all file from each folder of cuDNN and put it in "NVIDIA GPU Computing Toolkit/CUDA/v../" folder. There are 3 folder: bin, include, libs.
- Go to Edit environment variable and add those to the PATH:
    - ```C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.5\bin```
    - ```C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.5\libnvvp```
    - Note that version might be different depend on your choice
- Install [Zlib](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#install-zlib-windows) and put file zlibwapi.dll into folder ```bin``` that you have add it to the PATH in the previous step.
- Install tensorflow-gpu: ```pip install --ignore-installed --upgrade tensorflow-gpu```
- To know tensorflow is using gpu, open your envs shell and run this:
  ``` python
  >>> import tensorflow as tf
  >>> print("Num GPUs Available: ", len(tf.config.list_physical_devices('GPU')))
  ```
