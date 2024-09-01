# 아이쿠 공식계정보다 야구 영상이 더 많은 팔로워 얻을거라고 증명하기

📢 2024년 여름 [AIKU](https://github.com/AIKU-Official) 활동으로 진행한 프로젝트입니다.  
🎉 2024년 1/여름/2/겨울학기 AIKU Conference 열심히상 수상!

## 소개

2024년 야구 붐이 오면서 인스타 릴스, 유튜브 쇼츠 등에 중요 장면 영상을 올리는 계정이 기하급수적으로 늘어났습니다. 하지만 하루에 5경기, 한 경기당 최소 3시간씩은 걸리는 야구 경기를 모두 시청하고 중요한 장면을 선정하는 과정은 길고 복잡합니다.  
여기에 시간이 없는 현대인을 위해서 자동으로 하이라이트 장면을 추출해주는 모델을 준비했습니다. 

## 방법론

[MLB-youtube](https://github.com/piergiaj/mlb-youtube) 데이터셋 중 continuous(여러 개의 action이 포함된 1~2분 길이의 야구 경기 영상) 데이터를 활용하여, 중요한 action을 추출하는 것을 목표로 하였습니다.
데이터셋을 학습시키기 위해서 데이터 전처리는 다음과 같은 방식으로 진행합니다.

1. 모든 continuous 영상을 1초 단위로 분할합니다.
2. Action이 일어나는 구간을 True, 일어나지 않는 구간을 False로 설정한다.
3. True:False 1:1 샘플링을 진행한다.

모델은 EfficientNet-B0 모델을 베이스라인으로 Classification Head를 추가한 모델입니다.  
ImageNet-1K 데이터셋으로 사전 학습된 모델을 fine-tuning 하는 방식으로 학습이 진행되며, 모델은 1초 단위로 잘린 영상이 하이라이트 구간에 속하는지 판별합니다.

## 환경 설정

Google Colab 환경에서 사용할 수 있습니다.  
A100을 끊기지 않게 실행시킬 수 있는 컴퓨팅 단위를 준비해주세요.

## 사용 방법

1. [MLB-youtube](https://github.com/piergiaj/mlb-youtube) 데이터셋을 준비합니다.  
   본 프로젝트에서는 Continuous Video만을 필요로 하기 때문에 segment 데이터는 준비할 필요가 없습니다.
2. code 폴더에 있는 ipynb 폴더를 순서대로 실행시킵니다.  

## 예시 결과
아래 썸네일을 클릭하면 원본 영상이 뜹니다.   

[![원본 영상](https://img.youtube.com/vi/Sq2Igg3XjbM/0.jpg)](https://youtu.be/Sq2Igg3XjbM?si=QQl32IjPxeCEWjZ5) 

아래 썸네일을 클릭하면 모델의 Inference 결과물을 확인할 수 있습니다.   

[![결과 영상](https://img.youtube.com/vi/NNJyS-kMRB4/0.jpg)](https://youtu.be/NNJyS-kMRB4)


## 팀원

- [권보영](https://github.com/iamnotwhale): 데이터셋 구축/모델 학습/발표준비
- [김지연](https://github.com/delaykimm): 데이터셋 구축/모델 학습/결과 정리
- [송현지](https://github.com/kelly062001): 데이터셋 구축/모델 학습/결과 정리


