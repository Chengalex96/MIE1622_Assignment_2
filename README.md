# MIE1622_Assignment_2
 
The purpose of this assignment is to compare computational investment strategies based on selecting portfolios with equal risk contributions and using robust mean-variance optimization.

Three new strategies were added to assignment 1:

1. "Buy and hold" strategy
2. "Equally weighted" (also known as "1/n") portfolio strategy
3. "Minimum variance" portfolio strategy
4. "Maximum Sharpe ratio" portfolio strategy
5. "Equal risk contributions" portfolio strategy
6. "Leveraged equal risk contributions" portfolio strategy
7. "Robust mean-variance optimization" portfolio strategy

**Rounding procedure:** After determining the optimal weight and determining the number of stocks in the portfolio, we use the numpy round function to round each stock to the nearest integer. We run a while loop, in which in the first run, if there isn’t enough cash in the account only those units that were rounded up will go down by 1. If there still isn’t enough account, we overestimate and decrease all stocks by 1 (stocks that are not 0). We then add a unit to each stock that should be rounded up until we
go through all the stocks. 

**Equal risk contributions portfolio strategy**: compute a portfolio that has equal risk contributions to the standard deviation for each period and re-balance accordingly. You can use the IPOPT example from the lecture notes, but you need to compute the gradient of the objective function yourself (to validate your gradient computations you may use nite differences method).

**Leveraged equal risk contributions portfolio strategy**: take a long 200% position in equal risk contributions portfolio and short risk-free asset for each period and re-balance accordingly. You do not have to include a risk-free asset as an additional asset when calculating optimal positions. Just make sure that you subtract the amount borrowed when calculating portfolio value in a similar way as you do for transaction cost at each time period.

The initial shares in the portfolio in period 1 have been doubled (200% long position), in which the portfolio value calculation considers the borrowed risk-free asset by
subtracting the borrowed amount (with compounded interest) from the value of the portfolio. This allows the available risk-free asset to be considered as additional capital present in the investment strategy. 

**Robust mean-variance optimization portfolio strategy**: compute a robust mean-variance portfolio for each period and re-balance accordingly. You can use the CPLEX example from the lecture notes, but you need to select target risk estimation error and target return according to your preferences as an investor (provide justication of your choices).

From the mean-variance optimization, we can observe that low variations in expected returns and standard deviations can lead to drastic changes in weight allocations. We want to increase the stability by considering the estimation error within the optimization process.

**Target Risk Estimation Error:** Used the 1/n portfolio as the target return estimation error. This is a rough general band, if we were to choose it tighter, we may not get a solution to the optimization.

**Target Portfolio Return:** Used the weights of the minimum variance strategy and calculated the return. This must be greater than the return given by the mean-variance portfolio.

Objectives: Minimize the variance of the portfolio return, maximize the expected portfolio return, and minimize the portfolio return estimation error. We also wanted to compare this robust strategy with a non stable strategy such as the minimum variance strategy.

Constraints: Short selling of assets is not allowed and sum of assets weights must be equal to 1.

**Testing the Portfolios for 2020 and 2021 data**

Period 1: start date 01/02/2020, end date 02/28/2020
  Strategy "Buy and Hold", value begin = $ 1000013.00, value end = $ 893956.82
  Strategy "Equally Weighted Portfolio", value begin = $ 990881.79, value end = $ 892364.23
  Strategy "Mininum Variance Portfolio", value begin = $ 992756.22, value end = $ 915849.88
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 990063.46, value end = $ 922016.34
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 991597.39, value end = $ 898259.85
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 979011.20, value end = $ 792347.88
  Strategy "Robust Optimization Portfolio", value begin = $ 992167.76, value end = $ 917120.45

Period 2: start date 03/02/2020, end date 04/30/2020
  Strategy "Buy and Hold", value begin = $ 945076.08, value end = $ 949228.39
  Strategy "Equally Weighted Portfolio", value begin = $ 930690.93, value end = $ 862192.32
  Strategy "Mininum Variance Portfolio", value begin = $ 955714.76, value end = $ 850652.49
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 961925.93, value end = $ 1017080.69
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 937510.50, value end = $ 852698.61
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 866680.69, value end = $ 697055.16
  Strategy "Robust Optimization Portfolio", value begin = $ 958934.78, value end = $ 864852.26

Period 3: start date 05/01/2020, end date 06/30/2020
  Strategy "Buy and Hold", value begin = $ 937916.75, value end = $ 913415.30
  Strategy "Equally Weighted Portfolio", value begin = $ 830750.85, value end = $ 933850.30
  Strategy "Mininum Variance Portfolio", value begin = $ 826383.68, value end = $ 853443.62
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 974233.42, value end = $ 1175637.72
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 822445.39, value end = $ 917591.56
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 632356.56, value end = $ 823407.35
  Strategy "Robust Optimization Portfolio", value begin = $ 836233.43, value end = $ 916760.26

Period 4: start date 07/01/2020, end date 08/31/2020
  Strategy "Buy and Hold", value begin = $ 905419.70, value end = $ 994693.42
  Strategy "Equally Weighted Portfolio", value begin = $ 927447.26, value end = $ 1060445.57
  Strategy "Mininum Variance Portfolio", value begin = $ 855748.90, value end = $ 980875.15
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 1219489.44, value end = $ 1607444.05
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 913866.92, value end = $ 1053737.89
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 812039.88, value end = $ 1091706.41
  Strategy "Robust Optimization Portfolio", value begin = $ 923472.75, value end = $ 1051063.93

Period 5: start date 09/01/2020, end date 10/30/2020
  Strategy "Buy and Hold", value begin = $ 993194.54, value end = $ 971914.18
  Strategy "Equally Weighted Portfolio", value begin = $ 1068060.61, value end = $ 998834.67
  Strategy "Mininum Variance Portfolio", value begin = $ 982627.60, value end = $ 942075.73
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 1641529.42, value end = $ 1554592.34
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1061628.91, value end = $ 996450.02
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1103258.59, value end = $ 972890.89
  Strategy "Robust Optimization Portfolio", value begin = $ 1055917.97, value end = $ 1011280.01

Period 6: start date 11/02/2020, end date 12/31/2020
  Strategy "Buy and Hold", value begin = $ 983801.02, value end = $ 1004435.74
  Strategy "Equally Weighted Portfolio", value begin = $ 1007654.20, value end = $ 1194038.48
  Strategy "Mininum Variance Portfolio", value begin = $ 950551.92, value end = $ 1005253.01
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 1553235.25, value end = $ 1790601.57
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1004646.38, value end = $ 1180372.67
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 985020.65, value end = $ 1336413.02
  Strategy "Robust Optimization Portfolio", value begin = $ 1019121.50, value end = $ 1116589.15

Period 7: start date 01/04/2021, end date 02/26/2021
  Strategy "Buy and Hold", value begin = $ 1005601.39, value end = $ 956244.08
  Strategy "Equally Weighted Portfolio", value begin = $ 1180451.55, value end = $ 1266829.54
  Strategy "Mininum Variance Portfolio", value begin = $ 1003278.97, value end = $ 974346.31
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 1738720.52, value end = $ 1854192.65
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1167346.23, value end = $ 1220406.48
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1306087.11, value end = $ 1412116.37
  Strategy "Robust Optimization Portfolio", value begin = $ 1110415.44, value end = $ 1107893.25

Period 8: start date 03/01/2021, end date 04/30/2021
  Strategy "Buy and Hold", value begin = $ 957791.35, value end = $ 1019731.32
  Strategy "Equally Weighted Portfolio", value begin = $ 1297169.82, value end = $ 1398708.51
  Strategy "Mininum Variance Portfolio", value begin = $ 974664.73, value end = $ 1087408.46
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 1902630.85, value end = $ 2061846.72
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1244376.30, value end = $ 1355988.27
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1455770.61, value end = $ 1679283.36
  Strategy "Robust Optimization Portfolio", value begin = $ 1116908.34, value end = $ 1235677.06

Period 9: start date 05/03/2021, end date 06/30/2021
  Strategy "Buy and Hold", value begin = $ 1022204.61, value end = $ 987842.85
  Strategy "Equally Weighted Portfolio", value begin = $ 1397485.37, value end = $ 1459062.86
  Strategy "Mininum Variance Portfolio", value begin = $ 1087214.65, value end = $ 1076067.43
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 2053343.91, value end = $ 2015834.59
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1354832.83, value end = $ 1385002.90
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1672742.89, value end = $ 1733211.39
  Strategy "Robust Optimization Portfolio", value begin = $ 1234354.11, value end = $ 1231777.45

Period 10: start date 07/01/2021, end date 08/31/2021
  Strategy "Buy and Hold", value begin = $ 993283.49, value end = $ 975250.19
  Strategy "Equally Weighted Portfolio", value begin = $ 1466470.24, value end = $ 1517619.10
  Strategy "Mininum Variance Portfolio", value begin = $ 1076109.76, value end = $ 1085950.69
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 2014835.81, value end = $ 2120423.56
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1391221.46, value end = $ 1443019.64
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1741350.23, value end = $ 1845030.40
  Strategy "Robust Optimization Portfolio", value begin = $ 1234383.55, value end = $ 1270239.21

Period 11: start date 09/01/2021, end date 10/29/2021
  Strategy "Buy and Hold", value begin = $ 974520.08, value end = $ 949068.41
  Strategy "Equally Weighted Portfolio", value begin = $ 1513369.24, value end = $ 1563152.36
  Strategy "Mininum Variance Portfolio", value begin = $ 1080423.44, value end = $ 1056572.30
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 2101160.93, value end = $ 2143092.19
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1437078.64, value end = $ 1452054.31
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1828785.22, value end = $ 1858717.46
  Strategy "Robust Optimization Portfolio", value begin = $ 1262258.25, value end = $ 1234728.98

Period 12: start date 11/01/2021, end date 12/31/2021
  Strategy "Buy and Hold", value begin = $ 951350.41, value end = $ 932471.35
  Strategy "Equally Weighted Portfolio", value begin = $ 1584445.60, value end = $ 1646232.49
  Strategy "Mininum Variance Portfolio", value begin = $ 1053826.83, value end = $ 1047867.41
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 2112459.87, value end = $ 2216770.75
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 1462333.67, value end = $ 1515001.16
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 1874911.73, value end = $ 1980093.88
  Strategy "Robust Optimization Portfolio", value begin = $ 1228963.76, value end = $ 1256306.78

![image](https://github.com/user-attachments/assets/31fc08a8-73ad-4dd5-bf17-76dbe748d697)

This chart illustrates the daily value of the portfolio for each trading strategy over the years 2020 and 2021 using the daily prices. This will be discussed further below. The main takeaways are that maximum Sharpe’s ratio and leverage ERC do very well, many of these strategies start to pick up in value after 10/30/2020. 

![image](https://github.com/user-attachments/assets/cf1061ca-a975-401a-b8f8-e97adf5624a3)

The maximum drawdown is the maximum observed loss from a peak to a trough of a portfolio before a new peak is attained. It indicates the downside risk of a specified time period. We can find this using a rolling window for each period. We can see that the leveraged equal risk contribution has a much larger MDD since it’s investing more capital into the stocks. We can observe that the high returns strategies such as the maximum Sharpe ratio and the leveraged ERC have the highest risk (largest MDD).

![image](https://github.com/user-attachments/assets/8d3c2287-6630-4ce0-bfad-b37fe9a19b07)

This chart illustrates the weight allocation of each stock in the Minimum variance portfolio for the 12 trading periods. We can observe that the Verizon (VZ) stock dominates the portfolio through the 12 trading periods. This stock offers the lowest variance among all the stocks. (Assume trading period 0 is period 1).

![image](https://github.com/user-attachments/assets/bfc9d471-5fef-4166-814f-8b742736737f)

This chart illustrates the weight allocation of each stock in the Maximum Sharpe’s Ratio portfolio for the 12 trading periods. We can observe that there are much more fluctuations in the weight allocation of the stocks. This could be a larger issue if there are larger trading costs. 

![image](https://github.com/user-attachments/assets/0473b9d0-8bf2-4641-b8c6-2876962beb56)

This chart illustrates the weight allocation of each stock in the Robust Mean-Variance Optimization portfolio for the 12 trading periods. We can observe that the Verizon (VZ) stock still dominates the portfolio through the 12 trading periods similarly to minimum variance. We can observe that the stocks invested are more diversified than the Minimum Variance and the Maximum Sharpe Ratio strategy but also reduced the amount of trading (typically the same assets between periods), this is beneficial if trading costs are high. 

![image](https://github.com/user-attachments/assets/a82311d9-7a6c-4992-9858-aca61c95a852)

![image](https://github.com/user-attachments/assets/b000707d-ae12-4110-9406-4165fe97a766)

We could see that the maximum Sharpe ratio strategy has outperformed the other six methods over the 12 trading periods (2 years) in terms of portfolio value. The leveraged equal risk contribution strategy had the second highest portfolio value in which it observed the largest loss in the first few months and then started to rapidly increase its value after the second year. From the MDD graph and what we will see in the next two sections (recession periods), leveraging is risky, and need to be careful how we use it.
We can observe that the simple equally weighted strategy did well, seeing the third highest portfolio value which performed better than the equal risk contribution strategy came in fourth place. Our robust mean-variance strategy had the fifth highest and did better than the minimum variance strategy. Lastly is the buy-and-hold strategy. Thus, I would still select the maximum Sharpe ratio portfolio to manage my portfolio from the year 2020-2021. Sharpe ratio allows us to quantify and optimize the return per unit risk. We can observe that there are many more fluctuations among the weight allocation of the stocks in the Maximum Sharpe ratio strategy so this strategy may not be feasible if there are larger trading costs (Currently it is 0.5%). Taking large risks as with using the maximum Sharpe ratio is the best strategy in times of non-crisis nonrecession periods.

**Test Data for 2008:**

Period 1: start date 01/02/2008, end date 02/29/2008
  Strategy "Buy and Hold", value begin = $ 385097.15, value end = $ 325918.34
  Strategy "Equally Weighted Portfolio", value begin = $ 381647.53, value end = $ 326938.14
  Strategy "Mininum Variance Portfolio", value begin = $ 383268.36, value end = $ 327358.28
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 381265.54, value end = $ 332652.59
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 381846.82, value end = $ 329299.76
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 375707.93, value end = $ 270599.90
  Strategy "Robust Optimization Portfolio", value begin = $ 382274.61, value end = $ 332192.51

Period 2: start date 03/03/2008, end date 04/30/2008
  Strategy "Buy and Hold", value begin = $ 325807.08, value end = $ 349997.20
  Strategy "Equally Weighted Portfolio", value begin = $ 322065.15, value end = $ 354843.42
  Strategy "Mininum Variance Portfolio", value begin = $ 322920.70, value end = $ 366009.61
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 325785.77, value end = $ 344234.61
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 324469.25, value end = $ 361346.72
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 258023.51, value end = $ 331891.79
  Strategy "Robust Optimization Portfolio", value begin = $ 328178.03, value end = $ 362298.38

Period 3: start date 05/01/2008, end date 06/30/2008
  Strategy "Buy and Hold", value begin = $ 357929.49, value end = $ 322881.56
  Strategy "Equally Weighted Portfolio", value begin = $ 366452.44, value end = $ 308979.57
  Strategy "Mininum Variance Portfolio", value begin = $ 373420.44, value end = $ 351741.54
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 349024.91, value end = $ 313033.39
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 372138.70, value end = $ 322669.61
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 350563.60, value end = $ 251678.11
  Strategy "Robust Optimization Portfolio", value begin = $ 370781.52, value end = $ 340331.75

Period 4: start date 07/01/2008, end date 08/29/2008
  Strategy "Buy and Hold", value begin = $ 324349.75, value end = $ 326489.53
  Strategy "Equally Weighted Portfolio", value begin = $ 309434.67, value end = $ 315913.44
  Strategy "Mininum Variance Portfolio", value begin = $ 352084.80, value end = $ 356555.45
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 325404.17, value end = $ 315390.45
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 322317.70, value end = $ 326455.12
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 248011.28, value end = $ 256279.71
  Strategy "Robust Optimization Portfolio", value begin = $ 338726.80, value end = $ 340123.74

Period 5: start date 09/02/2008, end date 10/31/2008
  Strategy "Buy and Hold", value begin = $ 333252.73, value end = $ 274022.75
  Strategy "Equally Weighted Portfolio", value begin = $ 316692.21, value end = $ 231375.31
  Strategy "Mininum Variance Portfolio", value begin = $ 348646.41, value end = $ 269323.05
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 306616.50, value end = $ 229459.58
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 326213.86, value end = $ 241964.43
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 252821.60, value end = $ 84276.55
  Strategy "Robust Optimization Portfolio", value begin = $ 335384.90, value end = $ 259093.31

Period 6: start date 11/03/2008, end date 12/31/2008
  Strategy "Buy and Hold", value begin = $ 282342.11, value end = $ 305967.56
  Strategy "Equally Weighted Portfolio", value begin = $ 229962.96, value end = $ 198775.23
  Strategy "Mininum Variance Portfolio", value begin = $ 269733.03, value end = $ 248523.41
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 226771.37, value end = $ 175554.09
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 241112.92, value end = $ 212148.44
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 79583.36, value end = $ 21514.44
  Strategy "Robust Optimization Portfolio", value begin = $ 259965.10, value end = $ 241328.31

Period 7: start date 01/02/2009, end date 02/27/2009
  Strategy "Buy and Hold", value begin = $ 313366.90, value end = $ 258275.19
  Strategy "Equally Weighted Portfolio", value begin = $ 207261.94, value end = $ 169845.60
  Strategy "Mininum Variance Portfolio", value begin = $ 256572.57, value end = $ 244388.15
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 174923.22, value end = $ 145630.88
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 221021.22, value end = $ 188701.87
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 36265.90, value end = $ -28379.23
  Strategy "Robust Optimization Portfolio", value begin = $ 249412.90, value end = $ 226684.65

Period 8: start date 03/02/2009, end date 04/30/2009
  Strategy "Buy and Hold", value begin = $ 248688.22, value end = $ 286368.72
  Strategy "Equally Weighted Portfolio", value begin = $ 161619.15, value end = $ 259939.51
  Strategy "Mininum Variance Portfolio", value begin = $ 234752.02, value end = $ 320581.66
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 138601.74, value end = $ 180660.31
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 180804.55, value end = $ 271282.28
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ -47209.48, value end = $ 133623.58
  Strategy "Robust Optimization Portfolio", value begin = $ 218590.98, value end = $ 298521.05

Period 9: start date 05/01/2009, end date 06/30/2009
  Strategy "Buy and Hold", value begin = $ 287805.37, value end = $ 285824.08
  Strategy "Equally Weighted Portfolio", value begin = $ 259507.31, value end = $ 273156.85
  Strategy "Mininum Variance Portfolio", value begin = $ 318011.44, value end = $ 321342.79
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 179564.68, value end = $ 185441.09
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 270794.80, value end = $ 281310.14
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 129584.01, value end = $ 150649.69
  Strategy "Robust Optimization Portfolio", value begin = $ 296211.89, value end = $ 300275.44

Period 10: start date 07/01/2009, end date 08/31/2009
  Strategy "Buy and Hold", value begin = $ 286766.63, value end = $ 298338.27
  Strategy "Equally Weighted Portfolio", value begin = $ 272845.29, value end = $ 321639.02
  Strategy "Mininum Variance Portfolio", value begin = $ 321050.98, value end = $ 342363.71
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 180897.54, value end = $ 195509.76
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 281314.02, value end = $ 320028.09
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 147559.12, value end = $ 224994.78
  Strategy "Robust Optimization Portfolio", value begin = $ 300177.22, value end = $ 321067.62

Period 11: start date 09/01/2009, end date 10/30/2009
  Strategy "Buy and Hold", value begin = $ 291703.36, value end = $ 290193.57
  Strategy "Equally Weighted Portfolio", value begin = $ 310065.61, value end = $ 328220.99
  Strategy "Mininum Variance Portfolio", value begin = $ 334164.65, value end = $ 350926.72
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 187077.93, value end = $ 186948.32
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 310296.19, value end = $ 329115.53
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 202419.13, value end = $ 240053.39
  Strategy "Robust Optimization Portfolio", value begin = $ 313617.84, value end = $ 327933.00

Period 12: start date 11/02/2009, end date 12/31/2009
  Strategy "Buy and Hold", value begin = $ 288596.05, value end = $ 323101.02
  Strategy "Equally Weighted Portfolio", value begin = $ 329572.02, value end = $ 375644.43
  Strategy "Mininum Variance Portfolio", value begin = $ 348323.75, value end = $ 391102.48
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 186009.68, value end = $ 210603.75
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 329765.68, value end = $ 368937.71
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 238216.81, value end = $ 316610.61
  Strategy "Robust Optimization Portfolio", value begin = $ 326096.71, value end = $ 364555.49

![image](https://github.com/user-attachments/assets/72f71c91-c079-4a3f-83c1-8ade55e7d1bf)

This chart illustrates the daily value of the portfolio for each trading strategy over the market crash years
2008 and 2009 using the daily prices. This will be discussed further below. Main takeaways are that
maximum Sharpe’s ratio and leveraged ERC performed terribly during the time of crisis. Minimum
variance which performed poorly in 2020-2021 was the best strategy if used for the 2008-2009
recession period.

![image](https://github.com/user-attachments/assets/6595d0d5-b944-451f-b670-d63dc1a4acfa)

![image](https://github.com/user-attachments/assets/c2236ecb-12ce-41a5-ada8-226a260125dd)

![image](https://github.com/user-attachments/assets/817e267d-c082-42bb-8465-40e3a78ac25a)

![image](https://github.com/user-attachments/assets/2ec6d041-4df8-4820-8d02-51dd63ed9b60)

![image](https://github.com/user-attachments/assets/fe18af17-3bee-40e7-be62-c2c9964d7667)

It is the opposite of the 2021/2021 data, we could see that the maximum Sharpe ratio strategy has
performed the worst compared to the other six methods over the 12 trading periods (2 years) in terms
of portfolio value. The leveraged equal risk contribution strategy had the second lowest portfolio value
which is observed as the largest loss after a year of investing and then started to rapidly increase its
value after the 1.5-year mark. From the MDD graph, we can observe that leveraging is risky, especially
during a recession period. Luckily the portfolio started to pick up value, but as an investor seeing
that amount of loss is very unmanageable and stressful to continue investing in that strategy. Our buy-and-hold strategy had the third lowest portfolio value. We can observe that the simple equally weighted
strategy performed roughly the same as the equal risk contribution strategy and the robust minimum
variance strategy.
The minimum variance strategy seemed to perform the best in times of crisis and uncertainty. Thus, I
would still select the Minimum variance optimization strategy to manage my portfolio for the year
2008-2009 and in recession periods. We can observe that it was the only strategy that provided a net
positive return that was higher than the initial portfolio value. 

**Test Data for 2022**

Period 1: start date 01/03/2022, end date 02/28/2022
  Strategy "Buy and Hold", value begin = $ 890077.15, value end = $ 924072.93
  Strategy "Equally Weighted Portfolio", value begin = $ 881998.87, value end = $ 802771.38
  Strategy "Mininum Variance Portfolio", value begin = $ 885903.36, value end = $ 863773.70
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 881221.32, value end = $ 800281.21
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 882741.73, value end = $ 817665.70
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 869847.27, value end = $ 739757.29
  Strategy "Robust Optimization Portfolio", value begin = $ 883508.50, value end = $ 825486.75

Period 2: start date 03/01/2022, end date 04/29/2022
  Strategy "Buy and Hold", value begin = $ 921940.14, value end = $ 807230.89
  Strategy "Equally Weighted Portfolio", value begin = $ 783266.45, value end = $ 705860.50
  Strategy "Mininum Variance Portfolio", value begin = $ 855301.71, value end = $ 783180.34
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 783828.96, value end = $ 694300.44
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 801873.00, value end = $ 739191.61
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 702586.89, value end = $ 577325.07
  Strategy "Robust Optimization Portfolio", value begin = $ 813765.80, value end = $ 749219.23

Period 3: start date 05/02/2022, end date 06/30/2022
  Strategy "Buy and Hold", value begin = $ 806237.92, value end = $ 877550.83
  Strategy "Equally Weighted Portfolio", value begin = $ 716150.91, value end = $ 654771.07
  Strategy "Mininum Variance Portfolio", value begin = $ 786494.37, value end = $ 821074.11
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 687921.90, value end = $ 735767.23
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 747897.43, value end = $ 711427.92
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 589094.16, value end = $ 515854.34
  Strategy "Robust Optimization Portfolio", value begin = $ 752790.31, value end = $ 753378.22

Period 4: start date 07/01/2022, end date 08/31/2022
  Strategy "Buy and Hold", value begin = $ 892738.72, value end = $ 742946.10
  Strategy "Equally Weighted Portfolio", value begin = $ 656654.59, value end = $ 679066.98
  Strategy "Mininum Variance Portfolio", value begin = $ 826322.07, value end = $ 712545.00
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 732876.36, value end = $ 612899.86
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 715546.33, value end = $ 705070.50
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 518425.60, value end = $ 497373.49
  Strategy "Robust Optimization Portfolio", value begin = $ 758140.31, value end = $ 668196.19

Period 5: start date 09/01/2022, end date 10/31/2022
  Strategy "Buy and Hold", value begin = $ 742641.68, value end = $ 682506.51
  Strategy "Equally Weighted Portfolio", value begin = $ 675580.30, value end = $ 646270.98
  Strategy "Mininum Variance Portfolio", value begin = $ 711068.32, value end = $ 700722.40
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 607671.61, value end = $ 538152.79
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 703416.73, value end = $ 685372.60
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 488354.84, value end = $ 452278.62
  Strategy "Robust Optimization Portfolio", value begin = $ 666283.83, value end = $ 661895.44

Period 6: start date 11/01/2022, end date 12/30/2022
  Strategy "Buy and Hold", value begin = $ 683477.34, value end = $ 716351.42
  Strategy "Equally Weighted Portfolio", value begin = $ 648058.49, value end = $ 644566.45
  Strategy "Mininum Variance Portfolio", value begin = $ 708683.86, value end = $ 730346.54
  Strategy "Maximum Sharpe Ratio Portfolio", value begin = $ 533307.53, value end = $ 542874.92
  Strategy "Equal Risk Contributions Portfolio", value begin = $ 687738.59, value end = $ 685426.42
  Strategy "Leveraged Equal Risk Contributions Portfolio", value begin = $ 451286.92, value end = $ 446630.30
  Strategy "Robust Optimization Portfolio", value begin = $ 666620.13, value end = $ 676758.91

![image](https://github.com/user-attachments/assets/9fd457e4-ca08-464b-a2a3-8379e01e1019)

This chart illustrates the daily value of the portfolio for each trading strategy over the ‘Recession’ year
2022 using the daily prices. This will be discussed further below. The main takeaways are that it is following
somewhat similarly to 2008 in which the maximum Sharpe’s ratio and leveraged ERC strategy performed
terribly during the recession period. Minimum variance which performed poorly in 2020-2021 was the
best strategy if used for the 2022 recession period.

![image](https://github.com/user-attachments/assets/53120458-4851-435e-9ff8-ab34e78c6909)
