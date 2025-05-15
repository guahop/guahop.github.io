---
title: "[TIL] 250515"
date: 2025-05-15
categories: [TIL]
tags: [TIL, SAP, SQL, 삼성에서 ERP로 먹고사는 컨설턴트가 알려주는 SAP]
---

# TIL – 250515
<!-- 오늘 날짜 -->

---

## 📘 Today I Studied
<!-- 오늘 공부한 강의, 실습, 문서 등 -->

- 삼성에서 ERP로 먹고사는 컨설턴트가 알려주는 SAP 2장
- 프로그래머스 SQL문제 Lv.1 7문제

---

## 📖 Key Takeaways
<!-- 오늘 배운 주요 개념, 이론, 흐름 등을 자유롭게 정리하세요 -->

### SAP 역사 SAP R/1 ~ R/3

EoS (End of Service) : 오래된 버전의 솔루션을 더 이상 유지보수 하지 않는 것  
MRP : ‘자재 소요량’을 관리는 것  
- SAP R/1 : 자재 소요량을 관리 하는 솔루션 (회계)
- SAP R/2 : 자재 소요량뿐만 아니라 생산에 필요한 자원 전체를 관리하도록 영역 넓힘 (구매, 회계, 생산)
- SAP R/3 : 개발 부터 서비스까지 회사전체의 운영 프로세스를 통합적으로 관리하는 것(ERP) (개발, 영업, 구매, 회계, 생산, 품질, 서비스)

### SCM (Supply Chain Management)
- 공급망 관리 : 우리 회사(ERP) 포함해서 협력업체, 유통망, 고객까지 전체 관리하는 개념

- SRM (Supplier Relationship Management): 협력업체 관계 관리
- CRM (Customer Relationship Management): 고객 관계 관리
- BI (Business Intelligence): 경영 의사결정 지원
- WMS(Warehouse Management System): 창고 관리
- **MES (Manufacturing Execution System)**: 생산 실행 세밀히 관리

⮕ SAP은 ERP가 주류여서 나머지 솔루션을 합쳐서 확장ERP라고 부르기도 함

### SAP S/4HANA
- 인메모리 데이터베이스: 데이터처리와 실시간 데이터 분석을 가능하게 함
- 통합된 비즈니스 프로세스: 구매, 생산, 판매, 재무 등 다양한 비즈니스 프로세스를 통합하여 제공
- 클라우드: 인프라 비용 절감, 비즈니스 환경 변화에 빠르게 대응 가능

+) 인메모리시스템?  
 - 이전에는 필요한 계산들마다 디스크에서 데이터를 가져와서 계산하느라 입출력 병목때문에 시간이 오래걸렸는데 인메모리시스템으로 디스크는 백업,복구 용으로 사용하고 CPU가 바로 RAM에 접근해서 이 문제점을 없앴다. RAM은 디스크 보다 작지만 계산할 임시 데이터를 가지고 있는 공간이라고 보면 됨  
 - 주의!!! 디스크가 없어진 것이 아님!! RAM이 임시로 디스크에서 데이터를 가져와서 가지고 있는 것 작은 RAM 디비가 기동되는 시점에 디스크에서 데이터를 올림, 오래동안 사용하지 않은 데이터는 가끔 RAM에 없을 수도 있음 그때 디스크에서 꺼내옴
 RAM 데이터가 수정되면 주기적으로 디스크 데이터에도 업데이트 함

### 클라우드

- 자체 구축 (On-premises) : 클라우드 방식이 대중화 되기 전 시스템 도입하던 전통적인 방식 ⮕ 지금도 많은 기업에서 이 형태로 구축되고 운영되고 있다.

#### 클라우드 장점
- 경제성 : 사용 기능, 기간 기준으로 계약하므로 낭비 없음
- 유연성 : 계약 변경을 통해 필요하면 시스템 확장 가능, 불필요하면 축소도 가능
- 가용성 : 서비스 제공업체가 알아서 해줌
- 구축 기간: 서비스 제공업체가 준비된 자원을 활용하므로 신속하게 구축 가능

#### 클라우드 서비스는 빌리는 정도에 따라 세 가지 유형으로 나눌 수 있음
- SaaS (Service as a Service) : 전부 (하드웨어, 운영체제, 응용 프로그램)
- Paas (Platform as a Service) : 적당히 (하드웨어, 운영체제)
- Iaas (infrastructure as a Service) : 조금 (하드웨어)

#### 여기서 보안과 안정성에 두 가지로 나뉨
- 퍼블릭(Public) : 일반 대중들이 사용할 수 있게 만든 B2C형 클라우드 인프라 플랫폼, 대중들에게 서비스 접근이 허용됨
- 프라이빗(Private) : 특정 조직 안에서만 운영되고 접근이 가능한 폐쇄적인 B2B형 - - 클라우드 인프라 플랫폼, 사내망에서 구현되며 On 사이트거나 Off 사이트로 구축됨
하이브리드 (Hybrid) : 두 가지가 적절히 섞여야 할 때

### SQL 정리
```sql
SELECT 테이블명.컬럼명1, 테이블명.컬럼명2 
FROM 테이블명; 

SELECT 별칭.컬럼명1, 별칭.컬럼명2 
FROM 테이블명 AS 별칭; 

SELECT 컬럼명
FROM 테이블명
WHERE 컬럼명 IS NOT null # NOT 없어도 가능 
ORDER BY 컬럼명;


SELECT 컬럼명
FROM 테이블명
WHERE 필드명 = 데이터
ORDER BY 컬럼명;
```
1. IS NULL로 데이터 존재 유무 확인 하는거고 = 로 뒤에 데이터가 맞는지 확인


```sql
SELECT WAREHOUSE_ID, WAREHOUSE_NAME, ADDRESS, 
IFNULL(FREEZER_YN, 'N') as FREEZER_YN
FROM FOOD_WAREHOUSE
WHERE ADDRESS LIKE '경기도%'
```

1. IFNULL(컬럼명, 존재하지 않을때 채울 데이터) AS 별칭  
IFNULL이 새로운 필드를 만드는거라서 AS로 별칭 지정해주지 않으면 컬럼명에 그대로 IFNULL(컬럼명, 존재하지 않을때 채울 데이터)가 들어감 

2. LIKE는 문자열 패턴을 비교할 때 사용하는 조건절이
여기서 %는 "0개 이상의 어떤 문자든 가능하다"  
__는 _개수의 임의의 글자가 온다는 의미  ex) “경기?”


```sql
SELECT COUNT(USER_ID) AS USERS
FROM USER_INFO
WHERE JOINED LIKE '2021%' AND AGE BETWEEN 20 AND 29;
```
1. COUNT(컬럼명) AS 별칭  
COUNT는 NULL이 아닌 값만 센다

2. AND로 WHERE 조건 여러개 작성가능

3. 컬럼명 BETWEEN 최소값 AND 최대값  
BETWEEN은 숫자(또는 날짜 등)의 범위 안에 있는 값을 찾을 때 사용  
```sql
WHERE age >= 20 AND age <= 29 
```
위의 코드로 대체 가능


```sql
SELECT DR_NAME, DR_ID, MCDP_CD, DATE_FORMAT(HIRE_YMD, '%Y-%m-%d')
FROM DOCTOR
WHERE MCDP_CD = 'CS' OR MCDP_CD = 'GS'
ORDER BY HIRE_YMD DESC, DR_NAME;
```

1. DATE_FORMAT(컬럼명, '포맷')  
날짜형식을 문자열로 변환할 때 사용

2. WHERE 조건1 OR 조건2  
- OR은 둘 중 하나라도 충족하면 true  
- AND는 둘 다 충족해야 한다.
```sql
WHERE MCDP_CD IN ('CS', 'GS')
```
위의 코드로 대체 가능

3. ORDER BY 컬럼1 DESC, 컬럼2  
복수 기준 정렬 DESC 내림차순  
컬럼2는 ASC 오름차순인데 오름차순은 기본값이라서 생략 가능


---

## 💡 What I Realized
<!-- 오늘 느낀 점, 인사이트, 나만의 정리 -->

- 클라우드 시스템에 뭔지 말 할 수 있게 되었다.
- 헷갈리던 인메모리 방식을 이해함
- SQL 문법 정리할 것 한 바가지
