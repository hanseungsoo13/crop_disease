공부용 목적으로 나간 공모전으로 요약과 느낀점, 앞으로의 공부방향 등에 대해 정리한다.

## Summary

- Image
    - Image는 Pretrained 된 Model들로 Transfer Learning을 통해 학습한다.
    - Augmentation은 gray scale변환, gaussnoise, crop 등을 시도해 보았지만 성능 저하 (뭐가 문제였을까..?)
    - EfficientNet과 regnet을 이용하여 output 1000의 모델 구축
- CSV
    - Nan값이 있는 column들이 많아 모두 제거하고, Nan값이 없는 9개의 피쳐들만 이용
    - MinMax Scaling적용
    - 각 식물마다 데이터의 길이가 다르기 때문에 Zero padding 적용
    - max_len: 24*6
    - LSTM 적용
- Ensemble
    - Pytorch의 concat연산을 적용하여 Image모델의 1000개의 output과 CSV모델의 256 output을 더해줌
    - Dropout과 Relu 연산을 적용하여 25개로 분류하는 연산을 수행
- Training
    - Optimizer: Adam(lr=1e-3)
    - Scaler: GradScaler

## Contribution

1. Computer Vision분야의 첫번째 공모전으로, 어떤 식으로 성능을 발전시켜야 나가는지를 공부할 수 있었다.
2. 그동안 tensorflow만 많이 다뤄본 입장에서 Pytorch와 친해질 수 있는 좋은 기회 였다.
3. Transfer learning을 위한 논문 reading을 통해 모델들의 구조를 파악의 중요성을 알 수 있었다.

## 앞으로의 공부방향

1. 성능 향상을 위해서는 다양한 augmentation이 필수 인것 같다, augmentation 기법에 대해 공부가 필요하다.
    
    이 공모전에서 다양한 augmentation을 시도해 좋은 성능을 낸 수상자가 있음
    
    https://github.com/ztor2/dacon_competition_plant_disease
    
2. 단순히 모델만을 변경, 실험하는 것이 아닌, 나만의 무언가 방법이 필요하다. target에 대한 분석이나, 학습 방식에 대한 다양한 실험이 필요하다.
    
    이 공모전에서의 코드공유를 보면 target에 mask를 씌워 조건부확률로의 문제로 전환하려는 노력이 있었다.
    
    https://github.com/With-Coding-Cat/LG_plant_disease_diagnosis_competition
    
3. Computer Vision에 대한 이해도를 높이기 위해 다양한 논문들을 읽어보고 작은 프로젝트부터 천천히 복습해 나가야한다.
