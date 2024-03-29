Be Your Deep Eyes
===

運用影像辨識 YolactEdge，結合距離探測、語音警示 pyttsx，並嵌入至 Jetson Nano 中，期望借助資通訊科技的力量，創造有利視障人士的未來生活。 

Demonstration video
---
https://user-images.githubusercontent.com/69901137/192931918-060662e1-0618-4565-b80d-68a1e1e0be33.mp4

Category  
---

1. Person
2. Bicycle
3. Car
4. Motorcycle
5. Train
6. Lane
7. Bus
8. Fire Hydrant
9. Stop Sign
10. Sidewalk
11. Truck
12. Crossing
13. Obstruction
14. Traffic Light 

Installation
---

```
!pip install cython
!pip install opencv-python pillow pycocotools matplotlib
!pip install torchvision==0.5.0
!pip install torch==1.4.0
```

Training Data
---

```
!python train.py --config=yolact_base_config
```
<!-- - Pretrained Weights  
Please download pretrained weights [` yolact_edge_43_400000.pth `](https://drive.google.com/file/d/1-1oj2lMmGf7lqeURl24p0rLsxFJ4VNqL/view?usp=sharing) and put the corresponding weights file in the ` ./weights `
 
 ```
%cd /content/B-Protector/yolact
!mkdir -p weights
%cd weights
!gdown --id '1-1oj2lMmGf7lqeURl24p0rLsxFJ4VNqL'
```
 -->
 
Run on Video
---
```
!mkdir -p results/output_video

file_path = "data/video/test_video.mp4"
output_path = "results/output_video.mp4"
!python eval.py --disable_tensorrt --config=yolact_edge_config --trained_model=weights/yolact_edge_43_400000.pth --score_threshold=0.3 --top_k=100 --video={file_path}:{output_path}
```

Text to Speech
---
```
from gtts import gTTS  
  
mytext = '前方兩公尺有人，請往右兩步。' 
language = 'zh'
myobj = gTTS(text=mytext, lang=language, slow=False) 
myobj.save("output.mp3") 
```



