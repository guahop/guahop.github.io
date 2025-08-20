---
title: "개인 프로젝트 마이그레이션 기록 1: AWS 전환 배경과 목표"
date: 2025-08-20
categories: [프로젝트]
tags: [프로젝트, AWS, ASTERUM TRAVLER]
permalink: /project/asterumtravler-aws
---

# 개인 웹 프로젝트 인프라를 AWS로 옮기기 첫번째

## 1. AWS 전환 프로젝트 진행 이유

현재 저는 시스템/클라우드 엔지니어를 목표로 네트워크, 인프라, 클라우드 관련 지식을 학습하고 있습니다. 이번 프로젝트는 단순히 웹 애플리케이션을 개발하는 수준을 넘어, AWS 환경에서 실제로 인프라를 설계하고 운영해보는 경험을 쌓는 것을 목표로 하고 있습니다.

아직 AWS에 대한 경험이 부족하기 때문에 처음부터 완벽하게 구체적인 계획을 세우기보다는, 배포 환경을 AWS로 이전하는 것부터 시작하려 합니다. 이후 학습을 이어가면서 프로젝트에 필요한 인프라 기능들을 하나씩 적용하고, 네트워크 구성과 보안 강화를 병행하여 점진적으로 안정적인 환경을 구축해 나갈 계획입니다.

이 과정을 통해 단순히 "서비스를 올릴 수 있다"는 수준에서 벗어나, 실제 시스템/클라우드 엔지니어에게 요구되는 클라우드 인프라 설계·구축·운영 역량을 키워나가는 것이 가장 큰 목표입니다.

## 2. 개인 웹 프로젝트 소개 및 현재 구조

### 프로젝트 개요
ASTERUM TRAVELER는 버추얼 K-pop 아이돌 그룹 PLAVE 팬들을 위한 커뮤니티 및 정보 공유 플랫폼으로, React와 TypeScript를 기반으로 구현되었습니다. 프로젝트는 사용자 앱과 관리자(Admin) 페이지로 구분되어 있으며, 팬들이 아티스트와 관련된 다양한 활동을 편리하게 경험할 수 있도록 설계되었습니다.

### 주요 기능
- 제품 조회: PLAVE 멤버의 라이브 방송 또는 이미지 콘텐츠를 기준으로 관련 상품을 조회할 수 있는 기능 제공
- 팬 일정 관리: React Calendar 기반으로 플레이브 활동 및 이벤트 일정을 등록하고 확인 가능
- Dear 페이지: 팬들이 멤버들에게 메시지를 남기고 공유할 수 있는 커뮤니티 기능 제공
- 실시간 데이터 관리: 모든 게시글, 메시지, 일정은 Firebase Firestore를 통해 실시간 저장 및 동기화


### 현재 인프라 구조
Firebase를 활용한 서버리스 구조로 프론트엔드 개발 위주의 프로젝트입니다.
- 데이터베이스 및 스토리지: Firebase Firestore 및 Firebase Storage 활용
- 에러 로그 처리: Firebase Functions와 Slack Webhook을 이용한 에러 로그 수집
- 배포 환경: Vercel을 이용해 프론트엔드 애플리케이션 배포

특징: 별도의 서버 인프라 구축 없이, 제공되는 매니지드 서비스(Firebase + Vercel)를 조합하여 초기 MVP를 빠르게 구현


## 3. 마이그레이션 목표 및 계획
- Frontend 배포 환경:
    - Vercel → AWS S3 + CloudFront로 정적 사이트 배포
    - Route53 + ACM(AWS Certificate Manager)으로 HTTPS 도메인 적용

- Backend 환경:
    - Firebase → Node.js(Express) + MySQL 기반으로 이전
    - 초기 개발 환경: 로컬 Node.js + 로컬 MySQL
    - 운영 환경: AWS EC2(애플리케이션 서버) + RDS(MySQL DB)

- Storage 서비스:
    - Firebase Storage → AWS S3로 이전

- Error Logging & 모니터링:
    - Firebase Functions + Slack Webhook → AWS Lambda + CloudWatch Logs/EventBridge + Slack Webhook 조합으로 대체

- 인프라 고도화:
    - VPC를 활용한 네트워크 분리 및 보안 강화
    - AWS 학습하면서 점진적으로 AWS 보안/인프라 확장