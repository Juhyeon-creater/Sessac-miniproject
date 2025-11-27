# [새싹 헬스케어 서비스 기획자 부트캠프 4기] Mini Project - Team 6
## **웨어러블 디바이스를 활용한 경도인지장애(MCI) 예측**
팀명 : 6조 (강주현, 장은정, 이진호, 이정민)

## 1. 프로젝트 소개
웨어러블 워치로 수집한 수면 패턴·활동량·심박수가 인지기능 저하와 유의미한 연관을 보임을 확인하였고, 이를 기반으로 경도인지장애를 조기 예측하는 머신러닝 모델 및 앱 서비스를 설계했습니다.

- 일정: 2025.10.17 - 2025.10.22
- 사용 데이터: AI-Hub(활동/수면/인지기능 검사 데이터)
- 목표: 라이프로그 + 인지기능 점수를 결합하여 MCI 위험도를 예측하는 모델 구축 및 서비스화
- 프로세스:
  
<img width="1599" height="409" alt="image" src="https://github.com/user-attachments/assets/e04e515b-3aa3-4c2c-9c85-146b68d66def" />


## 2. 진행 내용 상세
스마트워치에서 수집된 걸음 수, 활동량, 수면 단계, 심박수 등의 생체 데이터를 기반으로
다음 과정을 수행했습니다.

Raw 데이터 수집

결측·이상치 처리 및 정규화

활동·수면·인지 점수 매칭

EDA 및 주요 특징 생성

CatBoost·RandomForest 등 비교 모델 학습 및 평가

결과 해석을 기반으로 앱 서비스 기획


## 3. 시작가이드

### 📂 디렉토리 구조 (Directory Structure)

```bash
├── 📁 data/                         # 웨어러블 raw data
│   ├── 1. Training/                 # 훈련 데이터
│   └── 2. Validation/               # 검증 데이터
│
├── 📁 Analysis/                     # 데이터 분석 과정
│   ├── 1_project_template.ipynb          # 프로젝트 개발 템플릿
│   ├── 2_data_collection_template.ipynb  # 데이터 수집·전처리
│   ├── 3_EDA.ipynb                        # 탐색적 데이터 분석
│   └── 4_model_fit.ipynb                  # 모델 학습 및 평가
│
├── .gitignore                       # Git 업로드 제외 설정
└── README.md                        # 프로젝트 설명서
```
### ⬇️설치
```bash
# 레포지토리 클론
git clone https://github.com/Juhyeon-creater/Sessac-miniproject.git

# 패키지 설치
pip install -r requirements.txt

# 실행 (원하는 모드 선택)
python main.py
```



## Stacks

**Environment**
<br>
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white)
![Anaconda](https://img.shields.io/badge/Anaconda-%2344A833.svg?style=for-the-badge&logo=anaconda&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
<br>
**Development & AI**
<br>
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![YOLO](https://img.shields.io/badge/YOLO-111F68?style=for-the-badge&logo=yolo&logoColor=white)
![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
<br>
**Communication**
<br>
![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=for-the-badge&logo=notion&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)
![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)
<br>
**Hardware**
<br>
![Raspberry Pi](https://img.shields.io/badge/-Raspberry_Pi-C51A4A?style=for-the-badge&logo=Raspberry-Pi)
<img src="https://img.shields.io/badge/Sensor-MPU6050-blue?style=for-the-badge" alt="MPU6050">
<br>
