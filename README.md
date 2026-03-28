# 이상준 | AI / Backend Engineer

문제를 정의하고, 가설로 검증하고, 구조로 해결하는 AI / Backend Engineer입니다.  
모델 성능 개선에서 출발해 백엔드, 배포, 비용, 운영 효율까지 함께 설계하는 방향으로 성장하고 있습니다.

[Resume](#resume) · [Values](#values) · [Projects](#projects) · [Education](#education)

---

## Resume

### Summary

멀티모달 AI 서비스와 Competition 프로젝트를 통해, 모델링 역량과 서비스 설계 역량을 함께 쌓아왔습니다.  
Competition에서는 `Dice 0.9546`, `mAP 0.711`, `Macro F1 83.12%`를 만들었고, Service에서는 `VLM API 호출 60% 절감`, `GPU 메모리 50% 절감`, `실시간 처리 5초 이내` 성과를 냈습니다.

### Snapshot

| Category | Details |
| --- | --- |
| Target Role | AI Engineer, Backend Engineer, AI / Backend SW Engineer |
| Core Strength | 문제 정의, 실험 설계, 비용 최적화, 서비스화 |
| Tech Focus | Python, FastAPI, Flask, PostgreSQL, Redis, PyTorch, LangGraph, Docker, AWS, GCP |
| Contact | `dltkdwns0730@gmail.com` |
| LinkedIn | `linkedin.com/in/sangjun-lee-3913493a7` |
| GitHub | `github.com/dltkdwns0730` |

### Highlights

- Re:View에서 ORB + pHash 기반 중복 제거로 **VLM API 호출 60% 절감**
- PAZULE에서 FP16 적용으로 **GPU 메모리 50% 절감**, 파주시장상 수상
- Hand Bone Segmentation에서 **Dice 0.9071 → 0.9546**, Private **7위**
- Object Detection에서 **mAP 0.684 → 0.711**
- Sentiment Analysis에서 **Macro F1 78.5% → 83.12%**

### Activities & Awards

- **네이버 부스트캠프 AI Tech 8기** | Computer Vision Track | 2025.09 - 2026.02
- **데이콘 파주 아이디어 혁신 대회** | PAZULE 팀 프로젝트 | **파주시장상** | 2025.12.22
- **Hand Bone Image Segmentation Competition** | Private **7위** / Public **7위**

## Values

| Keyword | Description |
| --- | --- |
| Problem First | 좋은 결과는 좋은 모델 하나보다, 문제를 정확히 정의하고 검증 가능한 가설로 쪼개는 과정에서 나온다고 믿습니다. |
| Data-Centric | 모델을 바꾸기 전에 데이터 분포, 실패 케이스, 평가 기준부터 확인하는 편입니다. |
| Teamwork | Git-flow, PR 리뷰, WandB, Notion 기록 규칙을 맞추고, 트러블슈팅 로그와 실험 인사이트를 팀 자산으로 남깁니다. |
| Growth | 한 프로젝트에서 드러난 한계를 다음 프로젝트의 설계 원칙으로 연결합니다. |
| Ownership | 모델 성능 개선에 그치지 않고, 서비스 구조와 운영 효율까지 함께 책임지는 엔지니어를 지향합니다. |

## Projects

### Index

#### Service

- [Re:View](#project-service-review): 강의 영상을 독립형 노트로 바꾸는 멀티모달 AI 서비스
- [PAZULE](#project-service-pazule): 파주 출판단지 체험형 보물찾기 서비스
- [Live Commerce](#project-service-live-commerce): 실시간 상품 인식 기반 라이브 커머스 서비스

#### Competition

- [Hand Bone Segmentation](#project-competition-hand-bone): Hand Bone X-ray 29개 뼈 분할
- [Object Detection](#project-competition-object-detection): 쓰레기 이미지 객체 검출 및 분류

#### Experiment

- [Sentiment Analysis](#project-experiment-sentiment): 네이버 영화 리뷰 4단계 감정 분류

### Service

<a id="project-service-review"></a>
#### Re:View

| Item | Details |
| --- | --- |
| Category | Service |
| Goal | 강의 영상에서 독립형 강의 노트를 자동 생성하고, 챗봇 튜터까지 연결하는 멀티모달 AI 서비스 구축 |
| Team | 5인 팀 |
| Role | 캡처 파이프라인 최적화, 백엔드 API 및 비동기 처리 구조 설계, 오디오 처리 개선, 아키텍처 개선안 문서화 |
| Stack | FastAPI, LangGraph, Gemini Flash, Clova Speech, OpenCV, Docker, GCP Cloud Run |

- **Problem**: Whisper의 한국어 인식률이 낮았고, 슬라이드 중복 캡처가 비용과 지연시간을 키웠으며, 모놀리스 구조는 확장성 한계가 있었습니다.
- **Definition**: 한국어 강의 환경에서는 STT 정확도와 슬라이드 중복 제어가 곧 품질과 비용 문제로 이어졌고, 파이프라인 구조 역시 서비스화 관점에서 재설계가 필요했습니다.
- **Solution**: Clova Speech 중심의 STT Router Pattern을 설계하고, ORB + pHash 기반 2단계 중복 제거 로직을 구현했으며, 비동기 처리 흐름과 6개 서비스 분산 전환안을 설계했습니다.
- **Result**: Clova WER **6%**, VLM API 호출 **60% 절감**, Summarizer 지연시간 **45s → 17.9s**, Capture F1 **0.77 → 0.97**
- **Links**: [GitHub](https://github.com/dltkdwns0730/Re-View) | [Notion](https://artistic-myrtle-971.notion.site/ReView-2f528309d08d805faa97d032c01a260d) | [Architecture Docs](https://github.com/dltkdwns0730/Re-View/blob/feature/architecture-improvement/docs/architecture-improvement.md)

<a id="project-service-pazule"></a>
#### PAZULE

| Item | Details |
| --- | --- |
| Category | Service |
| Goal | AI 기반 파주 출판단지 랜드마크 보물찾기 게임 개발 |
| Team | 5인 팀 |
| Role | 백엔드 리드, AI 검증 파이프라인 설계, LangGraph 멀티에이전트 구조 설계, 모델 경량화, GPS/EXIF 메타데이터 검증 로직 구현 |
| Stack | Flask, LangGraph, BLIP, CLIP, GPT-4o-mini, Docker, Supabase |

- **Problem**: BLIP, CLIP, GPT-4o-mini 등 여러 AI 모듈이 하나의 사용자 흐름 안에 엮여 있었고, 단일 코드 구조로는 검증 로직과 힌트 생성 흐름을 관리하기 어려웠습니다.
- **Definition**: 사용자 입력 검증, 정답 판별, 힌트 생성, 응답 포맷을 분리하지 않으면 서비스 품질과 개발 생산성이 모두 떨어지는 구조였습니다.
- **Solution**: Security, Tech, Design Agent로 역할을 나눈 LangGraph 구조를 설계했고, BLIP VQA, CLIP 감성 분석, GPT-4o-mini 힌트 생성기를 조합한 듀얼 AI 미션 체계를 구현했습니다.
- **Result**: **파주시장상**, BLIP FP16 적용으로 **GPU 메모리 50% 절감**, CLIP SDPA 적용으로 **추론 속도 37.5% 향상**, GPS + EXIF 검증으로 **부정 사진 95% 차단**
- **Links**: [GitHub](https://github.com/dltkdwns0730/PAZULE_AGENT) | [Notion](https://artistic-myrtle-971.notion.site/2f528309d08d80ffb5f3ec0977fb2854)

<a id="project-service-live-commerce"></a>
#### Live Commerce

| Item | Details |
| --- | --- |
| Category | Service |
| Goal | 실시간 라이브 스트리밍 중 상품 자동 인식 및 구매 링크 제공 |
| Team | 캡스톤 프로젝트 |
| Role | 전체 시스템 설계 및 구현 |
| Stack | AWS IVS, Rekognition, Lambda, DynamoDB, S3, API Gateway |

- **Problem**: 라이브 영상에서 상품을 감지하고 사용자 화면에 반영하기까지의 흐름이 지연되면, 추천 기능 자체가 사용성을 잃는 구조였습니다.
- **Definition**: 실시간성 확보와 운영 단순화를 동시에 만족시키기 위해서는 서버 관리 부담이 적고 이벤트 기반으로 연결되는 구조가 필요했습니다.
- **Solution**: AWS IVS, S3, Lambda, Rekognition, DynamoDB, IVS Metadata를 연결한 Event-Driven Serverless 파이프라인을 설계하고, Confidence 기준과 중복 방지 로직을 추가했습니다.
- **Result**: 전체 처리 **5초 이내**, **100% Serverless** 아키텍처 구현, Confidence **80% → 90%** 조정으로 오탐 최소화
- **Links**: [Notion](https://artistic-myrtle-971.notion.site/2f628309d08d8075bba5eee8ab9cfc7b)

### Competition

<a id="project-competition-hand-bone"></a>
#### Hand Bone Segmentation

| Item | Details |
| --- | --- |
| Category | Competition |
| Goal | Hand Bone X-ray 29개 뼈 Semantic Segmentation |
| Metric | Dice |
| Team | 6인 팀 |
| Role | EDA 기반 문제 정의, 데이터 재설계, 검증 지표 설계, 학습 전략 수립, 후처리 파이프라인 설계 |
| Stack | UNet++, SegFormer, Hausdorff Loss, FP16, Gradient Accumulation, WandB |

- **Problem**: Train은 Open 손 비율이 높고 Test는 Folded 손 비율이 높아 Domain Shift가 컸으며, 2048 해상도 학습 시 OOM과 라벨 품질 문제도 존재했습니다.
- **Definition**: 리더보드 점수만 따라가면 실제 Test 분포를 반영하지 못했고, 손목 overlap과 Folded 데이터 부족을 반영하는 검증 기준이 필요했습니다.
- **Solution**: TVS(Trustworthy Validation Score)를 설계하고, LL → RR 반전과 Carpal Bone crop으로 표본 다양성을 확보했으며, FP16 + Gradient Accumulation과 Cut & Fill 후처리를 적용했습니다.
- **Result**: Dice **0.9071 → 0.9546 (+5.2%p)**, Private **7위**, 경계 밖 픽셀 평균 **15.92% 감소**
- **Links**: [GitHub](https://github.com/dltkdwns0730/pro-cv-semanticsegmentation-cv-02) | [Notion](https://artistic-myrtle-971.notion.site/Hand-Bone-Image-Segmentation-2f528309d08d803482dde529f91f75ed)

<a id="project-competition-object-detection"></a>
#### Object Detection

| Item | Details |
| --- | --- |
| Category | Competition |
| Goal | 쓰레기 이미지 객체 검출 및 분류 |
| Metric | mAP |
| Team | 팀 프로젝트 |
| Role | DDQ 모델 단계적 개선, ViTDet 트러블슈팅 공유, 변인 통제 기반 실험 설계 |
| Stack | DINO Swin-L, DDQ, ViTDet, Pseudo Labeling, MMDetection, WandB |

- **Problem**: Transformer 계열 모델은 V100 환경에서 메모리 제약이 컸고, 단일 기법으로는 성능이 정체되었으며, 증강 기법 역시 모델별 호환성이 달랐습니다.
- **Definition**: 실험 우선순위를 명확히 하지 않으면 개선 효과를 분리하기 어렵고, 메모리 제약을 해결하지 못하면 고성능 모델 실험 자체가 불가능했습니다.
- **Solution**: Batch Size와 Mixed Precision 조합으로 학습을 안정화하고, DDQ에 LSJ와 Pseudo Labeling을 단계적으로 적용했으며, TTA와 증강 기법의 순수 효과를 분리 검증했습니다.
- **Result**: DDQ 성능 **0.684 → 0.711 (+3.9%)**, DINO Swin-L **0.7006**, 팀 내 Transformer 실험 진입 장벽 완화
- **Links**: [GitHub](https://github.com/dltkdwns0730/pro-cv-objectdetection-cv-02) | [Notion](https://artistic-myrtle-971.notion.site/Trash-Detection-2c928309d08d80e998b3c4273a990586)

### Experiment

<a id="project-experiment-sentiment"></a>
#### Sentiment Analysis

| Item | Details |
| --- | --- |
| Category | Experiment |
| Goal | 네이버 영화 리뷰 4단계 감정 분류 |
| Metric | Macro F1 |
| Team | 개인 실험 중심 |
| Role | 클래스 불균형 대응 전략 수립, TAPT 적용, 출력 레이어 개선, 키워드 기반 가중치 설계 |
| Stack | BERT, RoBERTa, KoELECTRA, TAPT, Focal Loss, WandB Sweep |

- **Problem**: Class 1 비율이 **9.7%**로 매우 낮았고, LLM 증강 데이터 품질 편차와 하이퍼파라미터 탐색 비용이 함께 존재했습니다.
- **Definition**: 단순 Under-sampling이나 Grid Search로는 클래스 불균형과 도메인 적응 문제를 동시에 해결하기 어려웠습니다.
- **Solution**: Focal Loss와 감정 키워드 가중치를 적용하고, 영화 리뷰 도메인 TAPT를 수행했으며, WandB Sweep 기반 Random Search와 MLP Head 확장을 적용했습니다.
- **Result**: Macro F1 **78.5% → 83.12%**, Class 1 성능 유의미한 개선, 탐색 효율 향상
- **Links**: [Notion](https://artistic-myrtle-971.notion.site/2f528309d08d8054aa88c91d54cae9f7)

## Education

### Academic Background

- **네이버 부스트캠프 AI Tech 8기** | Computer Vision Track | 2025.09 - 2026.02
- **한림대학교 소프트웨어학부 빅데이터전공** | GPA 3.59 / 4.50 | 2021.03 - 2025.02

### Certifications

- 정보처리기사
- 빅데이터분석기사
- ADsP

### Language

- TOEIC 920
- OPIc IH

---

문제의 본질을 먼저 찾고, 팀과 함께 검증 가능한 결과를 만드는 엔지니어를 지향합니다.
