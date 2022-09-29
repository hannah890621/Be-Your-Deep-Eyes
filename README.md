# Be Your Deep Eyes
Running testing data on Colaboratory, please click [` here `](https://colab.research.google.com/drive/1zX-Xrg19Cc8e_mQmhW7ObIwZMjkGrQWI?usp=sharing).  
For getting complete files, please download files [` here `](https://drive.google.com/drive/folders/1bLB9S-UIjCCLIHqkqjJ2_EVbtAzFYzrk?usp=sharing).  
# Labelme  
1. Sidewalk  
2. Traffic Lane  
3. Crosswalk  
4. Cars  
5. Obstacles  
6. People     
![img](example_image.png)

# Installation
- Install some other packages
```
!pip install cython
!pip install opencv-python pillow pycocotools matplotlib
!pip install torchvision==0.5.0
!pip install torch==1.4.0
```
- Build DCNv2
```
%cd /yolact/external/DCNv2
!python setup.py build develop
```

# Training Data
- Training Weights
```
!python train.py  --config=yolact_base_config --batch_size=1
```
- Pretrained Weights  
Please download pretrained weights [` yolact_base_153_10000.pth `](https://drive.google.com/file/d/1-1oj2lMmGf7lqeURl24p0rLsxFJ4VNqL/view?usp=sharing) and put the corresponding weights file in the ` ./weights `
```
%cd /content/B-Protector/yolact
!mkdir -p weights
%cd weights
!gdown --id '1-1oj2lMmGf7lqeURl24p0rLsxFJ4VNqL'
```
# Run on Images
```
%cd /content/B-Protector/yolact
!mkdir -p output_images
!mkdir -p final_info

file_path = "data/testing_data"
output_path = "output_images"
!python eval.py --trained_model=weights/yolact_base_153_10000.pth --config=yolact_base_config --score_threshold=0.15 --top_k=15 --images={file_path}:{output_path}
```
# Result
![img](result_image.png)
![img](result_image2.png)
![img](result_image3.png)

# Text to Speech
```
from gtts import gTTS  
  
mytext = '前方有障礙物，請往左兩步。' 
language = 'zh'
myobj = gTTS(text=mytext, lang=language, slow=False) 
myobj.save("output.mp3") 
```

# B-Protector Demonstration video
https://user-images.githubusercontent.com/69901137/150776433-be7a127c-1f75-4d86-90f1-ffcf217fc89f.mp4



