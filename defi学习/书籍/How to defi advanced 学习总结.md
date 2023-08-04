# How to defi advanced 学习总结


## DEFI 的分类


- 去中心化交易所 (DEX)
- DEX聚合器
- 去中心化借贷
- 去中心化稳定币
- 去中心化衍生品
- 去中心化保险

--------

- 去中心化指数
- 去中心化预测
- 去中心化固定利率协议
- 去中心化收益聚合器

--------

- 预言机 和 数据聚合器
- 多链协议 和 跨链桥


### 去中心化交易所 (DEX)

DEX是一个平台，可以实现代币的交易和直接交换，而不需要中介机构（即中心化交易所）。你不需要经历 "了解你的客户"（KYC）流程的麻烦，也不会受到管辖范围的限制。


1. 基于【订单薄】 <链上或链下>： dYdX、Deversifi、Loopring 。类似于CEX的买卖订单，区别在于，在CEXs中，交易的资产被保存在交易所的钱包里，而对于DEXs，交易的资产被保存在用户的钱包里。
2. 基于【流动性池】： Uniswap、SushiSwap、Curve、 Balancer、 Bancor、 PancakeSwap、 TerraSwap、 0x 。用AMM（自动做市商）来保证流动性，有双边流动性（存一对token）或单边流动性（当价格不在设定的区间或者有一个token未上链时），只有价格在设定的区间内才会使用，才有收益。

#### AMM算法

AMMs是一种数学函数，根据流动性池对资产进行算法定价。目前，有几个AMM公式被利用来迎合不同的资产定价策略。

1. 恒定乘积做市商公式：x * y = k  
恒定乘积做市商公式首先由Uniswap和Bancor推广，是市场上最流行的AMM。绘制时，它是一条凸形曲线，其中x和y代表流动性池中两个代币的数量，而k代表乘积。该公式有助于根据每个代币的可用数量，为两个代币创造一个价格范围。  
为了保持k不变，当x的供应增加时，y的供应必须减少，反之亦然。因此，所产生的价格本质上是不稳定的，因为交易的规模可能会影响到与池子规模有关的价格。大额交易造成的较高滑点可能会出现无常的损失。

2. 恒定和做市商公式：x + y = k
  恒定和做市商公式在绘制时形成一条直线。它是零滑点交易的理想模型，但不幸的是，它不能提供无限的流动性。这个模型是有缺陷的，因为当报价与其他地方交易的资产的市场价格不同时，它就会出现套利机会。套利者可以耗尽流动性池中的全部储备，不再为其他交易者留下可用的流动性。这种模式不适合大多数AMM使用案例。

3. 恒定平均值做市商公式：$`\nu = \prod_{t}B_{t}^{w_{t}}`$
  恒定平均值做市商公式，或者也被称为"价值函数"，是由Balancer创造并使之流行的。它允许流动性池中有两个以上的代币，并允许池子以超出标准50/50分布的比例添加不同的代币。这允许对池子里的不同资产进行可变的暴露，并使流动性池子里的任何资产之间的交换成为可能。

4. 稳定交换公式：


### DEX聚合器


DEX市场竞争非常激烈，多个DEX在竞争用户和流动性。因此，流动性往往是不一样的，导致资本管理效率低下。
虽然对小型交易的影响可能不大，但大型DEX交易将容易出现较高的价格滑点。这就是DEX聚合器帮助交易者在各种DEX中获得最佳价格执行的地方。
DEX聚合器通过汇集不同DEX的流动性来寻找最具成本效益的交易路线。通过在多个流动性池子中路由单一交易，进行大额交易的交易者可以节约gas成本，并尽量减少因流动性低而影响价格的成本。


1inch、Matcha、ParaSwap、DEX.AG（改名为Slingshot）、Totle

### 去中心化借贷

Compound、Maker、Aave(闪电贷)、Cream、Venus、Anchor、Alchemix、Liquity

（dYdX与Aave和Compound等其他借贷平台有一些共同特点--允许用户将其资产存入以赚取利息）

### 去中心化稳定币

Tether (USDT，曾叫RealCoin)、Maker (Dai，MakerDao的)、Ampleforth（AMPL）、Empty Set Dollar (ESD)、 Basis Cash (BAC)、 Frax Finance(FRAX)、 Fei Protocol (FEI)、 Reflexer (RAI)、 Float Protocol (FLOAT, 和Frax类似)、 Dynamic Set Dollar v2 (DSD)、 Gyroscope (GYR)、 TerraUSD (UST)


### 去中心化衍生品


1、去中心化永续合约：

Perpetual Protocol (基于虚拟自动做市商 vAMMs)、 dYdX (DEX 支持借贷，现货交易，保证金交易和永续合约交易)、 Futureswap、MCDEX、Injective Protocol

2、去中心化期权

Hegic、 Opyn、 Opyn v2、 FinNexus、 Auctus (允许用 闪电贷行权)、 Premia、 Antimatter、 Siren Protocol

3、合成资产

Synthetix (SNX)、 Universal Market Access（UMA)、 Mirror Protocol、 DEUS Finance

### 去中心化保险

Nexus Mutual (NXM)、 Armor Protocol、 Cover Protocol、 Unslashed Finance、 Nsure Network、 InsurAce

--------


### 去中心化指数

指数协议指的是资产管理者，而指数代币指的是指数的产品（相当于ETF）。这些指数代币代表你在指数基金中的份额，并使你有权从相关资产的资本增值中获得利润。此外，还有一些协议的治理代币，让你在决定指数协议的方向上有投票权。

1、Index Cooperative (INDEX):

DeFiPulse指数(DPI)
CoinShares加密黄金指数(CGI)
ETH 2倍杠杆指数 (ETH2X-FLI)
BTC 2倍杠杆指数 (BTC2X-FLI)
Metaverse指数代币（MVI）

2、Indexed Finance (NDX)、DEGEN指数(DEGEN)：

加密货币十大代币指数(CC10)
预言机五强指数（ORCL5）
DEFI 5强指数(DEFI5)
NFT平台指数 (NFTP)
484基金 (ERROR)
未来金融基金(FFF)

3、PowerPool集中投票权(CVP)：

Power指数池代币(PIPT)
Yearn生态系统指数 (YETI)
ASSY指数(ASSY)
Yearn Lazy Ape指数（YLA）

4、BasketDAO - 计息的DPI (BDPI)

5、Cryptex Finance - 加密总市值 (TCAP)


### 去中心化预测

预测协议如何运作？
与传统的预测市场不同，预测协议是去中心化的，必须依靠创新方法来运作。我们可以粗略地将预测的协议流程图分解为两个主要部分： 1. 做市商类型（Market-Making） 2. 决议模型（Resolution）


Augur (REP和REPv2)、 Omen、 Polymarket


### 去中心化固定利率协议

Yield (一个去中心化的借贷系统, fyDai)、 Saffron.Finance (SFI)、 Horizon Finance、 Notional、 BarnBridge、 88mph、 Pendle


### 去中心化收益聚合器


收益聚合器的诞生是为了满足用户投资策略自动化的需要，使他们不必为监测市场上的最佳收益农场而烦恼。下面我们就来看看几个去中心化的收益聚集器协议。

实现借贷平台之间资金的自动转换，以获得不同DeFi借贷平台的最佳收益。


Yearn Finance、 Alpha Finance、 Badger DAO (Badger Finance)、 Harvest Finance、 Pancake Bunny、 AutoFarm


--------

### 预言机 和 数据聚合器

在区块链和现实世界之间架起数据的桥梁。



1、 预言机协议 (Oracle)

Chainlink (link)、 Band Protocol、 DIA (Decentralized Information Asset)、 API3

2、数据聚合器 (Data Aggregators)

The Graph Protocol、 Covalent


### 多链协议 和 跨链桥

Ren、 ThorChain、 Binance Bridge、 Anyswap (去中心化跨链交易所)、 Terra Bridge、 Multichain.xyz、 Matic Bridge、 APYSwap
