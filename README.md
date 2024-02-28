# 👋 Intro
```　
안녕하세요! 데이터 사이언티스트를 꿈꾸는 최무성 입니다.  
지금까지 배웠던 내용들을 정리하고 복기하고자 본 페이지를 만들었습니다.  
기본적으로 각 프로젝트들의 개요와 맡았던 역할, 결과 및 배웠던 점들을 기록하였습니다.  
```

<br />



# 📝Projects
> 진행했던 프로젝트들을 정리해보았습니다.    
> 운영적인 측면에서는 팀원들과의 의사소통 및 역할 분배, 프로젝트 일정 관리를 맡아 프로젝트 전반적인 운영을 경험할 수 있었고,  
> 기술적인 측면에서는 대부분 모델링을 맡았으며 데이터 전처리 및 팀원들의 아이디어를 코드로 구현하는 역할을 수행하였습니다.

## 1. 💸 Lending Club 부도 예측 모형
부도 예측 모형 설계 _(서울대학교 빅데이터 핀테크 전문가 과정 6기, 6조 팀프로젝트)_
 - 핵심 역할 : 이진 분류 예측 모형 모델링, 목적함수 코드 구현, 모델 성능 시각화

 프로젝트 개요  
 - 목적 : 각 사용자 별 특징들을 기반으로 부도 예측 모형을 설계하여 수익 극대화
  
 - 데이터 : Lending Club Data
   - 데이터 형태 : 약 87만행 X 330열
   - 독립변수 : 연속, 범주, 이산형 으로 각 사용자의 특성 설명
   - 종속변수 : 부도 여부의 이산형 변수
   - 이상치가 많았고, 부도 데이터가 16%로 불균형 데이터
  
 - 데이터 처리
   - 사후 변수 제거 : 대출 승인 여부에 대한 판단 시점에 사용가능한 변수와 불가능 변수를 구분
   - 다중공선성 확인 : 연속형 변수 간 다중공선성을 가진 변수 제거
   - 파생 변수 생성 : 범주형 변수의 속성 및 분포를 고려하여 그룹화
   - 변수 스케일링 : 이상치와 극단치를 고려하여 Robust Scaler 사용
   - 데이터 샘플링 : 데이터의 총량을 고려하여 Under Sampling 진행
 
 - 사용한 모델
   - Decision Tree, Random Forest, Logistic Regression, XGBoost
   - 하이퍼 파라미터 최적화(필요한 경우) : 베이지안 최적화
  
   
프로젝트 결과 
| Model           | Logistic Regression | Random Forest | Decision Tree | XG Boost |
|-----------------|---------------------|---------------|---------------|----------|
| Accuracy        | 0.787               | 0.769         | 0.714         | 0.78     |
| Precision       | 0.323               | 0.308         | 0.27          | 0.321    |
| Recall          | 0.288               | 0.342         | 0.452         | 0.323    |
| F1 score        | 0.305               | 0.324         | 0.338         | 0.322    |
| 손실액           | 267569324           | 277022671     | 284704961     | 267977285|
| 손실 감소 비율* | 33%                 | 30.6%         | 28.7%         | 32.9%    |
  
  
배운 점   
- 모든 변수들을 사용하는 것이 좋은 것이 아님, 모델 사용 시점과 더불어 도메인 지식에 대한 깊은 고민이 필요  
- 모델 자체의 성능뿐만 아니라 해당 모델이 사용될 영역에서 어떤 효과를 이끌어낼 수 있는가, 즉 **'목적함수'** 의 중요성
 
> [발표 자료](https://github.com/kimphysicsman/MyLittelTrip_backend), [소스 코드](https://github.com/kimphysicsman/MyLittelTrip_backend)  

<br />

## 2. 👞 MyLittleShoes

> 신발 스타일링 _(내일배움캠프 - 4520조 팀프로젝트)_
>
> - 개발기간 : 2022.06.28-07.06
> - 핵심 역할 : 팀장, Generative model를 이용한 신발 스타일링 기능 구현
> - Language : python3
> - Skill : Django, Django-rest-framework
>
> [프로젝트 상세 설명](https://github.com/kimphysicsman/mylittleshoes_backend)

<br />

## 3. 🍻 MyLittleBeer

> 맥주 추천 _(내일배움캠프 - 판타스틱4조 팀프로젝트)_
>
> - 개발기간 : 2022.06.02-13
> - 핵심 역할 : 팀장, 맥주 Data 전처리 및 자카드 알고리즘을 이용한 추천 기능 구현 
> - Language : python3, javascript
> - Skill : Django, MySQL
>
> [프로젝트 상세 설명](https://github.com/kimphysicsman/mylittlebeer/)

<br />

## 4. 👊 MyLittelHero

> 닮은 마블 캐릭터 찾기 _(내일배움캠프 - 판타스틱4조 팀프로젝트)_
>
> - 개발기간 : 2022.05.18-25
> - 핵심 역할 : 팀장, CNN 모델별 학습 및 성능 비교, 닮은 마블 캐릭터 찾기 기능 구현
> - Language : python3   
> - Skill : flask, mongoDB
>
> [프로젝트 상세 설명](https://github.com/kimphysicsman/mylittlehero_backend)

<br />

## 5. 🎮 Sparta Fighter

> 2d 횡스크롤 격투 게임 _(내일배움캠프 - 개인 프로젝트)_
>
> - 개발기간 : 2022.04.25-27
> - 핵심 역할 : 캐릭터 클래스 구현 및 이벤트 루프 작성
> - Language : python3
>
> [프로젝트 상세 설명](https://github.com/kimphysicsman/sparta_fighter)

<br />

## 6. 🎶 RE:TRO | 그때 그 시절, 당신의 음악

> 1980-2010년 뮤직 웹사이트 _(메이킹챌린지 - 코딩왕조 팀프로젝트)_
>
> - 개발기간 : 2022.03.02-17
> - 핵심 역할 : 팀장, 노래 재생 기능, 좋아요 기능
> - Language : python3, javascript
> - Skill : flask, mongoDB
>
> [프로젝트 상세 설명](https://github.com/kimphysicsman/retro_main)

<br />

# 🎞 Youtube
<table>
  <tbody>
    <tr>
      <td>
        <a href="https://youtu.be/BYKYpyyJfKU" title="판타스틱4조 - 머신러닝기초 4주차 스터디영상">
          <img align="center" src="https://user-images.githubusercontent.com/68724828/186108751-0ad77c13-2115-4621-af8d-f4a11e5b3652.png" width="300" alt-text="판타스틱4조 - 머신러닝기초 4주차 스터디영상">
        </a>
      </td>
      <td>
        <a href="https://youtu.be/HR1b2hrxvbY" title="사오이십조 - DRF 5일차 스터디영상">
          <img align="center" src="https://user-images.githubusercontent.com/68724828/186109362-b40c300c-0906-4062-9bc3-8229e692af8e.png" width="300" alt-text="사오이십조 - DRF 5일차 스터디영상">
        </a>
      </td>
      <td>
        <a href="https://youtu.be/nXTzsSGfIbg" title="사오이십조 - 220624아침퀴즈 스터디영상">
        <img align="center" src="https://user-images.githubusercontent.com/68724828/186110013-b5c77cf3-0bbc-481a-897b-d3a30bc74be6.png" width="300" alt-text="사오이십조 - 220624아침퀴즈 스터디영상">
          </a>
      </td>
    </tr>
  </tbody>
</table>
> <b><em><a href="https://www.youtube.com/channel/UCdnXRtn_xnRWzZxUGY0yyWg/videos">More videos...</a></em></b>


<br />
<br />

# 📞 Contact

- 이메일 : kimphysicsman@gmail.com
- 블로그 : <a href="https://velog.io/@kimphysicsman">
  <img src="https://user-images.githubusercontent.com/68724828/185885678-8f619bfa-1160-4bb4-a026-f758a4014f82.png" height="26px" style="margin-top: 10px" />
  </a>
- 깃허브 : <a href="https://github.com/kimphysicsman">
  <img src="https://user-images.githubusercontent.com/68724828/185908612-22f4d219-78a7-4de7-bb02-deecaa63bffa.png" height="28px" style="margin-top: 10px" />
  </a>
- 유튜브 :<a href="https://www.youtube.com/channel/UCdnXRtn_xnRWzZxUGY0yyWg">
  <img src="https://user-images.githubusercontent.com/1569988/159397141-21463bc2-2acf-416b-aa15-235664556f34.png" height="24px" style="margin-top: 10px" />
  </a>
