# 2022 CUAI Winter Conference DA_T2(매의 눈) Repository
---- 
### 팀원
- 곽수민 (응용통계학과)
- 김우엽 (기계공학부)


### 주제 요약




### 회의
표로 만들기



### 작업 디렉토리 구조
```python
# 코드는 deep-text-recognition-benchmark 폴더 바로 상위 디렉토리에 존재
deep-text-recognition-benchmark
├── /data (원본 이미지 train)
│   ├── /train
│   │       ├── TRAIN_00001.jpg
│   │       ├── TRAIN_00002.jpg
│   │       ├── TRAIN_00003.jpg
│   │       └── ...
│   └── /test
│
├── /data_transformed (원본 데이터를 convert.py를 통해 변환한 후, train test split으로 train과 valid를 임의로 나눴음. gt.txt까지 생성)
│   ├── /train
│   # TRDG2DTRB/convert.py 를 통해 변환된 한글 학습데이터(train/valid 나눈 후 train 데이터는 Augmentation 진행)
│       ├── gt.txt
│       └── /images
│           #    image_[idx].[ext]
│           ├── image_00001.png
│           ├── image_00002.png
│           ├── image_00003.png
│           └── ...
│   └── /valid
│
├── /data_ocr (create_lmdb_dataset.py를 통해 lmdb 파일로 변환된 데이터)
│   ├── /training
│   │   └── /kordata
│   │       ├── data.lmdb
│   │       └── data.lmdb
│   └── /validation
│
├── /pretrained_model (학습시 사용할 pretrained 모델)
│   └── korean_g2.pth
│
├── /saved_models
│   # 사용자가 직접 학습한 모델이 저장되는 경로.
│   ├── TPS-VGG-BiLSTM-CTC-Seed1111
│   │   └── best_accuracy.pth
│   ├── TPS-VGG-RCNN-CTC-Seed1111
│   └── ....
│
├── demo.py (파일을 predict 하기 위한 파일. 원본 코드에서 character값을 수정하고, 저장되는 로그 파일의 형식을 수정함)
│
└── train.py (학습시 사용할 코드, 원본 코드에서 character 값을 수정)
