# State of Deep Learning on macOS

## GPU and Shader languages

- **NVIDIA and CUDA:** [NVIDIA stopped supporting macOS with CUDA 11](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html#title-new-features) and probably will focus even more on enhancing training on Linux GPU servers. Only Mac OS High Sierra (10.13) was supported by NVIDIA. [Unofficially](https://egpu.io/forums/mac-setup/imac-egpu-simply-for-3d-accelleration/), there are ways to enable a current Macbook or Mac Mini to use an NVIDIA graphics card in an eGPU housing. Yet, you have to expect a bumpy road with that since you need to switch back to macOS 10.13 to use CUDA as well.
- **Apple and Metal**: although it was [reported](https://developer.apple.com/videos/play/wwdc2018/609/?time=2149) that Google and the Tensorflow team will support accelerated training with Metal Performance Shader, but they have [canceled their efforts in favor of Tensorflow Tiny](https://github.com/tensorflow/tensorflow/issues/8211). It also seems like that [Metal lacks in general features to be able to be used by AMD and NVIDIA](https://github.com/RadeonOpenCompute/ROCm/issues/262#issuecomment-557947337):
	- Single-source programming model
	- Support for templated kernels and other common C++ features found in CUDA/HIP
	- Support for an offline compilation model
- **(mainly) AMD and OpenCL**: Although this would be the most platform-agnostic way for frameworks to enable the support for every GPU vendor, it has been dropped by Apple in favor for Metal and seems to lose more and more support from other companies. OpenCL is nowadays considered as dead.
- **AMD and ROCm**: After OpenCL was dropped by Apple, AMD started with their own CUDA offensive, called ROCm. But because Metal is [currently lacking](https://github.com/RadeonOpenCompute/ROCm/issues/262) [of features](https://forums.developer.apple.com/thread/8359), [there's no macOS support possible](https://github.com/ROCm-Developer-Tools/HIP/issues/150#issuecomment-321272082). 

## NVIDIA Docker support
NVIDIA is working now for a longer time period on a Docker wrapper to enable the usage of NVIDIA GPU access in Docker containers. This sounds promising, since Docker containers are platform-agnostic and could even ease the installing of DL frameworks. 

On a Mac, it seems to be not possible to have support for the `nvidia-docker` Docker wrapper [since `xhyve` weren't supporting PCI passthrough](https://github.com/NVIDIA/nvidia-docker/issues/101). Also, you need to have NVIDIA drivers installed on your Mac - and [NVIDIA just dropped the development of NVIDIA drivers for Mac](https://www.tonymacx86.com/threads/nvidia-drivers-for-macos-mojave.273211/).

## Is this the end?
Well, we can hope for WWDC2020. Will update this "guide" when there are some news.
