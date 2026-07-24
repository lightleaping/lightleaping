<div align="center">

<img src="./assets/profile-banner.svg" alt="김수진 AI Developer 프로필 배너" width="100%">

<br>

[![Python](https://img.shields.io/badge/Python-3561D8?style=flat-square&logo=python&logoColor=white)](#core-stack)
[![PyTorch](https://img.shields.io/badge/PyTorch-21AFC4?style=flat-square&logo=pytorch&logoColor=white)](#core-stack)
[![Vision AI](https://img.shields.io/badge/Vision_AI-151F32?style=flat-square)](#selected-projects)
[![NLP & Agent](https://img.shields.io/badge/NLP_%26_Agent-3561D8?style=flat-square)](#selected-projects)
[![FastAPI](https://img.shields.io/badge/FastAPI-21AFC4?style=flat-square&logo=fastapi&logoColor=white)](#core-stack)

</div>

---

## At a Glance

| **VISION AI** | **EQUIPMENT · SENSOR DATA** |
|---|---|
| ResNet18 분류 · Faster R-CNN 객체 탐지 · OpenCV · Grad-CAM · 실패 사례 분석 | AI4I MLP 고장 예측 · SHAP · Threshold · AutoEncoder 학습·평가 코드 기반 센서 파이프라인 |
| **NLP · AGENT** | **AI SERVICE SOLUTION** |
| Intent · Router · Tool · Evidence · BM25/Dense Retrieval · 연도별 논문 키워드 분석 | PyTorch Model · FastAPI · Streamlit · SQLite · Docker · API·통합 테스트 |

> **지원 직무 연결:** Vision · Time Series 관련 학습/센서 데이터 · NLP · 데이터 처리·분석 · Python · PyTorch · AI 서비스 구현  
> AI4I 프로젝트는 순차 Window 기반 시계열 예측이 아닌 **설비 상태 Feature 기반 분류**이며, RNN·LSTM은 전공 학습 경험으로 구분합니다.

---

## Project Map

<img src="./assets/ai-project-map.svg" alt="AI Project Map" width="100%">

---

# Selected Projects

| 프로젝트 | 핵심 구현 | 평가·역할 |
|---|---|---|
| **[제조 표면 결함 Vision AI](https://github.com/lightleaping/manufacturing-vision-defect-analysis-system)** | ResNet18 분류 · Faster R-CNN 6종 결함 탐지 · 실패 분석 · FastAPI · Streamlit | **DEFECT-class F1 97.92%** · **mAP@0.50 0.7077**<br>2026.07 · 개인 · 전 과정 구현 |
| **[AI4I 기반 설비 고장 예측](https://github.com/lightleaping/manufacturing-ai-quality-agent-reference)** | PyTorch MLP · 불균형 대응 · SHAP · LangGraph · Trace · SQLite | **Recall 82.35% · F1 44.62%** · Agent **6/6 PASS**<br>2026.05–07 · 개인 · 모델/Agent/API |
| **[제조 품질 분석 NLP Agent](https://github.com/lightleaping/manufacturing-mcp-agent)** | Question → Intent → Router → 4 Tools → Answer + Evidence | **4 Intents · 4 Tools · 2 Endpoints**<br>2026.04–05 · 개인 · Workflow/API/CI |
| **[다변량 센서 이상 탐지](https://github.com/lightleaping/sensor-anomaly-model-pipeline)** | 전처리 · 4→8→2→8→4 AutoEncoder · 학습/평가 Loop · Threshold · CLI/API 구조 | **파이프라인 구현 범위**<br>공개 Model·History·평가 Artifact 미보관 |
| **[공정거래 의결서 NLP 검색](https://github.com/lightleaping/fair-decision-rag)** | Query Classification · Dense Baseline · Section Boost · Top-5 Evidence | 공모전 **Team Lead** · 검색 평가 · Sprint/범위/통합 관리 |
| **[임상 의학 논문 NLP 동향 분석](https://github.com/lightleaping/clinical-medical-paper-nlp-trend-analysis)** | 팀원별 Web Scraping · 주제 선정 · 연도별 키워드 · WordCloud · 보고서 | 2025.03.04–06.24 · 전공 팀 프로젝트<br>개인 Scraping 코드 · **보고서 결론 작성** |

---

## Project Details

<details open>
<summary><b>01 · 제조 표면 결함 Vision AI — 분류·객체 탐지·실패 분석·서비스 연결</b></summary>

<br>

**Problem**  
이미지 전체의 정상·불량 여부뿐 아니라 결함의 종류와 위치를 함께 확인할 필요가 있었습니다.

**Implementation**
- Casting Product Image Data 7,348장 분석과 Train·Validation·Test 분할
- CNN Baseline과 ResNet18 전이학습을 동일 평가 기준으로 비교
- 오분류를 False Positive·False Negative로 구분하고 Grad-CAM으로 모델 반응 영역 확인
- NEU Surface Defect 1,800장, 6 Class Faster R-CNN 객체 탐지
- 누락·저확신·위치 오류·중복·클래스 혼동 분석
- FastAPI 분류·검출 Endpoint와 Streamlit 입력 화면 연결

**Evaluation**
- Classification Accuracy **97.34%**
- DEFECT-class F1 **97.92%**
- Detection Precision **0.812950**
- Detection Recall **0.526807**
- Detection F1 **0.639321**
- Test mAP@0.50 **0.707726**
- Mean Matched IoU **0.752338**

**Scope & Role**  
2026.07 · 개인 프로젝트 · 데이터 분석·모델·평가·실패 분석·API·화면·테스트·문서화 전반

**Limit**  
분류와 객체 탐지는 서로 다른 공개 데이터셋을 사용했습니다. Grad-CAM은 확정적인 판단 근거가 아니라 모델 반응 영역을 확인하는 보조 분석입니다.

</details>

<details>
<summary><b>02 · AI4I 기반 설비 고장 예측 — 모델·Evidence·Agent Trace</b></summary>

<br>

**Problem**  
고장 Class가 약 3.4%인 불균형 데이터에서는 Accuracy만으로 성능을 판단하기 어렵고, 예측 확률만으로는 판단 과정과 입력 특성의 영향을 확인하기 어려웠습니다.

**Implementation**
- 6개 설비 상태 Feature, StandardScaler, PyTorch MLP
- `pos_weight`와 Threshold 0.50–0.90 비교
- Prediction·Rule·SHAP Local·Permutation Importance Evidence
- LangGraph Routing, Trace Event, SQLite 실행 이력
- FastAPI Prediction·Agent·History API와 Streamlit Dashboard
- MCP stdio Tool 연결

**Evaluation**
- Accuracy **0.9305**
- Precision **0.3060**
- Recall **0.8235**
- F1 **0.4462**
- Deterministic Agent Evaluation **6/6 PASS**

**Scope & Role**  
2026.05–2026.07 · 개인 프로젝트 · 전처리·모델·Evidence·Agent·API·Dashboard·평가 전반

**Limit**  
Recall을 우선해 고장 누락을 줄였지만 오탐이 남아 있습니다. 실제 적용 시 고장 누락 비용과 점검 비용을 기준으로 Threshold를 다시 결정해야 합니다.

</details>

<details>
<summary><b>03 · 제조 품질 분석 NLP Agent — 질문을 제조 Tool과 Evidence로 연결</b></summary>

<br>

**Problem**  
불량률·센서 이상·라인 성능·원인 후보처럼 제조 질문마다 필요한 데이터와 계산 기능이 달랐습니다.

**Flow**
```text
사용자 질문 → Intent → Router → 제조 Tool → Answer + Evidence
```

**Implementation**
- `defect_rate`
- `sensor_anomaly`
- `line_performance`
- `quality_issue_candidates`
- `/agent/query`
- `/model/sensor-anomaly`
- Docker·GitHub Actions·pytest

**Evaluation**
- **4 Intents**
- **4 Tools**
- **2 Endpoints**
- **9 핵심 테스트**

**Scope & Role**  
2026.04–2026.05 · 개인 프로젝트 · 제조 데이터·Intent·Router·Tool·Evidence·FastAPI·CI 구현

**Limit**  
규칙 기반 `risk_score`는 머신러닝 원인 확률이 아니라 우선 점검 후보를 좁히는 휴리스틱입니다.

</details>

<details>
<summary><b>04 · 다변량 센서 이상 탐지 — 학습·평가·추론 파이프라인 구조</b></summary>

<br>

**Problem**  
Scale이 다른 온도·진동·압력·습도 데이터를 동일한 전처리와 이상 판별 흐름으로 연결할 필요가 있었습니다.

**Implementation**
- 데이터 생성·결측치 처리·Split·StandardScaler
- 4→8→2→8→4 AutoEncoder
- MSE Loss·Adam·학습/검증 Loop 코드
- Reconstruction Error와 Validation Percentile Threshold
- CLI와 FastAPI `/predict` 구조

**Verification**  
공개 코드에서 전처리·모델·학습·평가·추론 구조는 확인되지만, 저장된 Model·History·평가 Artifact는 공개돼 있지 않습니다.

**Scope & Role**  
개인 프로젝트 · AutoEncoder를 이용한 이상 탐지 **파이프라인 구현 경험**

**Limit**  
실행 완료 성능 수치나 운영 성능을 주장하지 않습니다.

</details>

<details>
<summary><b>05 · 공정거래 의결서 NLP 검색 — 검색 품질과 팀 프로젝트 운영</b></summary>

<br>

**Problem**  
긴 의결서에서 질문과 관련된 근거 구간을 중복 없이 찾고 원문 위치를 추적할 필요가 있었습니다.

**Implementation**
- Query Classification
- Dense Retrieval Baseline
- Section Boost
- 중복 없는 Top-5 `chunk_id`
- 검색 결과 O/△/X 수동 평가와 실패 사례 분석

**My Role**
- 공모전 Team Lead
- 질문 분류·Dense Baseline·Section Boost·검색 결과 평가
- 목표·역할·MVP 범위 설정
- Timepick·Notion 기반 주간 회의와 Sprint 운영
- 일정 변동 시 범위 재조정과 통합 상태 확인

**Limit**  
프로필에서는 인원수를 강조하지 않으며, 최종 Source 공개 범위와 실행 가능 상태는 저장소 README에서 구분합니다.

</details>

<details>
<summary><b>06 · 임상 의학 논문 NLP 동향 분석 — 연도별 키워드와 WordCloud</b></summary>

<br>

**Problem**  
관련 논문이 지속적으로 축적되는 임상 의학 분야에서 시기별 관심 주제와 기술 변화의 방향을 비교할 필요가 있었습니다.

**Process**
```text
팀원별 Web Scraping 코드 구현
→ 수집 가능 주제 논의
→ 임상 의학 선정
→ 연도별 논문 데이터 구분
→ 핵심 키워드 분석
→ WordCloud 시각화
→ 보고서 제출
```

**My Role**
- 개인 Python Web Scraping 코드 1개 구현
- 자료량·연도 정보·동향 분석 가능성을 고려한 주제 선정 논의 참여
- 연도별 키워드와 WordCloud 결과를 종합한 **보고서 결론 파트 작성**

**Project Info**  
2025.03.04–2025.06.24 · 동양미래대학교 · 전공 팀 프로젝트

**Limit**  
원본 Source·Dataset·WordCloud·보고서가 현재 보관돼 있지 않아 Documentation-only Case Study로 구분합니다. 모델 학습이나 정량 NLP 성능을 주장하지 않습니다.

</details>

---

## Core Stack

| 영역 | 기술 |
|---|---|
| **Language / Data** | Python · SQL · pandas · NumPy · scikit-learn |
| **AI / Vision** | PyTorch · torchvision · CNN · ResNet18 · Faster R-CNN · MLP · AutoEncoder · OpenCV · Grad-CAM |
| **NLP / Agent / Retrieval** | Intent · Router · Tool · Evidence · LangGraph · MCP · BM25 · Dense Retrieval · Section Boost |
| **Backend / Service** | FastAPI · Pydantic · Streamlit · SQLite · REST API |
| **Verification / Development** | pytest · Git · GitHub · Docker · GitHub Actions |

---

<details>
<summary><b>Evidence & Scope Principles</b></summary>

<br>

- 모델 수치는 저장 Artifact와 실행 로그로 확인한 범위만 표기합니다.
- AI4I 상태 Feature 분류와 순차 시계열 예측을 구분합니다.
- 전공 학습, 구현 코드, 실행 완료 결과와 운영 경험을 같은 수준으로 표현하지 않습니다.
- Grad-CAM을 모델의 확정적인 판단 근거라고 표현하지 않습니다.
- Source나 결과 Artifact가 없는 프로젝트는 Documentation-only 또는 Pipeline Implementation으로 구분합니다.
- 높은 수치뿐 아니라 Precision·Recall Trade-off, 실패 사례와 남은 한계를 함께 설명합니다.
- 제조 프로젝트는 공개·샘플 데이터 기반이며 실제 생산라인 운영 경험으로 과장하지 않습니다.

</details>

---

## Contact

- **GitHub**: [github.com/lightleaping](https://github.com/lightleaping)
- **Email**: workingskyroad@gmail.com

<!-- 공개용 포트폴리오 PDF를 업로드한 뒤 아래 링크를 활성화하세요.
- **Portfolio**: [AI Developer Portfolio](./docs/portfolio/soojin-kim-ai-developer-portfolio-public.pdf)
-->
