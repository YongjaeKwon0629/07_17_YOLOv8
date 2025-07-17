# 🎯 YOLOv8 & YOLOv11 기반 영상 객체 탐지 실험 및 실습 

---  
  
본 프로젝트는 **Ultralytics YOLOv8** 및 차세대 모델인 **YOLOv11**을 활용한 영상 기반 객체 탐지 실험입니다.  
직접 촬영한 주행 영상 및 YouTube 영상을 대상으로 실시간 객체 탐지를 수행하고, 결과를 시각화합니다.

---

## 🧪 실험 개요

| 미션 | 설명 |
|------|------|
| 🚗 미션 1 | 직접 업로드한 주행 영상 (19초 분량)에 YOLOv8을 적용하여 객체 탐지 수행 |
| 🔗 미션 2 | YouTube 링크를 통해 동일 영상을 다운로드하고 YOLOv8 추론 수행 |
| 🚀 미션 3 | YOLOv11의 최신 아키텍처 분석 및 향후 실험 준비 |

---

## 📍 YOLOv8 추론 결과

### ✅ 미션 1: 직접 업로드한 영상 처리

-  업로드한 영상은 `.avi` 형식으로 저장되며, 이름은 원본과 동일하게 유지됩니다.
-  결과 파일 경로 예시:
**/content/runs/detect/predict/KakaoTalk_20250707_100128756 (3).avi**


---

### ✅ 미션 2: YouTube 영상 다운로드 후 처리

- `yt-dlp`를 통해 영상 다운로드 후 `temp_video.avi`로 저장
- 동일한 YOLOv8 추론 과정을 거쳐 `.avi` 형식 결과 영상 생성
- 다운로드 오류 발생 시 Colab 좌측 파일 메뉴에서 직접 다운로드 가능

| 결과 영상 1 | 결과 영상 2 |
|-------------|-------------|
| <img width="500" src="https://github.com/user-attachments/assets/e1de854d-7df0-4455-9e49-37aba7b0d201" /> | <img width="500" src="https://github.com/user-attachments/assets/29ebfc31-da2c-4be6-b8dc-342491c644e8" /> |

---

## 🔍 YOLOv11: 차세대 모델 탐색

📖 [YOLOv11 공식 문서 (한글)](https://docs.ultralytics.com/ko/models/yolo11/)

YOLOv11은 YOLOv8 대비 **정확도**, **속도**, **모델 효율성**이 모두 향상된 최신 객체 탐지 모델입니다.  
YOLOv8의 구조를 기반으로 하되, **연산량 감소**와 **모바일 환경 최적화**를 고려하여 설계되었습니다.

### ⚙️ YOLOv8 vs YOLOv11 아키텍처 비교

| 구성 요소 | YOLOv8 | YOLOv11 |
|-----------|--------|---------|
| 백본(Backbone) | ELAN-CSP | RepNCSPELAN4C |
| Neck 구조 | PANet, FPN | CBLinearNeck |
| Head 구조 | YOLOHead (Conv) | DConvHead (Depthwise Conv) |
| 활성화 함수 | SiLU | SiLU, Swish (선택형) |

---

### 🧠 주요 구조 설명

- **RepNCSPELAN4C**: 향상된 표현력과 경량화된 백본 구조
- **CBLinearNeck**: 기존 FPN보다 간결하고 빠른 성능 제공
- **DConvHead**: 경량화된 Detection Head로 Edge 디바이스 최적화
- **활성화 함수 선택 가능**: SiLU 외에도 Swish 등 다양한 함수 지원

<img width="800" src="https://github.com/user-attachments/assets/1adbd9f7-c88c-47ce-b858-29e03341805c" />

---

## 🧬 YOLOv11 모델 종류

| 모델명 | 특징 |
|--------|------|
| `yolov11n.pt` | Nano: 가장 가볍고 빠름 |
| `yolov11s.pt` | Small: 기본형 |
| `yolov11m.pt` | Medium: 균형형 |
| `yolov11l.pt` | Large: 고정밀 |
| `yolov11x.pt` | X-Large: 최고 정밀도, 연산량 많음 |

> ⚠️ YOLOv11은 YOLOv8과 API 호환되지만, YOLOv5 이하 버전과는 호환되지 않습니다.

---

## 📘 실습 노트북

- 🧪 YOLOv8 실습 코드 보기  
  👉 [Colab에서 실행하기](#[https://colab.research.google.com/github/your-username/your-repo/blob/main/0717_YOLOv8_video.ipynb](https://colab.research.google.com/drive/1YkdD2cntW8IUDBbRL9MVYLTPB7ygXeiS#scrollTo=XXzTio84GdOx))

---

## 📁 참고 자료

- 📘 Colab 실습 파일: [`0717_YOLOv8_video.ipynb`](0717_YOLOv8_video.ipynb)
- 📚 YOLOv11 문서 (한글): [Ultralytics YOLOv11](https://docs.ultralytics.com/ko/models/yolo11/)
- 🧩 모델 저장 경로: `runs/detect/predict/`

---

## 🗂 향후 과제

- [ ] YOLOv11 설치 및 적용 실험 진행
- [ ] YOLOv8 vs YOLOv11 성능 비교 (FPS, 정확도, 연산량)
- [ ] YouTube 영상 인증(CAPTCHA) 우회 자동화
- [ ] `.avi → .mp4` 포맷 자동 변환 기능 추가

---

> ✍️ *이 실험은 컴퓨터 비전 및 자율주행 인식 모듈 연구의 일환으로 수행되었습니다.*
