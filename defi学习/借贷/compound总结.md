# compound 总结


compound 是一个 去中心化借贷 协议。

## 利率模型

https://learnblockchain.cn/article/2618

https://medium.com/steaker-com/defi-%E7%9A%84%E4%B8%96%E7%95%8C-compound-%E5%AE%8C%E5%85%A8%E8%A7%A3%E6%9E%90-%E5%88%A9%E7%8E%87%E6%A8%A1%E5%9E%8B%E7%AF%87-95e9b303c284


兑换率：存token能换多少ctoken

exchangeRate = (totalCash + totalBorrows - totalReserves) / totalSupply

totalCash（在合约留下的数量）：cToken 账户所拥有的ERC20 标的代币（underlying token）的数量。
totalBorrows（借出的总量）：从市场借出给借款人的 ERC20 标的代币的数量。
totalReserves（总储备金）：储备的 ERC20 标的代币的数量，可通过治理提取或转账。
totalSupply：ERC20函数，返回 cToken 的总发行量。

ctoken的数量 = erc20的数量 / exchangeRate


抵押因子：比如某个token的抵押因子是0.75，相当于存100的token能借出75的其他token


资金使用率 = 总借款 / (资金池余额 + 总借款 - 储备金)
utilizationRate = borrows / (cash + borrows - reserves)


借款利率分两种：

### 直线型
y = k*x + b
y 即 y 轴的值，即借款利率值，x 即 x 轴的值，表示资金使用率，k 为斜率，b 则是 x 为 0 时的起点值。

存款利率 = 资金使用率 * 借款利率 *（1 - 储备金率）
存款利率是指对应的ctoken的存款利率
supplyRate = utilizationRate * borrowRate * (1 - reserveFactor)

### 拐点型
资金使用率没超过拐点值时，利率公式和直线型的一样：
y = k*x + b

而超过拐点之后，则利率公式将变成：
y = k2*(x - p) + (k*p + b)
其中，k2 表示拐点后的直线的斜率，p 则表示拐点的 x 轴的值。因此，需要初始化的参数有 4 个：b、k、k2、p，分别对应了构造函数中的几个入参：baseRatePerYear、multiplierPerYear、jumpMultiplierPerYear、kink。而几个 PerYear 入参对应的就有几个 PerBlock 变量

存款利率的计算公式则和直线型的一样，没有变化。因为存款利率是随着借款利率而变的，所以斜率其实也跟随着借款利率而变化。


## 清算

清算阈值


seizeTokens = actualRepayAmount * liquidationIncentive * priceBorrowed / (priceCollateral * exchangeRate)

seizeTokens 即最后得到的抵押资产数量，是 cToken 的数量
actualRepayAmount 为代还款的实际金额
liquidationIncentive 是清算激励，该值目前为 1.08，即清算人可获得借款价值 8% 的额外收益
priceBorrowed 所借资产的当前价格
priceCollateral 抵押物的标的资产价格
exchangeRate 兑换率

用户借了 1500 USDC，抵押资产为 cETH。清算人要对这笔借款进行清算时，可代还款金额为 1500*0.5=750 USDC，清算的抵押资产就指定为 cETH。ETH 价格假设为 1990，兑换率为 0.02，那根据公式计算得出清算人可得到的抵押资产数量为 750 * 1.08 * 1 / (1990 * 0.02) = 810 / 39.8 = 20.3517... 即清算人最终可得到 20.3517... 多的 cETH。


