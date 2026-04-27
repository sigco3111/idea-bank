<div align="center">

# 💡 Idea Bank

**프로젝트 아이디어의 모든 것**

아이디어를 수집하고, 발전시키고, 실현하는 공간

[![Total Ideas](https://img.shields.io/badge/Total_Ideas-279-blue)](#)
[![Categories](https://img.shields.io/badge/Categories-10-purple)](#)
[![Status](https://img.shields.io/badge/Status-Collecting-yellow)](#)

</div>

---

## 📖 이 저장소는?

아이디어를 체계적으로 수집하고 관리하는 공간입니다.  
웹 개발, 게임, 시각화, 자동화 등 다양한 분야의 프로젝트 아이디어를 브레인스토밍하고 정리합니다.

모든 아이디어는 **GitHub + Vercel 배포 가능**, **무료 기술 스택 기준**, **기존 저장소와 중복 없음**을 원칙으로 합니다.

---

## 🗂️ 카테고리

| 카테고리 | 설명 | 아이디어 수 |
|----------|------|:----------:|
| 🌐 [3D 글로브](3D_Globe_Project_Ideas.md) | Globe.gl / Three.js 기반 지구 시각화 및 게임 | 49 |
| 🎮 [웹 게임](Web_Game_Project_Ideas.md) | 브라우저에서 즐기는 창의적 게임 | 27 |
| 📊 [데이터 시각화](Data_Visualization_Project_Ideas.md) | 인터랙티브 대시보드 & 시각화 | 24 |
| 🤖 [AI 에이전트](AI_Agent_Project_Ideas.md) | AI 기반 자동화 & 도구 | 27 |
| 📚 [교육 & 학습](Education_Learning_Project_Ideas.md) | 언어/수학/과학/코딩 학습 도구 | 22 |
| 🎵 [오디오 & 음악](Audio_Music_Project_Ideas.md) | Web Audio 기반 음악/사운드 프로젝트 | 25 |
| 🎨 [크리에이티브 & 아트](Creative_Art_Project_Ideas.md) | 드로잉/제너러티브아트/이미지편집 | 25 |
| ⚙️ [생산성 & 유틸리티](Productivity_Utility_Project_Ideas.md) | 시간관리/문서/개발자도구/생활유틸 | 25 |
| 🔬 [과학 & 시뮬레이션](Science_Simulation_Project_Ideas.md) | 물리/화학/천문/환경 시뮬레이션 | 25 |
| 🗺️ [deck.gl 지도 시각화](deckGL_Project_Ideas.md) | deck.gl / MapLibre 기반 대규모 지도 데이터 시각화 | 25 |

> 📌 카테고리는 지속적으로 확장됩니다.

---

## 🤖 AI 에이전트로 새 아이디어 생성하기

이 저장소의 핵심 목적은 **AI 에이전트가 중복 없이 새 프로젝트 아이디어를 생성**하는 것입니다.

### 사용법

에이전트에게 다음과 같이 요청하세요:

```
IDEA_GENERATION_GUIDE.md를 참고해서 [새 카테고리] 아이디어 파일을 만들어줘
```

**하나의 파일이면 충분합니다.** `IDEA_GENERATION_GUIDE.md`에 다음 내용이 모두 포함되어 있습니다:
- Section A: 기존 141개 저장소 목록 (중복 금지)
- Section B: 기존 254개 아이디어 목록 (중복 금지)
- 아이디어 형식 템플릿
- 생성 규칙 (한국어, 무료 기술, Vercel 배포)

### 아이디어 생성 파이프라인

1. 에이전트에게 `IDEA_GENERATION_GUIDE.md` 제공
2. 아이디어 초안 생성
3. 교차 검증으로 중복 확인
4. 최종 파일 작성 + `IDEA_INDEX.md` + `IDEA_GENERATION_GUIDE.md` 업데이트

## 🏆 추천 프로젝트

ICBM2가 구현 난이도 + 재미 + 독창성을 기준으로 선정한 Top 7

| 순위 | 프로젝트 | 장르 | 난이도 | 한 줄 평 |
|:----:|---------|------|--------|---------|
| 🥇 | **stock-nations** | 경제 | 보통 | 직관적, 뉴스 이벤트 재미, 구현 빠름 |
| 🥈 | **spy-wars** | 전략 | 보통 | 은밀전 긴장감, 쿠데타 메커니즘 독특 |
| 🥉 | **election-globe** | 정치 | 보통 | 선거 시뮬, 정책 카드 깊이 |
| 4 | **oil-politics** | 경제 | 보통 | OPEC 게임, 유가 시뮬 |
| 5 | **climate-negotiation** | 환경 | 보통 | 협상, 온도 게이지 긴장감 |
| 6 | **cyber-war** | 전쟁 | 보통 | 사이버 전쟁, 인프라 파괴 |
| 7 | **ancient-conquest** | 전략 | 높음 | 고대 문명, 기술 트리 |

---

## 📁 저장소 구조

```
idea-bank/
├── README.md                              # 이 파일
├── IDEA_GENERATION_GUIDE.md               # 🧭 AI 에이전트용 통합 가이드 (이 파일 하나로 중복 없는 아이디어 생성 가능)
├── IDEA_INDEX.md                          # 📋 전체 아이디어 마스터 인덱스 (254개)
├── EXISTING_REPOS.md                      # 📋 기존 저장소 목록 (141개, 중복 금지)
├── 3D_Globe_Project_Ideas.md              # 3D 글로브 아이디어 (49개)
├── 3D_Globe_Project_Ideas.pdf             # 3D 글로브 아이디어 PDF 요약
├── Web_Game_Project_Ideas.md              # 웹 게임 아이디어 (27개)
├── Data_Visualization_Project_Ideas.md    # 데이터 시각화 아이디어 (24개)
├── AI_Agent_Project_Ideas.md              # AI 에이전트 아이디어 (27개)
├── Education_Learning_Project_Ideas.md    # 교육 & 학습 아이디어 (22개)
├── Audio_Music_Project_Ideas.md           # 오디오 & 음악 아이디어 (25개)
├── Creative_Art_Project_Ideas.md          # 크리에이티브 & 아트 아이디어 (25개)
├── Productivity_Utility_Project_Ideas.md  # 생산성 & 유틸리티 아이디어 (25개)
├── Science_Simulation_Project_Ideas.md    # 과학 & 시뮬레이션 아이디어 (25개)
└── deckGL_Project_Ideas.md                # deck.gl 지도 시각화 아이디어 (25개)
```

---

## 🔄 아이디어 중복 방지 시스템

새로운 아이디어를 생성할 때 다음 파일들을 참조하여 중복을 방지합니다:

1. **[IDEA_GENERATION_GUIDE.md](IDEA_GENERATION_GUIDE.md)** — 🧭 AI 에이전트용 통합 가이드 (이 파일 하나로 충분)
2. **[IDEA_INDEX.md](IDEA_INDEX.md)** — 전체 254개 아이디어 마스터 인덱스
3. **[EXISTING_REPOS.md](EXISTING_REPOS.md)** — sigco3111 전체 141개 저장소 목록

**아이디어 생성 파이프라인:**
1. 에이전트에게 `IDEA_GENERATION_GUIDE.md` 제공 (Section A: 141개 기존 저장소 + Section B: 254개 기존 아이디어 + 형식 템플릿 + 규칙 모두 포함)
2. 아이디어 초안 생성
3. 교차 검증 에이전트가 인덱스와 비교하여 중복 확인
4. 최종 파일 작성 + `IDEA_INDEX.md` + `IDEA_GENERATION_GUIDE.md` 업데이트

---

## 🛠️ 기술 스택 가이드라인

모든 아이디어는 다음 원칙을 따릅니다:

- **비용:** 무료 (오픈소스 + 무료 API + Vercel Free)
- **배포:** Vercel 또는 GitHub Pages
- **프론트엔드:** HTML/CSS/JS, React, Next.js, Vue.js, Svelte
- **3D/시각화:** Globe.gl, Three.js, D3.js, Chart.js, deck.gl
- **오디오:** Web Audio API, Tone.js, Howler.js
- **데이터:** REST Countries, OpenSky, USGS, NASA, WHO 등 무료 API
- **백엔드:** 최소화 (localStorage / Supabase Free / Vercel Serverless)

---

## 📈 통계

<div align="center">

| 3D 글로브 | 웹 게임 | 데이터 시각화 | AI 에이전트 | 교육 | 오디오 | 아트 | 생산성 | 과학 | deck.gl | 총계 |
|:---------:|:-------:|:------------:|:-----------:|:----:|:------:|:----:|:------:|:----:|:-------:|:----:|
| 49 | 27 | 24 | 27 | 22 | 25 | 25 | 25 | 25 | 25 | **279** |

</div>

<div align="center">

```
3D 글로브  ████████████████████████████████████████████████ 49
웹 게임    ███████████████████████████ 27
AI 에이전트 ███████████████████████████ 27
deck.gl    █████████████████████████ 25
오디오     █████████████████████████ 25
아트       █████████████████████████ 25
생산성     █████████████████████████ 25
과학       █████████████████████████ 25
데이터시각화 ████████████████████████ 24
교육       ██████████████████████ 22
```

</div>

---

## 🤝 기여

이 저장소는 ICBM2와 주인님의 아이디어 수집 공간입니다.  
새로운 아이디어가 떠오르면 언제든 추가합니다.

---

<div align="center">

**💡 아이디어는 자본이다. — 아인슈타인**

Made with 🧠 by [ICBM2](https://github.com/sigco3111)

</div>
