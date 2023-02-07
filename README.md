# 2022 CUAI Winter Conference DA_T2(매의 눈) Repository


## 👪 팀원
- 곽수민 (응용통계학과)
- 김우엽 (기계공학부)


## ✍ 요약
본 연구는 차세대 에듀테크 서비스의 핵심 기술로 자리 잡은 OCR 기술을 유아 손글씨 인식에 특화하여 연구하였다. 

구현한 CNN 기반 모델은 Test Accuracy 85.55%의 성능을 기록하였으며 차후 교육 업계와 연동한다면 아이들의 효율적인 학습을 위한 교두보의 역할을 수행할 수 있을 것이다.



## ✔ 회의
|일자|내용|
|------|---|
|12/25|주제선정|
|12/28|계획논의|
|1/1|어그멘테이션, 모델링 논의|
|1/10|모델링 중간점검1|
|1/12|모델링 중간점검2|
|1/17|최종 모델 선정|
|1/26|소논문 구성 논의|
|1/30|소논문 완성|


## 모델 구조
- Transformation : **TPS**
<img src="https://user-images.githubusercontent.com/99728502/217172693-0c9f9669-b168-4027-a818-5cf5d9441090.png"  width="700" height="300"/>

**irregular text를 올곧은 텍스트로 변환**

- Feature Extraction : **VGG**
<img src="https://user-images.githubusercontent.com/99728502/217172822-3221183b-fbc5-4d96-9e15-7f14d4ebeb16.png"  width="700" height="300"/>

**글자를 인식하는 메인 모델**

- Sequence Modeling : **BiLSTM**
<img src="https://user-images.githubusercontent.com/99728502/217172924-439e0f2c-1d3f-4572-8a52-98f4d0731057.png"  width="700" height="300"/>

**인식된 이전 글자, 다음 글자 정보를 활용해 더 정확하게 예측**

- Prediction : **CTC**
<img src="https://user-images.githubusercontent.com/99728502/217173045-3a228fd7-d775-4328-aef7-57ba875d1c74.png"  width="700" height="300"/>

**글자 하나를 중복된 여러개의 글자로 인식하는 것을 해결**


## 💻 작업 디렉토리 구조
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
│   ├── /train_aug
│   # Augmentation 진행된 train 데이터
│       ├── gt.txt
│       └── /images
│           ├── image_00001.png
│           ├── image_00002.png
│           ├── image_00003.png
│           └── ...
│   ├── /valid
│   └── /test
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
```

## 🏆 최종결과
![image](https://user-images.githubusercontent.com/99728502/217172244-07419b96-7fff-47f0-a507-a9aa07c2d273.png)
