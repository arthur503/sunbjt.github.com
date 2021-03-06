--- 
layout: post
title: "好地段是怎么选出来的-从北京地铁看区域的重要性"
tags: 
- subway
- sna
status: unpublish
type: post
published: true
---

2012年最后一天，北京新开了四条地铁线，分别是6号线的一期、8号线一期的南段、9号线的北段、10号线二期。
这几条地铁极大的方便了市民的出行。鉴于北京地方台1号一整天都在介绍地铁开通的情况，不写点东西有点
对不起北京市民的称呼，于是胡言乱语了如下文字。

增加这几条线路之后，北京地铁现在的形状是这样的：

![](http://upload.wikimedia.org/wikipedia/commons/f/ff/Beijing-Subway.png)


# 好地段是怎么度量的？

地段的好坏不是那么容易区分，如果你常和置业顾问（中介）打交道，他们一般会说会说有如下几大因素影响板块价值：

- 学区，幼小初高
- 临近医院，三甲
- 交通方便，公交地铁
- 社区成熟，配套完备
- 空气好，水质好（上风上水上海淀）
- 等

这学区、医院、风水啥的暂时不在讨论范围内，社区成熟要实地去看，
说白了没有足够的数据进行分析。交通的话，至少还可以从北京新开地铁线路的角度，来说明交通便利的这个因素。

我们仔细琢磨一下这个事儿：


`如果从地铁网络中A点，到所有其他地铁站的“最短距离”的和最小的话，那这个站点一定是最便捷的`，这种站点大致在脑海里可以勾勒出来，
肯定是二环以内的，比如平安里站、西单站…… 

这个指标是可以度量的，它的学术名称为closeness，它反映的是网络中节点i到其他节点的平均最短距离。

`如果地铁网络中有这样一个站点A，其他的站点都要通过A才能到达其他的站`，
或者想象更为极端的情况，如果没有了站点A，那么你就不能从其站点到达另外一个站点。
这种站可以简单的想象为换乘站，比如国贸站、建国门站等，如果没有这个站那么就不能从一条地铁线便利地换成到另外一条，比如现在坑爹的
10号线豁口，只有公交摆渡，想想就麻烦。

同样这个指标也是可度量的，学名为betweenness。

`如果同A站点连接的站点都非常好，那么物以类聚，A站点也应该是一个很好的站点`。是的，这个也有度量的办法，它就是大名鼎鼎的Page Rank。
可以简单理解为A点的重要程度是周围连接点重要程度的加权。

# 哪些地铁站（区域）值得我们关注？

按照上述三个指标对229个地铁站进行聚类（8类），得到的结果如下：

![](http://i.imgur.com/fwdpM.png)

我们最关注的第5类（一梯队），这些站点属于白富美，三项指标均较高。各站点分别为：

> 六里桥站,公主坟站,知春路站,芍药居站,国贸站,角门西站,西直门站,军事博物馆站,
> 复兴门站,建国门站,东直门站,朝阳门站,崇文门站,宣武门站,车公庄站,白石桥南站

接着是稍稍差一点的第二梯队（昌平线的缘故，回龙观站、龙泽站这些站地位比较高）：

> 海淀黄庄站,北土城站,惠新西街南口站,三元桥站,呼家楼站,西二旗站,龙泽站,
> 回龙观站,霍营站,立水桥站,西单站,东单站,鼓楼大街站,安定门站,雍和宫站,平安里站,东四站

然后是比较有意思的第3类，除了Page Rank较低以外，其他两项指标均较高。站点名为：

> 知春里站,太阳宫站,大钟寺站,五道口站,光熙门站,柳芳站,木樨地站,南礼士路站,天安门西站,天安门东站,
> 王府井站,永安里站,积水潭站,东四十条站,北京站,前门站,和平门站,长椿街站,阜成门站,
> 国家图书馆站,动物园站,新街口站,菜市口站,陶然亭站,天坛东门站,磁器口站,北海北站,南锣鼓巷站,东大桥站,白堆子站,北京西站

接下来是绿色的类，包括：

> 西局站,莲花桥站,宋家庄站,石榴庄站,大红门站,角门东站,草桥站,纪家庙站,
> 首经贸站,丰台站,泥洼站,上地站,北苑站,望京西站,望京站,望京东站,崔各庄站,大望路站,
> 四惠站,北京南站,马家堡站,刘家窑站,蒲黄榆站,六里桥东站,七里庄站,丰台东大街站,丰台南路站,
> 四惠东站,高碑店站,公益西桥站,新宫站,肖村站,小红门站,旧宫站

但这类有两个分的不太清的站，宋家庄站和望京西站，归到第一类也不为过：

    k           a          c        b    PageRank
    1     莲花桥站 0.08062235 2395.367 0.004195873
    1     宋家庄站 0.07574751 3915.258 0.004822161
    1     望京西站 0.07922168 3962.192 0.004297528
    1     望京东站 0.06930091 2180.000 0.003029334


对于其他4类站点篇幅限制，不介绍。
全部的站点分类结果和三项得分请点击 [这里](https://github.com/sunbjt/sunbjt.github.com/blob/master/upload/csv/subway.csv)。

P.S.

如果用此法淘到好房子，记得叫我去喝酒～～

-------
-------

__还可以做的事情__：

- 对于个人来说，时常去的地区比较集中，因此这个网络实际是一个不等权的网络，
关于权重可以使用一些其他方式间接计算，比如北京城区的移动电话通话密度，但我这里暂时还没有地铁的经纬度数据，
还不能匹配二者

- 可以在安居客这类房地产网站上爬取区域房产价格，这样价格洼地就显而易见了

__数据说明__：

- 大兴线将公益西桥站、新宫站连接
- 1号线未计算高井站、福寿岭站两个站点
- 9号线、8号线、10号线已经补全，即暂时未开通的站点认为已经开通

__数据来源__：

- http://zh.wikipedia.org/wiki/北京地铁车站列表
- http://www.bjsubway.com/node/1820