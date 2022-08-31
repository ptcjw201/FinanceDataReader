# FinanceDataReader
FinanceDateReader project with Python




### FUNCTION 1 : KOSPI에 상장된 종목을 df_KOSPI 코스닥에 상장된 종목을 df_KOSDAQ라는 데이터프레임으로 각각 만든다. StockListing메소드를 사용하면 된다. 위 두 데이터 프레임은 ['Symbol', 'Name', 'Sector', 'Industry']을 칼럼으로 가지고 있으며 Symbol 변수가 위에서 지칭한 여섯자리 코드를 의미한다. 
	KOSPI와 KOSDAQ 그룹에 대해서 각각 몇 개의 상장사가 있는지 확인한다. 
	KOSPI라는 list로 df_KOSPI의 Symbol값들을 저장하고, KOSDAQ이라는 이름으로 df_KOSPI의 Symbol값들을 저장한다.   
	
파이썬의 finance-datareader 라이브러리를 import 했다. fdr.StockLising 메소드와 ‘KOSPI’, ‘KOSDAQ’ 인자를 이용해 df_KOSPI, df_KOSDAQ 데이터 프레임을 만들었다. 그 뒤, df_KOSPI 와 df_KOSDAQ 의 Symbol 값들을 각각 KOSPI, KOSDAQ 이라는 list에 저장했다. 위 코드와 같이 출력한 결과는 다음과 같다. 
 
 ![image](https://user-images.githubusercontent.com/31716679/187679185-60e878c7-816f-4d5c-8ec4-c5b95b341cf5.png)

List들이 정상적으로 저장이 되었고, KOSPI와 KOSDAQ은 각각 993, 1416개의 상장사가 있음을 알 수가 있다.

<br/><br/>

### FUNCTION2 : 삼성전자에 대한 주식 종목 코드를 df_KOSPI에서 검색하거나 간단히 검색엔진을 사용하여 검색한후  fdr.DataReader 메소드를 사용하여 자료를 받은후에 각 날짜에 대한 일별 주가 수익률을 꺽은선 그래프 형태로 그려본다.  

 ![image](https://user-images.githubusercontent.com/31716679/187679289-122d77e9-2b27-4242-beb3-3903aa8bb3b1.png)

검색 엔진을 이용하면, 삼성전자의 주식 종목 코드는 ‘005930’ 이란 것을 알 수 있다. 
2018년도에서의 일별 주가 수익률을 얻기 위해, 2018년도에서의 삼성전자의 정보를 담은 데이터 프레임을 만든다. 
‘Change’가 수익률을 의미하므로, plot 메소드를 이용해, df[‘Change’] 리스트를 꺾은 선 그래프로 나타내어 준다. 
X 축은 Date, Y축은 Change로 label 하였다. 실행 결과는 아래와 같다.
 
 ![image](https://user-images.githubusercontent.com/31716679/187679304-9a63619c-7f04-49ad-a8fb-edec24f203ab.png)  
<br/><br/>

### FUNTION3 : KOSDAQ과 KOSPI에서 거래되는 전체 기업들에 대해서 각각 일별 수익률의 연간 평균과 표준편차를 구해본다. 전체기업들에 대해 평균수익률-표준편차의 산포도를 그려본다.
 
![image](https://user-images.githubusercontent.com/31716679/187679438-422a038c-7f66-4f36-9947-d1f6a8b21797.png)
![image](https://user-images.githubusercontent.com/31716679/187679453-a9028b29-58c4-4c06-98e5-eb4d9ff96fd7.png)
 
왼쪽에서부터 KOSPI, KOSDAQ의 값들에 해당하는 평균 수익률 – 표준편차의 산포도이다. 평균은 대체로 0.00 에서 크게 벗어나지 않았음을 알 수 있고, 표준편차의 값이 KOSPI의 것이 KOSDAQ의 것보다 대체로 큰 것을 확인 할 수 있다. 일반적으로 수익률의 리스크가 크다고 생각할 수 있다. 

![image](https://user-images.githubusercontent.com/31716679/187679659-58b562d1-1acf-4338-8c3d-3803a833ee70.png)  
<br/><br/>

### FUNCTION4 : 회귀분석식을 한국시장에서 거래되는 모든 주식에 각각 α와 β를 Fitting 한다.
   

상단에 KOSPI의 평균 수익률, 측도의 산포도, 하단에 KOSDAQ의 평균 수익률, 측도의 산포도를 표시하게 하였다

![image](https://user-images.githubusercontent.com/31716679/187679902-28570d77-c124-479b-8c25-340f8f0966a9.png)

측도의 산포는 대체로 유사하나, 평균 수익률에서 KOSDAQ이 KOSPI보다 더 퍼져 있음을 알 수 있다. KOSPI는 선형관계가 존재한다는 강한 증거를 가지고 있다.
 
<br/><br/>
### FUNCTION 5 : Jegadeesh 와 Titman이 1993년에 작성한 논문은 미국 주식시장에서 흥미로운 사실을 발견한다. 즉 과거 수익률이 우수한 종목을 매수하고, 수익률이 부진한 종목을 매도할 경우, 3에서 12개월 정도 보유 기간에서 유의미한 수익률을 기록함을 확인하였다. 

3개월치 누적수익률과 6개월치 누적수익률의 막대그래프를 연속해 표시할 수 있도록 한다. 상단에는 KOSPI의 자료를, 하단에는 KOSDAQ의 자료를 위치시켰다. 
프로그램의 실행 결과는 다음과 같다. 

![image](https://user-images.githubusercontent.com/31716679/187680287-47a208aa-859b-4496-a167-1533820e436c.png)


1st부터 하위, 10th까지 상위 그룹들이다. 미국 주식시장과는 달리, 3개월에서 12개월 정도의 기간에서 유의미한 수익률을 기록하지 못했다. 

