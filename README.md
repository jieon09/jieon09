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

**인식과 제어를 잇는 로봇 비전 개발자** | YOLO 기반 객체 탐지 · 좌표 변환 · Vision-to-Action

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
