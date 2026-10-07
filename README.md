# 🌱 계속 만들고, 개선하고, 더 나은 구조를 고민하는 개발자입니다

Spring 기반 백엔드 개발자로 단순 구현을 넘어 **사용자에게 필요한 기능과 그 흐름을 함께 설계하는 데 집중합니다.**

아이디어를 실제 서비스로 구현하며 **기획 → 설계 → 개발 → 배포까지 전 과정을 경험하고 있습니다.**

---

# 💻 Project

## 🌐 InfraMesh
### 서로 다른 환경의 GPU·CPU 자원을 연결하여 AI 추론 작업을 분산 처리할 수 있도록 설계한 분산 AI 인프라 플랫폼

👉 [GitHub](https://github.com/InfraMeshLabs)

- 이기종 컴퓨팅 자원을 하나의 AI 추론 네트워크로 연결하기 위한 **분산 시스템 구조 설계**
- Console / Router / Worker / Node SDK로 역할을 분리하여 **확장 가능한 아키텍처 구성**
- 로컬 및 원격 AI Runtime을 연결할 수 있도록 **Ollama / vLLM / Custom Runtime 지원**
- 다양한 네트워크 환경의 Node가 참여할 수 있도록 **Direct / Outbound 연결 구조 설계**
- 공통 Node SDK를 Maven Central에 배포하여 **외부 Router / Worker 구현 확장 구조 제공**

👉 Backend / Architecture 관점

- Spring Boot 기반 **Control Plane 및 AI 요청 라우팅 파이프라인 설계**
- `ROUND_ROBIN`, `LEAST_LATENCY`, `LEAST_BUSY`, `AI_ROUTER` 등 **Worker Routing Strategy 구조 설계**
- Redis 기반 **Session Affinity**를 구현하여 동일 세션의 Worker 연결 유지
- Redis / In-Memory 기반 **Worker Capacity 관리 구조 설계**
- Worker의 요청 수, Queue, Latency, CPU/GPU/Memory/VRAM 상태를 활용할 수 있는 **Health 및 Routing 데이터 구조 설계**
- WebSocket 기반 Outbound 연결을 통해 외부에서 직접 접근하기 어려운 Node도 네트워크에 참여할 수 있도록 구성
- Router는 Worker 선택, Worker는 실제 Inference 실행을 담당하도록 **Routing과 Runtime 책임 분리**
- 공통 DTO 및 Node 연결 기능을 `infra-node` SDK로 분리하고 **Maven Central 배포 및 버전 관리**
- Docker 기반 Console 배포 및 GitHub Actions를 활용한 **빌드·릴리즈 자동화 구성**

### Repository

| Project | Description |
| --- | --- |
| `infra-console` | Organization, Team, Node 및 AI Infrastructure를 관리하는 Control Plane |
| `infra-node` | Router / Worker 연결을 위한 공통 SDK 및 Contract |
| `infra-router` | Worker 선택 및 Routing Strategy 구현을 위한 Reference Router |
| `infra-worker` | AI Runtime과 연결되어 실제 추론 요청을 실행하는 Reference Worker |

---

## 🔮 운결
### Spring AI와 Spring Batch를 활용하여 운세 데이터를 기록하고, 축적된 데이터를 기반으로 개인 맞춤형 인사이트를 제공하는 플랫폼

👉 [GitHub](https://github.com/ungyeol-log/.github)

- 기획부터 백엔드 개발까지 **전 과정을 직접 설계 및 구현**
- Spring AI를 활용한 **운세 생성과 일별 배치 기반 데이터 관리 구조 설계**
- 축적된 운세 데이터를 분석하여 **개인의 운의 흐름과 패턴을 해석하는 서비스 구현**

👉 Backend 관점

- Spring AI 기반 운세 생성 및 프롬프트 처리 구조 설계
- Spring Batch를 활용한 일별 운세 생성 및 데이터 적재 프로세스 구현
- 운세 데이터 및 사용자 기록을 관리하기 위한 API와 데이터 모델 설계
- 축적된 데이터를 기반으로 운의 흐름과 패턴을 분석하는 인사이트 제공 로직 구현
- 데이터 생성, 저장, 분석까지 이어지는 서비스 흐름 및 상태 관리 설계

---

## 🧭 Moti
### 개인 맞춤형 여행 루트를 추천하고, 사용자의 여행 스타일에 따라 자유롭게 계획을 구성할 수 있는 플랫폼

👉 [GitHub](https://github.com/moti-service) · [Web](https://motitour.com/) · [Google Play](https://play.google.com/store/apps/details?id=com.koboolean.moti) · [App Store](https://apps.apple.com/us/app/moti-%EB%AA%A8%ED%8B%B0-%EB%AA%A8%EB%91%90%EC%9D%98-%EC%97%AC%ED%96%89/id6753739255)

- 기획부터 개발, 배포까지 **혼자서 A-Z 전 과정을 담당**
- 여행 도메인을 기반으로 **사용자 맞춤형 추천 경험 설계 및 구현**
- 여행 루트를 유연하게 구성하기 위한 **도메인 중심 데이터 구조 설계**

👉 Backend 관점

- 추천/여행 도메인을 기준으로 **API 구조 및 데이터 모델 직접 설계**
- 사용자 입력과 여행 데이터를 결합하는 **추천 로직 구현 및 흐름 최적화**
- 서비스 흐름을 고려한 **데이터 처리 및 상태 관리 구조 설계**

---

## ⚙️ MetaGen
### 데이터 사전 또는 규칙 기반 명명법을 활용하여 메소드와 함수명을 자동으로 생성하고, 설계서 및 테스트 시나리오 작성을 지원하는 자동화 도구

👉 [GitHub](https://github.com/meta-gen) · [Docs](https://metagen-react.vercel.app/)

- 반복적인 네이밍 작업을 줄이기 위한 **개발 생산성 자동화 도구**
- 규칙 기반 네이밍을 통해 **일관된 코드 품질 유지**
- 설계 → 테스트 흐름까지 이어지는 **개발 프로세스 개선 구조 설계**

👉 Backend 관점

- 네이밍 규칙 및 데이터 사전을 기반으로 한 **생성 로직 설계**
- 설계 → 테스트로 이어지는 **데이터 흐름 구조 정의**
- 일관된 결과 생성을 위한 **도메인 모델링 및 처리 로직 구현**

---

## 📄 CV-FIT
### 포트폴리오 및 이력서 관리 프로젝트 (React, Spring Boot)

👉 [Service](https://cv-fit.com) · [GitHub](https://github.com/kobooleans/resume-project)

- 포트폴리오와 이력서 관리를 위한 서비스 구현

👉 Backend 관점

- 사용자/이력서 도메인 기반 **데이터 모델 및 API 설계**
- 이력서 데이터의 생성·수정·조회 흐름을 위한 **CRUD 구조 구현**
- 프론트엔드와의 연동을 고려한 **REST API 설계 및 데이터 처리**

---

## 🧳 SOLT
### 나홀로 여행자를 위한 추천 앱 (Flutter, Firebase)

👉 [GitHub](https://github.com/koboolean/chang_2nd_main_project)

- 여행 추천을 주제로 진행한 프로젝트

---

# 🧠 이런 걸 중요하게 생각합니다

- 기능 구현보다 **구조와 흐름을 먼저 고민하는 개발**
- 역할과 책임을 명확하게 나누는 **확장 가능한 아키텍처**
- 반복 작업을 줄이기 위한 **자동화와 생산성 개선**
- “일단 돌아가는 코드”보다 **지속 가능한 코드**
- 아이디어를 설계에 그치지 않고 **실제 서비스와 배포까지 연결하는 개발**

---

# 💻 Stack

## Backend

### Application Framework

<div>
  <img alt="Spring" src="https://img.shields.io/badge/SPRING-6DB33F?style=for-the-badge&logo=Spring&logoColor=white"/>
  <img alt="Spring Boot" src="https://img.shields.io/badge/SPRINGBOOT-6DB33F?style=for-the-badge&logo=SpringBoot&logoColor=white"/>
  <img alt="Spring Security" src="https://img.shields.io/badge/SPRING_SECURITY-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white"/>
  <img alt="Spring Cloud" src="https://img.shields.io/badge/SPRING_CLOUD-6DB33F?style=for-the-badge&logo=Spring&logoColor=white"/>
  <img alt="JPA" src="https://img.shields.io/badge/JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white"/>
</div>

### API / GraphQL

<div>
  <img alt="GraphQL" src="https://img.shields.io/badge/GRAPHQL-E10098?style=for-the-badge&logo=graphql&logoColor=white"/>
  <img alt="Netflix DGS" src="https://img.shields.io/badge/NETFLIX_DGS-E50914?style=for-the-badge&logo=netflix&logoColor=white"/>
  <img alt="Swagger" src="https://img.shields.io/badge/SWAGGER-85EA2D?style=for-the-badge&logo=swagger&logoColor=black"/>
</div>

### Testing Tools

<div>
  <img alt="JUnit5" src="https://img.shields.io/badge/JUNIT5-25A162?style=for-the-badge&logo=junit5&logoColor=white"/>
  <img alt="Mockito" src="https://img.shields.io/badge/MOCKITO-59666C?style=for-the-badge&logo=junit5&logoColor=white"/>
</div>

## Database

### RDBMS

<div>
  <img alt="Oracle" src="https://img.shields.io/badge/ORACLE-F80000?style=for-the-badge&logo=oracle&logoColor=white"/>
  <img alt="MariaDB" src="https://img.shields.io/badge/MARIADB-003545?style=for-the-badge&logo=mariadb&logoColor=white"/>
  <img alt="PostgreSQL" src="https://img.shields.io/badge/POSTGRESQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
</div>

### NoSQL Database

<div>
  <img alt="Firebase" src="https://img.shields.io/badge/FIREBASE-DD2C00?style=for-the-badge&logo=firebase&logoColor=white"/>
</div>

### Cache / In-Memory Data Store

<div>
  <img alt="Redis" src="https://img.shields.io/badge/REDIS-DC382D?style=for-the-badge&logo=redis&logoColor=white"/>
</div>

## Front

### Web Frontend Technologies

<div>
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-E34F26.svg?style=for-the-badge&logo=HTML5&logoColor=white"/>
  <img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6.svg?style=for-the-badge&logo=CSS3&logoColor=white"/>
  <img alt="JavaScript" src="https://img.shields.io/badge/JAVASCRIPT-F7DF1E.svg?style=for-the-badge&logo=JavaScript&logoColor=black"/>
  <img alt="TypeScript" src="https://img.shields.io/badge/TYPESCRIPT-3178C6.svg?style=for-the-badge&logo=TypeScript&logoColor=white"/>
</div>

### Frontend Frameworks / Libraries

<div>
  <img alt="Flutter" src="https://img.shields.io/badge/FLUTTER-02569B.svg?style=for-the-badge&logo=Flutter&logoColor=white"/>
  <img alt="React" src="https://img.shields.io/badge/REACT-61DAFB?style=for-the-badge&logo=React&logoColor=black"/>
  <img alt="Vue.js" src="https://img.shields.io/badge/VUE.JS-4FC08D?style=for-the-badge&logo=Vue.js&logoColor=black"/>
</div>

## DevOps

<div>
  <img alt="Docker" src="https://img.shields.io/badge/DOCKER-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img alt="Kubernetes" src="https://img.shields.io/badge/KUBERNETES-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white"/>
  <img alt="Jenkins" src="https://img.shields.io/badge/JENKINS-D24939?style=for-the-badge&logo=jenkins&logoColor=white"/>
  <img alt="Liquibase" src="https://img.shields.io/badge/LIQUIBASE-2962FF?style=for-the-badge&logo=liquibase&logoColor=white"/>
</div>

## Message Broker

<div>
  <img alt="Apache Kafka" src="https://img.shields.io/badge/APACHE_KAFKA-231F20?style=for-the-badge&logo=apachekafka&logoColor=white"/>
</div>

## AI / LLM

<div>
  <img alt="Spring AI" src="https://img.shields.io/badge/SPRING_AI-6DB33F?style=for-the-badge&logo=Spring&logoColor=white"/>
  <img alt="Ollama" src="https://img.shields.io/badge/OLLAMA-000000?style=for-the-badge&logo=ollama&logoColor=white"/>
  <img alt="vLLM" src="https://img.shields.io/badge/vLLM-4051B5?style=for-the-badge"/>
</div>

## 국내 통합 프레임워크

<div>
  <img alt="ExBuilder" src="https://img.shields.io/badge/EXBUILDER-3776AB?style=for-the-badge"/>
  <img alt="XPlatform" src="https://img.shields.io/badge/XPLATFORM-3776AB?style=for-the-badge"/>
</div>

---

# 🧑 GitHub

[![GitHub stats](https://github-readme-stats-fast.vercel.app/api?username=koboolean&show_icons=true&theme=transparent&rank_icon=github&line_height=28)](https://github.com/koboolean)

[![Top Langs](https://github-readme-stats-fast.vercel.app/api/top-langs/?username=koboolean&size_weight=0.3&count_weight=0.3&layout=donut&theme=transparent)](https://github.com/koboolean)
