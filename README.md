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

# 순서
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/61c0e5c9-ed2d-4b0e-8c4d-33bde7f2a3fe)


# 이진화

![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/1034c19f-1686-4fd4-b9c1-e239254b9722)
### 시각화& 리텐션& 고착도& 부트스트랩& A/B 검정을 진행하기 위한 데이터 전처리
* Bool 타입 retention_1& retention_7 데이터 이진화 적용
* True인 경우 '1'설정하여 '복귀' 처리
* False인 경우 '0' 설정하여 '미복귀' 처리


# 리텐션
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/ed2ae52f-e854-4c66-89c4-b8428aeb1472)
* 리텐션율 = (복귀 사용자 수/ 전체 사용자 수)*100
 * 리텐션율: 고객이 서비스를 지속해서 사용하여 유지되는 비율
* 게임 버전 gate_30 유저 복귀율이 gate_40 버전보다 높다 


# 고착도
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/3101a8b3-95af-46e4-b4d8-be2db9af315b)
* 고착도(Stickiness): 고객의 게임 참여도 지표
* DAU(일일 사용자)& MAU(월간 사용자)
* MAU 데이터 존재하지 않아 7일 복귀 데이터 사용하여 7일 복귀 유저의 게임 참여 비율을 대략적인 지표로 사용
* 결과 gate_40 버전의 7일 이내 복귀 유저의 참여도가 높다

# 부트스트랩
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/53f6a0c7-01de-443a-8e07-cd0c44e462d6)
## 부트스트랩을 적용하여 유저 복귀 비율 파악
 * 부트스트랩: 데이터 샘플을 재표본 하여 통계적 추정치의 변동성& 신뢰구간 추정하는 방법이며 샘플 내 데이터 무작위로 반복하여 고객 리텐션율 검증
* 단순 리텐션 값으로 gate_30 버전의 유저 복귀율이 우세하다고 판단 하기에 근거가 부족 하여 부트스트랩 적용
* 결과 1& 7일 이내 복귀율 모두 gate_30 버전 높음 확임
   
# Shapiro-Wilk 정규성 검사
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/2d822c84-6d64-4119-9016-653bfd0bb244)
## 모바일 게임의 게임 2개 버전의 정규 분포 확인
* 정규 분포 시각화 결과 이진화로 인하여 정규 분포를 따르지 않아 비 모수적 검정 방법 채택
* Mann-Whiney U& Chi-Square& Wilcoxon& Fisher 검정 방법 채택

# Mann-Whitey U 검정
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/d482737b-8872-4005-bd9e-902e013c8601)
* Mann-Whitney U: 2개의 독립적인 표본 간 중앙값 비교 할 때 사용되는 비모수적 검정 방법
* 1일 복귀결과 p-value 값 유의수준 0.05 이상보다 높게 출력됨으로 모바일 게임 gate_30& gate_40 버전 유저의 1일 이내 게임 복귀 유의미한 결과가 없다
* 7일 복귀결과 p-value값 유의수준 0.05보다 낮게 출력됨으로 gate_30& gate_40 버전 유저의 7일 이내 게임 복귀 유의미한 결과 있다 결론

# Chi-Square(카이제곱) 검정
![image](https://github.com/forkgmltnr/Mobile-Game-A-B-Testing/assets/61262393/9835305a-daf5-412d-831c-48df19ca4033)
* Chi-Square: 두 범주형 변수 사이 관계를 평가하거나 관측된 빈도와 예상 빈도 차이 검정
* 1일 복귀 결과 유의수준 p-value값 0.05이상 출력되어 유의미한 결과가 없다
* 7일 복귀 결과 p-value값 유의 수준 0.05이상보다 낮아 7일 복귀율에 대해 통계적으로 유의미한 연관성 결론


# Wilcoxon Rank-Sum Test 순위합 검정
* Wilcoxon: 관련된 2개 표본& 일치 표본& 반복 측정된 표본간 비교할 때 사용
* Wiolcoxon Rank-Sum Test: 2개 표본이 같은 분포에서 나왔는지 검정 할 때 사용
* 데이터가 정규 분포를 따르지 않고 이상치에 대한 영향이 적은 Wilcoxon 검정 사용
* 1일 복귀 결과 p-value가 유의 수준 0.05보다 높고 가장 측정치가 높게 나온 검정 방법이며 유의미한 결과 없음
* 7일 복귀 결과 p-value가 유의 수준 0.05보다 낮고 4개의 검정 방법 중 가장 측정치가 높게 출력 7일 복귀에 유의미한 결과 값 도출


# Fisher 검정
* Fisher: 2개의 범주형 변수 사이의 독립성 검정& 연관성에 대한 유의성 평가
* 카이제곱과 같이 Fisher 검정은 두 범주형 변수 사이의 독립성 평가하여 Fuisher 정확 검정 사용
* 1일 복귀 결과 유의수준 0.05보다 높아 유의미한 결과 미 존재
* 7일 복귀 결과 유의수준 0.05보다 낮아 유의미한 결과 존재

  
