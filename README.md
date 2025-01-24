# WooriCard-EK-Analytics 💳

> 우리카드 실 데이터를 활용한 ELK 기반 데이터 시각화 프로젝트

## 📑 Table of Contents
1. [Project Overview](#project-overview)
2. [Team Members](#team-members)
3. [Tech Stack](#tech-stack)
4. [System Architecture](#system-architecture)
5. [Data Pipeline](#data-pipeline)
6. [Environment Setup](#environment-setup)
7. [Data Visualization](#data-visualization)
8. [Troubleshooting](#troubleshooting)

## 🎯 Project Overview
카드 거래 데이터를 실시간으로 분석하고 시각화하여 의미 있는 인사이트를 도출하는 프로젝트입니다.

### 주요 목표
- 실시간 카드 거래 데이터 수집 및 처리
- ELK 스택을 활용한 데이터 파이프라인 구축
- Kibana를 통한 직관적인 데이터 시각화
- 거래 패턴 분석 및 인사이트 도출

## 🛠 Tech Stack
### Infrastructure
```bash
Ubuntu 24.04 LTS
VirtualBox
```

## EK Stack
Elasticsearch 7.11.1 
<br>
Kibana 7.11.1

## 🏗 System Architecture

```bash
[Elasticsearch] → 데이터 저장 및 인덱싱
      ↓
[Kibana] → 데이터 시각화 <- [데이터 csv 파일]

```

## 📊 Data Pipeline
1. 카드 거래 데이터 수집

카드 거래 데이터를 MySQL 데이터베이스에 저장
<br>
정기적인 데이터 업데이트


2. Elasticsearch 처리

수집된 데이터 인덱싱
<br>
검색 및 분석을 위한 데이터 구조화


3. Kibana 시각화

다양한 차트 및 대시보드 구성
<br>
실시간 데이터 모니터링















