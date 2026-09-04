## 백상호 · Baek Sangho

**사람이 반복하는 일을 자동으로 바꾸는 일을 합니다.**

보안 로그 자동 대응에서 시작해, 지금은 n8n과 LLM으로 콘텐츠 생산 파이프라인을 설계하고 운영합니다.

```
보안 (Splunk SIEM)  →  백엔드 (Java · Spring)  →  AI 자동화 (n8n · LLM)
```

---

### 무엇을 만들었나

**멀티브랜드 콘텐츠 자동화 — 생성 엔진**
클라이언트가 웹에서 콘텐츠를 요청하면 브랜드·채널별 webhook으로 호출되는 파이프라인을 담당했습니다.
리서치 · 생성 · 검수 · 발행이 이 안에서 처리됩니다.

| | |
|---|---|
| 워크플로우 | **28개** · 노드 **6,006개** |
| 직접 작성한 JavaScript 로직 노드 | **1,742개** |
| 실패 전용 처리 경로 | **22곳** |
| 외부 API 호출 간격 제어 | **276곳** |
| 자동 발행 실적 | 한 매체에 4개월간 **53편** · 약 **24만 자** |

**보험 콘텐츠 자동화 + AI 표현 검수**
사내에 없던 n8n을 직접 조사·도입해 기획부터 게시까지 잇는 파이프라인을 구축하고, 금융사 시연을 거쳐 서비스 제공 단계에 진입했습니다.

---

### 어떻게 생각하는가

**확장을 전제하고 설계합니다.**
브랜드마다 워크플로우를 복제하면 공통 로직 한 줄 고칠 때 전부를 손봐야 합니다.
브랜드 설정을 데이터로 분리하고 반복 처리를 공용 서브 워크플로우로 묶었습니다.

**LLM 가드레일은 세 겹으로 나눕니다.**
생성 단계 제약 · LLM 판정 · 정규식 필터.
규칙으로 결정되는 건 코드로 처리하고, 판단이 필요한 것만 LLM에 맡깁니다.
없는 걸 지어내는 문제는 검수로 못 잡으니 생성 단계에서 막습니다.

**돌아가게 만드는 것과 계속 돌아가게 두는 것은 다릅니다.**
실패했을 때 어디로 빠질지를 먼저 정하고 만듭니다.

---

### Stack

**AI · Automation**
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Claude](https://img.shields.io/badge/Claude-D97757?style=flat-square&logo=anthropic&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

**Backend**
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)

**Frontend**
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)

**Data**
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)

**Infra**
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=flat-square&logo=proxmox&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

**Security**
![Splunk](https://img.shields.io/badge/Splunk-0093C4?style=flat-square&logo=splunk&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=flat-square&logo=wireshark&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali%20Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)

---

### 집에서는

Proxmox 위에 자작 NAS(TrueNAS · OMV)와 Ubuntu · Rocky 서버를 올려두고 **로컬 LLM을 직접 돌립니다.**
Ollama와 LM Studio로 시작해 옵션을 조정해야 할 때는 llama.cpp나 파이썬 가상환경을 씁니다.
32GB RAM · GTX 1660 Super · RTX 5060 환경에서 4B~13B급까지 확인했고,
n8n에 로컬 모델을 붙여 클라우드 API 대신 써봤습니다.

PC 조립·수리와 액정·배터리 교체, 간단한 납땜도 취미입니다. 손으로 고치는 걸 좋아합니다.

---

### 📌 Projects

| 저장소 | 내용 |
|---|---|
| [Capstone](https://github.com/sangholabs/Capstone) | OpenCV · PyQt5 알약 이미지 뷰어 — 강원대 졸업작품 **장려상** |
| [backfront](https://github.com/sangholabs/backfront) | Spring Boot + React 학습 프로젝트 |
| [ShinhanDS-FinanceSWAcademy](https://github.com/sangholabs/ShinhanDS-FinanceSWAcademy) | 신한DS 금융SW 아카데미 수업 자료 |

> 재직 중 만든 n8n 워크플로우와 콘텐츠 자동화 파이프라인은
> 클라이언트 정보와 API 설정이 포함되어 있어 공개 저장소에 두지 않았습니다.
> 구조와 설계 판단은 별도로 설명드릴 수 있습니다.

---

### 📊 Stats

![stats](https://github-readme-stats.vercel.app/api?username=sangholabs&show_icons=true&hide_border=true&theme=graywhite)
![langs](https://github-readme-stats.vercel.app/api/top-langs/?username=sangholabs&layout=compact&hide_border=true&theme=graywhite)

### 📫 Contact

📮 sangho5550@gmail.com ｜ ✍️ [velog.io/@sangho5550](https://velog.io/@sangho5550)

<sub>2022~2025년 학부 · 부트캠프 시기 저장소는 <a href="https://github.com/sangho5550">@sangho5550</a>에서 이곳으로 옮겼습니다.</sub>
