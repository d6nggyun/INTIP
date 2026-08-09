# INTIP

인천대학교 재학생과 외국인 학생을 위한 학교 생활 정보 플랫폼입니다. <br>
공지사항, 학식 메뉴, 버스, 캠퍼스 시설, 동아리 정보가 여러 곳에 흩어져 있어서, 한 곳에서 확인할 수 있게 통합했습니다. <br>

App Store와 Google Play에 출시해 운영 중이고, 누적 2,500명 / DAU 약 200명 규모입니다. <br>

|  |  |
| --- | --- |
| 기간 | 2025.08 – 진행 중 |
| 소속 | INU AppCenter |
| 구성 | PM 1, 디자인 1, 백엔드 3, 프론트 2 |
| 담당 | 학교·학과 공지 크롤링 및 알림 기능, 대용량 알림 처리 구조와 로그 체계 개선 |

- App Store: https://apps.apple.com/kr/app/intip/id6740070975
- Google Play: https://play.google.com/store/search?q=intip&c=apps

<br>

## 기술 스택

| 영역 | 사용 기술 |
| --- | --- |
| Backend | Java, Spring Boot |
| Database | MySQL, Oracle, Redis |
| 크롤링 | Selenium |
| 알림 | Firebase FCM |
| 로그 / 모니터링 | Elasticsearch, Kibana, Elastic Agent, Micrometer, Prometheus, Grafana |
| 테스트 | JUnit 5 |
| Infra | Docker, Nginx |

 <br>
 
## 주요 기능

| 기능 | 설명 |
| --- | --- |
| 로그인 | 학교 포털 계정 기반 |
| 공지사항 | 전 학과 공지 크롤링 및 통합 제공 |
| 식당 메뉴 | 학식 메뉴 자동 수집 |
| 캠퍼스 지도 | 건물 위치 및 정보 |
| 커뮤니티 | 학교 생활 팁 공유 |
| 동아리 | 동아리 정보 제공 |
| 알림 | FCM 기반 키워드 자동 알림 |
| 버스 | 교내 버스 시간 정보 |

 <br>
 
## 아키텍처

<img width="2290" height="1162" alt="image" src="https://github.com/user-attachments/assets/8f60fe86-dfdb-488f-a402-b488636ca5d7" />

<br>

## 화면

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


