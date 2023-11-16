# 使用TheGraph索引合约数据

官网 [https://thegraph.com/studio/]

使用文档 
[https://learnblockchain.cn/article/2466] 
[https://thegraph.com/docs/zh/querying/querying-from-an-application/]

APIURL = 'https://api.thegraph.com/subgraphs/name/username/subgraphname' （/username/subgraphname 替换）
找子图工作室的端点可以去google搜：子图名称 Graphql endpoints

部署到subGraph后会生成query，在playground的右边按钮能找到，这是查询的关键字

参考代码
```
import { createClient, cacheExchange, fetchExchange } from 'urql'
import fetch from "node-fetch"


const APIURL = 'https://api.thegraph.com/subgraphs/name/uniswap/uniswap-v2'

const tokensQuery = `
  query {
    tokens(first: 1) {
      id
      symbol
      name
      decimals
    }
  }
`

const client = createClient({
  url: APIURL,
  exchanges: [cacheExchange, fetchExchange],
  fetch: fetch,
  fetchOptions: () => ({
    headers: {
      'Content-Type': 'application/json',
    },
  }),
})

const data = await client.query(tokensQuery).toPromise()
console.log(data.data)

```
