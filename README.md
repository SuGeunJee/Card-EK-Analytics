# Card-EK-Analytics 💳
> 카드 데이터를 활용한 EK(Elasticsearch-Kibana) 기반 데이터 시각화 프로젝트

# 📑 Table of Contents
1. [Project Overview](#-project-overview)
2. [Tech Stack](#-tech-stack)
3. [System Architecture](#-system-architecture)
4. [Environment Setup](#-environment-setup)
5. [Data Visualization](#-data-visualization)
6. [Troubleshooting](#-troubleshooting)

# 🎯 Project Overview
카드사의 거래 데이터를 Elasticsearch와 Kibana를 활용하여 시각화하는 프로젝트입니다.

## 주요 목표
- CSV 형태의 카드 거래 데이터 분석
- Elasticsearch를 통한 데이터 저장 및 검색
- Kibana를 활용한 데이터 시각화
- 거래 패턴 분석 및 인사이트 도출

# 🛠 Tech Stack
## Infrastructure
![Ubuntu](https://img.shields.io/badge/Ubuntu%2024.04%20LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)

## EK Stack
![Elasticsearch](https://img.shields.io/badge/Elasticsearch%207.11.1-005571?style=for-the-badge&logo=elasticsearch&logoColor=white)
![Kibana](https://img.shields.io/badge/Kibana%207.11.1-005571?style=for-the-badge&logo=kibana&logoColor=white)

# 🏗 System Architecture
![_- visual selection](https://github.com/user-attachments/assets/76f59835-be1a-43a1-ba32-dc24b78ef82a)

# 🔧 Environment Setup
## 1. Elasticsearch 설치 및 설정
1-1. GPG Key 추가
```
$ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo tee /usr/share/keyrings/elasticsearch-keyring.asc
```

1-2. apt 레포지토리 추가 (elasticsearch 7버전 다운로드하기 위한 레포 추가)
```
$ echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
```

1-3. apt-get Update (필수)
```
$ sudo apt-get update
```

1-4. elasticsearch-7.11.1 설치
```
$ sudo apt-get install elasticsearch=7.11.1
```

1-5. elasticsearch.yml 파일 Network 설정 변경
``` 
network.host: 0.0.0.0
http.port: 9200
discovery.type: single-node
```

1-6. elasticsearch 실행 확인
```
$ sudo systemctl status elasticsearch

$ sudo systemctl enable elasticsearch

$ sudo systemctl status elasticsearch

$ sudo systemctl start elasticsearch

$ sudo systemctl status elasticsearch
```
![image (1)](https://github.com/user-attachments/assets/58fcb9ab-0299-45c7-b145-90961d4da37b)

1-7. elasticsearch 로컬 접속 확인
```
$ curl -X GET "localhost:9200/"
```
![image](https://github.com/user-attachments/assets/16c45722-ef3c-4404-adb1-2ed805e1d92a)


1-8. elasticsearch 외부 접속 확인
- windows에서 127.0.0.1:9200 으로 접속

![image (2)](https://github.com/user-attachments/assets/3875c185-6f99-4cf5-834c-bd872b025217)

## 2. Kibana 설치 및 설정

2-1. kibana 설치
- Elastic 패키지 저장소가 이미 추가되어 있으므로 바로 설치 가능
```
$ sudo apt-get install kibana=7.11.1
```

2-2. kibana 실행 확인
```
$ sudo systemctl start kibana

$ sudo systemctl enable kibana
```

2-3. kibana.yml 파일 수정
```
server.host: “0.0.0.0”
elasticsearch.hosts: ["http://localhost:9200"] 주석 해제
```

2-4. kibana 재시작
```
$ sudo systemctl restart kibana
```

2-5. kibana 외부 접속 확인
- windows에서 127.0.0.1:5601로 접속
![image (4)](https://github.com/user-attachments/assets/7b7d14a6-df99-4007-a734-b4e398c4fa6f)

# 📈 Data Visualization
## Project 1 - 카드 이벤트를 열려고 하는데, 가장 많은 매출을 올릴 수 있는 방법을 찾아라!
- 가장 많은 매출을 올린 나이대 분석 - 30~50대가 가장 많은 매출을 올림
![다운로드](https://github.com/user-attachments/assets/0155c691-9672-475b-a442-592efd09058d)

- 그 나이대의 소비 패턴을 파악 - 유통, 요식업, 보험 등의 소비 패턴을 파악할 수 있었음
![다운로드 (1)](https://github.com/user-attachments/assets/3fb3908d-5b4d-4516-9ca7-1d75bba527dd)

### 실질적으로 실행할 수 있는 이벤트 목록
**유통 - 온라인 쇼핑 혜택**
- 유통업(94,803,010) 최대 소비
- 대형마트/온라인몰 결제 시 추가 포인트
- 정기결제 할인 혜택

**요식업 - 식비 절약 챌린지**
- 월 30만원 이상 식비 결제 시 캐시백 5%
- 구독형 배달앱 할인 서비스

**보험 - 건강케어 프로그램**
- 보험/병원 관련 소비 증가 추세
- 건강검진/병원 결제 시 추가 포인트
- 건강보험 연계 할인

**보너스: 세 혜택 모두 이용 시 추가 리워드 제공**

# ❗ Troubleshooting
## 1. 외부 접속 문제
문제: VirtualBox의 Ubuntu에서 실행 중인 Elasticsearch/Kibana에 윈도우에서 접속 불가
해결: network.host와 server.host를 0.0.0.0으로 설정하여 외부 접속 허용
