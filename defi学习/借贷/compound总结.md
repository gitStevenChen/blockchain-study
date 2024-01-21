# compound 总结


compound 是一个 去中心化借贷 协议。

## 利率模型

https://learnblockchain.cn/article/2618

https://medium.com/steaker-com/defi-%E7%9A%84%E4%B8%96%E7%95%8C-compound-%E5%AE%8C%E5%85%A8%E8%A7%A3%E6%9E%90-%E5%88%A9%E7%8E%87%E6%A8%A1%E5%9E%8B%E7%AF%87-95e9b303c284

### 直线型
y = k*x + b
y 即 y 轴的值，即借款利率值，x 即 x 轴的值，表示资金使用率，k 为斜率，b 则是 x 为 0 时的起点值。

资金使用率 = 总借款 / (资金池余额 + 总借款 - 储备金)
utilizationRate = borrows / (cash + borrows - reserves)

存款利率 = 资金使用率 * 借款利率 *（1 - 储备金率）
supplyRate = utilizationRate * borrowRate * (1 - reserveFactor)

### 拐点型
资金使用率没超过拐点值时，利率公式和直线型的一样：
y = k*x + b

而超过拐点之后，则利率公式将变成：
y = k2*(x - p) + (k*p + b)
其中，k2 表示拐点后的直线的斜率，p 则表示拐点的 x 轴的值。因此，需要初始化的参数有 4 个：b、k、k2、p，分别对应了构造函数中的几个入参：baseRatePerYear、multiplierPerYear、jumpMultiplierPerYear、kink。而几个 PerYear 入参对应的就有几个 PerBlock 变量

