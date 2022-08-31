# FinanceDataReader
FinanceDateReader project with Python




FUNCTION 1 : KOSPI에 상장된 종목을 df_KOSPI 코스닥에 상장된 종목을 df_KOSDAQ라는 데이터프레임으로 각각 만든다. StockListing메소드를 사용하면 된다. 위 두 데이터 프레임은 ['Symbol', 'Name', 'Sector', 'Industry']을 칼럼으로 가지고 있으며 Symbol 변수가 위에서 지칭한 여섯자리 코드를 의미한다. 
	KOSPI와 KOSDAQ 그룹에 대해서 각각 몇 개의 상장사가 있는지 확인한다. 
	KOSPI라는 list로 df_KOSPI의 Symbol값들을 저장하고, KOSDAQ이라는 이름으로 df_KOSPI의 Symbol값들을 저장한다. 

 
파이썬의 finance-datareader 라이브러리를 import 했다. fdr.StockLising 메소드와 ‘KOSPI’, ‘KOSDAQ’ 인자를 이용해 df_KOSPI, df_KOSDAQ 데이터 프레임을 만들었다. 그 뒤, df_KOSPI 와 df_KOSDAQ 의 Symbol 값들을 각각 KOSPI, KOSDAQ 이라는 list에 저장했다. 위 코드와 같이 출력한 결과는 다음과 같다. 
 
List들이 정상적으로 저장이 되었고, KOSPI와 KOSDAQ은 각각 993, 1416개의 상장사가 있음을 알 수가 있다.
FUNCTION2 : 삼성전자에 대한 주식 종목 코드를 df_KOSPI에서 검색하거나 간단히 검색엔진을 사용하여 검색한후  fdr.DataReader 메소드를 사용하여 자료를 받은후에 각 날짜에 대한 일별 주가 수익률을 꺽은선 그래프 형태로 그려본다.  

 
검색 엔진을 이용하면, 삼성전자의 주식 종목 코드는 ‘005930’ 이란 것을 알 수 있다. 2018년도에서의 일별 주가 수익률을 얻기 위해, 2018년도에서의 삼성전자의 정보를 담은 데이터 프레임을 만든다. ‘Change’가 수익률을 의미하므로, plot 메소드를 이용해, df[‘Change’] 리스트를 꺾은 선 그래프로 나타내어 준다. X 축은 Date, Y축은 Change로 label 하였다. 실행 결과는 아래와 같다.
 
정상적으로 출력되었음을 알 수 있다, 
FUNTION3 : KOSDAQ과 KOSPI에서 거래되는 전체 기업들에 대해서 각각 일별 수익률의 연간 평균과 표준편차를 구해본다. 전체기업들에 대해 평균수익률-표준편차의 산포도를 그려본다. 이러한 산포도를 KOSPI에 상장된 기업과 KOSDAQ에 상장된 기업에 대해 구분해서 각각 산포도를 그려본다. 이 두 변수간의 양의 관계가 있는가? 평균수익률은 일종의 사람들이 기대하는 수익률과 밀접한 관련이 있으며, 주가수익률의 표준편차가 클수록 일반적으로 수익률의 리스크(위험도)가 크다고 생각한다. 
 
 
각각 KOSPI, KOSDAQ의 평균 수익률과 표준편차의 값을 저장해 둘 빈 리스트를 만들어 둔다. for 문을 이용해 KOSPI 내부의 기업 코드들에 대해 데이터 프레임을 만든다. 만약 만들어진 데이터 프레임이 비어 있는 데이터 프레임이면 continue 문을 이용해 다음 기업 코드로 넘어간다. 만약 empty 인 데이터 프레임이 아니라면, dropna 값을 이용해 결측값을 처리힌다. 그 뒤에, 리스트 means_of_KOSPI와 sd_of_KOSPI에 각각의 데이터 프레임에 존재하는 2018년도의 수익률 리스트에 대해, 평균과 표준편차 값을 append 해준다. Statistics 라이브러리를 import 해서 mean 과 stdev 메소드를 이용해 평균과 표준편차 값을 구했다. KOSDAQ에 대해서도 같은 과정을 반복해, means_of_KOSDAQ과 sd_of_KOSDAQ에 평균과 표준편차의 값을 append해주었다. Subplot을 이용해 2*2의 공간을 만들고 KOSPI와 KOSDAQ을 각각 배치해 주었다. 평균 수익률 – 표준편차의 산포도를 그려야 하므로, scatter메소드를 이용했고, X좌표에는 means_of_ ~ , Y좌표에는 sd_of_ ~ 를 인자로 넘겨주었다. 산포도는 다음과 같다. 
 
왼쪽에서부터 KOSPI, KOSDAQ의 값들에 해당하는 평균 수익률 – 표준편차의 산포도이다. 평균은 대체로 0.00 에서 크게 벗어나지 않았음을 알 수 있고, 표준편차의 값이 KOSPI의 것이 KOSDAQ의 것보다 대체로 큰 것을 확인 할 수 있다. 일반적으로 수익률의 리스크가 크다고 생각할 수 있는 부분이다. 
FUNCTION4 : 회귀분석식을 한국시장에서 거래되는 모든 주식에 각각 α와 β를 Fitting 한다. 
	우리의 target 변수는 개별 주식의 일별수익률(change) – 무위험 수익률(0.03/365)이며
	feature는 KOSPI200의 일별수익률(change)- 무위험 수익률(0.03/365)이다.
	모든 주식에 대해서 리스크의 측도 β를 각각 구해보고, 평균 수익률과의 산포도를 그려보아라. 양의 관계를 발견할수 있는가?.
	3의 분석을 KOSPI 시장과 KOSDAQ 시장을 분리해서 시행한다. 
   
 
Target 변수는 개별 주식의 일별 수익률 – 무위험 수익률이다. 무뮈험 수익률 rf를 0.03/365 로 두었다. 2018년도에 해당하는 KOSPI200의 일별 수익률에서, rf를 빼 feature의 값들을 담은 list, feat를 생성했다. 그 다음은 KOSPI의 기업 코드들에 대해서 분석을 한다. Target 변수는 개별 주식의 일별 수익률 – 무위험 수익률 이므로, 각 주식 마다 target 리스트에 해당 값을 append해준다. 그 뒤, R_i^e=α+βR_M^e 에서 α와 β를 Fitting를 하는 과정에서 target와 feat의 리스트의 길이는 같아야 한다. 따라서, feat과 target의 길이가 같을 때 만 np.polyfit 메소드를 이용해 fit_a_KOSPI에 α 값을, fit_b_KOSPI 에 β 값을 append해 주었다. Feat과 target의 길이가 다른 경우가 존재하지만, 그 경우를 제하더라도 fit하기에 충분히 많은 경우라 판단했다. 또, 평균 수익률과 β 의 산포도를 그려야 하므로, feat와 target의 길이가 같았던 시점, 즉 fitting 과정에 관여되었던 기업코드 값들을 x_axis_KOSPI에 따로 append 해준다. 후에 x_axis_KOSPI 의 기업코드들을 이용해 means_of_KOSPI 에 기업별 평균 수익률을 append해준다. KOSDAQ의 경우도 동일하다. Subplot을 이용해 2*1의 공간을 할당한 뒤, 상단에 KOSPI의 평균 수익률, 측도의 산포도, 하단에 KOSDAQ의 평균 수익률, 측도의 산포도를 표시하게 하였다. 자료의 개수가 많으므로 점의 크기를 s=1인자를 이용해 작게 만들었다. 산포도는 다음과 같다. 측도의 산포는 대체로 유사하나, 평균 수익률에서 KOSDAQ이 KOSPI보다 더 퍼져 있음을 알 수 있다. KOSPI는 선형관계가 존재한다는 강한 증거를 가지고 있다.
 

FUNCTION 5 : Jegadeesh 와 Titman이 1993년에 작성한 논문은 미국 주식시장에서 흥미로운 사실을 발견한다. 즉 과거 수익률이 우수한 종목을 매수하고, 수익률이 부진한 종목을 매도할 경우, 3에서 12개월 정도 보유 기간에서 유의미한 수익률을 기록함을 확인하였다. 
이를 한국 시장에 있어서도 잘 적용되는지 간단한 형태로 확인을 해보고자 한다. 
	전체 주식에 대해서 1월 2일과 6월 29일까지 누적 수익률을 구한다 이 누적수익률은 (6월 29일 종가-1월 2일 종가)/ 1월 2일 종가로 계산한다. 
	이 전체 수익률을 바탕으로 수익률 상위 – 하위까지 10개 그룹으로 구분한다. 
	각 기업에 대해 7월 2일부터 9월 28일 (3개월 누적 수익률) 및 7월 2일부터 12월 28일까지의 누적수익률 (6개월 누적 수익률)을 1번과 동일한 방법으로 구한다.
	1-6월부터 누적 수익률 10개 기업 그룹별로 3개월 그룹수익률의 평균 및 6개월 누적 수익률의 평균값을 계산하여 막대그래프 형식으로 표시한다.
	KOSPI와 KOSDAQ으로 상장 기업그룹을 나누어 1-4번까지 작업을 반복한다.  
A5.
         


Q5에서 주어진 누적 수익률 공식을 이용해, 1월 2일에서부터 6월 29일까지의 누적 수익률을 먼저 구해야 한다. 년도는 2018년도를 사용하기로 한다. KOSPI의 기업 코드들을 이용해 각각의 날짜의 데이터프레임을 가져와 df_for_0629_KOSPI, df_for_0102_KOSPI에 저장한다. 이 데이터프레임 들에는 간혹 ‘Change’ column이 없는 경우가 있다. 따라서 bool문을 이용해 ‘Change’가 있는 데이터 프레임에 대해서만 종가 검색을 실시한다. if문을 통과하면, close_0102_KOSPI 와 close_0629_KOSPI 에 각각 날짜의 종가 값을 저장한다. 
여기서 ‘Close’의 type은 Series이다. 따라서 바로 연산할 수 없으며, 빈 값인지 아닌지 확인을 먼저 거친 후에 float형으로 캐스팅 해서 cumx 에 저장한다. 이후에, dictionary를 이용해 cumx 값을 저장한다. key값은 기업코드, value는 cumx 이다. 모든 정리가 끝나면, dict_of_KOSPI들의 value들의 값에 대해서 오름차순으로 정렬한 후, groups_of_KOSPI 에 기업코드 값들을 10분할 후 저장해 이중 리스트 구조를 만든다. 
다음 이중 for문을 이용해, 모든 기업코드들의 값에 대해 7월 2일, 9월 28일, 12월 28일에 대한 데이터 프레임들을 구한다. 위와 같은 방법으로 ‘Close’값들을 가져와 누적 수익률을 계산해 list_of_3month_change_KOSPI, list_of_6month_change_KOSPI 에 append 한다. 위 두 리스트 또한 10분할 해 groups_of_3monthchange_KOSPI, groups_of_6monthchange_KOSPI 로 나누어 준다. 두 이중 리스트에 대해서, [0][i]위치에 있는 리스트들을 statistics.mean 메소드를 이용해 평균값으로 대체해준다. KOSDAQ에 대해서도 위의 과정들을 동일하게 수행해준다. 
Visualization에 대해서는 x_values1, x_values2를 이용해 3개월치 누적수익률과 6개월치 누적수익률의 막대그래프를 연속해 표시할 수 있도록 한다. lb는 인덱스 명이다. 인덱스들을 알맞은 위치에 놓기 위해서 plt.xticks 메소드를 이용한다. plt.bar 메소드를 이용해 3개월치와 6개월치 누적수익률을 표기한다. plt.subplot를 이용해, 상단에는 KOSPI의 자료를, 하단에는 KOSDAQ의 자료를 위치시켰다. 프로그램의 실행 결과는 다음과 같다. 
  
1st부터 하위, 10th까지 상위 그룹들이다. 미국 주식시장과는 달리, 3개월에서 12개월 정도의 기간에서 유의미한 수익률을 기록하지 못했다. 

