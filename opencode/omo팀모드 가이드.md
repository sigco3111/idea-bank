# oh-my-openagent Team Mode 사용 가이드

> v4.0.0의 핵심 기능 — 여러 AI 에이전트가 팀을 이루어 병렬로 작업하는 멀티 에이전트 시스템

---

## 목차

1. [Team Mode란?](#1-team-mode란)
2. [현재 설정 상태](#2-현재-설정-상태)
3. [사용 방법 (4가지)](#3-사용-방법-4가지)
4. [팀 정의 파일 만들기](#4-팀-정의-파일-만들기)
5. [카테고리 가이드](#5-카테고리-가이드)
6. [tmux 실시간 시각화](#6-tmux-실시간-시각화)
7. [Team Mode 전용 스킬](#7-team-mode-전용-스킬)
8. [12개 팀 도구 참조](#8-12개-팀-도구-참조)
9. [주의사항](#9-주의사항)
10. [문제 해결](#10-문제-해결)

---

## 1. Team Mode란?

### 비유로 이해하기

```
일반 모드 (기존):
┌─────────────┐
│  Sisyphus   │ ← 혼자 다 함 (탐색, 구현, 검증, 문서...)
└─────────────┘

Team Mode (v4.0):
┌─────────────┐
│  Lead (리더) │ ← Sisyphus가 팀장 역할
├─────────────┤
│ 👤 Scout-1  │ ← src/ 디렉토리 auth 패턴 탐색 (deep)
│ 👤 Scout-2  │ ← 테스트 커버리지 확인 (quick)
│ 👤 Scout-3  │ ← API 스펙 분석 (deep)
│ 👤 Scout-4  │ ← 보안 취약점 점검 (quick)
└─────────────┘
    ↕ team_send_message (서로 메시지로 소통)
    ↕ team_task_create    (공유 할일 목록)
```

### 핵심 개념

- **리더 에이전트**(Sisyphus)가 **전문가 멤버**들을 고용하여 동시에 작업
- 멤버들은 **team_\* 도구**로 소통 (메시지, 공유 작업 목록)
- tmux에서 각 멤버의 작업을 **실시간**으로 감시 가능

---

## 2. 현재 설정 상태

### 설정 파일 위치

- 전역 설정: `~/.config/opencode/oh-my-openagent.json`
- 팀 정의: `~/.omo/teams/{팀이름}/config.json`
- 샘플 팀: `~/.omo/teams/code-explorers/config.json`

### 현재 Provider 구성

| Provider | 동시성 | 사용 에이전트 |
|---|---|---|
| `minimax-coding-plan` | 2 | sisyphus, oracle, prometheus, metis, momus, atlas |
| `github-copilot` | 3 | librarian, explore, sisyphus-junior, quick 카테고리 |

### Team Mode 설정값

```jsonc
"team_mode": {
  "enabled": true,                // Team Mode 활성화됨
  "tmux_visualization": true,     // tmux 시각화 켜짐
  "max_parallel_members": 2,      // 최대 2명 동시 실행
  "max_members": 4,               // 팀당 최대 4명
  "max_wall_clock_minutes": 120   // 최대 2시간 실행
}
```

---

## 3. 사용 방법 (4가지)

### 방법 1: 직접 지시 (가장 간단)

에이전트에게 팀을 만들어서 작업하라고 말하면 됩니다:

```
code-explorers 팀을 만들어서 이 프로젝트 구조를 분석해줘
```

```
팀 모드로 code-explorers 팀을 생성하고, 각 멤버에게 작업을 할당해
```

```
팀을 구성해서 병렬로 코드 리뷰를 진행해줘
```

에이전트가 알아서:
1. `team_create` → 팀 스폰
2. `team_task_create` → 멤버별 작업 할당
3. `team_send_message` → 진행 상황 수집
4. `team_delete` → 작업 완료 후 팀 해산

### 방법 2: hyperplan 스킬 (계획 검증)

```
hyperplan으로 이 작업 계획을 검증해줘
```

5개의 적대적 에이전트가 서로 다른 각도에서 계획을 공격합니다.
코드 작성 전에 계획의 허점을 발견할 수 있습니다.

### 방법 3: security-research 스킬 (보안 감사)

```
security-research로 이 프로젝트의 보안 취약점을 점검해줘
```

3명 취약점 헌터 + 2명 PoC 엔지니어가 코드베이스를 병렬로 보안 감사합니다.
심각도는 실제 악용 가능성 기준으로 산정됩니다.

### 방법 4: ultrawork와 조합

```
ultrawork — 팀 모드로 병렬 분석 진행해
```

---

## 4. 팀 정의 파일 만들기

### 파일 위치

```
# 사용자 전역
~/.omo/teams/{팀이름}/config.json

# 프로젝트 전용
<프로젝트>/.omo/teams/{팀이름}/config.json
```

동일한 이름이 있으면 프로젝트 전용이 우선합니다.

### 기본 구조

```json
{
  "name": "팀이름",
  "description": "팀 설명",
  "lead": {
    "kind": "subagent_type",
    "subagent_type": "sisyphus"
  },
  "members": [
    {
      "kind": "category",
      "name": "멤버이름",
      "category": "deep",
      "prompt": "이 멤버에게 할당할 작업 설명"
    }
  ]
}
```

### 멤버 종류

| `kind` 값 | 의미 | 언제 쓰나 |
|---|---|---|
| `"subagent_type"` | 직접 에이전트 지정 | sisyphus, atlas 등 전문 에이전트 필요 시 |
| `"category"` | 카테고리별 자동 모델 매칭 | **대부분의 경우 이걸 쓰면 됨** → prompt 필수 |

### 실제 예시: 코드 탐색 팀

```json
{
  "name": "code-explorers",
  "description": "코드베이스를 여러 각도에서 병렬 탐색하는 팀",
  "lead": {
    "kind": "subagent_type",
    "subagent_type": "sisyphus"
  },
  "members": [
    {
      "kind": "category",
      "name": "deep-analyst",
      "category": "deep",
      "prompt": "코드베이스의 아키텍처와 핵심 패턴을 깊이 분석해줘."
    },
    {
      "kind": "category",
      "name": "quick-scout",
      "category": "quick",
      "prompt": "프로젝트의 파일 구조와 설정 파일을 빠르게 스캔해줘."
    }
  ]
}
```

### 실제 예시: 보안 감사 팀

```json
{
  "name": "security-audit",
  "description": "보안 취약점을 병렬로 점검하는 팀",
  "lead": {
    "kind": "subagent_type",
    "subagent_type": "sisyphus"
  },
  "members": [
    {
      "kind": "category",
      "name": "injection-checker",
      "category": "deep",
      "prompt": "SQL 인젝션, XSS, CSRF 등 입력값 관련 취약점을 찾아줘."
    },
    {
      "kind": "category",
      "name": "auth-checker",
      "category": "deep",
      "prompt": "인증/인가 로직에서 권한 상승, 세션 관리 취약점을 찾아줘."
    }
  ]
}
```

---

## 5. 카테고리 가이드

멤버의 `category`에 따라 자동으로 모델이 매칭됩니다.

| 카테고리 | 용도 | 현재 모델 | 추천 상황 |
|---|---|---|---|
| `deep` | 깊은 분석 + 자율 구현 | MiniMax-M2.7 | 코드 구조 분석, 복잡한 리팩토링 |
| `quick` | 빠르고 단순한 작업 | GPT-5 Mini | 파일 검색, 간단한 확인 |
| `ultrabrain` | 고난도 논리/수학 | MiniMax-M2.7 | 복잡한 알고리즘, 아키텍처 결정 |
| `visual-engineering` | 프론트엔드/UI | GPT-4.1 | 디자인, CSS, 컴포넌트 작업 |
| `artistry` | 창의적 문제 해결 | GPT-4o | 비표준적 접근이 필요한 작업 |
| `writing` | 문서/글 작성 | GPT-4.1 | README, API 문서 |
| `unspecified-high` | 범용 (고강도) | MiniMax-M2.7 | 분류 애매한 복잡한 작업 |
| `unspecified-low` | 범용 (저강도) | GPT-4o | 분류 애매한 단순 작업 |

---

## 6. tmux 실시간 시각화

### 활성화 조건

- 설정에서 `tmux_visualization: true` (이미 켜져 있음)
- **tmux 세션 안에서** OpenCode를 실행해야 함

### 실행 방법

```bash
# 1. tmux 세션 시작
tmux

# 2. OpenCode 실행
opencode

# 3. Team Mode 사용 → 자동으로 화면 분할
```

### 화면 구성

```
┌──────────────────────────────────────────────┐
│  tmux 화면                                    │
├──────────────┬───────────────────────────────┤
│              │                               │
│  멤버 1      │  멤버 2                        │
│  (deep)      │  (quick)                      │
│              │                               │
└──────────────┴───────────────────────────────┘
```

- 각 멤버가 **자기 전용 tmux pane**에서 실시간 작업
- `team_delete` 시 pane 자동 정리
- 멤버 shutdown 시 해당 pane만 닫고 레이아웃 자동 재배치

### tmux 없이도 작동함

tmux 세션 밖에서 OpenCode를 실행하면:
- Team Mode 자체는 **정상 작동**
- 시각화만 스킵됨 (에러 발생하지 않음)

---

## 7. Team Mode 전용 스킬

### hyperplan — 계획 검증

```
hyperplan으로 이 작업 계획을 검증해줘
```

| 구성 | 설명 |
|---|---|
| 5개 적대적 에이전트 | 서로 다른 각도에서 계획을 공격 |
| 검증 시점 | 코드 작성 **전** |
| 목적 | 계획의 허점, 누락, 위험을 사전 발견 |

### security-research — 보안 감사

```
security-research로 보안 취약점을 점검해줘
```

| 구성 | 설명 |
|---|---|
| 3명 취약점 헌터 | 다양한 보안 취약점 탐색 |
| 2명 PoC 엔지니어 | 실제 악용 가능성 검증 |
| 심각도 산정 | 실제 exploitability 기준 |

---

## 8. 12개 팀 도구 참조

에이전트가 내부적으로 사용하는 도구입니다. 사용자가 직접 호출할 필요는 없지만, 이해하면 도움이 됩니다.

### 생명주기 도구

| 도구 | 용도 |
|---|---|
| `team_create` | 팀 생성 + 멤버 세션 스폰 |
| `team_delete` | 팀 해산 (리더 전용, 활성 멤버 없을 때만) |
| `team_shutdown_request` | 리더가 멤버에게 종료 요청 |
| `team_approve_shutdown` | 멤버 또는 리더가 종료 승인 |
| `team_reject_shutdown` | 멤버 또는 리더가 종료 거부 |

### 커뮤니케이션 도구

| 도구 | 용도 |
|---|---|
| `team_send_message` | 멤버 간 메시지 전송 (리더는 브로드캐스트 가능) |
| `team_status` | 팀 전체 런타임 상태 조회 |
| `team_list` | 등록된 팀 + 활성 팀 목록 |

### 작업 관리 도구

| 도구 | 용도 |
|---|---|
| `team_task_create` | 공유 작업 목록에 작업 추가 |
| `team_task_list` | 작업 목록 조회 |
| `team_task_update` | 작업 상태 업데이트 (claimed, done 등) |
| `team_task_get` | 특정 작업 상세 조회 |

---

## 9. 주의사항

### 동시성 제한 (현재 설정 기준)

| 항목 | 값 | 의미 |
|---|---|---|
| max_parallel_members | 2 | 동시에 2명까지 실행 |
| minimax-coding-plan 동시성 | 2 | minimax 모델 동시 요청 2개 |
| github-copilot 동시성 | 3 | copilot 모델 동시 요청 3개 |

> **주의**: minimax 동시성이 2이므로, 팀원 2명이 모두 minimax를 사용하면 리더(Sisyphus)는 폴백 모델(gpt-4.1)로 전환됩니다.

### 제한 사항

| 항목 | 내용 |
|---|---|
| 중첩 팀 불가 | 팀원이 또 팀을 만들 수 없음 |
| 비동기 메시지 | `team_send_message`는 "보내고 잊기" — 답장 대기 안 함 |
| 참여 불가 에이전트 | oracle, librarian, explore 등 읽기 전용 에이전트는 팀원 불가 |
| 종료 바이패스 불가 | 활성 멤버가 있으면 `team_delete` 거부됨 |

### multimodal-looker 변경 안내

`zai-coding-plan` 구독 만료로 인해 multimodal-looker(이미지 분석)가 `minimax-coding-plan/MiniMax-M2.7`로 변경되었습니다. 비전 기능이 필요한 경우 추후 비전 지원 모델로 교체하세요.

---

## 10. 문제 해결

### Team Mode가 작동하지 않을 때

```bash
# 1. 설정 확인
bunx oh-my-openagent doctor

# team-mode 체크 항목: tmux/git 가용성, 등록된 팀 수, 활성 런타임 디렉토리

# 2. 설정 파일 확인
cat ~/.config/opencode/oh-my-openagent.json | grep team_mode

# 3. 팀 정의 파일 확인
ls ~/.omo/teams/
```

### tmux 시각화가 안 보일 때

- tmux 세션 안에서 OpenCode를 실행했는지 확인
- `which tmux`로 tmux 설치 확인
- tmux 없어도 Team Mode 자체는 작동함

### 폴백이 너무 자주 발생할 때

- minimax 동시성 한계(2)에 도달하고 있을 가능성
- 팀원 수를 1명으로 줄이거나, github-copilot 모델을 사용하는 카테고리로 멤버 구성
- `max_parallel_members`를 1로 낮추기

---

## 빠른 참조 카드

```
# 팀으로 코드 분석
code-explorers 팀을 만들어서 프로젝트를 분석해줘

# 계획 검증
hyperplan으로 계획을 검증해줘

# 보안 감사
security-research로 보안 점검해줘

# 팀 + ultrawork
ultrawork — 팀 모드로 병렬 분석해

# 새 팀 정의 만들기
~/.omo/teams/{팀이름}/config.json 파일 작성

# 상태 확인
bunx oh-my-openagent doctor
```

---

*마지막 업데이트: 2026-05-11*
