# huobi_backtest
> 数字货币回测行情服务器- 收费版

* 根据需求，自动提前下好N年N多币种历史数据(1分钟线),回测服务器自动转换1分钟线成为日线，4小时线，1小时等，并全部调入内存数据库，以便达到每个get_price()调用 小于 1.5ms的超高速历史回测行情，用最短的时间验证你的想法和策略 (从理论到实践，真金白银需要三思而行) 

### 功能特点
* 系统可以获取从2015年至今所有火币上线币种的全部历史行情，各个币种对都能精确到1分钟线。

* 系统调用API同我们的开源的火币行情服务器huobi_info完全一致 ( https://github.com/mpquant/huobi_intf ),原则上是希望一套代码通行回测和实盘

* API价格获取： `get_price('btc.usdt', end_date='2017-09-04 13:56:00', count=8000, frequency='1h')`   
  包括按天，4小时，1小时，15分钟，5分钟等，支持2015年后历史任意时间，任意条数数据获取

* 行情服务器编程语言是python,采用高性能异步网络框架tornado做WebApi, 标准json返回，所有语言都能方便调用

* 系统采用csv标准格式记录历史数据，一个币种一个文件，便于其他工具分析，分享，保存 (具体格式参考下面表格)
    |date|open|close|low|high|money|volume|
    |----|----|----|----|----|----|-------|
    |2020-01-01 00:00:00|7194.7|7200.0|7186.19|7200.0|102.743|738706.346|
    |2020-01-01 00:01:00|7200.0|7218.2|7199.99|7219.58|70.711|509693.211|
    |2020-01-01 00:02:00|7218.21|7216.22|7213.09|7218.44|17.445|125889.77|
    |2020-01-01 00:03:00|7216.21|7218.37|7215.48|7221.91|13.034|94091.100|
    |2020-01-01 00:04:00|7218.37|7213.05|7210.01|7220.13|14.005|101042.531|
