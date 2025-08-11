# KD손해보험 관리자 시스템 (백엔드 프로젝트)

## 📌 프로젝트 개요
- **목적**: KD손해보험의 고객, 상품, 계약, 공지사항 등 보험 업무를 효율적으로 관리하는 **관리자 페이지** 백엔드 구축
- **특징**: Spring Legacy 기반, CRUD 중심의 안정적 시스템 + 관리자 UI
- **목표**: 보험 업무 프로세스의 **자동화** 및 **간소화**

---

## 🏗 시스템 아키텍처
[Browser] → [Web Server] → [WAS (Spring MVC)] → [MySQL DB]
브라우저: HTML, CSS, JavaScript (UI 렌더링)

웹서버: 정적 자원 처리 + 프록시 역할

WAS: Spring MVC, Controller → Service → DAO → DB

DB: Oracle 기반, MyBatis 연동

---

## 🛠 기술 스택
프레임워크	Spring Legacy, MyBatis
DB	Oracle DB, HikariCP
보안	Spring Security
프론트엔드(View)	JSP, JSTL, Bootstrap, jQuery
빌드/환경	Maven, Eclipse, Apache Tomcat
버전관리	Git, GitHub

---

## 📂 데이터베이스 설계
주요 테이블: customer(고객), insured_person(피보험자), contract(계약), notice(공지사항)

제약 조건:

고객 삭제 시 피보험자 존재하면 불가

피보험자 삭제 시 계약 존재하면 불가

ERD

고객 ↔ 피보험자(1:N)

고객 ↔ 계약(1:N)

피보험자 ↔ 계약(1:N)

---

## 🚀 워크플로우
1. 로그인
관리자 ID/PW 검증 → 실패 시 오류 메시지

로그인 성공 시 대시보드 이동

2. 대시보드
전체 고객/피보험자/계약/공지사항 수 표시

월별 계약 그래프, 상품별 계약 비율

최근 계약 & 공지사항 목록 표시

3. 고객 관리
고객 등록 → 상세 조회 → 수정/삭제

삭제 시 연결된 피보험자 확인 후 진행

4. 피보험자 관리
등록 → 상세 조회 → 수정/삭제

삭제 시 계약 여부 확인

5. 계약 관리
등록 → 상세 조회 → 수정/삭제

보험상품명, 기간, 상태 변경 가능

6. 공지사항 관리
등록(중요도 설정 가능) → 상세 조회(댓글 지원) → 수정/삭제

7. 정적 페이지
상품 관리, 보상 청구, 약관 관리, 시스템 설정, 관리자 교육자료, 시스템 로그 등

---

## 📑 API 명세 (요약)
고객 관리: /customer (GET, POST, PUT, DELETE)

피보험자 관리: /insured (CRUD)

계약 관리: /contract (CRUD)

공지사항 관리: /notice (CRUD, 댓글 포함)

---

## 📌 실행 방법
### 1. 프로젝트 클론
git clone https://github.com/사용자/KD-insurance-admin.git

### 2. DB 세팅
Oracle DB 생성 후 /sql/init.sql 실행

### 3. 서버 실행
mvn clean install
Tomcat에 배포 후 접속

---

## 👥 팀 구성
### Team Alegria

역할 분담: DB 설계, API 구현, 프론트엔드, 문서화 등
