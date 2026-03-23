# 이상준 | Backend Developer

AI 서비스의 백엔드 파이프라인을 설계하고, 비용·지연·품질을 구조적으로 최적화하는 개발자입니다.

## Tech Stack

**Backend** · Python, FastAPI, Flask, PostgreSQL, Supabase  
**AI/ML** · LangGraph, OpenCV, PyTorch, CLIP, BLIP, VLM/LLM 파이프라인  
**Cloud** · AWS (Lambda, S3, DynamoDB, IVS, Rekognition)  
**Tools** · Docker, Git, Slack, Notion

## Projects

### 🎬 Re:View — 멀티모달 AI 강의 노트 자동 생성 서비스
> FastAPI + LangGraph + PostgreSQL 기반 생성형 AI 서비스

STT(음성)와 VLM(화면)을 결합하여 강의 노트를 자동 생성하고, LangGraph 기반 챗봇으로 질의응답을 제공하는 서비스입니다.

**담당:** 백엔드 API 서버 구축, DB 스키마 설계, 캡처 파이프라인 설계 및 최적화

| KPI | Before | After | 개선 |
|-----|--------|-------|------|
| Summarizer 입력 토큰 | 9,065 | 5,396 | **-40.5%** |
| Summarizer 지연시간 | 45s | 17.9s | **-60.2%** |
| 중복 캡처 수 | 11 | 5 | **-55%** |
| VLM API 호출 수 | 6 | 3 | **-50%** |
| 캡처 F1-score | 0.77 | 0.97 | **+0.20** |

🔗 **[프로젝트 상세 (Notion)](https://artistic-myrtle-971.notion.site/ReView-2f528309d08d805faa97d032c01a260d)** · **[GitHub Repo](https://github.com/seolbbb/Re-View)**

---

### 🧩 PAZULE — AI 기반 체험형 지역 관광 플랫폼
> CLIP/BLIP + LangGraph 멀티에이전트 · **파주시장상 수상 (최우수상)**

파주 출판단지 관광 활성화를 위한 AI 보물찾기 서비스입니다. 사용자가 촬영한 사진을 BLIP(장소 인식)과 CLIP(감성 분석)으로 검증하고, 실패 시 GPT-4o-mini가 힌트를 생성합니다.

**담당:** 백엔드 리드 (API 서버, AI 파이프라인, 모델 경량화, GPS 검증)

- FP16 적용으로 GPU 메모리 **50% 절감**
- Scaled Dot Product Attention으로 추론 속도 **37.5% 향상**
- GPS/시간 메타데이터 검증으로 부정 행위 **95% 차단**

🔗 **[프로젝트 상세 (Notion)](https://artistic-myrtle-971.notion.site/2f528309d08d80ffb5f3ec0977fb2854)** · **[GitHub Repo](https://github.com/dltkdwns0730/PAZULE)**

---

### 🛒 상호작용형 라이브 커머스 — 실시간 AI 객체 탐지
> AWS 서버리스 아키텍처 (Lambda + Rekognition + DynamoDB + IVS)

라이브 스트리밍 중 화면에 등장하는 상품을 AI로 자동 인식하여, 실시간으로 상품 정보와 구매 링크를 제공하는 서비스입니다.

**담당:** 전체 시스템 설계 및 구현 (개인 프로젝트)

- 이벤트 기반 서버리스 파이프라인으로 전체 처리 **5초 이내** 달성
- Confidence 임계값 조정(80%→90%)으로 유사 객체 오탐 해결

---

## Competition

| 프로젝트 | 성과 | 핵심 기여 |
|---------|------|---------|
| 재활용 품목 Object Detection | **13팀 중 2위** (mAP 0.6986) | DINO/DDQ Swin-L 파이프라인, Pseudo Labeling |
| Hand Bone Segmentation | Dice **0.9546** | 손목 특화 모델 설계, GroupKFold 검증 구축 |

## Education & Certification

- **네이버 부스트캠프 AI Tech 8기** (CV) · 2025.09 ~ 2026.02
- **한림대학교** 빅데이터학과 · 2021.03 ~ 2025.02
- 정보처리기사 · 빅데이터분석기사 · TOEIC 920
