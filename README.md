<div align="center">

<img src="./assets/profile_banner.svg" alt="김수진 AI Developer 프로필 배너" width="100%">

<br>

[![Vision AI](https://img.shields.io/badge/Vision_AI-21AFC4?style=flat-square)](https://github.com/lightleaping/manufacturing-vision-defect-analysis-system)
[![Manufacturing Data](https://img.shields.io/badge/Manufacturing_Data-3561D8?style=flat-square)](https://github.com/lightleaping/manufacturing-ai-quality-agent-reference)
[![NLP & Agent](https://img.shields.io/badge/NLP_%26_Agent-151F32?style=flat-square)](https://github.com/lightleaping/manufacturing-mcp-agent)
![Python](https://img.shields.io/badge/Python-3561D8?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-21AFC4?style=flat-square&logo=pytorch&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-151F32?style=flat-square&logo=fastapi&logoColor=white)

</div>

---

## Project Map

<img src="./assets/manufacturing_ai_project_map.svg" alt="Manufacturing AI Project Map" width="100%">

---

## Job Fit Summary

| 공고 핵심 | 프로젝트에서 보여주는 근거 |
|---|---|
| **Vision** | ResNet18 이미지 분류 · Faster R-CNN 객체 탐지 · OpenCV · 오분류 및 Detection 실패 분석 |
| **Time Series / Data** | RNN·LSTM 기본 구조 학습 · 센서 AutoEncoder 이상 탐지 · 설비 상태 Feature 기반 고장 예측 |
| **NLP** | 제조 질문 Intent·Router·Tool·Evidence · BM25/Dense Retrieval · Section Boost |
| **AI Service Solution** | PyTorch Model → FastAPI → Streamlit·SQLite · 입력 검증 · API·통합 테스트 |

> **주요 개발 언어와 프레임워크:** Python · PyTorch · FastAPI  
> **평가 방식:** Accuracy · Precision · Recall · F1 · mAP · IoU · Confusion Matrix · 실패 사례 분석

---

# Featured Projects

## 01 · 제조 표면 결함 Vision AI

[![Repository](https://img.shields.io/badge/Repository-151F32?style=flat-square&logo=github&logoColor=white)](https://github.com/lightleaping/manufacturing-vision-defect-analysis-system)
![Vision](https://img.shields.io/badge/Vision-21AFC4?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-3561D8?style=flat-square)

| 구분 | 내용 |
|---|---|
| **Problem** | 이미지 전체의 정상·불량 판정만으로는 결함의 종류와 위치를 확인하기 어려웠습니다. |
| **Implementation** | CNN Baseline과 ResNet18 분류를 비교하고, Faster R-CNN으로 6종 표면 결함을 탐지했습니다. 오분류·누락·위치 오류·중복·클래스 혼동을 분석한 뒤 FastAPI와 Streamlit으로 연결했습니다. |
| **Evaluation** | **DEFECT-class F1 97.92%** · **Test mAP@0.50 0.7077** · Mean Matched IoU 0.7523 |
| **Project Info** | **2026.07 · 개인 프로젝트** · 데이터 분석·모델 개발·평가·실패 분석·API·화면·테스트·문서화 전반 |

---

## 02 · AI4I 기반 설비 고장 예측

[![Repository](https://img.shields.io/badge/Repository-151F32?style=flat-square&logo=github&logoColor=white)](https://github.com/lightleaping/manufacturing-ai-quality-agent-reference)
![Equipment AI](https://img.shields.io/badge/Equipment_AI-3561D8?style=flat-square)
![Agent](https://img.shields.io/badge/Agent-21AFC4?style=flat-square)

| 구분 | 내용 |
|---|---|
| **Problem** | 고장 Class가 약 3.4%인 불균형 데이터에서는 Accuracy만으로 고장 탐지 성능을 판단하기 어렵고, 예측 확률만으로는 판단 과정과 입력 특성의 영향을 확인하기 어려웠습니다. |
| **Implementation** | PyTorch MLP에 `pos_weight`, StandardScaler와 Threshold 비교를 적용했습니다. Prediction·Rule·SHAP Evidence, LangGraph Workflow, Trace와 SQLite History를 FastAPI·Streamlit으로 연결했습니다. |
| **Evaluation** | **Recall 82.35% · Precision 30.60% · F1 44.62%** · Agent Evaluation **6/6 PASS** |
| **Project Info** | **2026.05–2026.07 · 개인 프로젝트** · 데이터 전처리·모델·Agent·Evidence·API·Dashboard·평가·문서화 전반 |

> 고장 누락을 줄이는 방향으로 Recall을 우선했지만 오탐이 남아 있으며, 실제 적용 시 고장 누락 비용과 점검 비용을 기준으로 Threshold를 다시 결정해야 합니다.

---

## 03 · 제조 품질 분석 NLP Agent

[![Repository](https://img.shields.io/badge/Repository-151F32?style=flat-square&logo=github&logoColor=white)](https://github.com/lightleaping/manufacturing-mcp-agent)
![NLP](https://img.shields.io/badge/NLP-151F32?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-3561D8?style=flat-square)

| 구분 | 내용 |
|---|---|
| **Problem** | 불량률·센서 이상·라인 성능·원인 후보처럼 제조 질문마다 필요한 데이터와 계산 기능이 달랐습니다. |
| **Implementation** | 질문을 Intent로 분류하고 Router가 4개 제조 Tool 중 필요한 기능을 선택해 Answer와 Evidence를 반환하도록 구현했습니다. AutoEncoder 모델 Endpoint, Docker와 GitHub Actions도 구성했습니다. |
| **Evaluation** | **4 Intents · 4 Tools · 2 Endpoints · 9 핵심 테스트** |
| **Project Info** | **2026.04–2026.05 · 개인 프로젝트** · 제조 데이터·Intent·Router·Tool·Evidence·FastAPI·CI 구현 |

---

## 04 · 다변량 센서 이상 탐지

[![Repository](https://img.shields.io/badge/Repository-151F32?style=flat-square&logo=github&logoColor=white)](https://github.com/lightleaping/sensor-anomaly-model-pipeline)
![Sensor](https://img.shields.io/badge/Sensor_Data-3561D8?style=flat-square)
![AutoEncoder](https://img.shields.io/badge/AutoEncoder-21AFC4?style=flat-square)

| 구분 | 내용 |
|---|---|
| **Problem** | 여러 센서값을 개별 임계값으로만 판단하면 변수 간 정상 패턴에서 벗어난 상태를 하나의 이상 점수로 확인하기 어렵습니다. |
| **Implementation** | 온도·진동·압력·습도 데이터를 전처리하고 정상 데이터로 AutoEncoder를 학습했습니다. Validation Reconstruction Error의 95 Percentile로 Threshold를 정하고 CLI와 FastAPI 추론으로 연결했습니다. |
| **Evaluation** | Accuracy·Precision·Recall·F1·Confusion Matrix 평가 · 샘플 이상 데이터 **Recall 1.0** |
| **Project Info** | **개인 프로젝트** · 데이터 생성·전처리·학습·Threshold·평가·CLI·API·문서화 전반 |

> 샘플·합성 데이터 기반 결과이며 실제 설비의 시간 순서, Noise, Drift와 운영 비용을 반영한 성능으로 표현하지 않습니다.

---

## 05 · 공정거래 의결서 NLP 검색

[![Repository](https://img.shields.io/badge/Repository-151F32?style=flat-square&logo=github&logoColor=white)](https://github.com/lightleaping/fair-decision-rag)
![Team Project](https://img.shields.io/badge/Team_Project-3561D8?style=flat-square)
![Retrieval](https://img.shields.io/badge/Retrieval-21AFC4?style=flat-square)

| 구분 | 내용 |
|---|---|
| **Problem** | 긴 공정거래 의결서에서 질문과 관련된 근거 구간을 직접 찾고 원문 위치를 추적하기 어려웠습니다. |
| **Implementation** | Query Classification, Dense Retrieval Baseline, Section Boost와 Top-5 검색 결과 평가를 담당했습니다. 팀장으로 목표·기술 역할·개발 일정·MVP 범위를 관리했습니다. |
| **Evaluation** | 중복 없는 Top-5 `chunk_id` 규칙 · 검색 결과 O/△/X 수동 평가 · 실패 사례와 검색 기준 개선 |
| **Project Info** | **공모전 팀 프로젝트 · Team Lead** · 주간 회의·Sprint·일정 조율·범위 관리·통합 검증 |

---

## Development Approach

| 01 · DATA | 02 · MODEL | 03 · VERIFY | 04 · SERVICE |
|---|---|---|---|
| 구조·분포·품질·Split 확인 | Baseline 이후 개선 모델 비교 | 지표·오분류·실패 사례와 한계 확인 | API·화면·입력 검증·테스트 연결 |

```text
문제와 필요성 정의
→ 데이터 분석
→ Baseline 구현
→ 개선 모델 비교
→ 정량 평가
→ 실패 사례 분석
→ FastAPI와 사용자 화면 연결
→ 테스트와 문서화
```

---

## Collaboration & Team Leadership

공모전 프로젝트에서 팀장으로 다음 과정을 운영했습니다.

- 공모전 요구 조건을 기준으로 목표·필수 기능·MVP 범위 결정
- 기술 기능별 담당 파트와 완료 시점 설정
- Timepick과 Notion으로 주간 회의·Sprint·회의록·일정 관리
- GitHub를 통해 구현 진행도와 파트 간 연결 상태 확인
- 일정 지연 시 일부 구현 범위를 재분배하고 필수 기능을 우선해 제출 일정 관리

---

## Core Stack

| 영역 | 기술 |
|---|---|
| **Language / Data** | Python · SQL · pandas · NumPy · scikit-learn |
| **AI / Deep Learning** | PyTorch · torchvision · CNN · ResNet18 · Faster R-CNN · MLP · AutoEncoder |
| **Vision** | Image Classification · Object Detection · OpenCV · Grad-CAM |
| **NLP / Agent** | Intent Classification · Router · Tool · Evidence · LangGraph · MCP · OpenAI API |
| **Retrieval** | BM25 · Dense Retrieval · FAISS · Section Boost · Top-K · Evidence Trace |
| **Backend / Service** | FastAPI · Pydantic · REST API · Streamlit · SQLite |
| **Verification / Development** | pytest · Git · GitHub · Docker · GitHub Actions |

---

<details>
<summary><b>Experience Scope & Limitations</b></summary>

<br>

- AI4I 프로젝트는 시간 순서 Window를 사용하는 시계열 예측이 아니라 설비 상태 Feature 기반 고장 위험 분류입니다.
- RNN·LSTM은 전공 과정에서 기본 구조를 학습했으며, 프로젝트에서는 센서 이상 탐지와 설비 상태 기반 예측을 구현했습니다.
- Grad-CAM은 모델의 확정적인 판단 근거가 아니라 상대적으로 강하게 반응한 영역을 확인하는 보조 분석으로 사용했습니다.
- Detection은 Test mAP@0.50 0.7077을 기록했지만 Recall 0.5268로 결함 누락이 남아 있습니다.
- 제조 프로젝트는 공개 데이터와 샘플 데이터를 사용했으며 실제 반도체·디스플레이 생산라인 운영 경험으로 과장하지 않습니다.
- 모델 결과는 높은 수치만 선택하지 않고 Precision·Recall Trade-off와 실패 사례를 함께 설명합니다.

</details>

---

## Contact

- **GitHub**: [github.com/lightleaping](https://github.com/lightleaping)
- **Email**: workingskyroad@gmail.com
