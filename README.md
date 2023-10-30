# SSAM
- **S**oo-gang **S**hin-cheong **A**pplication **M**anager

## 주제
- 초/중/고등학생을 위한 수강신청 앱


### 1. 기술 스택
<div align=center> 
  <img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> 
  <img src="https://img.shields.io/badge/spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white"> 
  <img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
  <img src="https://img.shields.io/badge/elasticsearch-a0c443?style=for-the-badge&logo=elasticsearch&logoColor=white"> 
  <img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white">
</div>

### 2. 주요 기능
- 회원가입 및 로그인
    - 회원가입
        - 학교/교사, 학생으로 구분하여 회원가입 진행
        - 아이디:이메일(또는 카카오/구글)
        - 권한요청(관리자 승인)
        - 패스워드:제약조건에 따른 패스워드 설정
    - 로그인
- 수강신청 과목 목록 출력
- 과목 상세 내용 출력
- 수강 신청한 과목들로 시간표 구성
- 질문/답변 커뮤니티

### 3. 구현 우선순위
- 1순위 : 회원가입/로그인과 관련한 모든 기능, 수강신청 과목 등록/리스트 출력, 과목 상세 출력
- 2순위 : 수강신청 과목과 관련한 정보 검색(ElasticSearch : 과목 소개와 과목 목표에 담긴 키워드를 중심으로 검색), 질문/답변 커뮤니티 기능 구현
- 3순위 : 개인 시간표 구성, 교재/부교재 사진 추가, 커뮤니티 대댓글 추가

### 4. 권한에 따른 기능

[공통]
- 회원가입/로그인

[관리자]
- 관리자는 admin 계정으로 본 서비스의 모든 권한을 가집니다.
- 관리자는 학교 또는 교사 권한을 요청한 사용자를 확인한 뒤, 요청한 권한을 승인할 수 있습니다.

[교사]
- 교사는 teacher 계정으로 로그인하여 API에 접근할 수 있습니다.
- 교사는 과목과 관련한 정보를 작성하여 학교 계정에 '과목 리스트에 추가 요청'을 할 수 있습니다.
- 과목와 관련한 정보는 다음과 같습니다.
    - 과목명
    - 과목세부내용 : 과목 소개, 선행 과목, 과목 목표, 이수 학년
    - 이수 학점
    - 주교재/부교재 소개(URL)
    - 요일
    - 시간

[학교]
- 학교 계정 관리자는 school 계정으로 로그인 후 API에 접근할 수 있습니다.
- 학교 계정 관리자는 학년별 최소/최대 수강신청 학점을 설정할 수 있습니다.
- 학교 계정 관리자는 교사가 요청한 과목 리스트 추가 요청 명세를 확인한 후 승인 또는 반려를 할 수 있습니다.
- 학교 계정 관리자가 과목을 승인하는 경우 학점에 따라 시간표를 배정합니다.
- 학교 계정 관리자가 승인한 과목은 과목 리스트에 출력됩니다.

[학생]
- 학생은 student 계정으로 로그인하여 서비스를 이용할 수 있습니다.
- 학생은 과목을 조회할 수 있습니다.
- 학생은 배정된 학점을 기준으로 과목을 선택하여 수강신청할 수 있습니다.
- 학생은 수강신청한 교과목들로 시간표를 만들 수 있습니다.


# ERD
![Alt text](ssam_erd_8.png)