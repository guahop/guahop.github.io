---
title: "[TIL] 2025.06.30"
date: 2025-06-30
categories: [TIL]
tags: [TIL, 한국정보교육원]
permalink: /til/2025-07-10/
---

# TIL – 2025-06-30
<!-- 오늘 날짜 -->

---

## 📘 Today I Studied
<!-- 오늘 공부한 강의, 실습, 문서 등 -->
- 한국정보교육원 KT클라우드와 NHN Cloud로 완성하는 클라우드 엔지니어 양성 1일차
- 네트워크(Network)란?
- 네트워크 분류 (기준 : 규모 단위, 통신 방식)
- 프로토콜(Protocol)
- MAC address vs IP address

---

## ✏️ Key Takeaways
<!-- 오늘 배운 주요 개념, 이론, 흐름 등을 자유롭게 정리하세요 -->

### 네트워크란?
- 무엇을 연결하는 것 (망이 모여서 함께 일하는 것)
- PC (단말기=터미널) - Network - PC
- 구성범위에 따른 네트워크 분류 (규모적으로 분류)
    - LAN (Local Area Network)
    - MAN (Metro Area Network)
    - WAN (Wide Area Network)

#### 1. LAN
- 근거리 통신망
- 한정된 좁은 지역에 구성된 네트워크 (ex. PC방, 사무실 등)
- LAN 구성 장비로는 Switch(Bridge), HUB 등이 있다
- HUB란? 터미널 연결 장치 (터미널을 쉽게 연결or제거하기 위해)
    - 종류 1. Dummy Hub => HUB라고 부름
    - 종류 2. Switch Hub => Switch라고 부름

#### 2. WAN
- 원거리통신망
- 넓은 지역을 연결하는 네트워크 ex) LAN과 LAN을 서로 연결하는 광역 네트워크
- WAN 구성 장비로는 Router가 있다

#### 인터넷 (Internet)
- LAN과 WAN들이 연결된 거대한 네트워크
- 정보 공유 목적으로 구성된 통신망의 집합체
- 네트워크가 확장됨에 따라 연결된 네트워크간에는 서로 동일한 프로토콜(protocol)을 사용해야 할 필요가 생겼다
- 여기서 프로토콜을 언어(규칙)로 비유할 수 있다

---

### Network Protocol (통신 규약)
#### 일반적 정의
- 네트워크 내의 컴퓨터들끼리 통신을 효율적으로 하기 위한 여러 가지 규칙

#### 기술적 정의
- 규칙들 또는 상호 합의된 것들의 모임으로, 데이터의 포맷과 전송에 대한 것들을 정의하는 것
- 서로 다른 네트워크가 통신을 하기 위한 언어 혹은 약속
- 네트워크상에는 많은 규칙이 존재하는데 서로 연결된 네트워크는 같은 **규칙(Network Protocol)**을 사용해야 한다
- 대표적인 네트워크 프로토콜 : 인터넷 환경에서 데이터를 전송하는 **TCP/IP**
- LAN프로토콜 WAN프로토콜이 따로 있다
- 통신을 하는데 있어 약속 사항은 전부 통신 프로토콜이다

#### 통신 방식에 따른 네트워크 분류
##### 1. 유니캐스트 (Unicast) : 상대 알고 있을때 
- 1:1 통신 
- ex) 아홉이에게 아홉아

##### 2. 멀티캐스트 (Multicast) : 상대 알고 있을 때
- 특정 다수와 통신
- ex) 아홉이가 있는 분단에서 아홉이를 찾음

##### 3. 브로드캐스트 (Broadcast) : 모를 때
- 전부에게 통신 
- ex) 아홉이가 어딘지 모르고 전체에서 찾음
- 불필요한 트래픽 발생함
- LAN은 브로드캐스트로 통신한다.

> 요청 할 때는 유니 or 멀티 or 브로드캐스트로 통신  
> 응답할 때는 반드시 유니캐스트 

--- 


### 네트워크의 주소 체계
- MAC address: 물리적 주소 (Physical address)
- IP address: 논리적 주소 (Logical address)


#### 설명

- 도메인을 IP주소로 변경 해주는거 (DNS)
- IP 주소에서 데이터통신을 위한 MAC주소를 알아내는 것 (ARP)  
- Domain -- (DNS)  -- IP Address -- (ARP) -- MAC Address
- 각 장비들은 정확한 통신을 위해 네트워크 상에서 서로 구분해야 함 > MAC(Media Access Control) address
- TCP/IP 사용하는 네트워크에서는 IP address를 사용하여 통신
- **최종적으로 MAC address를 사용하여 데이터를 전달** (MAC address가 있어야 데이터 통신 가능)
- 네트워크 장비의 인터페이스는 고유의 MAC address를 가지고 있다.
- ex) NIC카드, Router, Switch 등

### MAC address
- 네트워크에 연결된 장비들이 가지는 48bit의 고유한 주소 (전 세계에서 유일한 주소)
- 물리적 주소 (Physical address)
- 이진수 48bit 16진수로 표현
- 앞의 24비트는 생산자(생산회사)를 나타내는 코드: OUI라고 부름
- 뒤의 24비트는 회사에서 각 장비에 분배하는 host identifier

### IP address
- 이진수 32비트
- 논리적 주소 (Logical address)


--- 
## 🌱 What I Realized
<!-- 오늘 느낀 점, 인사이트, 나만의 정리 -->

- 지금은 단어와 개념들이 낯설지만 6개월 지나 수료할 때쯤에는 익숙해져 있길 바란다.
- 첫날인데 6개월동안 TIL이 쌓였으면 좋겠다.

---

## 👀 Questions & Next Steps
- IP Address 이어서 진도 나감
<!-- 내일 할 것, 궁금한 점, 더 찾아볼 개념 등 -->
