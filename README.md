# 2022_Winter_DA_T2


deep
├── /data_final (원본 이미지, 만약 Augmentation을 진행하게 되면 하나 더 만들었음)
│   ├── /train
│   │       ├── TRAIN_00001.jpg
│   │       ├── TRAIN_00002.jpg
│   │       ├── TRAIN_00003.jpg
│   │       └── ...
│   ├── /train_labeled (제목을 TRAIN 대신에 라벨로 변경)
│   │       ├── 머_00001.jpg
│   │       ├── 안녕_00002.jpg
│   │       ├── 사랑_00003.jpg
│   │       └── ...
│   └── /test
│
├── /data_transformed (원본 데이터를 convert.py를 통해 변환한 후, train test split으로 train과 valid를 임의로 나눴음. gt.txt까지 생성)
│   ├── /training
│   │   └── /kordata
│   │       # TRDG2DTRB 프로젝트를 통해 변환된 한글 학습데이터
│   │       ├── gt.txt
│   │       └── /images
│   │           #    image_[idx].[ext]
│   │           ├── image_00001.png
│   │           ├── image_00001.png
│   │           ├── image_00001.png
│   │           └── ...
│   ├── /validation
│   └── /test
│
├── /data_ocr (create_lmdb_dataset.py를 통해 lmdb 파일로 변환된 데이터)
│   ├── /training
│   │   └── /kordata
│   │       ├── data.lmdb
│   │       └── data.lmdb
│   ├── /validation
│   └── /test
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
