# Mobile-Game-A-B-Testing
* 프로젝트 주제: 모바일 게임 이탈 유저 복귀 전략을 위한 A/B 검정
* 프로젝트 목적: 게임 업데이트 개선- 가설을 세워 유저 복귀가 좋은 게임 버전 업데이트 및 마케팅 전략 제시
* 프로젝트 기간: 2024.02 - 2024.02

# 데이터 소개
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/05b42033-c726-47e2-984a-7ded0f3cf35c)
* version: 플레이어가 게임을 일시적으로 중지하는 시점
  *  version은 게임 플레이 레벨 30& 40(gate_30& gate_40)에서 활성화되어 유저의 게임 플레이를 중단하여 게임을 진행하기 위해서는
광고를 보거나 인앱 구매로 게임을 바로 구매 해야한다
* sum_gamerounds: 첫 주에 유저가 플레이한 게임 라운드 수
* retention_1: 게임 설치 후 1일 이내 복귀 여부
* retention_7: 게임 설치 후 7일 이내 복귀 여부

# 이진화

![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/1034c19f-1686-4fd4-b9c1-e239254b9722)
* 시각화& 리텐션& 고착도& 부트스트랩& A/B 검정을 진행하기 위한 데이터 전처리
* Bool 타입 retention_1& retention_7 데이터 이진화 적용
* True인 경우 '1'설정하여 '복귀' 처리
* False인 경우 '0' 설정하여 '미복귀' 처리
