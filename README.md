# 멀티모달 AI Engineer

> 데이터로 문제를 정의하고 수치로 개선하며, 배운 것을 활용해 현실 문제를 해결하는 가치를 만듭니다.

---

## 📬 Contact

| | |
|---|---|
| 이름 | 이상준 |
| 연락처 | 010-3632-3972 |
| 이메일 | [dltkdwns0730@gmail.com](mailto:dltkdwns0730@gmail.com) |

---

## 🎓 Education

- **네이버 커넥트재단 — 부스트캠프 AI Tech 8기 CV 트랙** `2025.09 – 2026.02 · 수료`
- **한림대학교 — 소프트웨어학부 빅데이터전공 (복수전공: 콘텐츠IT)** `2021.03 – 2025.02 · 학사 졸업`

---

## 🔗 Channel

- GitHub: [dltkdwns0730](http://github.com/dltkdwns0730)
- Notion: [포트폴리오](https://www.notion.so/33028309d08d81e8b2fbf2cddaf1773a)
- LinkedIn: [linkedin](https://www.linkedin.com/in/sangjun-lee-3913493a7/?skipRedirect=true)

---

## 🏆 Certificate & Award

| 항목 | 취득일 |
|---|---|
| [데이콘] 파주시장상 | 2025.12 |
| 정보처리기사 | 2024.09 |
| 빅데이터분석기사 | 2025.07 |
| ADsP | 2024.09 |
| TOEIC 920점 | 2024.08 |
| OPIc IH | 2026.03 |

---

## 💡 Introduce

멀티모달 AI 시스템을 실제 서비스에 적용하며, 데이터로 문제를 정의하고 성능·비용·지연시간을 함께 개선해 왔습니다.

- 강의 내용을 다시 정리하는 데 시간이 많이 든다는 불편함에서 출발해 STT·VLM 기반 강의 노트 생성 서비스와 챗봇 튜터를 구현했고, LangGraph 기반 Agent 구조, Vector DB 기반 검색, LLM-as-Judge 품질 검증, 비동기 처리 파이프라인을 적용해 노트 생성 품질과 처리 병목을 개선했습니다.
- BLIP 관련 학습을 바탕으로 파주 출판단지 활성화를 위한 멀티모달 AI 서비스를 기획·개발했고, 랜드마크 방문 인증과 소비 쿠폰 제공 기능을 구현해 최우수상(29팀 중 2위, 파주시장상)을 수상했습니다.
- 라이브 방송 중 상품 정보를 확인하려면 판매자 설명을 기다리거나 별도로 검색해야 하는 불편을 줄이기 위해, 화면에 등장한 상품을 자동 인식해 실시간 상품 정보와 구매 링크를 제공하는 서비스를 구현했습니다.
- Object Detection과 Hand Bone Segmentation 프로젝트에서는 OOM, 소형 객체 성능 저하, 데이터 분포 차이를 분석하고, 실험 방향과 검증 전략을 조정해 모델 성능을 개선했습니다.

---

## 🚀 Projects

### [서비스] 강의 노트 자동 생성

> STT와 VLM을 결합해 강의 영상의 텍스트와 슬라이드를 통합 분석하고, 강의 노트와 챗봇 튜터를 제공하는 서비스.

`2025.11.28 ~ 2026.02.11` · 5인 팀 · FastAPI · LangGraph · Gemini3-flash · Qwen3-VL · PostgreSQL · Docker · GCP Cloud Run

**역할**
- 캡처 로직 개선, 전처리 파이프라인 최적화, 프롬프트 및 출력 구조 표준화.

**핵심 기여**
- 마우스 커서, 화면 전환, 미세 움직임 때문에 동일 슬라이드가 반복 캡처되는 문제를 확인하고, 안정된 프레임만 저장하도록 캡처 시점을 조정한 뒤 pHash+ORB 기반 중복 제거와 구간 병합 로직을 적용 → **VLM 호출 비용 약 50% 절감**, 슬라이드 타임라인 정합성 확보.
- STT와 슬라이드 캡처가 순차 실행되며 전처리 시간이 길어지는 병목을 분석하고, 두 단계를 병렬 처리하는 구조로 파이프라인 최적화 → **30분 강의 영상 기준 전처리 시간 3분 32.8초 → 1분 57.1초 (-44.9%)**.
- VLM과 Judge 단계의 출력 형식을 표준화하고 Judge 프롬프트를 구조화·경량화해 노트 생성과 품질 검증 안정성 확보 → **Judge 통과율 80% → 95%**, 평균 Judge 토큰 수 16,370 → 14,734 (-10.0%).

**Links** · [Notion](https://www.notion.so/ReView-2f528309d08d805faa97d032c01a260d) · [GitHub](https://github.com/seolbbb/Re-View)

---

### [경진대회] 파주 출판단지 활성화 AI 서비스

> 파주 출판단지 관광 활성화를 위해, 현장에서 촬영한 사진으로 장소와 분위기를 함께 검증하고 실패 시 LLM 힌트를 제공하는 이미지 미션형 AI 서비스.

`2025.10.13 ~ 2025.11.17` · 5인 팀 · **파주시장상(29팀 중 2위)** · Flask · LangGraph · BLIP · CLIP · GPT-4o-mini

**역할**
- 백엔드 리드, 멀티모달 추론 API 설계, 메타데이터 검증 로직 구현, 모델 서빙 최적화, 수상 이후 LangGraph 기반 멀티에이전트 구조 개선.

**핵심 기여**
- GPS·촬영 시각 메타데이터 검증을 적용해 현장 촬영 사진만 처리하도록 제한 → **부정 사진 업로드 차단률 약 95%** 확보.
- BLIP·CLIP 동시 서빙으로 GPU 메모리 부족과 응답 지연이 발생하는 문제를 분석하고, 모델 경량화와 처리 구조 개선으로 **GPU 메모리 사용량 50% 절감**, 전체 처리 시간 **15초 → 10초 (-33%)**.
- 수상 이후: 입력 검증, AI 분석, 응답 포맷팅이 하나의 흐름에 묶여 있던 구조를 LangGraph 기반 역할별 에이전트로 분리해, 보안 검증·추론 로직·응답 형식을 단계별로 독립 수정할 수 있도록 개선.

**Links** · [Notion](https://www.notion.so/AI-2f528309d08d80ffb5f3ec0977fb2854) · [GitHub(Agent버전)](https://github.com/dltkdwns0730/PAZULE_AGENT)

---

### [서비스] 실시간 상품 인식 라이브 커머스

> 라이브 스트리밍 화면의 상품을 자동 인식해 실시간 상품 정보와 구매 링크를 제공하는 서비스.

`2024.09 ~ 2024.12` · 개인 · 한림대학교 · AWS IVS · Rekognition · Lambda · DynamoDB · S3

**역할**
- 이벤트 기반 파이프라인 설계 및 구현, 상품 인식 로직 개선, 실시간 메타데이터 연동.

**핵심 기여**
- 실시간 상품 노출 구조 부재 문제를 확인하고, IVS·S3·Lambda·Rekognition·DynamoDB를 연결한 이벤트 기반 파이프라인을 설계해 **프레임 추출부터 상품 정보 노출까지 5초 이내** 처리.
- Rekognition의 유사 객체 오탐 문제를 확인하고, 신뢰도 조정으로 잘못된 상품 정보 노출 감소.
- 동일 상품의 반복 노출 문제를 확인하고, 메타데이터 중복 제거 로직 적용.

---

### [컴피티션] 손뼈 X-ray Semantic Segmentation

> 손뼈 X-ray 이미지에서 29개 뼈를 픽셀 단위로 분할하는 semantic segmentation 프로젝트.

`2025.12.17 ~ 2026.01.06` · 6인 팀 · 부스트캠프 AI Tech 8기 · PyTorch · UNet++ · SegFormer · UPerNet

**역할**
- EDA 기반 문제 정의, 손목 crop 기반 UNet++ 실험, 검증 지표 설계.

**핵심 기여**
- Open 중심 학습 분포와 Folded 중심 테스트 분포 차이로 validation 점수가 실제 test 성능을 잘 예측하지 못하는 문제를 확인하고, ID 기반 GroupKFold와 Open/Folded 가중 검증 지표를 적용해 모델 선택 기준을 실제 평가 분포에 맞게 조정.
- 손등 구간에 overlap이 집중되어 분할 성능 병목이 발생하는 문제를 확인하고, 손등 crop 기반 특화 모델을 별도로 학습해 전체 모델과 결합함으로써 **손목 Dice 0.9071 → 0.9546** 개선.

**Links** · [Notion](https://www.notion.so/X-ray-Segmentation-2f528309d08d803482dde529f91f75ed) · [GitHub](https://github.com/boostcampaitech8/pro-cv-semanticsegmentation-cv-02)

---

### [컴피티션] 재활용 품목 탐지 Object Detection

> 재활용 쓰레기 이미지에서 10개 클래스를 탐지하는 object detection 프로젝트.

`2025.12.04 ~ 2025.12.11` · 6인 팀 · 부스트캠프 AI Tech 8기 · PyTorch · MMDetection · DINO · DDQ · CO-DINO · V100 32GB

**역할**
- Transformer 기반 탐지 모델 실험, 소형 객체 성능 개선.

**핵심 기여**
- W&B 로그 분석으로 소형 객체 탐지 성능 저하를 확인하고, DDQ에 LSJ(객체 크기 변화 증강)와 pseudo labeling(신뢰도 높은 예측 재활용)을 적용해 **mAP 0.684 → 0.7112**, **mAP_small 0.058 → 0.118** 향상.
- 대형 Transformer 탐지 모델 학습 시 메모리 제약 문제를 확인하고, AMP(메모리 효율 개선)를 적용해 실험 안정성 확보.

**Links** · [Notion](https://www.notion.so/Object-Detection-2c928309d08d80e998b3c4273a990586) · [GitHub](https://github.com/boostcampaitech8/pro-cv-objectdetection-cv-02)

---

## 🛠 Skill

### AI / ML
- **CV:** Semantic Segmentation, Object Detection
- **NLP:** BERT/RoBERTa/KoELECTRA 파인튜닝, LLM API 활용
- **VLM API:** BLIP, CLIP, Qwen
- **Framework:** PyTorch, Hugging Face, MMDetection, SMP
- **모델 최적화:** FP16, AMP, Gradient Checkpointing, Pseudo Labeling, LSJ, pHash+ORB

### 백엔드 / 인프라
- **Language:** Python
- **Web:** FastAPI, Flask
- **DB:** PostgreSQL, DynamoDB
- **Cloud:** GCP Cloud Run, AWS (IVS, Rekognition, Lambda, S3)
- **DevOps:** Docker, GitHub Actions (CI/CD)

### 실험 / 협업
- WandB, Git/GitHub, Slack, Notion
