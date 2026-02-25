![Python-3](https://github.com/user-attachments/assets/4ac03e2d-bdb7-49c7-90f5-675570eee4cf)



# ChannelTalk ROI Simulation

## 제작자
Gabia 클라우드사업팀 인턴 Dylan (김동현)

---

## 목적

Gabia Cloud의 ChannelTalk 유지 타당성을 정량적으로 검증하기 위한  
Monte Carlo 기반 ROI 시뮬레이션

- 대상 비용: ChannelTalk 연간 9,000,000원
- 계약 존속 기간: 12개월
- 분석 기준: 연간 진성 문의 → 계약 전환 → 연간 매출 발생 구조

---

## 1. Work Stream

### 1. Cost Assumption
- ChannelTalk 연간 비용: 9,000,000원
- 계약 존속 기간: 12개월

### 2. Inquiry Modeling
- 월 평균 66건 진성 문의 가정
- Poisson 분포 기반 연간 문의 수 생성

### 3. Conversion Logic
- 전환율 가정
- 계약 월 단가 범위 설정

### 4. Monte Carlo Simulation
- 50,000회 반복 실행
- 연간 순이익 분포 계산

### 5. Output
- 손익분기 최소 계약 단가
- 계약 건수별 손익분기 단가
- 시나리오별 순이익 분포
- ROI 달성 확률

---

## 2. Calculation Logic

### 기본 파라미터

| 항목 | 값 |
|------|------|
| Annual Cost | 9,000,000 KRW |
| Contract Duration | 12개월 |
| Simulation Count | 50,000회 |
| 월 평균 문의 | 66건 |

---

### 문의 생성 로직

연간 문의 수는 Poisson 분포 기반으로 생성됩니다.

- 월 평균 λ = 3.0
- 1일 평균 3건
- 월 22영업일
- 12개월 반복

---

### 매출 계산 로직

각 문의에 대해 전환 조건:


if random < conversion_rate:
계약 발생


계약 매출:


계약 월 단가 × 12개월


---

### 순이익 계산


연간 순이익 = 총 계약 매출 − 9,000,000원


시각화 단위는 만원 기준으로 변환합니다.

---

## 3. Scenario 정의

| 시나리오 | 전환율 | 계약 월 단가 범위 |
|----------|--------|------------------|
| 최악 | 0.5% | 500,000 ~ 2,000,000 |
| 보수 | 1% | 500,000 ~ 8,000,000 |
| 기본 | 2% | 2,000,000 ~ 10,000,000 |

---

## 4. ROI 정의

ROI 달성 조건:


연간 순이익 > 0


ROI 달성 확률:


(순이익 > 0 인 시뮬레이션 횟수 ÷ 50,000) × 100


---

## 해석 포인트

- ChannelTalk은 고단가 계약 1~2건으로 손익분기 가능
- 응답 지연은 전환율 하락으로 직결
- 핵심 변수는 문의 수가 아니라 전환율

---

## Disclaimer

1. 확률 기반 가정 시뮬레이션 모델
2. 실제 성과는 전환율 및 계약 단가에 따라 달라짐
3. 내부 영업 데이터 일부 미반영
4. 구조적 ROI 검증 목적 분석

---

Copyright © 2026 Dylan (Donghyun Kim)
