# Text detection from Natural Images using CTPN

This repo offers varied solution to **Scene text detection** based on
 -  CTPN (connectionist text proposal network). It is implemented in tensorflow. The origin paper can be found [here](https://arxiv.org/abs/1609.03605). 
 
 - & also ,alternative older approaches, such as 
 
	- CRNN Model
	- DenseNet-OCR


***
**Please Note**:I have to reonstruct this repo. The repo is written based on older dependencies**, such as 
- tensorflow-gpu==1.4.0 (to be upgraded to latest stable version - **tensorflow-gpu==1.12. 0** and **cuda==9.0** , the compatible **cuDNN version==7.1. 4**). 
- Model is saved in **hdf5** (not so optimized model servable / model serialization format). I'll re-factor the code with TF2.0, and save the model as **protobuff (.pb)** model serialization format.
- It's trained on **GTX1070 GPU**. I'm planning to retrain this on **TPU**.
- I'll reonstruct this repo with serving using **TF_Serving** for **Quantization and Pruning**.
***

## Architecure of CTPN-Model, NVIDIA-GPU 

|CTPN Model Architecture |NVIDIA-GPU Architecture|
|:--:|:--:|
|<img src="/data/CTPNArchitecture.png" width=600 height=200 /> |<img src="https://cloud.githubusercontent.com/assets/3028125/12213714/5b208976-b632-11e5-8406-38d379ec46aa.png" width=300 height=200 />|
|Please refer to [CTPN Architecture explaine](https://www.researchgate.net/figure/Architecture-of-the-Connectionist-Text-Proposal-Network-CTPN-We-densely-slide-a_fig4_308277110)|Please refer to [NVIDIA-GPU](https://github.com/NVIDIA/nvidia-docker)|
| VGGNet -> BLSTM of 256D ->FC of 512D ->output layer MLP for text/non-text scores|check CUDA version using ```nvcc --version```. cuDNN version using ```cat /usr/include/cudnn.h -pipeto- grep CUDNN_MAJOR -A 2```. tensorflow-gpu version using ``` pip freeze -pipeto- grep tensorflow-gpu``` |

## Multiple AI Model Approaches 

* CTPN Model
* DenseNet-OCR
* CRNN 

CTPN Model is the latest as of date. & that's the way to go about. As 

- CTPN is latest & the most effective for  Scene text detection.
- Even though most data sets are based on English, CTPN perform well in Chinese positioning as well.

#### Codeset for these approaches
- [CTPN Model for Scene Text Detection](https://github.com/DeepHiveMind/Text_Detection_Images_IDCard_CTPN/tree/master/ctpn)
- [DenseNet-OCR Model for Scene Text Detection](https://github.com/DeepHiveMind/Text_Detection_Images_IDCard_CTPN/tree/master/densent_ocr)
- [CRNN Model for Scene Text Detection](https://github.com/DeepHiveMind/Text_Detection_Images_IDCard_CTPN/tree/master/CRNN)


### 2 older AI approaches

- Vantage view of 2 older AI approaches
```
CRNN：  VGGNet + BLSTM + BLSTM + CTC 

DenseNet-OCR ：DenseNet + CTC 

```

- Result Comparision

| Model Architecture  | run time on GPU | Accuracy | Model Servable size |
| ---------- | -----------| ---------- | -----------|
| CRNN | 60ms | 0.972 | oops missed it. |
| DenseNet-OCR | 8ms | 0.982 | 18.9MB |


# some results
`NOTICE:` all the photos used below are collected from the internet. If it affects you, please contact me to delete them.
<img src="/data/res/006.jpg" width=320 height=480 /><img src="/data/res/008.jpg" width=320 height=480 />
<img src="/data/res/009.jpg" width=320 height=480 /><img src="/data/res/010.png" width=320 height=320 />
***
## oriented text connector
- oriented text connector has been implemented, i's working, but still need futher improvement.

<img src="/data/res/007.jpg" width=320 height=240 /><img src="/data/res_oriented/007.jpg" width=320 height=240 />
<img src="/data/res/008.jpg" width=320 height=480 /><img src="/data/res_oriented/008.jpg" width=320 height=480 />
***

#### Interactive Live Demo of 'Scene Text Detection'
[Interactive demo reference](https://pan.baidu.com/share/init?surl=oEWTrx20G41iNaJYF-xa6w)
