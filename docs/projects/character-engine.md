# 세계관 AI 캐릭터 기억·행동 엔진

[작업 저장소](https://github.com/lightleaping/world-character-engine) · [첫 미션](https://github.com/lightleaping/world-character-engine/blob/main/docs/MISSION-01.md)

상태: 1회차 상태·행동 엔진 구현 및 자동 테스트 완료.

## 목표

캐릭터가 세계관·페르소나를 유지하고 이전 사건을 기억하며, 현재 상태에 맞는 반응과 행동을 선택하도록 구현합니다.

첫 범위는 캐릭터 1명, 작은 세계, 제한된 장소·행동, 텍스트 또는 간단한 웹 인터페이스입니다. XR은 포함하지 않습니다. 실제 세계관과 캐릭터 설정은 사용자가 확정합니다.

## 계획 흐름

입력 → 페르소나·현재 상태 로드 → 관련 기억 검색 → 구조화된 반응/행동 제안 → 코드 검증 → 도구 실행 → 상태 변경 → 응답·기억 저장

## 구현 단계

- [ ] 캐릭터·장소·상태·허용 행동 정의.
- [ ] 페르소나와 구조화된 응답 구현.
- [ ] 최근 대화와 현재 상태 관리.
- [ ] 장기 기억 저장·검색.
- [ ] 행동 유효성 검사와 도구 실행.
- [ ] 실패·중복 요청·사용자별 기억 분리.
- [ ] 기억·행동·응답 평가와 API 연결.

LangGraph는 상태·분기 관리의 필요가 생길 때 검토합니다. 프레임워크 사용만으로 Agent 기능이 완성됐다고 표시하지 않습니다.

## 평가 설계

- 관련 기억 검색, 기억이 없을 때의 응답.
- 현재 위치·소지품 등 실제 상태와 응답의 일치.
- 유효하지 않은 이동·상호작용 거부.
- 도구 실패 시 상태 유지와 이유 설명.
- 같은 요청 재시도 시 중복 행동 방지.
- 다른 사용자의 기억이 검색되지 않는지 확인.

## 현재 구현 결과

- Python으로 독립적인 초기 상태 생성.
- 허용 행동 목록과 구조화된 행동 제안 검증.
- 상태 선행 조건을 통과한 행동만 실행.
- 도구 실패 시 상태 유지와 완료 행동의 중복 실행 차단.
- 검증된 실행 결과를 캐릭터 대사로 변환.
- 성공·실패·누락·미지원·중복·상태 불변을 확인하는 자동 테스트 13개 통과.

현재 결과는 결정론적 상태·행동 엔진 범위입니다. LLM, RAG, 장기 기억, 사용자별 격리와 API는 아직 구현하지 않았습니다.

[엔진 코드](https://github.com/lightleaping/world-character-engine/blob/main/character_engine.py) · [자동 테스트](https://github.com/lightleaping/world-character-engine/blob/main/test_character_engine.py) · [1회차 학습 설명](https://github.com/lightleaping/world-character-engine/blob/main/docs/ROUND-01-LEARNING-GUIDE.md)

[전체 현황](../STATUS.md) · [기록 양식](../TEMPLATES.md)
