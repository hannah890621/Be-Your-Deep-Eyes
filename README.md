# B-Protector

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
- Trained Weights
```
!python train.py  --config=yolact_base_config --batch_size=1
```
# Images
```
!rm output_images/testing_output -r
!mkdir -p output_images/testing_output

file_path = "data/project/testing_data"
output_path = "output_images/testing_output"
!python eval.py --trained_model=weights/yolact_base_153_10000.pth --config=yolact_base_config --score_threshold=0.15 --top_k=15 --images={file_path}:{output_path}
```
# Video
```
!rm output_video/testing_output -r
!mkdir -p output_video/testing_output

file_path = "test_video/test_video.mp4"
output_path = "output_video/testing_output"
!python eval.py --trained_model=weights/yolact_base_153_10000.pth --config=yolact_base_config --score_threshold=0.15 --top_k=15 --video={file_path}:{output_path}
```
