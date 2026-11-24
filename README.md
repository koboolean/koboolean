
# 👋 안녕하세요. 문제를 발견하고, 더 나은 구조를 고민하는 백엔드 개발자입니다.

Spring을 중심으로 **서비스의 구조와 흐름을 설계하고 구현하는 백엔드 개발자**입니다.

단순히 요구사항에 맞춰 기능을 구현하기보다, **왜 필요한 기능인지, 어떤 구조가 유지보수와 확장에 유리한지**를 고민하며 개발합니다.

아이디어를 코드로 옮기는 데 그치지 않고 **기획 → 설계 → 개발 → 배포 → 운영 → 개선**까지 직접 경험하며, 지속적으로 발전시킬 수 있는 서비스를 만드는 것을 중요하게 생각합니다.

여행 서비스, 개발 생산성 도구, AI 기반 서비스를 직접 개발해 왔으며, 현재는 서로 다른 환경의 GPU·CPU 자원을 연결하여 AI 추론 요청을 분산 처리하는 **InfraMesh**와 AI 기반 데이터 모델링·메타데이터 관리 오픈소스 플랫폼 **Lexorma**를 개발하고 있습니다.

## 🔭 주요 프로젝트

- 🌐 **InfraMesh** — 이기종 GPU·CPU 자원을 연결하는 분산 AI 추론 인프라 플랫폼
- 🧩 **Lexorma** — 논리·물리 데이터 모델링, 데이터 표준화 및 AI 메타데이터 관리 오픈소스 플랫폼
- ⚙️ **MetaGen** — 네이밍·설계·테스트를 지원하는 개발 생산성 자동화 도구 *(유지보수 종료)*
- 🔮 **운결** — Spring AI와 Spring Batch 기반 개인 맞춤형 운세 인사이트 플랫폼 *(개발종료)*
- 🧭 **Moti** — 개인 맞춤형 여행 추천 및 일정 관리 서비스 *(운영 중단 · 재개발 예정)*

## 💡 주요 관심 분야

`Backend Architecture` · `Distributed Systems` · `AI Infrastructure` · `Data Modeling` · `Metadata Management` · `Developer Productivity` · `Service Design`

---

# 💻 Projects

## 🌐 InfraMesh

### 분산된 GPU·CPU 자원을 연결하여 AI 추론 요청을 효율적으로 분산 처리하는 AI 인프라 플랫폼

👉 [GitHub](https://github.com/InfraMeshLabs)

**프로젝트 개요**

InfraMesh는 서로 다른 네트워크와 컴퓨팅 환경에 존재하는 AI 실행 자원을 하나의 추론 인프라로 연결하기 위한 프로젝트입니다.

AI 요청을 관리하고 실행할 Worker를 선택하는 과정과 실제 AI 추론을 수행하는 과정을 분리하여, 다양한 AI Runtime과 라우팅 전략을 유연하게 확장할 수 있도록 설계하고 있습니다.

- 이기종 컴퓨팅 자원을 연결하기 위한 **분산 AI 추론 아키텍처 설계**
- Console / Router / Worker / Node SDK로 역할과 책임을 분리한 **모듈형 구조**
- Ollama / vLLM / Custom Runtime을 연결할 수 있는 확장 구조
- 다양한 네트워크 환경을 고려한 **Direct / Outbound 연결 방식**
- 공통 Node SDK를 Maven Central에 배포하여 외부 Router 및 Worker 구현 지원

**Backend / Architecture**

- Spring Boot 기반 **Control Plane 및 AI 요청 처리 파이프라인 설계**
- `ROUND_ROBIN`, `LEAST_LATENCY`, `LEAST_BUSY`, `AI_ROUTER` 기반 **Worker Routing Strategy 구현**
- Redis 기반 **Session Affinity**를 통한 동일 세션의 Worker 연결 유지
- Redis / In-Memory 기반 **Worker Capacity 및 In-Flight 요청 관리**
- Worker 상태 정보를 활용한 **Health Monitoring 및 동적 라우팅 구조 설계**
- WebSocket 기반 Outbound 연결로 외부에서 직접 접근하기 어려운 Node의 참여 지원
- Router의 Worker 선택 책임과 Worker의 Inference 실행 책임 분리
- 조직·팀·노드 중심의 자원 관리 및 API Key 기반 접근 제어
- 팀 단위 데이터 라우팅 정책을 통해 내부·외부 AI Runtime 사용 범위 제어
- 공통 DTO 및 Node 연결 기능을 `infra-node` SDK로 분리하고 Maven Central 배포 및 버전 관리
- Docker 기반 Console 배포 및 GitHub Actions를 활용한 빌드·릴리스 자동화

**Repository**

| Project | Description |
| --- | --- |
| `infra-console` | Organization, Team, Node 및 AI Infrastructure를 관리하는 Control Plane |
| `infra-node` | Router / Worker 연결을 위한 공통 SDK 및 Contract |
| `infra-router` | Worker 선택 및 Routing Strategy 구현을 위한 Reference Router |
| `infra-worker` | AI Runtime과 연동하여 추론 요청을 실행하는 Reference Worker |

---

## 🧩 Lexorma

### 논리·물리 데이터 모델링, 데이터 표준화 및 AI 메타데이터 관리를 통합하는 오픈소스 플랫폼

> **프로젝트 상태: 개발 중 · MetaGen 후속 프로젝트**

👉 [GitHub](https://github.com/Lexorma/Lexorma)

**프로젝트 개요**

Lexorma는 데이터베이스의 구조와 업무적 의미를 체계적으로 관리하기 위한 **오픈소스 데이터 모델링 및 메타데이터 관리 플랫폼**입니다.

기존 MetaGen의 개발 경험을 바탕으로 데이터 모델링, 데이터 표준화, 메타데이터 관리 기능을 통합하고, AI를 활용한 메타데이터 분석 및 데이터베이스 역공학으로 확장하고 있습니다.

단순히 데이터 사전이나 설계 문서를 생성하는 도구를 넘어, **데이터베이스의 구조와 의미를 분석하고, 표준화하며, 모델과 실제 데이터베이스 사이의 정합성을 관리할 수 있는 플랫폼**을 지향합니다.

특히 AI가 분석한 결과를 무조건 적용하기보다 **사용자의 검토와 승인 과정을 통해 데이터의 신뢰성을 확보하는 구조**를 중요하게 생각합니다.

**Data Modeling / ERD**

- 논리 엔터티·속성·식별자·관계를 관리하는 **논리 데이터 모델링**
- 스키마·테이블·컬럼·인덱스·제약조건을 관리하는 **물리 데이터 모델링**
- 논리·물리 ERD 조회 및 레이아웃 관리
- 복합 FK, 복합 인덱스, UNIQUE / CHECK 제약조건 관리
- 논리 엔터티·속성과 물리 테이블·컬럼 간 **매핑 관리**
- 논리·물리 모델 간 명칭, 타입, 길이, 필수 여부, 식별자 등 정합성 비교
- 데이터 모델과 테이블 관리 기능 간 연동

**Data Standardization / Metadata Management**

- 표준 단어·용어·도메인 기반 **데이터 표준 사전 관리**
- 표준 용어의 영문 약어를 활용한 컬럼명 생성
- 표준 항목 사용 현황 조회 및 **표준화 품질 진단**
- 데이터 사전 및 테이블·컬럼 메타데이터 관리
- 원본 DB 카탈로그 수집 및 모델 테이블과의 매핑
- 원본 테이블 매핑 예외 처리 및 원본 COMMENT 비교
- 표준화 규칙과 데이터 모델의 정합성 관리
- Excel 기반 데이터 사전 및 표준 정보 가져오기·내보내기

**AI / Metadata Intelligence**

- 로컬 LLM을 우선 고려한 **AI 메타데이터 분석 아키텍처**
- 메타데이터를 활용한 AI 기반 업무적 의미 분석 및 제안 기능 개발
- AI 분석 결과와 기존 메타데이터를 연결하는 검토 구조
- AI 제안에 대한 **사람 중심 평가 및 승인 워크플로**
- 평가 확정 전 제안 내용 블라인드 처리 및 필수 판정 검증
- 평가 결과에 따른 승인 전 재검증과 데이터 정합성 보호
- 외부 DB에 대한 상시 연결 대신 **필요 시 카탈로그 동기화** 방식 적용

**Backend / Architecture**

- Spring Boot + React SPA 기반 **단일 애플리케이션 / 단일 JAR 배포**
- Gradle 멀티 모듈 기반 공통·인증·시스템·운영·데이터 도메인 책임 분리
- Spring Security 및 Spring Session JDBC 기반 세션 인증
- 계층형 RBAC 및 프로젝트 단위 데이터 격리
- PostgreSQL 기반 운영 환경과 H2 기반 테스트 환경 구성
- Flyway 기반 데이터베이스 스키마 버전 관리
- Spring Data JPA / QueryDSL 기반 데이터 접근 계층
- Docker 멀티스테이지 빌드를 통한 React·Spring Boot 통합 배포
- 선택적 외부 DB 연결 및 AI 설정을 통한 **설정 최소화**
- AI 연동은 내부 Tool Calling을 우선하고 MCP는 선택적 확장 방식으로 설계

**향후 확장 방향**

- AI 기반 데이터 사전 생성 및 표준 용어 추천 고도화
- 데이터베이스 역공학 및 모델 동기화 기능 확장
- 스키마 변경 추적과 영향도 분석
- 추가 DBMS 및 OpenAI 호환 LLM Runtime 지원 확대
- 외부 개발 도구 및 AI 에이전트를 위한 선택적 MCP 연동
- 데이터 거버넌스와 메타데이터 품질 관리 기능 강화

**Project Direction**

Open Source Data Modeling & Metadata Management Platform

---

## ⚙️ MetaGen

### 데이터 사전과 규칙 기반 명명법을 활용하여 개발 과정의 반복 작업을 줄이는 생산성 자동화 도구

> **프로젝트 상태: 유지보수 종료 · 후속 프로젝트 Lexorma**

👉 [GitHub](https://github.com/meta-gen) · [Docs](https://metagen-react.vercel.app/)

**프로젝트 개요**

MetaGen은 개발 과정에서 반복적으로 발생하는 메소드·함수 네이밍, 설계 문서 작성 및 테스트 시나리오 구성을 지원하기 위해 개발한 생산성 자동화 도구입니다.

데이터 사전과 규칙 기반 자동화를 활용하여 개발 과정에서 반복적으로 발생하는 작업을 줄이고, 일관된 개발 산출물을 생성하는 것을 목표로 개발했습니다.

기존 프로젝트의 신규 기능 개발 및 유지보수는 종료하고, 데이터 모델링과 메타데이터 관리 기능을 중심으로 확장한 후속 오픈소스 프로젝트 **Lexorma**로 개발 방향을 전환했습니다.

- 데이터 사전 및 규칙 기반 **메소드·함수명 자동 생성**
- 일관된 네이밍 규칙을 통한 코드 가독성과 품질 개선
- 설계서 및 테스트 시나리오 작성 지원
- 반복적인 개발 작업을 줄이기 위한 자동화 구조 설계

**Backend / Automation**

- 데이터 사전과 명명 규칙을 활용한 생성 로직 설계
- 일관된 결과 생성을 위한 규칙 및 데이터 모델링
- 설계 → 테스트로 이어지는 데이터 처리 흐름 정의
- 개발 생산성 향상을 위한 자동화 기능 구현

---

## 🔮 운결

### Spring AI와 Spring Batch를 활용해 운세 데이터를 축적하고 개인 맞춤형 인사이트를 제공하는 플랫폼

👉 [GitHub](https://github.com/ungyeol-log)

**프로젝트 개요**

일별 운세 데이터를 생성하고 축적하여, 단순한 운세 조회를 넘어 사용자의 기록과 데이터 흐름을 기반으로 개인화된 인사이트를 제공하기 위한 프로젝트입니다.

- 서비스 기획부터 **백엔드 아키텍처 및 데이터 모델 직접 설계**
- Spring AI를 활용한 운세 생성 및 프롬프트 처리 구조
- Spring Batch 기반 일별 데이터 생성·적재 프로세스
- 축적된 운세 데이터와 사용자 기록을 활용한 개인화 로직 구현

**Backend / Data Processing**

- Spring AI 기반 AI 요청 및 응답 처리 구조 설계
- Spring Batch를 활용한 **일별 운세 생성·저장 작업 구성**
- 운세 데이터 및 사용자 기록 관리 API 구현
- 데이터 축적을 고려한 도메인 모델 및 저장 구조 설계
- 생성 → 저장 → 분석 → 인사이트 제공으로 이어지는 데이터 처리 흐름 구현

---

## 🧭 Moti

### 개인 맞춤형 여행 루트를 추천하고 사용자의 여행 스타일에 따라 자유롭게 일정을 구성할 수 있도록 개발한 여행 플랫폼

> **프로젝트 상태: 서비스 운영 중단 · 재개발 예정**
>
> 초기 버전을 웹과 모바일 앱으로 출시하고 운영한 경험을 바탕으로, 향후 서비스 구조와 사용자 경험을 개선하여 재개발할 예정입니다.

👉 [GitHub](https://github.com/moti-service)

**프로젝트 개요**

Moti는 사용자의 여행 선호도를 기반으로 여행지를 추천하고, 여행 일정을 직접 구성하고 관리할 수 있도록 개발한 개인 프로젝트입니다.

서비스의 아이디어 구상부터 개발, 클라우드 인프라 구성, 모바일 앱 출시 및 운영까지 전 과정을 직접 수행했습니다.

- 개인 프로젝트로 **기획 → 설계 → 개발 → 배포 → 운영 전 과정 수행**
- 사용자 선호도를 반영한 **맞춤형 여행 추천 기능 설계 및 구현**
- 여행 일정의 자유로운 생성·수정·관리를 위한 도메인 구조 설계
- 웹 서비스 및 Android / iOS 앱 출시 경험
- AWS 기반 서비스 인프라 구축 및 운영
- 초기 서비스 운영 종료 후 재개발을 위한 구조 개선 계획

**Backend / Service Architecture**

- 여행 추천 및 일정 관리 도메인의 **REST API와 데이터 모델 설계**
- 사용자 입력과 여행 데이터를 결합하는 추천 로직 구현
- 여행 일정 생성·수정·조회에 필요한 데이터 처리 및 상태 관리
- 서비스 특성을 고려한 백엔드 API 및 데이터 흐름 설계
- AWS 기반 애플리케이션·데이터베이스·네트워크 인프라 운영 경험
- 배포 및 운영뿐 아니라 서비스 종료에 따른 **클라우드 리소스 정리와 비용 관리 경험**

**향후 개선 방향**

- 초기 서비스 구조를 재검토하고 유지보수성과 확장성을 고려한 아키텍처 개선
- 여행 추천 및 일정 관리 경험 개선
- 서비스 운영 효율성과 인프라 비용을 고려한 배포 구조 재설계

---

## 📄 CV-FIT

### 이력서와 포트폴리오 정보를 체계적으로 관리하기 위한 웹 서비스

👉 [GitHub](https://github.com/kobooleans/resume-project)

- React와 Spring Boot 기반 이력서 관리 서비스
- 사용자 및 이력서 정보를 중심으로 한 도메인 모델 설계
- 이력서 생성·수정·조회 등 **CRUD API 구현**
- 프론트엔드와 백엔드 간 REST API 연동
- 사용자 입력 데이터 관리 및 처리 흐름 구현

---

## 🧳 SOLT

### 나홀로 여행자를 위한 여행 추천 모바일 앱

👉 [GitHub](https://github.com/koboolean/chang_2nd_main_project)

- Flutter 및 Firebase를 활용한 여행 추천 애플리케이션 개발
- 모바일 환경에서의 사용자 경험 및 여행 추천 기능 구현 경험

---

# 🧠 Development Philosophy

개발할 때 다음과 같은 기준을 중요하게 생각합니다.

- **문제 중심의 개발** — 기능 구현에 앞서 해결하려는 문제와 요구사항을 이해합니다.
- **역할과 책임의 분리** — 변경과 확장에 유연한 구조를 설계합니다.
- **유지보수 가능한 코드** — 동작하는 코드뿐 아니라 이후의 변경까지 고려합니다.
- **자동화와 생산성 개선** — 반복적인 작업을 줄이고 개발 과정의 효율성을 높입니다.
- **실제 서비스 경험** — 아이디어를 개발과 배포에 연결하고 운영 과정에서 개선점을 발견합니다.

---


# 💻 Tech Stack

## Backend

### Language / Application Framework

<div>
  <img alt="Java" src="https://img.shields.io/badge/JAVA-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img alt="Spring" src="https://img.shields.io/badge/SPRING-6DB33F?style=for-the-badge&logo=spring&logoColor=white"/>
  <img alt="Spring Boot" src="https://img.shields.io/badge/SPRING_BOOT-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"/>
  <img alt="Spring Security" src="https://img.shields.io/badge/SPRING_SECURITY-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white"/>
  <img alt="Spring Cloud" src="https://img.shields.io/badge/SPRING_CLOUD-6DB33F?style=for-the-badge&logo=spring&logoColor=white"/>
  <img alt="Spring Batch" src="https://img.shields.io/badge/SPRING_BATCH-6DB33F?style=for-the-badge&logo=spring&logoColor=white"/>
</div>

### ORM / Data Access

<div>
  <img alt="JPA" src="https://img.shields.io/badge/JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white"/>
  <img alt="QueryDSL" src="https://img.shields.io/badge/QUERYDSL-0769AD?style=for-the-badge"/>
  <img alt="MyBatis" src="https://img.shields.io/badge/MYBATIS-BF0000?style=for-the-badge"/>
</div>

### API / GraphQL

<div>
  <img alt="REST API" src="https://img.shields.io/badge/REST_API-005571?style=for-the-badge"/>
  <img alt="GraphQL" src="https://img.shields.io/badge/GRAPHQL-E10098?style=for-the-badge&logo=graphql&logoColor=white"/>
  <img alt="Netflix DGS" src="https://img.shields.io/badge/NETFLIX_DGS-E50914?style=for-the-badge&logo=netflix&logoColor=white"/>
  <img alt="Swagger" src="https://img.shields.io/badge/SWAGGER-85EA2D?style=for-the-badge&logo=swagger&logoColor=black"/>
</div>

### Testing

<div>
  <img alt="JUnit5" src="https://img.shields.io/badge/JUNIT5-25A162?style=for-the-badge&logo=junit5&logoColor=white"/>
  <img alt="Mockito" src="https://img.shields.io/badge/MOCKITO-59666C?style=for-the-badge"/>
  <img alt="Testcontainers" src="https://img.shields.io/badge/TESTCONTAINERS-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
</div>

## Database

### RDBMS

<div>
  <img alt="Oracle" src="https://img.shields.io/badge/ORACLE-F80000?style=for-the-badge&logo=oracle&logoColor=white"/>
  <img alt="MariaDB" src="https://img.shields.io/badge/MARIADB-003545?style=for-the-badge&logo=mariadb&logoColor=white"/>
  <img alt="PostgreSQL" src="https://img.shields.io/badge/POSTGRESQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
</div>

### NoSQL / Cache

<div>
  <img alt="Firebase" src="https://img.shields.io/badge/FIREBASE-DD2C00?style=for-the-badge&logo=firebase&logoColor=white"/>
  <img alt="Redis" src="https://img.shields.io/badge/REDIS-DC3829?style=for-the-badge&logo=redis&logoColor=white"/>
</div>

## Frontend

### Web Technologies

<div>
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white"/>
  <img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css&logoColor=white"/>
  <img alt="JavaScript" src="https://img.shields.io/badge/JAVASCRIPT-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
  <img alt="TypeScript" src="https://img.shields.io/badge/TYPESCRIPT-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
</div>

### Frameworks / Libraries

<div>
  <img alt="React" src="https://img.shields.io/badge/REACT-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
  <img alt="Vue.js" src="https://img.shields.io/badge/VUE.JS-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white"/>
  <img alt="Flutter" src="https://img.shields.io/badge/FLUTTER-02569B?style=for-the-badge&logo=flutter&logoColor=white"/>
</div>

## DevOps / Infrastructure

### Container / Cloud

<div>
  <img alt="Docker" src="https://img.shields.io/badge/DOCKER-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img alt="Kubernetes" src="https://img.shields.io/badge/KUBERNETES-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white"/>
  <img alt="AWS" src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white"/>
</div>

### CI/CD / Build / Migration

<div>
  <img alt="Jenkins" src="https://img.shields.io/badge/JENKINS-D24939?style=for-the-badge&logo=jenkins&logoColor=white"/>
  <img alt="Gradle" src="https://img.shields.io/badge/GRADLE-02303A?style=for-the-badge&logo=gradle&logoColor=white"/>
  <img alt="Flyway" src="https://img.shields.io/badge/FLYWAY-CC0200?style=for-the-badge&logo=flyway&logoColor=white"/>
  <img alt="Liquibase" src="https://img.shields.io/badge/LIQUIBASE-2962FF?style=for-the-badge&logo=liquibase&logoColor=white"/>
</div>

## Message Broker

<div>
  <img alt="Apache Kafka" src="https://img.shields.io/badge/APACHE_KAFKA-231F20?style=for-the-badge&logo=apachekafka&logoColor=white"/>
</div>

## AI / LLM Integration

<div>
  <img alt="Spring AI" src="https://img.shields.io/badge/SPRING_AI-6DB33F?style=for-the-badge&logo=spring&logoColor=white"/>
  <img alt="LangChain" src="https://img.shields.io/badge/LANGCHAIN-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white"/>
</div>

---

# 🧑 GitHub

<p align="center">
  <a href="https://github.com/koboolean">
    <img height="180" src="https://github-stats-extended.vercel.app/api?username=koboolean&show_icons=true&theme=transparent&rank_icon=github&line_height=28" />
  </a>
  <a href="https://github.com/koboolean">
    <img height="180" src="https://github-stats-extended.vercel.app/api/top-langs/?username=koboolean&size_weight=0.3&count_weight=0.3&layout=donut&theme=transparent" />
  </a>
</p>
