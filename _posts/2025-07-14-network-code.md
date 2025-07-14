---
title: "[네트워크] 실습 코드 정리"
date: 2025-07-14
categories: [네트워크]
tags: [네트워크, 한국정보교육원]
permalink: /network/network-code
---

# [네트워크] 실습 코드 정리
<!-- 오늘 날짜 -->

---

<details>
<summary>운영 모드 정리</summary>
<div markdown="1">
- 일반사용자 모드
```Switch> ```

- 관리자 모드
```
Switch> enable
Switch#
```

- 관리자 모드 나가기 
```Switch# exit```

- 전역 설정 모드
```
Switch# conf t : 꼭 관리자모드에서만 할 수 있음
Switch(config)#
```

- 인터페이스 모드
```
Switch(config)# interface f0/1
Switch(config-if)#
```

- 라인 모드
    - Console
        ```
        Switch(config)#line console 0
        Switch(config-line)#
        ```
    - VTY (무선 접속)
        ```
        Switch(config-line)#line vty 0 4 : 동시에 5명 접근 가능
        Switch(config-line)#
        ```
    - AUX
        ```
        Switch(config)#line aux 0 > 라우터에만
        Switch(config-line)#
        ```
</div>
</details>

<details>
<summary>원격 접속 (VTY)</summary>
<div markdown="1">
- Switch
    ```
    Switch(config)#int vlan 1
    Switch(config-if)#ip address 192.168.10.100 255.255.255.0
    Switch(config-if)#no shutdown
    Switch(config-if)#ip default-gateway 192.168.10.1  (라우터주소, 이거 안넣어주면 다른 네트워크에서는 접속 안됨)
    Switch(config)#line vty 0 4
    Switch(config-if)#password 1234   : 외부 PC로 접근하려면 패스워드 설정되어 있어야한다.
    Switch(config-if)#login
    ```

- Router
    ```
    Router(config)#int fa0/0
    Router(config-if)#ip add 192.168.10.1 255.255.255.0
    Router(config-if)#no shutdown
    Router(config)# line vty 0 4 >> 무선접속 비밀번호 설정
    Router(config-if)#password 1234   : 외부 PC로 접근하려면 패스워드 설정되어 있어야한다.
    ```

- 접속 방법
    - 명령 프롬프트 ```c:\ telnet 192.168.10.100```

</div>
</details>


<details>
<summary>도움이 되는 명령어</summary>
<div markdown="1">
- 도움말: ```?```
- 명령어 자동 완성 기능: ```[TAB]```
- 한 번에 관리자 모드 이동: ```CTRL + z or end```
- 잘못된 명령어 쳐서 빠져나가는 법: ```CTRL+SHIFT +6```
- 평문으로 설정된 패스워드를 암호화 하는법: ```Switch(config)#service password-encryption```
- ```SW1(config-line)#exec-timeout 0 0 : 원래는 아무것도 안하고 시간 지나면 로그아웃 되어버림```
- ```SW1(config-line)#no ip domain-lookup : 잘못된 명령어 치면 멈춰버리는데 그거 방지```

</div>
</details>

---

## VLAN

<details>
<summary>VLAN 생성 및 할당</summary>
<div markdown="1">

- Switch 1
    ```
    Switch(config)#vlan 100
    Switch(config-vlan)#name Study

    Switch(config)#int fa0/1
    Switch(config-if)#switchport mode access
    Switch(config-if)#switchport access vlan 100
    ```

- Switch 2
    ```
    Switch(config)#vlan 200
    Switch(config-vlan)#name dance
    Switch(config)#int range fa0/3-4
    Switch(config-if-range)#switchport mode access
    Switch(config-if-range)#switchport access vlan 200
    ```

- VLAN 지나갈 수 있게 Trunking
    ```
    Switch(config)#interface fa0/24
    Switch(config-if)#switchport mode trunk 
    ```

- L3 스위치에서 trunk 하는법
    ```
    Switch(config-if)#switchport trunk encapsulation dot1q 
    Switch(config-if)#switchport mode trunk
    ```

</div>
</details>

<details>
<summary>VLAN 할당</summary>
<div markdown="1">
- R1
    ```
    Router(config-if)#ip add 192.168.10.1 255.255.255.0
    Router(config-if)#no sh

    Router(config)#interface fa0/0.100
    Router(config-subif)#encapsulation dot1Q 100
    Router(config-subif)#ip address 172.16.10.1 255.255.255.0

    Switch(config)#interface fa0/23
    Switch(config)#sw mo tr // switch에서 trunk 해주면 됨
    ```
</div>
</details>

<details>
<summary>VTP (VLAN Trunking Protocol)</summary>
<div markdown="1">
- 운영모드
    - Server: VLAN 생성/수정/삭제 가능, 다른 클라이언트들에게 VLAN 정보 제공/ 전달
    - Client :  VLAN 생성/수정/삭제 불가능, 다른 클라이언트들에게 VLAN 정보 제공/ 전달
    - Transparent:  VLAN 생성/수정/삭제 가능, 다른 클라이언트들에게 VLAN 정보 제공/ 전달 - 본인이 만든거는 전달X 서버 VLAN만 전달

-  VLAN 정보 공유 조건
    1. VTP 프로토콜 버전 동일  
    2. VTP 도메인 동일  
    3. VTP 패스워드 동일  

- vtp 상태 보기
    ```Switch(config)# do show vtp status```

- Switch Server
    ```
    Switch(config)#vtp domain cisco
    Switch(config)#vtp password 1234
    ```

- Switch Client
    ```
    Switch(config)#vtp mode client
    Switch(config)#vtp domain cisco
    Switch(config)#vtp password 1234
    ```
</div>
</details>


---

<details>
<summary>원격 접속 (VTY)</summary>
<div markdown="1">
</div>
</details>


