# 🗺️ deck.gl 게임 프로젝트 아이디어 모음
> deck.gl / MapLibre / React 기반 지도 레이어를 핵심 메커니즘으로 활용한 창의적 웹 게임 아이디어
> 생성일: 2026-04-28 | 작성: ICBM2

---

## 📌 배경

deck.gl은 Uber가 개발한 GPU 가속 대규모 데이터 시각화 프레임워크입니다. HexagonLayer, ArcLayer, TripsLayer, HeatmapLayer, ScatterplotLayer, PathLayer, ColumnLayer, GridLayer, GeoJsonLayer, PointCloudLayer 등 60+ 레이어를 제공합니다. 이 레이어들을 **게임 메커니즘 그 자체**로 활용하면 실제 지리 데이터 기반의 독창적인 게임을 만들 수 있습니다. 본 문서는 deck.gl의 시각화 레이어를 핵심 게임플레이로 사용하는 창의적인 지도 기반 게임 아이디어를 정리합니다.

**핵심 차별화:** 기존 3D 글로벌 게임(Globe.gl/Three.js)이 3D 지구본 위에서의 게임이라면, 본 카테고리는 **2D 지도 위 deck.gl 레이어 자체가 게임 규칙**이 되는 것이 특징입니다. HexagonLayer로 영토를 나누고, ArcLayer로 연결을 만들고, HeatmapLayer로 숨겨진 것을 찾는 식의 고유한 게임 경험을 제공합니다.

---

## 참고: 기존 관련 저장소 (중복 금지)

### 게임 (48개 + 관련)
- `geoPoly` — 지구마블 3D 보드 게임 (Globe.gl)
- `iron-dome` — 3D 미사일 방어 시뮬레이션 게임 (Three.js)
- `Kingdoms3Lite` — 삼국지 턴제 전략 게임
- `super-robot-lite` — 슈퍼로봇대전 턴제 전략 게임
- `xcom-lite` — 턴제 전술 분대 전략 게임
- `stock-game` / `stock-invest-game` / `stonks-9800` — 주식 시뮬레이션 게임
- `real-estate-king` — 부동산 매매 임대 시뮬레이션 게임
- `department-tycoon` / `juice-tycoon` / `pixel-farm-story` / `air-management` — 경영 시뮬레이션
- 기타 48개 게임 저장소 (IDEA_GENERATION_GUIDE.md Section A 참조)

### 3D 글로벌 게임 아이디어 (40개 — 3D_Globe_Project_Ideas.md)
- `pirate-ship` — 해적 항로 추적 게임 (Globe.gl)
- `city-tycoon` — 도시 건설 경영 시뮬레이션
- `bio-plague` — 바이러스 확산 vs 방어 대전
- `trade-winds` / `trade-empire` — 무역 경영 게임
- `fortress-earth` — 외계 침공 방어 타워디펜스
- `spy-wars` — 냉전 스파이 게임
- `resource-war` — 자원 점령 턴제 전쟁
- `smuggler-empire` — 밀수 제국 건설
- 기타 (IDEA_GENERATION_GUIDE.md Section B 참조)

### deck.gl 시각화 아이디어 (25개 — deckGL_Project_Ideas.md)
- 모든 아이디어가 **데이터 시각화**이며, 게임이 아님

---

## 📊 요약 테이블

| 번호 | 제목 | 분야 | 난이도 | 핵심 deck.gl 레이어 | 한 줄 포인트 |
|---|---|---|---|---|---|
| 1 | 헥사곤 정복자 | 전략/영토 | 보통 | HexagonLayer | 실제 지도 위 영토 확장 리스크 |
| 2 | 해양 패권전 | 전략/영토 | 보통 | PolygonLayer | EEZ 기반 해양 자원 쟁탈 |
| 3 | 도시 연결 제국 | 전략/영토 | 보통 | ArcLayer | 도시 간 네트워크 확장 경영 |
| 4 | 방어선: 실제 지형 타워디펜스 | 전략/영토 | 보통 | PathLayer + ScatterplotLayer | 실제 지형 활용 타워 배치 |
| 5 | 정보전 커맨드 | 전략/영토 | 보통 | ScatterplotLayer | 실제 지도 위 스파이 배치 전략 |
| 6 | 도주 추격전 | 추적/수색 | 높음 | TripsLayer | 범죄자 이동 경로 추적 시뮬 |
| 7 | 심해 잠수함 사냥 | 추적/수색 | 높음 | PointCloudLayer | 해저 지형 위 잠수함 탐지 |
| 8 | 실종 수색 최적화 | 추적/수색 | 보통 | GridLayer | 수색 구역 할당 퍼즐 |
| 9 | 밀수 루트 차단 | 추적/수색 | 보통 | ArcLayer | 실제 항로 기반 밀수 탐지 |
| 10 | 물류 왕국 | 경영/건설 | 보통 | PathLayer + ColumnLayer | 실제 도로망 배송 경영 |
| 11 | 스마트 시티 빌더 | 경영/건설 | 높음 | ColumnLayer + GeoJsonLayer | 도시 인프라 배치 시뮬 |
| 12 | 에너지 그리드 건설 | 경영/건설 | 보통 | ArcLayer + ScatterplotLayer | 전력 인프라 구축 퍼즐 |
| 13 | 항만 무역 제국 | 경영/건설 | 높음 | ScatterplotLayer + ArcLayer | 실제 항만 데이터 무역 경영 |
| 14 | 열섬 탐정 | 퀴즈/탐험 | 쉬움 | HeatmapLayer | 도시 열섬 현상 지역 맞추기 |
| 15 | 고고학 발굴 탐험 | 퀴즈/탐험 | 보통 | GeoJsonLayer | 실제 유적 분포 발굴 어드벤처 |
| 16 | 해저 비밀 탐험대 | 퀴즈/탐험 | 보통 | PointCloudLayer + PathLayer | 해저 지형 기반 탐사 |
| 17 | 인구 이동 예측가 | 퀴즈/탐험 | 보통 | ArcLayer + HeatmapLayer | 이동 패턴 예측 퀴즈 |
| 18 | 운석 요격 지휘소 | 액션/재난 | 높음 | ArcLayer | 궤적 예측 + 요격 게임 |
| 19 | 산불 진화대 | 액션/재난 | 높음 | HeatmapLayer + PathLayer | 화재 확산 방어 시뮬 |
| 20 | 홍수 방어 커맨더 | 액션/재난 | 보통 | PolygonLayer + ColumnLayer | 강물 데이터 제방 건설 |
| 21 | 지진 대피 시뮬레이터 | 액션/재난 | 보통 | GridLayer + PathLayer | 단층대 데이터 대피 최적화 |
| 22 | 태풍 진로 예측 대결 | 액션/재난 | 보통 | PathLayer + ScatterplotLayer | 실제 태풍 경로 예측 |
| 23 | 야생동물 서식지 설계자 | 시뮬레이션 | 보통 | GeoJsonLayer + HeatmapLayer | 동물 분포 기반 보호구역 설계 |
| 24 | 지하자원 채굴왕 | 시뮬레이션 | 보통 | GridLayer + ColumnLayer | 광물 분포 기반 채굴 경영 |
| 25 | 통신망 구축 대작전 | 시뮬레이션 | 보통 | ScatterplotLayer + ArcLayer | 인구 밀도 기반 기지국 배치 |

---

## 🏆 ICBM2 최종 추천 Top 7

1. **헥사곤 정복자** — HexagonLayer가 자연스럽게 게임 보드가 되는 독창적 메커니즘, 구현 직관적
2. **도주 추격전** — TripsLayer 애니메이션이 추격전 그 자체, 시각적 임팩트 강함
3. **물류 왕국** — PathLayer 경로 최적화가 경영 게임과 완벽 결합
4. **열섬 탐정** — HeatmapLayer를 퀴즈 도구로 활용, 진입 장벽 낮고 중독성 높음
5. **산불 진화대** — 실시간 HeatmapLayer 확산이 긴장감 극대화
6. **방어선: 실제 지형 타워디펜스** — 실제 지형이 맵이 되는 독창적 타워디펜스
7. **심해 잠수함 사냥** — PointCloudLayer 해저 지형이 게임 공간, 시각적 독창성 최고

---

# PART 1: 전략 / 영토

### 1. 🎯 헥사곤 정복자 — 실제 지도 위 영토 확장 리스크 게임

**기술:** React, deck.gl HexagonLayer, MapLibre, Zustand
**난이도:** 보통

**내용:**
- 한국 지도를 HexagonLayer 육각형 셀로 분할, 각 셀이 영토
- 턴제로 인접 셀을 점령하여 영토 확장 (리스크/Risk 스타일)
- 셀마다 인구/자원/방어력 부여, 전략적 선택 필요
- AI 상대와 자동 전투, 셀 색상으로 세력 분포 시각화
- 50턴 내 전국 통일이 목표

**포인트:** HexagonLayer가 곧 게임 보드! 지도 위 전략 보드게임

---

### 2. 🎯 해양 패권전 — EEZ 기반 해양 자원 쟁탈 게임

**기술:** React, deck.gl PolygonLayer, MapLibre, 공공 해양데이터
**난이도:** 보통

**내용:**
- 실제 EEZ(배타적 경제수역) 경계를 PolygonLayer로 표시
- 해양 자원(어장, 해저광물, 해상풍력) 위치를 ScatterplotLayer로 배치
- 선단을 배치해 자원 채취, 해군 배치해 영토 방어
- 인접국과 외교/분쟁 이벤트 발생
- 해양 자원 점유율 70% 달성 시 승리

**포인트:** 실제 해양 경계가 게임 맵! 해양 자원 전략 시뮬레이션

---

### 3. 🎯 도시 연결 제국 — 도시 간 교통 네트워크 확장 경영

**기술:** React, deck.gl ArcLayer, MapLibre, 공공 교통데이터
**난이도:** 보통

**내용:**
- 전국 주요 도시를 ScatterplotLayer로 배치
- ArcLayer로 도시 간 연결(도로/철도/항공)을 구축
- 연결망 확장으로 물류/여객 수익 창출, 자본 확보
- 연결 거리·지형에 따른 건설 비용 차등 적용
- 제한 자본으로 가장 효율적인 네트워크 구축이 핵심

**포인트:** ArcLayer가 곧 사업 투자! 최적 네트워크 설계 경영

---

### 4. 🎯 방어선: 실제 지형 타워디펜스 — 실제 지형 활용 타워 배치 방어

**기술:** React, deck.gl PathLayer + ScatterplotLayer, MapLibre
**난이도:** 보통

**내용:**
- 실제 지도 위 산/강/도로를 PathLayer로 표현한 맵
- 적 유닛이 실제 도로를 따라 진입 (PathLayer 애니메이션)
- ScatterplotLayer로 방어 타워를 실제 지형에 배치
- 산/강/바다 등 실제 지형이 타워 배치 제약 조건
- 웨이브마다 적 종류·수 증가, 타워 업그레이드 시스템

**포인트:** 실제 지형이 맵이 되는 타워디펜스! 지형 이해가 필수 전략

---

### 5. 🎯 정보전 커맨드 — 실제 지도 위 스파이 배치 전략

**기술:** React, deck.gl ScatterplotLayer, MapLibre, Zustand
**난이도:** 보통

**내용:**
- 실제 도시/시설을 ScatterplotLayer로 표시한 전략 맵
- 스파이 유닛을 주요 시설에 배치, 정보 수집/암살/공작 수행
- 적 스파이 탐지 vs 아군 스파이 은닉의 정보 전쟁
- 성공 확률은 거리·시설 등급·스파이 능력치에 따라 산정
- 제한 턴 내 핵심 정보 획득 미션 클리어

**포인트:** ScatterplotLayer 위에서 펼쳐지는 보이지 않는 전쟁

---

# PART 2: 추적 / 수색

### 6. 🎯 도주 추격전 — 범죄자 이동 경로 실시간 추적 시뮬레이션

**기술:** React, deck.gl TripsLayer, MapLibre, Zustand
**난이도:** 높음

**내용:**
- TripsLayer로 범죄자 이동 경로를 실시간 애니메이션
- 수사관을 ScatterplotLayer로 배치, 추적 루트 최적화
- 범죄자는 교통수단(도보/차량/대중교통) 변경하며 도주
- CCTV 위치 HeatmapLayer로 탐지 확률 시각화
- 제한 시간 내 포반이 목표, 난이도별 도주자 수·속도 조절

**포인트:** TripsLayer 애니메이션이 추격전 그 자체! 실시간 긴장감

---

### 7. 🎯 심해 잠수함 사냥 — 해저 지형 위 잠수함 탐지 게임

**기술:** React, deck.gl PointCloudLayer, MapLibre, WebGL
**난이도:** 높음

**내용:**
- 실제 해저 지형 데이터를 PointCloudLayer로 3D 렌더링
- 소나 핑(ping)을 발사해 잠수함 위치 추리
- PointCloudLayer의 색상으로 수심 표시, 해구·해령이 장애물
- 잠수함은 해류를 타고 이동, 소나 음영 지역에 은닉 가능
- 연료·소나 에너지 제한 내 탐지 임무 수행

**포인트:** 실제 해저 지형이 게임 공간! PointCloudLayer의 독창적 활용

---

### 8. 🎯 실종 수색 최적화 — GridLayer 기반 수색 구역 할당 퍼즐

**기술:** React, deck.gl GridLayer, MapLibre, Zustand
**난이도:** 보통

**내용:**
- 실제 지도를 GridLayer로 셀 분할, 각 셀에 지형·접근성 부여
- 제한 수색대를 배치해 실종자 발견 확률 최대화
- 산/숲/도시 등 지형별 수색 시간·발견 확률 차등
- 시간 경과에 따라 수색 반경 확장, 새로운 단서 등장
- 최소 시간·최소 인원으로 실종자 발견이 핵심

**포인트:** GridLayer로 수색 구역을 전략적으로 할당하는 퍼즐

---

### 9. 🎯 밀수 루트 차단 — 실제 항로 기반 밀수품 탐지 게임

**기술:** React, deck.gl ArcLayer, MapLibre, Zustand
**난이도:** 보통

**내용:**
- 실제 항구/공항을 ScatterplotLayer로 표시
- ArcLayer로 물류 이동 경로 표시, 그중 밀수 경로 혼입
- 세관 요원을 배치해 의심 경로 검문, 밀수품 적발
- 항로 색상(정상/의심/확인) 구분, 검문 리소스 제한
- 의심 경로 중 밀수 비율 추리, 오탐지 최소화 전략

**포인트:** ArcLayer로 물류망을 시각화한 추리 게임

---

# PART 3: 경영 / 건설

### 10. 🎯 물류 왕국 — 실제 도로망 기반 배송 경영 시뮬레이션

**기술:** React, deck.gl PathLayer + ColumnLayer, MapLibre, 공공 도로데이터
**난이도:** 보통

**내용:**
- 실제 도로망을 PathLayer로 표시한 경영 맵
- 물류센터(ColumnLayer)를 배치, 배송 경로(PathLayer) 최적화
- 주문 발생 시 가까운 물류센터에서 배송, 거리→비용→수익 계산
- 수익으로 물류센터·차량 확충, 서비스 영역 확대
- 경쟁 업체 AI와 시장 점유율 경쟁

**포인트:** 실제 도로망 위에서 펼쳐지는 물류 경영 대전

---

### 11. 🎯 스마트 시티 빌더 — 도시 인프라 배치 시뮬레이션

**기술:** React, deck.gl ColumnLayer + GeoJsonLayer, MapLibre, 공공 도시데이터
**난이도:** 높음

**내용:**
- 실제 도시 구역(GeoJsonLayer) 위에 인프라(ColumnLayer) 배치
- 주택/상업/공장/공원/도로 등 구역 지정
- 인프라 배치에 따라 인구·수익·환경·만족도 실시간 변화
- 교통 혼잡도 HeatmapLayer로 시각화, 최적 도로망 설계
- 목표 인구·만족도 달성 시 레벨업, 새로운 구역 해금

**포인트:** 실제 도시 구역 위 인프라 배치! 도시계획 시뮬레이션

---

### 12. 🎯 에너지 그리드 건설 — 전력 인프라 구축 퍼즐

**기술:** React, deck.gl ArcLayer + ScatterplotLayer, MapLibre
**난이도:** 보통

**내용:**
- 실제 전력 소비 데이터를 HeatmapLayer로 시각화한 맵
- 발전소(ScatterplotLayer)와 송전망(ArcLayer)을 배치
- 수요 지역에 전력 공급 시 수익 발생, 미공급 지역 패널티
- 재생에너지(풍력/태양)는 날씨 데이터에 따라 출력 변동
- 제한 예산 내 최대 전력 커버리지 달성이 목표

**포인트:** 실제 전력 수요 분포 위 인프라 퍼즐

---

### 13. 🎯 항만 무역 제국 — 실제 항만 데이터 기반 물류/무역 경영

**기술:** React, deck.gl ScatterplotLayer + ArcLayer, MapLibre, 공공 항만데이터
**난이도:** 높음

**내용:**
- 전 세계 주요 항만(ScatterplotLayer)을 거점으로 무역 경영
- 항만 간 화물 이동을 ArcLayer로 시각화
- 항만별 물품 가격·수요 차이 활용한 매매 차익 실현
- 선단 확장→신항로 개척→특산품 독점으로 성장
- 시장 이벤트(폭풍·분쟁·호황)로 가격 변동

**포인트:** 실제 항만 데이터로 짜는 글로벌 무역 시뮬레이션

---

# PART 4: 퀴즈 / 탐험

### 14. 🎯 열섬 탐정 — 도시 열섬 현상 지역 맞추기 퀴즈

**기술:** React, deck.gl HeatmapLayer, MapLibre, 공공 기온데이터
**난이도:** 쉬움

**내용:**
- 실제 도시 기온 데이터를 HeatmapLayer로 시각화
- 열섬 현상(온도 높은 지역)이 어디인지 클릭하여 맞추기
- 정답과의 거리에 따라 점수 차등 부여
- 힌트 시스템 (공원/아스팔트 비율 등)
- 레벨업 시 도시 규모 확대, 난이도 상승
- 전 세계 주요 도시 랭킹 시스템

**포인트:** HeatmapLayer로 숨겨진 온도 분포 추리! 교육적 + 중독성

---

### 15. 🎯 고고학 발굴 탐험 — 실제 유적 분포 발굴 어드벤처

**기술:** React, deck.gl GeoJsonLayer, MapLibre, 문화재청 오픈API
**난이도:** 보통

**내용:**
- 실제 문화재/유적 분포를 GeoJsonLayer로 표시 (숨김 상태)
- 지도 위 클릭으로 발굴 시도, 주변 단서(지형/지질)로 유적 추리
- 발굴 성공 시 유물 정보 표시, 컬렉션 수집
- 잘못된 발굴은 예산 소모, 예산 관리가 핵심
- 시대별(선사/삼국/조선) 미션, 각 시대 유적 전체 발굴 시 클리어

**포인트:** 실제 문화재 데이터가 숨겨진 보물! 지도 위 발굴 어드벤처

---

### 16. 🎯 해저 비밀 탐험대 — 실제 해저 지형 데이터 기반 탐사 게임

**기술:** React, deck.gl PointCloudLayer + PathLayer, MapLibre, NOAA 해저데이터
**난이도:** 보통

**내용:**
- 실제 해저 지형(PointCloudLayer)을 탐사하는 잠수정 게임
- 해저 화산·열수구·해구 등 지형에 숨겨진 보물/생물 발견
- 연료·산소 자원 관리하며 탐사 경로(PathLayer) 계획
- 발견한 해저 생물/광물 도감 수집
- 깊이별 난이도 구간, 심해일수록 희귀 발견 확률 증가

**포인트:** 실제 해저 지형을 탐험하는 잠수정 어드벤처

---

### 17. 🎯 인구 이동 예측가 — 실제 인구 데이터 기반 이동 패턴 예측 게임

**기술:** React, deck.gl ArcLayer + HeatmapLayer, MapLibre, 통계청 인구데이터
**난이도:** 보통

**내용:**
- 실제 시군구별 인구 데이터를 HeatmapLayer로 시각화
- 인구 이동(ArcLayer) 패턴을 보고 다음 시즌 이동 예측
- 예측 정확도에 따라 점수 획득, 누적 랭킹
- 힌트: 일자리·주택·교통 인프라 데이터
- 전국/수도권/지소멸 등 다양한 시나리오

**포인트:** 실제 인구 데이터로 미래를 예측하는 소셜 예측 게임

---

# PART 5: 액션 / 재난

### 18. 🎯 운석 요격 지휘소 — 궤적 예측 + 요격 액션 게임

**기술:** React, deck.gl ArcLayer, MapLibre, WebGL
**난이도:** 높음

**내용:**
- 운석 궤적을 ArcLayer로 3D 곡선 표시, 지도 위 낙하 지점 예측
- 요격 미사일 발사로 궤적 변경/파괴, 타이밍이 핵심
- 도시 밀집도(HeatmapLayer)에 따라 피해 점수 차등
- 연속 웨이브로 운석 크기·속도·개수 증가
- 방어망 업그레이드 시스템, 전 세계 주요 도시 보호

**포인트:** ArcLayer 궤적이 곧 운석! 실시간 궤적 예측 요격

---

### 19. 🎯 산불 진화대 — 화재 확산 방어 시뮬레이션

**기술:** React, deck.gl HeatmapLayer + PathLayer, MapLibre, 산림청 데이터
**난이도:** 높음

**내용:**
- 실제 산림/지형 데이터 위에서 산불 발생 시나리오
- HeatmapLayer로 불 확산 실시간 시각화 (바람 방향·속도 반영)
- 진화대(PathLayer)를 배치해 방어선 구축, 확산 차단
- 물·진화제 자원 제한, 헬기·지상팀 전략적 배치
- 주민 대피 경로 최적화 미션 병행

**포인트:** HeatmapLayer로 불이 번지는 모습이 실시간으로! 긴장감 폭발

---

### 20. 🎯 홍수 방어 커맨더 — 강물 데이터 기반 제방 건설 시뮬레이션

**기술:** React, deck.gl PolygonLayer + ColumnLayer, MapLibre, 하천 데이터
**난이도:** 보통

**내용:**
- 실제 강/하천 데이터(PolygonLayer) 위 홍수 시뮬레이션
- 강수량 증가에 따른 수위 상승 실시간 표시
- 제방/댐(ColumnLayer)을 배치해 홍수 방어
- 하류 인구밀도가 높을수록 방어 성공 시 점수 가산
- 제방 건설 예산 제한, 상류 vs 하류 투자 분배 전략

**포인트:** 실제 강물 데이터로 홍수 방어! 물리 시뮬 + 전략

---

### 21. 🎯 지진 대피 시뮬레이터 — 단층대 데이터 기반 대피 최적화

**기술:** React, deck.gl GridLayer + PathLayer, MapLibre, 지질 데이터
**난이도:** 보통

**내용:**
- 실제 단층대 데이터를 PathLayer로 표시
- 지진 발생 시 진앙·규모·예상 피해(GridLayer) 실시간 표시
- 주민을 안전한 대피소로 경로(PathLayer) 지정
- 시간 제한 내 최대 인구 대피가 목표
- 여진 발생 시 추가 대피, 교통 상황 변동

**포인트:** 실제 단층대 데이터로 지진 대피 시뮬레이션

---

### 22. 🎯 태풍 진로 예측 대결 — 실제 태풍 경로 데이터 예측 게임

**기술:** React, deck.gl PathLayer + ScatterplotLayer, MapLibre, 기상청 태풍데이터
**난이도:** 보통

**내용:**
- 과거 태풍 데이터를 바탕으로 태풍 진로(PathLayer) 예측 대결
- 태풍 현재 위치(ScatterplotLayer)와 기상 조건 제시
- 12시간/24시간/48시간 후 위치를 지도에 클릭하여 예측
- 실제 경로와의 편차에 따라 점수 산정
- 전 세계 유명 태풍 시나리오 100+ 수록

**포인트:** 실제 태풍 데이터로 진로 예측 정확도를 겨루는 게임

---

# PART 6: 시뮬레이션

### 23. 🎯 야생동물 서식지 설계자 — 동물 분포 기반 보호구역 설계 게임

**기술:** React, deck.gl GeoJsonLayer + HeatmapLayer, MapLibre, 환경부 야생동물데이터
**난이도:** 보통

**내용:**
- 실제 야생동물 분포(HeatmapLayer)를 보고 최적 보호구역 설계
- GeoJsonLayer로 보호구역 경계를 그리면 생태 점수 산정
- 멸종위험종 포함 여부, 서식지 연결성, 인프라 충돌 최소화
- 예산 제한 내 최대 생태 다양성 보호가 목표
- 시즌별 새로운 지역·종 추가, 랭킹 시스템

**포인트:** 실제 야생동물 분포로 최적 보호구역을 설계하는 에코 퍼즐

---

### 24. 🎯 지하자원 채굴왕 — 광물 분포 기반 채굴 경영 시뮬레이션

**기술:** React, deck.gl GridLayer + ColumnLayer, MapLibre, 광물 분포데이터
**난이도:** 보통

**내용:**
- 실제 광물(석탄/철광/희토류 등) 분포를 GridLayer로 표시
- 채굴 시설(ColumnLayer)을 배치해 자원 채취
- 광맥 깊이에 따른 채굴 비용·위험도 증가
- 시장 가격 변동에 따른 수익 변화, 매도 타이밍 전략
- 환경 영향(HeatmapLayer) 관리, 과도 채굴 시 패널티

**포인트:** 실제 광물 분포 위에서 자원 채굴 최적화 경영

---

### 25. 🎯 통신망 구축 대작전 — 인구 밀도 기반 기지국 배치 퍼즐

**기술:** React, deck.gl ScatterplotLayer + ArcLayer, MapLibre, 인구 밀도데이터
**난이도:** 보통

**내용:**
- 실제 인구 밀도(HeatmapLayer)를 기반으로 통신 서비스 영역 설계
- 기지국(ScatterplotLayer) 배치, 백홀 망(ArcLayer) 구축
- 기지국 커버리지 반경 내 인구수 = 수익, 커버리지 외 = 기회비용
- 지형(산/건물)에 따른 전파 차폐 영역 표시
- 제한 예산 내 최대 인구 커버리지 달성, 5G/4G 선택 전략

**포인트:** 실제 인구 분포로 최적 통신망을 설계하는 인프라 퍼즐

---

## 📋 파트별 요약

| 파트 | 아이디어 수 | 핵심 레이어 | 게임 장르 |
|------|:----------:|------------|-----------|
| PART 1: 전략/영토 | 5 | HexagonLayer, PolygonLayer, ArcLayer, ScatterplotLayer | 전략, 경영 |
| PART 2: 추적/수색 | 4 | TripsLayer, PointCloudLayer, GridLayer, ArcLayer | 추리, 액션 |
| PART 3: 경영/건설 | 4 | PathLayer, ColumnLayer, GeoJsonLayer, ArcLayer | 경영, 시뮬 |
| PART 4: 퀴즈/탐험 | 4 | HeatmapLayer, GeoJsonLayer, PointCloudLayer, ArcLayer | 퀴즈, 어드벤처 |
| PART 5: 액션/재난 | 5 | ArcLayer, HeatmapLayer, PolygonLayer, PathLayer, GridLayer | 액션, 시뮬 |
| PART 6: 시뮬레이션 | 3 | GeoJsonLayer, GridLayer, ColumnLayer, ScatterplotLayer | 시뮬, 퍼즐 |
| **총계** | **25** | — | — |

---

## 🔧 공통 기술 스택

| 구성요소 | 기술 | 비고 |
|----------|------|------|
| 프론트엔드 | React 18+, TypeScript | Vercel 배포 |
| 지도 렌더링 | deck.gl 9.x + MapLibre GL JS | GPU 가속 |
| 상태관리 | Zustand | 경량 상태 관리 |
| 데이터 | 공공데이터포털, 통계청, 기상청, NOAA | 무료 API |
| 스타일링 | Tailwind CSS | 빠른 UI 구성 |
| 배포 | Vercel Free | 무료 호스팅 |

---

*이 파일은 deck.gl의 시각화 레이어를 핵심 게임 메커니즘으로 활용하는 창의적인 게임 아이디어를 정리합니다.*
*기존 141개 저장소 및 279개 아이디어와 중복되지 않는 독창적인 아이디어만 수록합니다.*
