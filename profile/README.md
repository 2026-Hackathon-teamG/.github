<div align="center">

# 🏆 2026 TUK X INU HACKATHON 🏆

### 창의아이디어상 수상
### Best Idea Award • 참여기업/기업인 공동상 

## 📰 왜 만들었나

2026년 9월 말부터 국내 금융권에서 잇따라 고객 데이터 유출 사고가 발생했습니다.
은행들이 사고를 인지하는 데 **15시간~67시간**이 걸렸고, 해외 IP를 차단해도
공격자는 **다른 취약점을 파고들며 조회를 이어갔습니다.**

> "해외 IP 차단에 나섰지만 공격자들은 다른 취약점을 파고들며 조회를 이어갔다"
> — 신한은행 침해사고 보고서 (국민일보 10/2)

금융감독원이 꼽은 의심 징후도 IP 하나로는 잡히지 않습니다: 파라미터를 바꾼 연속 탐색,
응답 확인 후 수초 내 재접근, IP를 바꾼 저속·분산 요청. **IP 차단만으로는 더 이상 충분하지 않습니다.**

## 🍯 허니셀이란

공격자가 접근할 법한 지점에 **미리 덫(미끼망)을 만들어 두고, 밟으면 그 세션을 가둡니다.**

- 정상 사용자는 그대로 진짜 은행 서비스로
- 공격으로 의심되는 세션은 진짜와 똑같이 보이는 **미끼 서비스**로 자동 라우팅
- 미끼를 밟은 세션의 행동 패턴을 실시간으로 수집·분석해서 **방어 규칙을 자동으로 생성**
- 생성된 규칙은 쌓여서 **동시에 작동** — 공격 수법은 하나씩 막아도, 방어는 누적됨

### 시험한 공격 수법 5가지

| 수법 | 공격 | 방어 |
|---|---|---|
| **A** | 비밀번호 대입 (brute force) | IP 실패 횟수 차단 |
| **B** | IP 로테이션 | 같은 브라우저 지문 합산 차단 |
| **C** | 정찰 → 악성코드 배포 | 로그인 응답 균일화 |
| **D** | 읽기 전용 에이전트(자동화 스캐너) | 숨은 안내문으로 미끼 유도 → 접촉 즉시 격리 |
| **E** | 미끼 회피 + MFA 피로 공격 | MFA 번호 일치(number matching) |

> 모든 공격 시험은 팀이 직접 소유한 가상 은행 환경에서만 수행했으며, 실제 금융권 사건의 재현이 아닙니다.

## 🏗 시스템 아키텍처
<img width="1648" height="1087" alt="image (1)" src="https://github.com/user-attachments/assets/c1ec90bd-7bbe-460f-8873-50472ecc00ae" />


**공격 시험은 AI가, 판정과 규칙은 코드가, 오탐 확인은 담당자가 합니다.**

| 서비스 | 역할 |
|---|---|
| [`gateway`](./gateway) | 진입점. 정상/공격 트래픽 라우팅 분기, Redis 이벤트 발행 |
| [`bank`](./bank) | 실제 은행 API (Django) — 로그인, MFA, 고객 조회 |
| [`agent`](./agent) | 공격 에이전트(Red Agent) — LLM 기반 자율 공격 시뮬레이션 |
| [`detector`](./detector) | 탐지엔진 · Judge · Blue Agent (비동기 워커) |
| [`frontend`](https://github.com/2026-Hackathon-teamG/frontend) | 은행 챗봇 UI(bank-ui) · 관제 화면(ops-ui) |

## 🎬 데모




## 🛠 기술 스택

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=flat-square&logo=slack&logoColor=white)

## 👥 팀원 소개

| 이름 | 역할 |
|---|---|
| 김형수 | 팀장 · Full-stack |
| 김대건 | Backend |
| 김도훈 | Frontend |
| 김재헌 | Frontend |
| 박성빈 | Frontend |
| 이예빈 | Full-stack |

---

<div align="center">

**2026 TUK X INU HACKATHON**

</div>
