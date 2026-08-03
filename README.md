# 안녕하세요! 박지언입니다 👋

## 🎥 프로젝트 관련 영상 링크 모음

-그림 그리GO, LEGO 만들GO (M0609)

https://youtu.be/gXeqeLA6e1I

-박물관이 살아있다 (TurtleBot4 유물 도난 감지·추적)

https://youtu.be/aF0MTN9tACY

-VR 노인 치매 예방 솔루션: 기억의 정원

https://youtu.be/zyJ4J2y4ZPU

-ROBOCASE

https://youtu.be/sebBmTJKYpg

-딸기 SimGO, 딸기Farm

https://youtu.be/T1Tjz3cdnXY

---

## 🤖 About Me

**로봇 Vision 개발자** | YOLO 기반 객체 탐지 · 좌표 변환 · Vision-to-Action

Doosan Robotics ROKEY 부트캠프에서 ROS2, YOLO, OpenCV, Isaac Sim 등을 활용해 로봇 비전 프로젝트를 진행해 왔습니다.
저는 카메라가 무엇을 인식했는지보다, **그 인식 결과가 로봇의 실제 좌표와 동작으로 얼마나 정확하고 안정적으로 이어지는지**를 설계하는 데 관심이 많습니다.

주요 관심 분야는 **Robot Vision / Object Detection, Depth Estimation · 3D Perception, Vision-based Navigation, Multi-Robot Collaboration**입니다.

- 📧 **Email:** pigrachel70@gmail.com
- 💻 **GitHub:** github.com/jieon09
- 🎯 **Main Focus:** YOLO 기반 비전 모델 개발·성능 검증, RGB-D 좌표 변환, 협동로봇 제어 연동, 클라우드 기반 서빙 파이프라인
- 🧭 **Development Style:** 여러 학습 실험을 정량 지표(mAP, F1 등)로 비교·검증하고, 문제 원인을 STAR 구조로 정리해 README/PPT까지 문서화하는 방식으로 프로젝트를 정리합니다.

---

## 🛠 Tech Stack

**Core Languages**
Python · C++ · C

**Robotics & Simulation**
ROS2 · Nav2 · Gazebo · RViz · Isaac Sim · Doosan Robotics (M0609)

**Vision & AI**
YOLO(v8) · OpenCV · TensorFlow

**Backend / Database / Cloud**
FastAPI · Flask · PostgreSQL · SQLite · AWS (EC2 · S3 · RDS)

**Tools**
Git · Linux

---

## 🤖 Focus Areas

**Vision AI & Object Detection**
- YOLOv8 기반 객체 탐지를 유물 도난 감지, 레고 색상 분류, 사용자 사진 분석 등 서로 다른 도메인에 반복 적용
- 학습 실험(배치·에폭·YOLO 버전 조합)을 mAP50, mAP50-95, F1-Score로 비교해 단일 최고 수치가 아닌 추론 안정성 기준으로 최종 모델 선정

**Vision-to-Action (좌표 변환 · 로봇 제어)**
- 3점 캘리브레이션으로 비전 인식 좌표(row/col)를 로봇 base 좌표계로 변환, 협동로봇 조립 동작에 연계
- RGB-D depth 처리(9×9 patch median 필터링)와 핀홀 카메라 역투영으로 픽셀 좌표를 3차원 실제 좌표로 변환, TF 변환을 통해 map 좌표로 연결

**Multi-Robot Collaboration**
- 두 대의 로봇이 동시에 같은 대상을 추적하지 않도록 상호 배제 토픽 설계
- 순찰 로봇과 운반 로봇 간 호출 신호 기반 협업 구조 설계

**클라우드 기반 AI 서비스 파이프라인**
- FastAPI 기반 REST API로 모델 서빙 및 백엔드 연동 구현
- AWS EC2에 서버 배포, S3에 이미지 저장·URL 생성, RDS 연동을 통한 클라이언트 서빙 파이프라인 구축

---

## 📂 Featured Projects

### 1️⃣ 박물관이 살아있다 — YOLOv8 기반 실시간 객체 탐지 및 TurtleBot4 추적 시스템

**Role:** 기획 / 시스템 설계 / 웹 UI 구현 / DB 설계
**Tech Stack:** ROS2, YOLOv8, OAK-D, Flask, SQLite, Nav2, Web UI

**Main Contribution:**
- YOLOv8 모델을 8회 재학습(Train1~8)하며 mAP50, mAP50-95, F1-Score를 비교, 최고 수치가 아닌 mAP≥0.99를 가장 오래 유지한 모델(Train5)을 최종 선정
- OAK-D 카메라의 bbox 중심 픽셀과 depth 패치 median 필터링(9×9, 0.2~5.0m)으로 3차원 좌표 계산, 핀홀 역투영 후 TF 변환으로 map 좌표 산출
- robot2·robot8 두 대가 동시에 같은 도둑을 추적하지 않도록 catch_thief_2/8 토픽으로 상호 배제 로직 구현, pose_hold_time(2초)으로 좌표 재발행 안정화
- 웹캠이 이미 탐지하는 유물까지 로봇이 중복 탐지하던 비효율을 발견해, 사각지대 순찰 중심으로 배치를 개선하자고 직접 제안

---

### 2️⃣ 그림 그리GO, LEGO 만들GO (M0609) — 비전 인식 기반 레고 자동 조립 로봇

**Role:** 로봇 위치 제어 및 비전 인식
**Tech Stack:** ROS2, Python, YOLO, OpenCV, Flask, PostgreSQL, GSTT

**Main Contribution:**
- 3점 캘리브레이션(보드 좌상·좌하·우하) 기반으로 row/col 셀 인덱스를 robot base 좌표로 변환하는 로직 구현
- YOLO 기반 색상 분류로 블록 종류 인식, 순응제어로 압입 시 접촉력을 흡수해 로봇팔 긴급정지 없이 안정적 조립 달성
- 특정 컬럼(14열) 이상에서 기구적 오차가 누적되는 문제를, 전체 좌표계 재보정 없이 해당 구간에만 조건부 XY 보정값을 적용해 국소적으로 해결
- STT 연동 긴급 정지·재개 제어 로직 개발, 음성 명령 기반 실시간 안전 제어 인터페이스 구현

---

### 3️⃣ VR 노인 치매 예방 솔루션: 기억의 정원

**Role:** 기획 / 시스템 설계 / K-TMT-e · YOLOv8 · FastAPI · EC2·S3·RDS · STT/TTS 구현
**Tech Stack:** AWS EC2, AWS S3, AWS RDS, FastAPI, Unity

**Main Contribution:**
- 사용자 사진 업로드 → YOLOv8 오브젝트 추출(70% 이상 정확도만 선별) → AWS S3 저장 → RDS에 URL 기록 → Unity 클라이언트 연동으로 이어지는 파이프라인을 FastAPI 기반으로 직접 구축
- K-TMT-e 기반 인지 기능 평가 로직 설계, STT/TTS로 NPC와의 음성 상호작용 구현
- 광주 남구치매안심센터에서 60~80대 어르신 대상 실사용자 평가 진행 중 조작 어려움·어지러움 문제 발견 → 화면을 고정 뷰로 바꾸고 조작을 트리거 하나로 단순화해 개선, 재평가에서 "어지럽지 않고 쉽다"는 긍정 평가와 완주율·몰입도 향상 확인

---

### 4️⃣ ROBOCASE — 웹 도안 기반 폰케이스 자동 제작 협동로봇

**Role:** 기획 / 시스템 설계 / 웹 UI 구현 / DB 설계
**Tech Stack:** ROS2, Python, OpenCV, Flask, SQLite, Web UI

**Main Contribution:**
- Phone App(Canvas 도안) → Flask Server(SQLite 주문 저장) → Stroke JSON(OpenCV) → Pixel→mm 좌표 변환 → M0609 MoveLine으로 이어지는 end-to-end 자동화 파이프라인 설계
- Stroke JSON이 있으면 원본 좌표를 우선 사용하고, 없을 경우 OpenCV HSV/Contour/Boundary Centerline으로 fallback path 생성, Catmull-Rom·resampling·path connect로 로봇 경로 안정화
- 로봇팔이 설정값보다 높은 위치로 치솟는 문제를, 코드상 초기 설정뿐 아니라 티칭펜던트의 로봇 무게·Gripper 설정까지 함께 맞춰야 한다는 것을 파악해 해결
- 관리자 웹페이지 제작, M0609 긴급정지 알람, DB 설계 주도

---

### 5️⃣ 딸기 SimGO, 딸기Farm — Isaac Sim 기반 Smart Farm 협업 로봇

**Role:** 기획 / 시스템 설계 / 사족보행 로봇 이동
**Tech Stack:** Isaac Sim, ROS2, Python, Rviz

**Main Contribution:**
- Occupancy Map 생성, Nav2 Goal Pose 기반으로 Spot(사족보행 로봇)이 호출 신호(/call_quadruped) 수신 시 목표 화분 위치로 이동하도록 구현
- Spot policy가 ROS2 topic을 직접 받지 않는 문제를, cmd_vel/상태를 UDP로 주고받는 양방향 bridge를 직접 구현해 해결 — ROS2·Nav2·Isaac Sim 간 연동의 한계를 보완하는 경험
- 바구니 적재량 기준 자동 창고 왕복으로 무인 운반 사이클 구현

---

## 🧾 Project Summary

| Project | Main Role | Core Keywords |
|---|---|---|
| 박물관이 살아있다 | Vision AI / Multi-Robot Tracking | YOLOv8, Depth 좌표 변환, TF, 상호 배제 |
| 그림 그리GO, LEGO 만들GO | 비전 인식 / 로봇 좌표 제어 | 3점 캘리브레이션, YOLO 색상 분류, 순응제어 |
| 기억의 정원 | Team Lead / Cloud Vision Pipeline | YOLOv8, FastAPI, AWS EC2·S3·RDS, Unity |
| ROBOCASE | Team Lead / Robot Process | M0609, OpenCV, Flask, MoveLine |
| 딸기 SimGO | 시스템 설계 / 사족보행 로봇 이동 | Isaac Sim, Nav2, UDP Bridge |

---

## 📫 Contact

GitHub: https://github.com/jieon09
Email: pigrachel70@gmail.com
