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
AI-Hub: [치매 고위험군 웨어러블 라이프로그]([https://aihub.or.kr/](https://www.aihub.or.kr/aihubdata/data/view.do?pageIndex=1&currMenu=&topMenu=&srchOptnCnd=OPTNCND001&searchKeyword=%EC%84%BC%EC%84%9C&srchDetailCnd=DETAILCND001&srchOrder=ORDER002&srchPagePer=20&srchDataRealmCode=REALM006&aihubDataSe=data&dataSetSn=226))
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

## 5. 프로젝트 결과
- CN vs Dem — Dual-Axis Feature Comparison: 정상군(CN)과 치매군(Dem)의 수면 점수 및 활동량 비교 분석 결과
  - 정상군은 치매군보다 수면 점수가 약 8점 높았으며(78.5 vs 70.5) 일일 활동량은 약 1.76배 많았습니다(370 vs 210).
    이는 양질의 수면과 활발한 신체 활동이 인지 기능 유지에 핵심적인 역할을 하며 두 지표를 결합하면 치매 조기 예측의 주요 바이오마커로 활용할 수 있음을 시사합니다.
<img width="890" height="589" alt="image" src="https://github.com/user-attachments/assets/ffc00874-64fd-4614-ac1d-3a346e329dcb" />


- 활동 총량과 수면주기 변화량 간의 관계 (99% 신뢰구간): 정상군(파란색)과 진단군(주황색)의 활동량과 수면 패턴 변화 상관관계 분석
  - 활동량이 증가할수록 수면주기 변화량이 감소하는 음의 상관관계를 보이며 특히 진단군(주황색)은 활동량이 낮은 구간에서 수면 변화량의 편차가 크게 나타납니다.
    이는 규칙적인 신체 활동이 안정적인 수면 패턴 유지에 기여하며 활동량 저하 시 수면 불안정성이 증가함을 의미합니다.
<img width="789" height="580" alt="image" src="https://github.com/user-attachments/assets/17db6d0f-867d-40f7-b18c-7dd73edc177d" />


- 휴식시간과 알으잠 길이 간의 관계 (정상군 vs 진단군, 99% 신뢰구간): 정상군(CN)과 진단군(Dem)의 휴식시간과 수면 길이의 상관관계 분석
  - 휴식시간이 증가할수록 수면 길이가 선형적으로 증가하는 강한 양의 상관관계를 보이며 진단군(주황색)이 정상군(파란색)보다 전 구간에서 약간 더 높은 수면 시간을 기록합니다.
    이는 치매군이 신체적 피로 회복을 위해 더 많은 수면 시간이 필요하거나 과도한 수면이 인지 저하의 신호일 수 있음을 시사합니다.
<img width="720" height="481" alt="image" src="https://github.com/user-attachments/assets/1034bbf4-685f-4d1a-a811-3d1ab197bf72" />


- 정상군 vs 진단군 — 깊은 수면 점수 & 수면시 최저 심박수: 정상군과 진단군의 수면의 질 및 생리적 지표 비교 분석
  - 정상군은 진단군보다 깊은 수면 점수(90 vs 57)와 최저 심박수(60 vs 51)가 모두 높게 나타나 정상군이 더 안정적이고 양질의 수면을 취하고 있음을 보여줍니다.
    진단군의 낮은 수면 점수와 심박수는 자율신경계 기능 저하 및 수면 중 생리적 회복 능력 감소를 의미하며 이는 인지 기능 저하와 밀접한 관련이 있습니다.
<img width="1189" height="589" alt="image" src="https://github.com/user-attachments/assets/f93b537a-98eb-4c98-a651-9d8b4197032f" />


- 정상군 vs 진단군 — 총 활동량 & 휴식 시간: 정상군과 진단군의 일일 활동 패턴 및 휴식 시간 비교 분석
  - 정상군은 총 활동량(410)이 진단군(260)보다 약 1.58배 높지만 휴식 시간은 정상군(490)이 진단군(610)보다 약 120분 적어 정상군이 더 활동적이면서도 효율적인 에너지 관리를 하고 있음을 보여줍니다.
    진단군의 낮은 활동량과 긴 휴식 시간은 신체적 활력 저하와 과도한 피로감을 반영하며 이는 치매 환자의 전형적인 생활 패턴 변화를 나타냅니다.
<img width="1189" height="589" alt="image" src="https://github.com/user-attachments/assets/96c8b820-e9c5-40b4-850c-4977c9ec283e" />


- 정상군 — 수면 시간 변동성
  - 정상군은 약 2년간 수면 시간이 대체로 안정적이며 평균 10,000-20,000 범위 내에서 변동하고 2-3회의 일시적 스파이크(80,000 수준)를 제외하면 일관된 패턴을 유지합니다.
<img width="1990" height="489" alt="image" src="https://github.com/user-attachments/assets/e3664a02-cdd6-44ad-9b85-82d92a8ad09e" />


- 진단군 — 수면 시간 변동성
  - 진단군은 수면 시간의 변동성이 매우 크고 불규칙하며, 주기적으로 높은 피크(100,000 수준)가 반복되고 다양한 색상의 라인들이 서로 다른 패턴을 보여 개인 간 수면 패턴 차이가 크고 전반적으로 불안정한 수면 상태를 나타냅니다.
<img width="1990" height="489" alt="image" src="https://github.com/user-attachments/assets/dc63e45c-ba33-4536-b1ef-423ac35ce373" />


- 정상군 상관계수 (activity vs sleep)
  - 정상군은 진단군보다 상관관계가 더 약하고 균일하며(대부분 연한 파란색/흰색) activity_rest를 제외하면 활동량과 수면 지표 간의 명확한 연관성이 적어 정상군이 활동과 수면을 독립적으로 조절하며 안정적인 생체 리듬을 유지함을 시사합니다.
<img width="1122" height="784" alt="image" src="https://github.com/user-attachments/assets/9ff0acf0-3fd9-4b79-a4ec-c64e4077ec95" />


- 진단군 상관계수 (activity vs sleep)
  - 진단군은 활동량과 수면 지표 간 상관관계가 불균일하며 특히 activity_rest와 일부 수면 지표(sleep_duration, sleep_light, sleep_midpoint_delta 등) 간에 약한 양의 상관관계(주황색)가 관찰되나 전반적으로 뚜렷한 패턴이 없어 생활 리듬의 불규칙성을 보여줍니다.
<img width="1122" height="784" alt="image" src="https://github.com/user-attachments/assets/bc773a1e-fd60-418d-8c33-bd1980199498" />



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

