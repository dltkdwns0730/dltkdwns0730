<div align="center">
  <h1>이상준 | AI / Backend Engineer</h1>
  <p><b>실험으로 병목을 찾고, 구조로 성능과 비용을 개선하며, AI 기능을 서비스로 연결합니다.</b></p>
  <p>모델 성능 개선에서 시작해 백엔드, 배포, 아키텍처까지 함께 설계하는 엔지니어로 성장하고 있습니다.</p>

  <a href="mailto:dltkdwns0730@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email" />
  </a>
  <a href="https://www.linkedin.com/in/sangjun-lee-3913493a7/">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="https://github.com/dltkdwns0730">
    <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub" />
  </a>
  <img src="https://komarev.com/ghpvc/?username=dltkdwns0730&style=flat-square&color=blue" alt="profile views" />
</div>

---

## At a Glance

- **비용 최적화**: Re:View에서 **VLM API 호출 60% 절감**, PAZULE에서 **GPU 메모리 50% 절감**
- **성능 개선**: Summarizer **45s → 17.9s**, Capture F1 **0.77 → 0.97**
- **서비스화 경험**: FastAPI/Flask, LangGraph, Docker, Cloud Run, AWS Serverless
- **일하는 방식**: 데이터와 병목을 먼저 해석하고, 단일 변수 중심 실험으로 개선 효과를 검증

## Growth Journey

### 1. 실험을 설계하고 성능을 개선하는 법을 배웠습니다.

부스트캠프 대회와 모델 실험을 통해, 감으로 모델을 바꾸기보다 데이터와 실패 케이스를 먼저 해석하는 습관을 만들었습니다.

- Hand Bone Segmentation: Hausdorff Loss + Cut&Fill로 **Dice 0.9546**
- Object Detection: DDQ + Pseudo Labeling 기반 반복 개선으로 **mAP 0.711**
- Sentiment Analysis: TAPT + 앙상블 + 6단계 실험 반복으로 **F1 83.12%**

### 2. AI 기능을 사용자 경험으로 연결하는 법을 익혔습니다.

모델 성능 자체보다, 사용자가 체감하는 흐름과 검증 로직이 더 중요하다는 점을 프로젝트를 통해 배웠습니다.

- **PAZULE**: CLIP, BLIP, LangGraph를 결합한 관광 체험형 서비스 구현
- **라이브 커머스 추천**: AWS Serverless 기반 실시간 상품 인식 파이프라인 설계
- 결과적으로 AI 기능을 단일 모델이 아니라 제품 흐름 안에서 설계하는 관점을 갖게 되었습니다.

### 3. 이제는 비용과 아키텍처까지 함께 설계합니다.

최근에는 "모델이 동작한다"를 넘어서, 비용, 응답속도, 배포 구조까지 함께 개선하는 방향으로 성장하고 있습니다.

- **Re:View**에서 ORB + pHash로 중복 슬라이드를 제거해 **VLM API 호출 60% 절감**
- Summarizer 지연시간을 **45s → 17.9s**로 단축하고 Capture F1을 **0.77 → 0.97**로 개선
- 모놀리스에서 **6개 서비스 분산 전환안**을 설계하며 Redis, Kafka 기반 아키텍처 개선 문서화

## Representative Projects

### Re:View | 멀티모달 AI 강의 노트 자동 생성
> FastAPI + LangGraph + Gemini Flash | 5인 팀 | AI & Backend Infra | 198 commits

강의 영상의 음성과 슬라이드를 함께 해석해, 영상 없이도 이해 가능한 독립형 노트를 만드는 서비스입니다.

- **Role**: 캡처 파이프라인 최적화, 백엔드 API 및 비동기 처리 구조 설계, 배포 자동화, 아키텍처 개선안 문서화
- **Impact**: VLM API 호출 **60% 절감**, Summarizer 지연시간 **45s → 17.9s**, Capture F1 **0.77 → 0.97**
- **Links**: [GitHub](https://github.com/dltkdwns0730/Re-View) | [Notion](https://artistic-myrtle-971.notion.site/ReView-2f528309d08d805faa97d032c01a260d) | [Architecture Docs](https://github.com/dltkdwns0730/Re-View/blob/feature/architecture-improvement/docs/architecture-improvement.md)

### PAZULE | AI 기반 파주 관광 체험 플랫폼
> Flask + CLIP/BLIP + LangGraph Multi-Agent | 5인 팀 | Backend Lead | 파주시장상 수상

사용자 사진을 바탕으로 장소와 감성을 검증하고, 실패 시 힌트를 생성하는 체험형 관광 서비스입니다.

- **Role**: 백엔드 리드, AI 검증 파이프라인 설계, 모델 경량화, GPS/EXIF 메타데이터 검증 로직 구현
- **Impact**: BLIP FP16 적용으로 **GPU 메모리 50% 절감**, CLIP Scaled Attention으로 **추론 속도 37.5% 향상**, GPS + EXIF 검증으로 **부정 사진 95% 차단**
- **Links**: [GitHub](https://github.com/dltkdwns0730/PAZULE_AGENT) | [Notion](https://artistic-myrtle-971.notion.site/2f528309d08d80ffb5f3ec0977fb2854)

### 라이브 커머스 실시간 상품 추천
> AWS IVS + Rekognition + Lambda + DynamoDB | 캡스톤 프로젝트

라이브 스트리밍 화면에 등장한 상품을 감지해, 상품 정보와 구매 흐름을 실시간으로 연결하는 서버리스 서비스입니다.

- **Role**: 전체 시스템 설계 및 구현
- **Impact**: 이벤트 기반 서버리스 파이프라인으로 전체 처리 **5초 이내**, 신뢰도 기준 조정으로 오탐 이슈 완화
- **Links**: [Notion](https://artistic-myrtle-971.notion.site/2f628309d08d8075bba5eee8ab9cfc7b)

## Tech Focus

- **Backend**: Python, FastAPI, Flask, PostgreSQL, Redis
- **AI / ML**: PyTorch, OpenCV, HuggingFace, LangGraph, CLIP, BLIP, LLM/VLM Pipeline
- **Infra**: Docker, GCP Cloud Run, AWS Lambda, DynamoDB, IVS, Rekognition, GitHub Actions
- **Collaboration**: Git, WandB, Notion, Slack

## Education

- **네이버 부스트캠프 AI Tech 8기** | Computer Vision Track | 2025.09 - 2026.02
- **한림대학교 소프트웨어학부 빅데이터전공** | GPA 3.59 / 4.50 | 2021.03 - 2025.02
- **Certifications**: 정보처리기사, 빅데이터분석기사, ADsP
- **Language**: TOEIC 920, OPIc IH

## GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=dltkdwns0730&show_icons=true&theme=default&hide_border=true&count_private=true" height="165" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=dltkdwns0730&layout=compact&theme=default&hide_border=true" height="165" />
</p>

---

<div align="center">
  <sub>모델 성능을 넘어서, 서비스 구조와 운영 효율까지 책임지는 엔지니어를 지향합니다.</sub>
</div>
