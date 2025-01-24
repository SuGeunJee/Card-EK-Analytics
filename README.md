# WooriCard-EK-Analytics 💳
> 우리카드 실 데이터를 활용한 EK(Elasticsearch-Kibana) 기반 데이터 시각화 프로젝트

## 📑 Table of Contents
1. [Project Overview](#project-overview)
2. [Tech Stack](#tech-stack)
3. [System Architecture](#system-architecture)
4. [Environment Setup](#environment-setup)
5. [Data Visualization](#data-visualization)
6. [Troubleshooting](#troubleshooting)

## 🎯 Project Overview
우리카드의 실제 거래 데이터를 Elasticsearch와 Kibana를 활용하여 시각화하는 프로젝트입니다.

### 주요 목표
- CSV 형태의 카드 거래 데이터 분석
- Elasticsearch를 통한 데이터 저장 및 검색
- Kibana를 활용한 데이터 시각화
- 거래 패턴 분석 및 인사이트 도출

## 🛠 Tech Stack
### Infrastructure
![Ubuntu](https://img.shields.io/badge/Ubuntu%2024.04%20LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)

### EK Stack
![Elasticsearch](https://img.shields.io/badge/Elasticsearch%207.11.1-005571?style=for-the-badge&logo=elasticsearch&logoColor=white)
![Kibana](https://img.shields.io/badge/Kibana%207.11.1-005571?style=for-the-badge&logo=kibana&logoColor=white)

## 🏗 System Architecture
![_- visual selection](https://github.com/user-attachments/assets/76f59835-be1a-43a1-ba32-dc24b78ef82a)
[Elasticsearch] → 데이터 저장 및 인덱싱
     ↓
[Kibana] → 데이터 시각화 <- [데이터 csv 파일]

## 🔧 Environment Setup
### 1. Elasticsearch 설치 및 설정
# Elasticsearch 설정
network.host: 0.0.0.0
discovery.type: single-node

### 2. Kibana 설치 및 설정
# Kibana 설정
server.port: 5601
server.host: "0.0.0.0"
elasticsearch.hosts: ["http://localhost:9200"]


## 📈 Data Visualization
[시각화 섹션 - 추후 추가 예정]

## ❗ Troubleshooting
### 1. 외부 접속 문제
문제: VirtualBox의 Ubuntu에서 실행 중인 Elasticsearch/Kibana에 윈도우에서 접속 불가
해결: network.host와 server.host를 0.0.0.0으로 설정하여 외부 접속 허용
