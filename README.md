# 🎓 INTIP - 인천대학교 통합 정보 플랫폼

> **INTIP**은 인천대학교 재학생 및 외국인 학생을 위한  
> 학교 생활 맞춤형 종합 정보 제공 서비스입니다.

---

## 📌 프로젝트 소개

학교 공지사항, 학식 메뉴, 버스 정보, 동아리, 생활 팁 등  
여러 곳에 흩어져 있는 정보를 한 곳에 통합하여  
학생들이 필요한 정보를 빠르게 확인할 수 있도록 설계한 플랫폼입니다.

현재 **App Store / Google Play에 출시되어 실사용 중**이며,  
일일 활성 사용자(DAU) 약 **200명**을 유지하고 있습니다.

---

## 📱 서비스 화면

<table>
  <tr>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/9e30342a-2fa0-4c7c-ac6c-238e93452843" width="250"/>
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/a44ff537-2bea-4f49-8f62-3b651b497195" width="250"/>
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/0ca838e5-c144-4756-875d-ad555a7951ae" width="250"/>
    </td>
  </tr>
</table>

---

## 🔗 다운로드 링크

- 🍎 App Store  
  [https://apps.apple.com/kr/app/intip/id6740070975](https://apps.apple.com/kr/app/intip/id6740070975)

- 🤖 Google Play  
  [https://play.google.com/store/search?q=intip&c=apps](https://play.google.com/store/search?q=intip&c=apps)

---

## 🏗 시스템 아키텍처

<img width="2290" height="1162" alt="image" src="https://github.com/user-attachments/assets/8f60fe86-dfdb-488f-a402-b488636ca5d7" />

---

## ⚙️ 주요 기능

| 기능 | 설명 |
|------|------|
| 🔐 로그인 | 학교 포털 기반 로그인 |
| 📁 공지사항 | 전 학과 공지 크롤링 및 통합 제공 |
| 🍳 식당 메뉴 | 학식 메뉴 자동 수집 및 제공 |
| 🗺️ 캠퍼스 지도 | 건물 위치 및 정보 확인 |
| 💬 커뮤니티 | 학교 생활 팁 공유 |
| 🎬 동아리 | 동아리 정보 제공 |
| 🔔 알림 | FCM 기반 키워드 자동 알림 |
| 🚌 버스 | 교내 버스 시간 정보 제공 |

---

## 🔎 핵심 기술 설계 및 문제 해결

### 1️⃣ FCM 대량 알림 처리 구조 개선 (OOM 해결)

대량 알림 전송 시, 단일 트랜잭션 내에서 수천 개의 엔티티가  
영속성 컨텍스트에 유지되며 **메모리 급증(OOM 위험)** 문제가 발생했습니다.

#### 해결

- 500건 단위 **batch chunking**
- 각 배치 처리 후 `flush()` 및 `clear()` 수행
- 영속성 컨텍스트 주기적 초기화

#### 결과

✔ OOM 위험 제거  
✔ 안정적인 대량 알림 전송 구조 확보  
✔ 메모리 사용량 예측 가능 구조 개선  

---

### 2️⃣ 학과 공지 크롤러 성능 최적화

기존에는 전체 공지를 삭제 후 재삽입하는 구조로 인해  
불필요한 DB I/O와 트랜잭션 충돌이 발생했습니다.

#### 해결

- 학과/제목/날짜 기반 **중복 필터링 로직 도입**
- diff 기반 신규 데이터만 저장
- DELETE/INSERT 최소화

#### 결과

✔ 크롤링 시간 **60초 → 30초 (50% 단축)**  
✔ DB 쓰기 횟수 감소  
✔ 서버 부하 및 충돌 감소  

---

### 3️⃣ 랜덤 정렬 성능 개선 (ORDER BY RAND 제거)

`ORDER BY RAND()` 사용으로 Full Table Scan 발생.

#### 해결

- 랜덤 정렬 전용 컬럼 추가
- 사전 생성된 랜덤 키 기반 조회
- 스케줄러로 하루 단위 인덱스 재생성

#### 결과

✔ Full Table Scan 제거  
✔ 조회 성능 안정화  
✔ 데이터 증가에도 확장 가능한 구조 확보  

---

### 4️⃣ 로그 저장 구조 개선

일일 수천 건 로그가 단일 테이블에 누적되며  
저장 공간 증가 및 조회 성능 저하 발생.

#### 해결

- 운영 로그 / 보관 로그 테이블 분리
- 불필요한 컬럼 제거
- 저장 데이터 경량화 및 압축 전략 적용

#### 결과

✔ 일일 로그 1000건 → 200건 (80% 이상 감량)  
✔ 테이블 비대화 방지  
✔ 장기 운영에 적합한 구조 확보  

---

## 🛠 기술 스택

| 영역 | 기술 |
|------|------|
| Backend | Spring Boot |
| Database | MySQL, Oracle |
| Cache | Redis |
| Push | Firebase FCM |
| Infra | Docker, Nginx |
| Test | JUnit5 |

---

## 📈 프로젝트 성과

- App Store / Google Play 실서비스 운영
- 신규 사용자 200명 확보
- DAU 약 60명 유지
- 실사용 환경에서 대량 알림 및 데이터 처리 구조 안정화
