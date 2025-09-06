## 이조합 : RescueBot 🤖

**"솔루션 다운 때문에 다시 출근하지 말자! 우리의 워라밸 구조자 RescueBot"**

Amazon Q Developer Hackathon으로 구현한 지능형 인프라 자동 복구 시스템입니다.

## 어플리케이션 개요

RescueBot은 CloudWatch 알람을 실시간으로 모니터링하고, AI 분석을 통해 자동으로 시스템 장애를 복구하는 지능형 운영 자동화 솔루션입니다. 특히 MySQL 연결 오류와 같은 일반적인 장애 상황에서 SaltStack을 통해 자동으로 서비스를 재시작하여 운영자의 수동 개입 없이 시스템을 정상화합니다.

### 핵심 가치
- 🌙 **야간/주말 긴급 출근 방지**: 자동 복구로 워라밸 보장
- 🚀 **신속한 장애 대응**: 평균 복구 시간 90% 단축
- 🧠 **AI 기반 분석**: Amazon Bedrock Claude를 활용한 지능형 장애 분석
- 📱 **실시간 알림**: Slack을 통한 즉시 상황 공유

## 주요 기능

**<자동 복구>**
<img width="1150" height="553" alt="Image" src="https://github.com/user-attachments/assets/2804ec71-5eeb-4936-ba57-7a7fcdf3e4e5" />
**<수동 복구>**

<img width="474" height="497" alt="Image" src="https://github.com/user-attachments/assets/41bb335a-2e69-4215-ae85-986061e4c486" />


### 1. 실시간 모니터링 및 자동 복구
- CloudWatch 알람 실시간 수집
- MySQL connection error 자동 감지
- SaltStack을 통한 자동 서비스 재시작
- FQDN 기반 정확한 타겟 서버 식별

### 2. AI 기반 장애 분석
- Amazon Bedrock ClaudeSonnet 모델 활용
- 근본 원인 분석 (Root Cause Analysis)
- 권장 조치 사항 제시
- 예방 조치 가이드 제공

### 3. 통합 알림 시스템
- Slack Webhook을 통한 실시간 알림
- 장애 발생부터 복구까지 전 과정 추적
- AI 분석 결과 자동 공유
- 처리 시간 및 성공/실패 상태 리포팅

### 4. 배치 처리 및 스케줄링
- 신규 알람 이벤트 자동 처리
- 단일/배치 레코드 처리 지원
- APScheduler 기반 주기적 모니터링
- 처리 상태 추적 및 관리

### 5. RESTful API 및 Swagger UI
- 완전한 CRUD 기능 제공
- Swagger UI를 통한 API 문서화
- 테스트 데이터 삽입 기능
- 실시간 시스템 상태 모니터링

## 시스템 아키텍처

## 동영상 데모
**수동 작업 실행**

![Image](https://github.com/user-attachments/assets/7f2f61ad-f9a0-407e-a604-3b9e513918da)


**자동 작업 실행**
![Image](https://github.com/user-attachments/assets/a5942d53-8fa7-4b2d-9cdc-3adb38ca34d0)


### 주요 데모 시나리오
1. MySQL 연결 오류 발생 시뮬레이션
2. RescueBot 자동 감지 및 분석
3. SaltStack을 통한 자동 서비스 재시작
4. Slack 알림 및 AI 분석 결과 공유
5. 전체 복구 프로세스 완료

## 리소스 배포하기

### Docker를 이용한 로컬 배포

```bash
# 1. 저장소 클론
git clone https://github.com/your-repo/team14-aws-hackathon.git
cd team14-aws-hackathon/1.code

# 2. 환경변수 설정
cp .env.example .env
# .env 파일에서 실제 값으로 수정

# 3. Docker Compose로 배포
docker-compose up -d --build

# 4. 서비스 확인
curl http://localhost:3000/health
```

### AWS 클라우드 배포 아키텍처
<img width="762" height="791" alt="image" src="https://github.com/user-attachments/assets/0c2aa6df-c6ac-48d9-a97f-ac17c7958e20" />

### 리소스 정리

```bash

# AWS 리소스 정리
cloudformation 에서 제거
```

## 프로젝트 기대 효과 및 예상 사용 사례

### 기대 효과

1. **운영 효율성 향상**
   - 평균 장애 복구 시간 90% 단축
   - 야간/주말 긴급 출근 80% 감소
   - 운영 인력 업무 부담 50% 경감

2. **비용 절감**
   - 장애로 인한 서비스 다운타임 최소화
   - 운영 인력 야근/특근 비용 절약
   - 고객 이탈 방지를 통한 매출 보호

3. **서비스 안정성 강화**
   - 99.9% 이상의 서비스 가용성 달성
   - 장애 대응 표준화 및 자동화
   - 인적 오류로 인한 2차 장애 방지

### 예상 사용 사례

1. **E-commerce 플랫폼**
   - 결제 시스템 DB 연결 오류 자동 복구
   - 주문 처리 서비스 장애 시 즉시 대응

2. **게임 서비스**
   - 게임 서버 다운 시 자동 재시작


### 확장 가능성
- **Slat Command Flow 기능 추가**: 원하는 작업 플로우 / 이벤트 조건 기능 추가
- **다양한 장애 유형 지원**: Apache, 제우스, Nginx, Redis, 모니터링 솔루션 VM 등
- **멀티 클라우드 대응**: AWS, Private Cloud 통합 관리
- **ML 기반 예측**: 장애 예측 및 사전 대응
- **IaaS도 PaaS처럼**: 원하는 salt command flow 추가로 자동화 이후 VM내 서비스들도 PaaS처럼 쓰자!

---

**RescueBot과 함께 더 이상 새벽 3시에 출근하지 마세요! 🌙✨**
