# [새싹 헬스케어 서비스 기획자 부트캠프 4기] Mini Project - Team 6
## **웨어러블 디바이스를 활용한 경도인지장애(MCI) 예측**
팀명 : 6조 (강주현, 장은정, 이진호, 이정민)

## 1. 프로젝트 개요
경도인지장애(MCI) 환자의 생활 패턴 데이터를 분석하여 치매로의 전환을 예측하는 머신러닝 프로젝트입니다. 
수면 패턴, 활동량, 휴식 시간 등의 생활 데이터를 활용하여 조기 진단 및 예방 관리를 지원합니다.

## 2.프로젝트 목표
- MCI 환자의 치매 전환 위험도 예측 (정상인 vs 경도인지장애 환자 분류)
- 생활 패턴과 치매 발병 간의 상관관계 분석
- 치매 예측에 영향을 미치는 핵심 Feature 도출

- 일정: 2025.10.03 - 2025.10.22 (3주)
- 사용 데이터: AI-Hub(활동/수면/인지기능 검사 데이터)
- 목표: 라이프로그 + 인지기능 점수를 결합하여 MCI 위험도를 예측하는 모델 구축 및 서비스화
- 프로세스:
  
<img width="1599" height="409" alt="image" src="https://github.com/user-attachments/assets/e04e515b-3aa3-4c2c-9c85-146b68d66def" />

- Team 6 멤버
  - 강주현(나) : 데이터 수집, 전처리, 상관관계 분석, 최종 발표
  - 서비스기획1 : 서비스 기획, 디자인
  - 데이터분석2 : 모델 평가, 하이퍼파라미터 튜닝

- 데이터 출처
AI-Hub: [경도인지장애 환자 생활 데이터](https://aihub.or.kr/)
  - 300명 | 총 3,9000건
  - 활동 데이터 (15,000 건 | 시계열 데이터)
  - 수면 데이터 (15,000 건 | 시계열 데이터)
  - MMSE 인지기능 검사 (9,000 건 | 진단 레이블: CN(정상)/MCI(경증)/Dem(중증))

## 3. 진행 내용 상세
스마트워치에서 수집된 걸음 수, 활동량, 수면 단계, 심박수 등의 생체 데이터를 기반으로
다음 과정을 수행했습니다.

Raw 데이터 수집 -> 결측·이상치 처리 및 정규화 -> 활동·수면·인지 점수 매칭 -> EDA 및 주요 특징 생성 -> CatBoost·RandomForest 등 비교 모델 학습 및 평가 -> 결과 해석을 기반으로 앱 서비스 기획


## 4. 시작가이드

### 📂 디렉토리 구조 (Directory Structure)

```bash
├── 📁 data/                         # 웨어러블 raw data
│   ├── Training/                 # 훈련 데이터
│   └── Validation/               # 검증 데이터
│
├── 📁 Analysis/                     # 데이터 분석 과정
│   ├── 1_project_template.ipynb          # 프로젝트 개발 템플릿
│   ├── 2_data_collection_template.ipynb  # 데이터 수집·전처리
│   ├── 3_EDA.ipynb                        # 탐색적 데이터 분석
│   └── 4_model_fit.ipynb                  # 모델 학습 및 평가
│
├── 📁 results/                           # 시각화
│   ├── CN_delta.png
│   ├── Dem_delta.png
│   └── Feature Importance.png
├── requirements.txt         
└── README.md                        # 프로젝트 설명서
```

## Stacks

**Environment**  
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white)
![Anaconda](https://img.shields.io/badge/Anaconda-%2344A833.svg?style=for-the-badge&logo=anaconda&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05033.svg?style=for-the-badge&logo=git&logoColor=white)

**Development & AI**  
![Python](https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![CatBoost](https://img.shields.io/badge/CatBoost-FFCC00?style=for-the-badge)
![Matplotlib](https://img.shields.io/badge/Matplotlib-white?style=for-the-badge&logo=matplotlib&logoColor=black)
![Seaborn](https://img.shields.io/badge/Seaborn-4C8CB5?style=for-the-badge)

**Communication**  
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)
![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)

