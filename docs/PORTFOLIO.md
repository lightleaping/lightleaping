# 김수진 | 프로젝트 포트폴리오

**Vision·딥러닝·LLM/Agent를 실제 서비스로 연결하는 개발을 지향합니다.**

Python 기반 AI 서비스·Backend 개발을 목표로, 네 프로젝트를 통해 데이터·모델·서비스·Agent의 연결을 직접 구현하고 검증하려 합니다.

> 현재 공개 자료는 프로젝트 설계와 학습 미션입니다. 아래 기능과 기술은 구현 목표이며, 완성 데모·신규 평가 수치는 아직 없습니다.

## 프로젝트별 관점

| 프로젝트 | 핵심 질문 | 평가 방향 |
|---|---|---|
| Structured Bloom | 사용자 조건에 맞는 추천을 안정적인 서비스로 제공할 수 있는가? | 조건 준수·기록 일관성·AI 기능 비교 |
| 이상탐지·분석 Agent | 사례 기반 오류를 찾고 원인 후보를 근거와 함께 설명할 수 있는가? | 검출·오탐·지연·원인 후보·보고서 근거 |
| 코디 추천·보드 | 실제 상품을 적절한 조합으로 추천하고 정확한 이미지로 보여줄 수 있는가? | 조합 평가·조건 준수·상품 추적·보드 품질 |
| 캐릭터 엔진 | 기억과 상태를 유지하며 유효한 행동만 실행할 수 있는가? | 기억 검색·상태 일관성·행동 검증 |

---

## 01. Structured Bloom

**AI 서비스 · Backend · Streamlit 재구현 준비**

쉴 시간이 생겨도 무엇을 할지 정하기 어려운 사용자가 간단한 입력으로 활동을 선택하도록 돕는 서비스입니다.

- **입력:** 현재 기분, 사용 가능한 시간, 활동 피드백
- **목표 출력:** 추천 활동, 추천 이유, 활동 이력
- **적용 예정 기술:** Python · Streamlit · FastAPI · SQLite, 필요 시 PostgreSQL
- **첫 작업:** 기분과 시간을 입력받아 활동 하나를 보여주는 화면.

화면은 Streamlit으로 구현합니다. React·JavaScript 직접 개발은 이번 범위에 포함하지 않습니다.

[프로젝트 저장소](https://github.com/lightleaping/structured-bloom-streamlit) · [진행 기록](https://github.com/lightleaping/structured-bloom-streamlit/blob/main/PROGRESS.md)

---

## 02. 사례 기반 이상탐지·분석 Agent

**딥러닝 · 실험 평가 · Agent · 연구·실험 설계**

오류를 발견하는 것에서 나아가, 어떤 관측 변화가 나타났고 가능한 원인은 무엇인지 근거와 함께 확인하는 시스템을 연구합니다.

- **입력:** 사례를 반영한 소프트웨어 시계열과 관측 가능한 상태
- **목표 출력:** 이상 구간, 원인 후보와 근거, 사건별 자동 보고서
- **적용 예정 기술:** Python · NumPy/Pandas · scikit-learn · PyTorch · LLM/Agent
- **첫 작업:** 대상 시스템·변수·첫 오류와 실제 사례 근거를 정의하는 설계 카드.

하드웨어 제작·실제 센서 설치·XR은 제외합니다. 합성 시나리오 평가와 실제 현장 성능을 구분하며, 평가 정답은 모델·Agent 입력에 제공하지 않습니다.

[프로젝트 저장소](https://github.com/lightleaping/case-based-anomaly-agent) · [진행 기록](https://github.com/lightleaping/case-based-anomaly-agent/blob/main/PROGRESS.md)

---

## 03. 코디 추천·보드 서비스

**Vision · 모델 응용 · 데이터 연결·구현 준비**

상품을 개별적으로 보는 사용자가 서로 어울리는 조합과 전체 구성을 한눈에 확인할 수 있도록 만드는 프로젝트입니다.

- **입력:** 실제 상품 사진·정보, 기준 의류, 원하는 스타일·예산
- **목표 출력:** 추천 세트의 상품 ID, 선택 이유, 실제 사진으로 구성한 코디 보드
- **적용 예정 기술:** Python · PyTorch · 이미지 임베딩 · Pillow/rembg · FastAPI
- **첫 작업:** 실제 상품 3개의 이미지와 메타데이터를 상품 ID로 연결.

실제 상품 일부로 시작하며 가상 착용은 제외합니다. 비슷한 상품을 찾는 유사도와 함께 입기 좋은 궁합을 구분합니다. 확인하지 않은 재고는 미확인으로 둡니다.

[프로젝트 저장소](https://github.com/lightleaping/fashion-outfit-board) · [진행 기록](https://github.com/lightleaping/fashion-outfit-board/blob/main/PROGRESS.md)

---

## 04. 세계관 AI 캐릭터 엔진

**Python · 상태 관리 · 행동 검증 · LLM/Agent 기반 설계**

대화가 이어져도 캐릭터의 설정과 기억이 유지되고, 말로 제안한 행동이 실제 세계 상태와 일치하도록 만드는 프로젝트입니다.

- **입력:** 사용자 발화, 페르소나, 기억, 현재 세계 상태
- **목표 출력:** 캐릭터 응답, 검증된 행동 결과, 갱신된 상태와 기억
- **적용 예정 기술:** Python · LLM · RAG · FastAPI, 필요에 따라 LangGraph
- **1회차 결과:** 상태·행동 엔진 구현, 실패·중복·상태 불변을 포함한 자동 테스트 13개 통과.
- **다음 작업:** 사용자 입력에서 구조화된 행동 제안을 생성하고 OpenAI API와 연결.

현재 구현은 Python 결정론적 엔진 범위이며 LLM·RAG·장기 기억은 아직 연결하지 않았습니다. XR은 제외합니다. 이후에도 LLM의 행동 제안은 프로그램이 유효성을 검사한 뒤 실행하도록 설계합니다.

[프로젝트 저장소](https://github.com/lightleaping/world-character-engine) · [진행 기록](https://github.com/lightleaping/world-character-engine/blob/main/PROGRESS.md)

---

## 결과 공개 기준

실행 화면과 데모는 실제 구현 후, 성능은 데이터·분할·표본 수·지표·실행 조건과 함께 추가합니다. 직접 구현한 범위와 참고 코드·AI 도움을 구분합니다.

[전체 진행 현황](STATUS.md) · [프로필로 돌아가기](../README.md)
