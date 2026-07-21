# Lancet Global Health 제재-사망률 논문 재현 패키지

Rodríguez, Rendón, Weisbrot (2025). "Effects of international sanctions on
age-specific mortality: a cross-national panel data analysis."
Lancet Glob Health 2025; 13: e1358–66.

## 파일 구성
- `monte_carlo_sanctions.py`: 일방제재(unilateral sanctions)로 인한 연간 초과사망자
  수의 95% 신뢰구간을 몬테카를로 시뮬레이션(N=1000)으로 재현하는 스크립트

## 필요한 원본 데이터 (Harvard Dataverse에서 다운로드, doi:10.7910/DVN/ZJSHU4)
- `mortality1_r-1.dta`: 국가-연도 패널 (제재지표, 통제변수, 연령별 로그사망률)
- `un_single_age_life_t.dta`: UN 단일연령 생명표 (인구·사망자, 국가-연도-연령별)

## 재현 절차 요약
1. `mortality1_r-1.dta`를 1971-2021년으로 제한
2. PanelOLS(국가·연도 고정효과, 국가 클러스터 표준오차)로 unilateral_sanctions의
   연령대별 계수(β)와 표준오차(SE) 추정
   -> 논문 부록 Table 2(비가중)와 오차범위 내 거의 정확히 일치 확인됨
3. `un_single_age_life_t.dta`를 논문의 연령 구간(0-1, 1-5, 5-10, 10-15, 15-60,
   60-80)으로 재집계 (단위: UN 인구국 관례상 '천 명' -> ×1000 환산 필요)
4. 2012-2021년 제재 대상국-연도에 대해, β를 정규분포 N(β̂, SE)에서 1000회
   추출하며 매번 초과사망자 = 관측사망자 × (1 - exp(-β))를 계산해 합산
5. 1000개 연평균 추정치의 평균과 2.5/97.5 백분위수로 95% CI 산출

## 핵심 결론
- 재현된 중심추정치(534,902명/연)와 95% CI([300,733, 759,047])는 논문 공식
  수치(564,258명/연, CI [367,838, 760,677])와 근접하게 일치 -> 논문 결과는
  공개 데이터로 독립 재현 가능함을 확인
- CI 상한(약 76만 명)을 50년으로 단순 외삽하면 약 3,800만 명이 나오며, 이는
  일부 인터뷰에서 인용된 "제재로 인한 3,800만 명 사망" 수치와 거의 정확히
  일치함 -> 해당 수치는 논문의 "중심 추정치"가 아니라 신뢰구간 상한을
  대표값처럼 사용한 것임을 시사
