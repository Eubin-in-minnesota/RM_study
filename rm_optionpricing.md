RM: Option Pricing
================
Eubin Lim
Feb 12th, 2021

Last Updated : March 24th, 2021

## Option

### 기초 개념

  - 미래의 일정 시점에 일정 가격으로 주식, 채권, 통화 등의 기초자산을 매수하거나 매도할 수 있는 권리    
  - Option buyer: 옵션을 행사할 권리를 보유하되 의무는 없음. 좋은 결과만 얻을 수 있는 대신 상응하는 대가(옵션
    프리미엄) 지불해야 함
  - Option seller: 옵션 프리미엄을 수취하고 옵션 매수자의 옵션 행사에 응해야 할 의무 있음
  - 옵션의 손익구조: 비대칭적
      - Option buyer: 손실 제한, 이익 무제한
      - Option seller: 이익 제한, 손실 무제한
  - Call option: 약정일에 약정 행사가격으로 기초자산을 매수할 수 있는 권리
  - Put option: 약정일에 약정 행사가격으로 기초자산을 매도할 수 있는 권리

### Option Premium = Intrinsic Value + Extrinsic Value

#### Intrinsic Value

옵션의 내재가치: 옵션매수자가 권리를 행사함으로써 얻는
권리

| 구분      | Call Option           | Put Option            | Intrinsic Value |
| ------- | --------------------- | --------------------- | --------------- |
| ITM 내가격 | 기초자산의 시장가격 \> 옵션 행사가격 | 기초자산의 시장가격 \< 옵션 행사가격 | \+              |
| ATM 등가격 | 기초자산의 시장가격 = 옵션 행사가격  | 기초자산의 시장가격 = 옵션 행사가격  | 0               |
| OTM 외가격 | 기초자산의 시장가격 \< 옵션 행사가격 | 기초자산의 시장가격 \> 옵션 행사가격 | \-              |

  - 콜옵션의 내재가치 = Max\[(기초자산의 시장가격 - 콜옵션의 행사가격), 0\]  
  - 풋옵션의 내재가치 = Max\[(풋옵션의 행사가격 - 기초자산의 시장가격), 0\]

#### Extrinsic Value

옵션의 시간가치: 만기까지의 기간에서 기초 자산 가격의 변화에 따라 이익을 얻을 수 있는 가능성에 대한 가치를 의미, 이는 미래의
기초자산의 가격 변동에 따라 기대되는 프리미엄으로 해석 가능  

  - 시간 가치는 만기에 가까울수록 변동성이 작아져 감소  
  - 만기 때의 시간 가치는 0  
  - ATM, OTM 옵션에서는 권리 행사 시 얻을 수 있는 내재가치가 없으므로 시간 가치만 존재함

### Application

#### Put-Call Parity:

  - 콜옵션과 풋옵션 간에는 일정한 등가관계 성립
  - 같은 가격으로 행사하게 되는 call 가격과 put 가격은 동일한 가치를 가짐
  - Formula:
    ![c+Ke^{-rT}=p+S\_t](https://latex.codecogs.com/png.latex?c%2BKe%5E%7B-rT%7D%3Dp%2BS_t
    "c+Ke^{-rT}=p+S_t")  

### Option Pricing Models

  - Black-Scholes Model
  - Cox-Ross-Rubinstein Model(이항분포)
  - Monte Carlo Simulation

## Black-Scholes Model: Option Pricing for European Option

*Call option:
![c=S\_0N(d\_1)-Ke^{-rT}N(d\_2)](https://latex.codecogs.com/png.latex?c%3DS_0N%28d_1%29-Ke%5E%7B-rT%7DN%28d_2%29
"c=S_0N(d_1)-Ke^{-rT}N(d_2)")    
*Put option:
![p=Ke^{-rT}N(-d\_2)-S\_0N(-d\_1)](https://latex.codecogs.com/png.latex?p%3DKe%5E%7B-rT%7DN%28-d_2%29-S_0N%28-d_1%29
"p=Ke^{-rT}N(-d_2)-S_0N(-d_1)")    
where
![d\_1=\\frac{\\ln(S\_0/K)+(r+\\sigma^2/2)T}{\\sigma\\sqrt{T}}](https://latex.codecogs.com/png.latex?d_1%3D%5Cfrac%7B%5Cln%28S_0%2FK%29%2B%28r%2B%5Csigma%5E2%2F2%29T%7D%7B%5Csigma%5Csqrt%7BT%7D%7D
"d_1=\\frac{\\ln(S_0/K)+(r+\\sigma^2/2)T}{\\sigma\\sqrt{T}}")
   
![d\_2=\\frac{\\ln(S\_0/K)+(r-\\sigma^2/2)T}{\\sigma\\sqrt{T}}=d\_1-\\sigma\\sqrt{T}](https://latex.codecogs.com/png.latex?d_2%3D%5Cfrac%7B%5Cln%28S_0%2FK%29%2B%28r-%5Csigma%5E2%2F2%29T%7D%7B%5Csigma%5Csqrt%7BT%7D%7D%3Dd_1-%5Csigma%5Csqrt%7BT%7D
"d_2=\\frac{\\ln(S_0/K)+(r-\\sigma^2/2)T}{\\sigma\\sqrt{T}}=d_1-\\sigma\\sqrt{T}")
   
![N(d)=P(X\<d), \\textrm{where} X\\sim
N(0,1)](https://latex.codecogs.com/png.latex?N%28d%29%3DP%28X%3Cd%29%2C%20%5Ctextrm%7Bwhere%7D%20X%5Csim%20N%280%2C1%29
"N(d)=P(X\<d), \\textrm{where} X\\sim N(0,1)")  

p.s. European Option: 만기일에만 권리를 행사할 수 있음

### Premise

  - (안전자산) 안전자산의 수익률은 변화가 없는 ‘무위험 수익률’  
  - (랜덤워크) 기초자산가격의 순간 로그 수익률은 무한한 임의보행(Brownian
motion)

### Option Parameters

| Parameter                                                               | 설명                                                                                                        |
| ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| ![S](https://latex.codecogs.com/png.latex?S "S") 기초자산가격                 | \- 행사가격과 기초자산가격 간의 차이는 만기 시 옵션가격과 밀접한 관계 <br /> - 만기에는 내재가치가 남아 있거나 옵션가치가 0이 됨 <br /> - 옵션 가격 결정에 가장 큰 영향 |
| ![K](https://latex.codecogs.com/png.latex?K "K") 행사가격                   | \- 모든 옵션은 옵션을 행사할 때 적용되는 가격을 갖게 됨 <br /> - 다양한 행사가격을 두는 이유는 다양한 risk/reward 관계를 제공함으로써 선택 범위 확장           |
| ![T](https://latex.codecogs.com/png.latex?T "T") 잔존만기                   | \- 잔존만기가 길수록 옵션의 가치가 더 큼                                                                                  |
| ![r](https://latex.codecogs.com/png.latex?r "r") 이자율                    | \- 현물옵션의 경우 이자율 고려함(cost of carry) <br /> - put-call parity()에 영향끼침 <br /> - 금리가 올라갈 경우 콜옵션 가격 상승         |
| ![\\sigma](https://latex.codecogs.com/png.latex?%5Csigma "\\sigma") 변동성 | \- volatility는 불확실성의 양을 나타내는 표현법 <br /> - 내재변동성 vs 실현변동성 <br /> - 위험과 수익은 trade-off 관계                    |

``` r
s=280 # 기초자산 가격
k=280 # 행사가격
t=21/252 # 기간(연단위)
r=0.0354 # 연 이자율
sigma=0.2294 # 변동성(연 단위)

d1=(log(s/k)+(r+sigma^2/2)*t)/(sigma*sqrt(t))
d2=d1-sigma*sqrt(t)

call=s*pnorm(d1, mean=0, sd=1)-k*exp(-r*t)*pnorm(d2, mean=0, sd=1)
call
```

    ## [1] 7.804731

``` r
put=k*exp(-r*t)*pnorm(-d2, mean=0, sd=1)-s*pnorm(-d1, mean=0, sd=1)
put
```

    ## [1] 6.979948

## Pricing function

  - Call: position=1    
  - Put: position=2

<!-- end list -->

``` r
pricing=function(position,s,k,t,r,sigma){
  d1=(log(s/k)+(r+sigma^2/2)*t)/(sigma*sqrt(t))
  d2=d1-sigma*sqrt(t)
  # call: position=1
  if(position==1){
    result=s*pnorm(d1, mean=0, sd=1)-k*exp(-r*t)*pnorm(d2, mean=0, sd=1)
  }
  # put: position=2
  else{
    result=k*exp(-r*t)*pnorm(-d2, mean=0, sd=1)-s*pnorm(-d1, mean=0, sd=1)
  }
  return(result)
}
pricing(1, 100, 110, 21/252, 0.0354, 0.2294)
```

    ## [1] 0.2571818

## Sensitivity a.k.a Greeks

| Greeks                                                                    | Based on                                              | Formula                                                                                                                                                                                                 | Description                                                                                                                                            |
| ------------------------------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Delta ![\\delta](https://latex.codecogs.com/png.latex?%5Cdelta "\\delta") | ![S](https://latex.codecogs.com/png.latex?S "S") 기초자산 | ![\\delta=\\frac{\\partial f}{\\partial S}](https://latex.codecogs.com/png.latex?%5Cdelta%3D%5Cfrac%7B%5Cpartial%20f%7D%7B%5Cpartial%20S%7D "\\delta=\\frac{\\partial f}{\\partial S}")                 | \- 주가 1단위 변동 시 옵션 가격 변동 비율 <br /> - call: 0.00-1.00, put: -1.00-0.00                                                                                   |
| Gamma ![\\gamma](https://latex.codecogs.com/png.latex?%5Cgamma "\\gamma") | ![S](https://latex.codecogs.com/png.latex?S "S") 기초자산 | ![\\gamma=\\frac{\\partial^2 f}{\\partial S^2}](https://latex.codecogs.com/png.latex?%5Cgamma%3D%5Cfrac%7B%5Cpartial%5E2%20f%7D%7B%5Cpartial%20S%5E2%7D "\\gamma=\\frac{\\partial^2 f}{\\partial S^2}") | \- 기초자산 변동에 따른 델타의 변동 비율 <br /> - Gamma가 0.05, delta가 0.53일 때, 주가가 1단위 상승한다면 새로운 call delta는 0.58 <br /> - 옵션 매수는 long gamma(+), 옵션 매도는 short gamma(-) |
| Theta ![\\theta](https://latex.codecogs.com/png.latex?%5Ctheta "\\theta") | ![T](https://latex.codecogs.com/png.latex?T "T") 시간   | ![\\theta=\\frac{\\partial f}{\\partial T}](https://latex.codecogs.com/png.latex?%5Ctheta%3D%5Cfrac%7B%5Cpartial%20f%7D%7B%5Cpartial%20T%7D "\\theta=\\frac{\\partial f}{\\partial T}")                 | \- 1일 결과에 따른 옵션의 시간 가치 감소 <br /> - Theta가 0.2이고 콜 종가 $4.25이며 주가 변동 없다면 익일 개시가는 $4.05                                                                   |
| Vega ![\\nu](https://latex.codecogs.com/png.latex?%5Cnu "\\nu")           | ![v](https://latex.codecogs.com/png.latex?v "v") 변동성  | ![\\nu=\\frac{\\partial f}{\\partial \\sigma}](https://latex.codecogs.com/png.latex?%5Cnu%3D%5Cfrac%7B%5Cpartial%20f%7D%7B%5Cpartial%20%5Csigma%7D "\\nu=\\frac{\\partial f}{\\partial \\sigma}")       | \- 변동성 1%에 대한 옵션가격 변동 <br /> - Vega 0.25, 콜 이론가 $2.50이면 변동성 1% 상승 시 이론가 $2.75로 변동                                                                      |
| Rho ![\\rho](https://latex.codecogs.com/png.latex?%5Crho "\\rho")         | ![r](https://latex.codecogs.com/png.latex?r "r") 이자율  | ![\\rho=\\frac{\\partial f}{\\partial r}](https://latex.codecogs.com/png.latex?%5Crho%3D%5Cfrac%7B%5Cpartial%20f%7D%7B%5Cpartial%20r%7D "\\rho=\\frac{\\partial f}{\\partial r}")                       | \- 시장이자율 1% 변동에 대한 옵션가격 변동 <br /> - Rho 0.06, 콜 이론가 $3.50이면 금리 1% 상승 시 콜 가격 $3.56                                                                      |
