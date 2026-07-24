# 김수진 | AI / RAG / Agent Portfolio

인공지능소프트웨어를 전공하며 Python 기반 데이터 처리, RAG 검색 구조, AI Agent workflow, FastAPI API, Streamlit UI, PyTorch 모델 서빙 프로젝트를 진행했습니다.

최근에는 취업 포트폴리오용 프로젝트를 중심으로, 사용자 입력을 단순히 답변으로 연결하는 것이 아니라 **입력 처리 → 의도 분류 → 근거 검색 → 검증 → API/UI 출력**까지 이어지는 구조를 구현하고 있습니다.

---

## Tech Stack

### AI / RAG / Agent

- RAG
- Intent Classification
- Evidence Retrieval
- Grounded Answer
- Self-check Validation
- Source-aware Reranking
- BM25 Retrieval
- Dense Retrieval
- FAISS
- SentenceTransformer
- LangGraph / MCP 구조 학습

### Backend / Serving

- Python
- FastAPI
- Streamlit
- REST API
- JSON Response
- SQLite
- Docker
- pytest
- GitHub Actions

### AI / ML

- PyTorch
- AutoEncoder
- Anomaly Detection
- Reconstruction Error
- Threshold-based Classification
- Precision / Recall / F1-score
- scikit-learn
- pandas / NumPy

---

## Featured Projects

### 1. Multimodal Intent QA Agent

텍스트와 이미지 입력을 공통 document 구조로 변환하고, 질문 intent를 분류한 뒤 관련 evidence를 검색해 Grounded Answer와 Self-check validation을 제공하는 QA Agent 프로젝트입니다.

- 텍스트 / 이미지 입력 처리
- OCR 결과 또는 최종 이미지 텍스트 기반 image document 생성
- Intent classification
- SentenceTransformer embedding
- FAISS retrieval
- Source-aware reranking
- Grounded Answer
- Self-check validation
- Cost Estimate
- Streamlit UI
- FastAPI `/agent/query`

Repository: https://github.com/lightleaping/multimodal-intent-qa-agent

---

### 2. Manufacturing MCP Agent

제조 데이터 질문을 intent로 분류하고, 필요한 MCP-style Tool을 선택해 생산·품질·설비 센서 데이터를 분석한 뒤 answer와 evidence를 반환하는 AI Agent 백엔드 프로젝트입니다.

- 제조 샘플 데이터 생성
- SQLite 기반 데이터 저장
- CSV-to-DB pipeline
- Intent routing
- MCP-style Tool function 분리
- LangGraph workflow 구조
- FastAPI `/agent/query`
- PyTorch SensorAutoEncoder 기반 `/model/sensor-anomaly`
- Docker 실행 환경
- pytest 테스트
- GitHub Actions CI

Repository: https://github.com/lightleaping/manufacturing-mcp-agent

---

### 3. Sensor Anomaly Model Pipeline

센서 데이터를 생성하고 전처리한 뒤, 정상 데이터 기반 PyTorch AutoEncoder를 학습해 reconstruction error로 이상 여부를 판단하는 AI 모델 개발 파이프라인입니다.

- 센서 데이터 생성
- 결측치 처리
- StandardScaler 정규화
- Train / Validation / Test split
- PyTorch AutoEncoder 학습
- Validation error 기반 threshold 설정
- Precision / Recall / F1-score 평가
- Confusion Matrix 저장
- CLI prediction
- FastAPI inference API

Repository: https://github.com/lightleaping/sensor-anomaly-model-pipeline

---

### 4. Local Document Organizer Agent

로컬 문서를 업로드하면 텍스트 품질 검사, 로컬 임베딩 기반 문서 유형 분류, 키워드 추출, 요약, 추천 파일명 생성, 중복 후보 탐지, Markdown 리포트 생성을 수행하는 문서 자동화 Agent입니다.

- PDF / TXT / Markdown 문서 처리
- 텍스트 품질 검사
- 깨진 PDF 감지
- 로컬 SentenceTransformer 기반 문서 유형 분류
- README 프로젝트명 감지
- 키워드 추출
- 추천 파일명 생성
- 중복 후보 탐지
- Markdown 리포트 생성
- 선택적 Ollama 로컬 LLM 요약 모드

Repository: https://github.com/lightleaping/local-document-organizer-agent

---

### 5. Course Study RAG Tutor

수업자료 기반 RAG 학습 도우미입니다. Markdown/TXT 수업자료를 chunk 단위로 나누고, 사용자의 질문과 관련된 근거를 검색한 뒤 file_name, chunk_id, score와 함께 답변을 제공합니다.

- Keyword Retrieval
- Embedding Retrieval
- Hybrid Retrieval
- Chunk-based evidence
- Grounded Answer
- Streamlit UI
- 검색 방식 비교
- sample result 문서화

Repository: https://github.com/lightleaping/course-study-rag-tutor

---

### 6. Fair Decision RAG

공정거래위원회 공개 의결서 데이터를 대상으로 질문 유형 분류, BM25 검색, Dense Retrieval, Section Boost를 적용해 중복 없는 기존 chunk_id Top-5를 반환하는 로컬 RAG 검색 모듈입니다.

- 공정거래 의결서 질문 유형 분류
- BM25 Retrieval
- Dense Retrieval
- Section Boost
- Top-k Selector
- 중복 없는 Top-5 chunk_id 반환
- 기존 chunk_id 유지
- 결과 JSON 저장
- 검증 리포트 생성

Repository: https://github.com/lightleaping/fair-decision-rag

---

## Additional Projects

### BizTalk AI

생성형 AI를 활용한 비즈니스 영어 학습 앱 프로젝트입니다. OpenAI API를 활용해 영어 학습 시나리오와 AI 캐릭터 대화를 생성하고, Azure Speech SDK 기반 STT/TTS 기능을 적용했습니다.

- OpenAI API 활용
- 영어 학습 시나리오 생성
- AI 캐릭터 대화
- Azure Speech SDK
- STT / TTS
- 사용자 입력 기반 서비스 흐름

---

### Movie Review Sentiment Analysis

영화 리뷰 데이터를 수집하고 전처리한 뒤, 긍정·중립·부정 감정 분류와 주요 키워드 시각화를 수행한 데이터 분석 프로젝트입니다.

- 텍스트 데이터 수집
- 데이터 전처리
- 감정 분류
- 키워드 시각화
- 결과 해석

---

## Portfolio Direction

저는 다음 방향의 직무를 목표로 준비하고 있습니다.

- AI Agent Engineer
- RAG / LLM Application Developer
- AI Backend Developer
- AI Model Developer
- Data / AI Service Developer

프로젝트를 진행할 때는 단순히 모델이나 API를 호출하는 데서 끝내지 않고, 입력 데이터 구조, 검색 품질, 근거 trace, 검증 기준, API 응답 형식, 실행 문서화까지 함께 설계하려고 합니다.

---

## Contact

- GitHub: https://github.com/lightleaping
- Email: workingskyroad@gmail.com
