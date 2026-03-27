# 이상준 | AI / Backend Engineer

실험으로 병목을 찾고, 구조로 성능과 비용을 개선하며, AI 기능을 서비스로 연결합니다.

Contact: `dltkdwns0730@gmail.com`  
LinkedIn: `linkedin.com/in/sangjun-lee-3913493a7`  
GitHub: `github.com/dltkdwns0730`

---

## What I Value

- **가치관**: 좋은 결과는 좋은 모델 하나보다, 문제를 정확히 정의하고 검증 가능한 가설로 쪼개는 과정에서 나온다고 믿습니다.
- **성장 목표**: 모델 성능 개선 경험을 출발점으로, 이제는 백엔드, 배포, 비용, 운영 효율까지 함께 책임지는 AI/Backend Engineer로 성장하고 있습니다.
- **성취**: Competition에서는 Dice **0.9546**, mAP **0.711**, Macro F1 **83.12%**를 만들었고, Service에서는 VLM API 호출 **60% 절감**, GPU 메모리 **50% 절감**, 실시간 처리 **5초 이내**를 구현했습니다.
- **팀워크**: Git-flow, PR 리뷰, WandB, Notion 기록 규칙을 맞추고, 트러블슈팅 로그와 실험 인사이트를 문서화해 팀 전체의 시행착오를 줄이는 방식으로 협업합니다.
- **성격**: 문제가 생기면 감으로 밀어붙이기보다 로그와 실패 케이스로 원인을 좁히고, 배운 점을 다음 프로젝트의 설계 원칙으로 연결하는 편입니다.

## Project Map

### Service

- [Re:View](#project-service-review): 강의 영상을 독립형 노트로 바꾸는 멀티모달 AI 서비스입니다. 설계 목적은 STT, VLM, 요약 파이프라인을 실제 사용자 가치와 비용 효율로 연결하는 것입니다.
- [PAZULE](#project-service-pazule): 파주 출판단지 체험형 보물찾기 서비스입니다. 설계 목적은 검증, 힌트 생성, 응답 포맷을 멀티에이전트 구조로 분리해 사용자 경험을 설계하는 것입니다.
- [Live Commerce](#project-service-live-commerce): 실시간 상품 인식 기반 라이브 커머스 서비스입니다. 설계 목적은 100% Serverless로 낮은 운영 부담의 실시간 추천 파이프라인을 만드는 것입니다.

### Competition

- [Hand Bone Segmentation](#project-competition-hand-bone): Hand Bone X-ray에서 29개 뼈를 분할하는 프로젝트입니다. 목표는 **Dice**를 높이되, Domain Shift를 반영하는 신뢰 가능한 검증 기준을 함께 설계하는 것이었습니다.
- [Object Detection](#project-competition-object-detection): 쓰레기 객체 검출 프로젝트입니다. 목표는 **mAP** 향상이며, 변인 통제 기반 실험으로 탐지 파이프라인을 단계적으로 고도화하는 데 집중했습니다.

### Experiment

- [Sentiment Analysis](#project-experiment-sentiment): 네이버 영화 리뷰 4단계 감정 분류 프로젝트입니다. 목표는 **Macro F1** 향상이며, 클래스 불균형과 도메인 적응 문제를 함께 해결하는 방향으로 모델링했습니다.

## Project Details

### Service

<a id="project-service-review"></a>
#### Re:View
> Service | 5인 팀 | 목표: 강의 영상에서 독립형 강의 노트 자동 생성 + 챗봇 튜터 구현

- **역할**: 캡처 파이프라인 최적화, 백엔드 API 및 비동기 처리 구조 설계, 오디오 처리 개선, 아키텍처 개선안 문서화
- **문제 발생**: Whisper의 한국어 인식률이 낮았고, 슬라이드 중복 캡처가 비용과 지연시간을 키웠으며, 모놀리스 구조는 확장성 한계가 있었습니다.
- **문제 정의**: 한국어 강의 환경에서는 STT 정확도와 슬라이드 중복 제어가 곧 품질과 비용 문제로 이어졌고, 파이프라인 구조 역시 서비스화 관점에서 재설계가 필요했습니다.
- **문제 해결**: Clova Speech 중심의 STT Router Pattern을 설계하고, ORB + pHash 기반 2단계 중복 제거 로직을 구현했으며, 비동기 처리 흐름과 6개 서비스 분산 전환안을 설계했습니다.
- **성과**: Clova WER **6%**, VLM API 호출 **60% 절감**, Summarizer 지연시간 **45s → 17.9s**, Capture F1 **0.77 → 0.97**
- **자세히**: [GitHub](https://github.com/dltkdwns0730/Re-View) | [Notion](https://artistic-myrtle-971.notion.site/ReView-2f528309d08d805faa97d032c01a260d) | [Architecture Docs](https://github.com/dltkdwns0730/Re-View/blob/feature/architecture-improvement/docs/architecture-improvement.md)

<a id="project-service-pazule"></a>
#### PAZULE
> Service | 5인 팀 | 파주시장상 수상 | 목표: AI 기반 파주 출판단지 랜드마크 보물찾기 게임 개발

- **역할**: 백엔드 리드, AI 검증 파이프라인 설계, LangGraph 멀티에이전트 구조 설계, 모델 경량화, GPS/EXIF 메타데이터 검증 로직 구현
- **문제 발생**: BLIP, CLIP, GPT-4o-mini 등 여러 AI 모듈이 하나의 사용자 흐름 안에 엮여 있었고, 단일 코드 구조로는 검증 로직과 힌트 생성 흐름을 관리하기 어려웠습니다.
- **문제 정의**: 사용자 입력 검증, 정답 판별, 힌트 생성, 응답 포맷을 분리하지 않으면 서비스 품질과 개발 생산성이 모두 떨어지는 구조였습니다.
- **문제 해결**: Security, Tech, Design Agent로 역할을 나눈 LangGraph 구조를 설계했고, BLIP VQA, CLIP 감성 분석, GPT-4o-mini 힌트 생성기를 조합한 듀얼 AI 미션 체계를 구현했습니다.
- **성과**: 파주시장상 수상, BLIP FP16 적용으로 **GPU 메모리 50% 절감**, CLIP SDPA 적용으로 **추론 속도 37.5% 향상**, GPS + EXIF 검증으로 **부정 사진 95% 차단**
- **자세히**: [GitHub](https://github.com/dltkdwns0730/PAZULE_AGENT) | [Notion](https://artistic-myrtle-971.notion.site/2f528309d08d80ffb5f3ec0977fb2854)

<a id="project-service-live-commerce"></a>
#### Live Commerce
> Service | 캡스톤 프로젝트 | 목표: 실시간 라이브 스트리밍 중 상품 자동 인식 및 구매 링크 제공

- **역할**: 전체 시스템 설계 및 구현
- **문제 발생**: 라이브 영상에서 상품을 감지하고 사용자 화면에 반영하기까지의 흐름이 지연되면, 추천 기능 자체가 사용성을 잃는 구조였습니다.
- **문제 정의**: 실시간성 확보와 운영 단순화를 동시에 만족시키기 위해서는 서버 관리 부담이 적고 이벤트 기반으로 연결되는 구조가 필요했습니다.
- **문제 해결**: AWS IVS, S3, Lambda, Rekognition, DynamoDB, IVS Metadata를 연결한 Event-Driven Serverless 파이프라인을 설계하고, Confidence 기준과 중복 방지 로직을 추가했습니다.
- **성과**: 전체 처리 **5초 이내**, **100% Serverless** 아키텍처 구현, Confidence **80% → 90%** 조정으로 오탐 최소화
- **자세히**: [Notion](https://artistic-myrtle-971.notion.site/2f628309d08d8075bba5eee8ab9cfc7b)

### Competition

<a id="project-competition-hand-bone"></a>
#### Hand Bone Segmentation
> Competition | 6인 팀 | 목표: Hand Bone X-ray 29개 뼈 Semantic Segmentation | Metric: Dice

- **역할**: EDA 기반 문제 정의, 데이터 재설계, 검증 지표 설계, 학습 전략 수립, 후처리 파이프라인 설계
- **문제 발생**: Train은 Open 손 비율이 높고 Test는 Folded 손 비율이 높아 Domain Shift가 컸으며, 2048 해상도 학습 시 OOM과 라벨 품질 문제도 존재했습니다.
- **문제 정의**: 리더보드 점수만 따라가면 실제 Test 분포를 반영하지 못했고, 손목 overlap과 Folded 데이터 부족을 반영하는 검증 기준이 필요했습니다.
- **문제 해결**: TVS(Trustworthy Validation Score)를 설계하고, LL → RR 반전과 Carpal Bone crop으로 표본 다양성을 확보했으며, FP16 + Gradient Accumulation과 Cut & Fill 후처리를 적용했습니다.
- **성과**: Dice **0.9071 → 0.9546 (+5.2%p)**, Private **7위**, 경계 밖 픽셀 평균 **15.92% 감소**
- **자세히**: [GitHub](https://github.com/dltkdwns0730/pro-cv-semanticsegmentation-cv-02) | [Notion](https://artistic-myrtle-971.notion.site/Hand-Bone-Image-Segmentation-2f528309d08d803482dde529f91f75ed)

<a id="project-competition-object-detection"></a>
#### Object Detection
> Competition | 팀 프로젝트 | 목표: 쓰레기 이미지 객체 검출 및 분류 | Metric: mAP

- **역할**: DDQ 모델 단계적 개선, ViTDet 트러블슈팅 공유, 변인 통제 기반 실험 설계
- **문제 발생**: Transformer 계열 모델은 V100 환경에서 메모리 제약이 컸고, 단일 기법으로는 성능이 정체되었으며, 증강 기법 역시 모델별 호환성이 달랐습니다.
- **문제 정의**: 실험 우선순위를 명확히 하지 않으면 개선 효과를 분리하기 어렵고, 메모리 제약을 해결하지 못하면 고성능 모델 실험 자체가 불가능했습니다.
- **문제 해결**: Batch Size와 Mixed Precision 조합으로 학습을 안정화하고, DDQ에 LSJ와 Pseudo Labeling을 단계적으로 적용했으며, TTA와 증강 기법의 순수 효과를 분리 검증했습니다.
- **성과**: DDQ 성능 **0.684 → 0.711 (+3.9%)**, DINO Swin-L **0.7006**, 팀 내 Transformer 실험 진입 장벽 완화
- **자세히**: [GitHub](https://github.com/dltkdwns0730/pro-cv-objectdetection-cv-02) | [Notion](https://artistic-myrtle-971.notion.site/Trash-Detection-2c928309d08d80e998b3c4273a990586)

### Experiment

<a id="project-experiment-sentiment"></a>
#### Sentiment Analysis
> Experiment | 목표: 네이버 영화 리뷰 4단계 감정 분류 | Metric: Macro F1

- **역할**: 클래스 불균형 대응 전략 수립, TAPT 적용, 출력 레이어 개선, 키워드 기반 가중치 설계
- **문제 발생**: Class 1 비율이 **9.7%**로 매우 낮았고, LLM 증강 데이터 품질 편차와 하이퍼파라미터 탐색 비용이 함께 존재했습니다.
- **문제 정의**: 단순 Under-sampling이나 Grid Search로는 클래스 불균형과 도메인 적응 문제를 동시에 해결하기 어려웠습니다.
- **문제 해결**: Focal Loss와 감정 키워드 가중치를 적용하고, 영화 리뷰 도메인 TAPT를 수행했으며, WandB Sweep 기반 Random Search와 MLP Head 확장을 적용했습니다.
- **성과**: Macro F1 **78.5% → 83.12%**, Class 1 성능 유의미한 개선, 탐색 효율 향상
- **자세히**: [Notion](https://artistic-myrtle-971.notion.site/2f528309d08d8054aa88c91d54cae9f7)

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

모델 성능을 넘어서, 서비스 구조와 운영 효율까지 책임지는 엔지니어를 지향합니다.
