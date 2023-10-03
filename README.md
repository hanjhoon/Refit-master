# Refit-master
Refit 최종본
## ☑️ 프로젝트 소개

- AI를 사용한 의류 분류와 매칭, 현 위치별 가까운 옷 분리수거 위치 안내, 자신의 의류 종류에 해당하는 캠페인 추천 기능이 프로젝트의 핵심 기술입니다.

### ☑️ REFIT 비즈니스 모델
![image](https://github.com/hanjhoon/Refit-master/assets/121271030/eb40abe6-ceeb-4391-b642-354a73b9ddde)

---

### ☑️ Information Architecture
![image](https://github.com/hanjhoon/Refit-master/assets/121271030/3bc3b96c-beb0-4ab8-b4bc-7f97824c9ca6)

---

### ☑️ Service Architecture
![image](https://github.com/hanjhoon/Refit-master/assets/121271030/00775810-81da-459e-a66b-1d51b7f75433)

---

### ☑️ API 설계
![image](https://github.com/hanjhoon/Refit-master/assets/121271030/bc8ee3dd-01bc-4633-b34b-2b0afa07cb5e)
![image](https://github.com/hanjhoon/Refit-master/assets/121271030/331666cc-97d8-473b-8ad5-0fe2ac57a476)

---


## ☑️ 상세 정보

- 카테고리
    - 의류/친환경
- 내용 및 기능
    - 옷 정리 관련 커뮤니티 기능
        - 옷 정리 팁 공유
            - 옷 정리 관련 질의 응답
            - 필요한 경우 GPT API 연결
        - 옷 무료 나눔
            - 일반 의류, 반려동물 옷, 아기 옷 등
    - 의류 서비스 관련 위치 정보
        - 짐 보관 장소 정보(여분 자리) 및 위치
        - 코인 빨래방 위치 정보 제공
        - 세탁소 위치 및 리뷰 제공
        - 헌 옷 수거함 위치
    - 옷장 내의 옷을 쉽게 분류하고 정리할 수 있는 기능
        - 옷장이 혼잡해서 옷을 찾기 어려운 경우
        - 옷의 상태를 기록하고 관리하는 것이 어려운 경우
        - 옷을 나누거나 기부하고 싶은 경우 (연계)
    - AI를 통한 의류 이미지 분석 및 매칭
        - 의류 카테고리 분류
        - 세탁 및 보관, 처리 방법, 팁 제공
        - 필요로 하는 사람, 업체 정보 리스트 제공
        - 해당 의류 관련 진행 중인 캠페인
        - 옷장 내의 옷을 쉽게 분류하고 정리할 수 있는 기능(연계)
    - 날씨 관련 의류 정보
        - 세탁하기 좋은 날(세탁 지수 제공)
        - 옷 정리가 적절한 시기 정보
    - 옷 정리 관련 가구 및 생활용품 정보
        - 옷 정리 팁 및 리뷰 공유를 통한 아래 상품 정보 연결 및 제공
            - 옷걸이
            - 선반
            - 행거
            - 습기제거제
            - 의류 스타일러 가전
    - 의류 관련 캠페인 정보 제공
        - 헌 옷 수거 불우 이웃 돕기 캠페인
        - 진행중인 업사이클링 캠페인

---

### ☑️ 구현 기술 내역

+ Back-End : 거리 기능별 추천 시스템, spring + 타 기술을 통한 AI 기능 탑재

  + 사랑의 옷체통 : 댓글, 옷 등록, 나눔이나 기부 시 적용되는 마일리지 시스템 추가

  + 각각 AI 캠페인, 의류 나눔 게시판, google map API 기반 근처 의류수거함 찾기, 캠페인 리스트로 설정

+ AI : 기본 옷 + 헌 옷 image classification, 분류, label별로 25만 → 4만장의 데이터셋

  + spring → flask API 요청 시 inference model을 통한 학습 진행 후 label + 정확도 결과 도출

  + efficient B0, MobileNet V2, diffusion + inception V3 등 여러 모델 시연 후 최상의 모델 선택

  + data argumentation, ensemble을 통해 정확도 개선 

+ Docker로 백엔드 컨테이너화 이후 flask와 연동, aws ec2를 통해 이미지 저장

  + 이미지 url을 json 형식으로 flask에 POST 하면 inference 후 다시 json 형식으로 ec2로 반환

---

### ☑️ 레퍼런스

[Image Classification | Papers With Code](https://paperswithcode.com/task/image-classification)

https://dacon.io/competitions

https://debuggercafe.com/transfer-learning-using-efficientnet-pytorch/

[Home | TensorFlow Hub (tfhub.dev)](https://tfhub.dev/)

[open-mmlab/mmdetection: OpenMMLab Detection Toolbox and Benchmark (github.com)](https://github.com/open-mmlab/mmdetection)

[ultralytics/ultralytics: NEW - YOLOv8 🚀 in PyTorch > ONNX > CoreML > TFLite (github.com)](https://github.com/ultralytics/ultralytics/tree/main)

[DeepLearningExamples/PyTorch/Classification/ConvNets/efficientnet at master · NVIDIA/DeepLearningExamples · GitHub](https://github.com/NVIDIA/DeepLearningExamples/tree/master/PyTorch/Classification/ConvNets/efficientnet)

---

### ☑️ 참고 자료

[https://www.notion.so/REFIT-243af98333744e3a90cb05431e2fc42f](https://www.notion.so/REFIT-243af98333744e3a90cb05431e2fc42f?pvs=21)

https://github.com/yuj0630/Refit

https://velog.io/@jaehyeong/Flask-%EC%9B%B9-%EC%84%9C%EB%B2%84-AWS-EC2%EC%97%90-%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0
