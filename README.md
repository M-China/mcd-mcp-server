<p align="center">
  <a href="https://open.mcd.cn/mcp" target="_blank">
    <img src="https://img.mcd.cn/gallery/3fa1addc20b6d2d8.jpeg" align="middle" width = "1000" />
  </a>
</p>

<p align="center">
	简体中文 | <a href="README_EN.md">English</a>
</p>

# 介绍

**什么是麦当劳 MCP 服务?**
- 麦当劳 MCP 服务是一个遵循 Model Context Protocol（MCP）标准的数据交互接口服务，由麦当劳中国提供，面向中国大陆地区（不含港澳台）使用。
- 麦当劳MCP服务现已覆盖麦乐送点餐、到店取餐、团餐、积分兑换券、活动日历查询等业务场景。更多实用工具正在持续开发上线。
- 麦当劳 MCP Server 开放平台官网：[https://open.mcd.cn/mcp](https://open.mcd.cn/mcp)

# 1. 申请 MCP Token
- 第一步：点击右上角【登录】按钮
  <div class="img"><img src="https://img.mcd.cn/gallery/91178777592c9118.jpeg" alt="" width="1000" /></div>
- 第二步：跳转到登录页使用手机号验证登录
  <div class="img"><img src="https://img.mcd.cn/gallery/c7b5d9e9cdd2c786.png" alt="" width="1000" /></div>
  登录成功后跳转回首页，“登录”按钮变成控制台
  <div class="img"><img src="https://img.mcd.cn/gallery/a854347bb1339ee1.jpeg" alt="" width="1000" /></div>
- 第三步：申请 MCP Token\
  点击右上角“控制台”后，会弹出控制台弹窗\
  点击激活按钮，申请 MCP Token
  <div class="img"><img src="https://img.mcd.cn/gallery/37434d0289646b80.png" alt="" width="1000" /></div>
- 第四步：同意服务协议
  <div class="img"><img src="https://img.mcd.cn/gallery/62916ae518d0876d.png" alt="" width="1000" /></div>
- 第五步：MCP Token 申请成功，可以一键复制
  <div class="img"><img src="https://img.mcd.cn/gallery/3d14672fe32c8090.png" alt="" width="1000" /></div>

# 2. 快速开始
> 下面介绍如何将 MCP Server 接入到 MCP Client 中，开始使用 MCP 功能。\
> 麦当劳中国提供了远程托管的 MCP Server，用户只需在 MCP Client 中配置接入地址和 MCP Token 即可使用。


## 2.1 接入地址
> 服务器接入地址：`https://mcp.mcd.cn`

## 2.2 传输协议与安全
> 使用 **Streamable HTTP** 协议接入\
> 为了识别用户身份和权限，需要在请求头中携带 **Authorization** 字段，格式如下：
``` text
Authorization: Bearer YOUR_MCP_TOKEN
```

## 2.3 MCP 配置 JSON 示例：
> 为了方便使用，我们提供了JSON 配置示例。\
> 复制下面的配置，替换 **YOUR_MCP_TOKEN** 为实际 MCP Token，粘贴到 MCP Client 的 MCP Server 配置中即可。
``` json
{
  "mcpServers": {
    "mcd-mcp": {
      "type": "streamablehttp",
      "url": "https://mcp.mcd.cn",
      "headers": {
        "Authorization": "Bearer YOUR_MCP_TOKEN"
      }
    }
  }
}
```

## 2.4 注意事项：
> - 每个 Token 每分钟最多允许 600 次请求，超过限制会返回 429 错误码，请合理控制请求频率。
> - 请确保 MCP Client 支持 Streamable HTTP 协议。
> - 请妥善保管 MCP Token，避免泄露给他人。

## 2.5 MCP Client 推荐

|    Client     |                                 Link                                 |
|:-------------:|:--------------------------------------------------------------------:|
|   WorkBuddy   | https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Connector |
| Cherry Studio |            https://docs.cherry-ai.com/advanced-basic/mcp             |
|    Cursor     |       https://cursor.com/cn/docs/context/mcp#protocol-support        |
|     Kiro      |                      https://kiro.dev/docs/mcp/                      |
|     Trae      |           https://docs.trae.cn/ide/model-context-protocol            |
|    VSCode     | https://code.visualstudio.com/docs/copilot/customization/mcp-servers |

## 2.6 各平台接入教程：
### 2.6.1 Cherry Studio
> **前置条件**：需申请到麦当劳中国的 MCP Token，教程：[申请 MCP Token](#1-申请-mcp-token)\
> 参考 Cherry Studio 官方文档：https://docs.cherry-ai.com/advanced-basic/mcp

1、 打开 Cherry Studio，进入设置页面\
2、 选择“MCP”选项卡\
3、 点击“添加”按钮\
4、 在弹出的下拉框中，选择“从 JSON 导入”

<div class="img"><img src="https://img.mcd.cn/gallery/662175d6e573bb31.png" alt="" width="1000" /></div>

从上面复制JSON粘贴进去， **一定记得替换 “YOUR_MCP_TOKEN”**，然后点击“确定”按钮

<div class="img"><img src="https://img.mcd.cn/gallery/932b5bea7c9a79eb.png" alt="" width="1000" /></div>

添加完成后，请打开启用开关

<div class="img"><img src="https://img.mcd.cn/gallery/ade1966003d77e3b.png" alt="" width="1000" /></div>

配置完成。现在可以在聊天窗口中使用 MCP 功能。
<div class="img"><img src="https://img.mcd.cn/gallery/16721f738e7f631e.png" alt="" width="1000" /></div>


### 2.6.2 Cursor
> 前置条件：需申请到麦当劳中国的 MCP Token，教程：[申请 MCP Token](#1-申请-mcp-token)\
> 参考 Cursor 官方文档：https://cursor.com/cn/docs/context/mcp

打开 Cursor，点击顶部菜单栏【设置】→【Tools & MCP】，在 Installed MCP Servers 中点击【Add Custom MCP】

<div class="img"><img src="https://img.mcd.cn/gallery/b4817eeb8c597384.png" alt="" width="1000" /></div>

在打开的 mcp.json 文件中填入从上面复制的JSON内容，一定记得替换 YOUR_MCP_TOKEN 为实际 MCP Token，点击【关闭】并选择【保存】

<div class="img"><img src="https://img.mcd.cn/gallery/671f20806476f7f7.png" alt="" width="1000" /></div>

回到设置页面中，此时应显示可用的麦当劳mcp工具，服务状态应显示为【已连接】

<div class="img"><img src="https://img.mcd.cn/gallery/75a3dabf77fac237.png" alt="" width="1000" /></div>

按下 CTRL/CMD + L 打开右侧 Agent 对话框，接下来就可以直接在对话框中输入需求，让 AI 为我们调用工具了

<div class="img"><img src="https://img.mcd.cn/gallery/fed973ae04371908.png" alt="" width="1000" /></div>


### 2.6.3 TRAE
> 前置条件：需申请到麦当劳中国的 MCP Token，教程：[申请 MCP Token](#1-申请-mcp-token)\
> 参考 TRAE 官方文档：https://docs.trae.cn/ide/model-context-protocol

打开 Trae，点击【设置】→【MCP】→ 【手动添加】进行添加

<div class="img"><img src="https://img.mcd.cn/gallery/1b29297767cc5458.png" alt="" width="1000" /></div>
<div class="img"><img src="https://img.mcd.cn/gallery/720beadfcd8c7573.png" alt="" width="1000" /></div>

在打开的手动配置页面中填入从上面复制的JSON内容，一定记得替换YOUR_MCP_TOKEN 为实际 MCP Token，点击【确认】

<div class="img"><img src="https://img.mcd.cn/gallery/a532f0555f6d0497.png" alt="" width="1000" /></div>

回到MCP页面中，此时应显示可用的麦当劳mcp工具，服务状态应显示为【已连接】

<div class="img"><img src="https://img.mcd.cn/gallery/abe84f630677bfd7.png" alt="" width="1000" /></div>

回到对话框中 ，选择【Builder with MCP】

<div class="img"><img src="https://img.mcd.cn/gallery/32970b601e173816.png" alt="" width="1000" /></div>
<div class="img"><img src="https://img.mcd.cn/gallery/68c6f494dfda0627.png" alt="" width="1000" /></div>

接下来就可以直接在对话框中输入需求，让 AI 为我们调用工具了
<div class="img"><img src="https://img.mcd.cn/gallery/4b82125a6902a916.png" alt="" width="1000" /></div>

## 2.7 错误码说明

| code | 原因 | 处理建议 |
|:----:|:----:|:---------|
| 401 | MCP Token 无效、已过期或未提供 | 检查 Authorization 请求头和 MCP Token 配置 |
| 429 | 触发限流（超过 600 次/分钟） | 降低请求频率，合理控制调用间隔 |

# 3. 工具列表
> MCP Server 目前所支持的 Tools

<table>
  <thead>
    <tr>
      <th style="white-space: nowrap; text-align: center;"><strong>Tool</strong></th>
      <th style="min-width: 100px;"><strong>Name</strong></th>
      <th><strong>Description</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="white-space: nowrap; text-align: center;">list-nutrition-foods</td>
      <td>餐品营养信息列表</td>
      <td>获取麦当劳常见餐品的营养成分数据，包括能量、蛋白质、脂肪、碳水化合物、钠、钙等信息。当用户咨询麦当劳餐品的热量、营养，或需要帮助用户搭配指定热量套餐时使用此工具</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-query-addresses</td>
      <td>获取用户可配送地址列表</td>
      <td>查询用户已创建的配送地址列表，用于外送点餐时选择配送地址</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-create-address</td>
      <td>新增配送地址</td>
      <td>当用户无可配送地址或需新增收货地址时使用，用于创建新的可配送地址</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-query-stores</td>
      <td>查询可配送的门店列表</td>
      <td>外送场景下查询用户收货地址附近可配送门店</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meal-assistance</td>
      <td>查询助餐服务</td>
      <td>仅企业团餐场景下，查询该门店支持的助餐服务</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-nearby-stores</td>
      <td>查询附近可用门店</td>
      <td>查询用户提供地址附近的麦当劳餐厅</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-store-coupons</td>
      <td>查询用户当前门店下可用的优惠券列表</td>
      <td>查询用户在当前门店下可使用的优惠券列表，用于点餐时选择可用优惠</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meals</td>
      <td>查询当前可售卖的餐品列表</td>
      <td>查询当前门店可售卖的餐品菜单（分类、餐品编码、标签等），用于点餐选品</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meal-detail</td>
      <td>查询餐品详情</td>
      <td>根据餐品编码查询餐品详情套餐组成，用于查看套餐包含内容以及可以替换选项</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">calculate-price</td>
      <td>商品价格计算</td>
      <td>根据用户选购商品列表（可含优惠券）计算商品金额、配送费、优惠金额及应付总价</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">create-order</td>
      <td>创建订单</td>
      <td>根据门店信息、就餐方式、商品列表等信息创建订单，返回订单详情与支付链接</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">cancel-order</td>
      <td>取消订单</td>
      <td>取消点餐订单。当用户说&quot;取消订单&quot;、&quot;我要取消&quot;、&quot;帮我取消一下订单&quot;时，可使用该工具进行取消</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-order</td>
      <td>查询订单详情</td>
      <td>查询订单状态、订单内容、配送信息等，用于用户查看订单进度或确认订单信息</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">order-list</td>
      <td>查询历史订单</td>
      <td>查询近期的到店/外送历史订单（非商城订单，商城订单请使用 mall-order-list）</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">campaign-calendar</td>
      <td>活动日历查询工具</td>
      <td>查询麦当劳中国当月的营销活动日历，返回进行中、往期和未来日期的活动</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">available-coupons</td>
      <td>麦麦省券列表查询</td>
      <td>查询用户当前可领取的麦麦省的优惠券列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">auto-bind-coupons</td>
      <td>麦麦省一键领券</td>
      <td>自动领取麦麦省所有当前可用的麦当劳优惠券。无需指定具体的优惠券和couponId，系统会自动领取用户可领的所有券</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-coupons</td>
      <td>我的优惠券查询</td>
      <td>查询用户有哪些可用的优惠券。支持用户查看账户下所有优惠券列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-account</td>
      <td>我的积分查询</td>
      <td>查询用户积分账户信息，包括可用积分、累计积分、冻结积分、即将过期积分等</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-points-products</td>
      <td>查询麦麦商城商品列表</td>
      <td>查询麦麦商城内可使用积分兑换或现金购买的商品（不包括使用积分兑换的第三方兑换码）</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-product-detail</td>
      <td>查询麦麦商城商品详情</td>
      <td>查询商城商品详细信息（图片、积分、有效期、说明、详情等）</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-create-order</td>
      <td>积分兑换商品下单</td>
      <td>使用积分兑换虚拟或实物商品，完成积分校验、积分扣减及发券或实物库存扣减，返回兑换订单号和券码信息</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">now-time-info</td>
      <td>获取当前时间信息</td>
      <td>返回当前的完整时间信息，以便于 LLM 知道当前的时间和日期</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-lottery-info</td>
      <td>查看积分抽奖活动信息</td>
      <td>查询当前积分抽奖活动的基本信息，包括活动状态、奖品列表、抽奖消耗规则和用户可用资源</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">draw-lottery</td>
      <td>积分抽奖</td>
      <td>执行一次积分抽奖，消耗积分或次数，返回是否中奖及奖品信息</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-prizes</td>
      <td>查看我的奖品</td>
      <td>查询用户在积分抽奖活动中获得的全部奖品记录，支持分页，按中奖时间倒序排列</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-order-list</td>
      <td>麦麦商城订单查询</td>
      <td>查询麦麦商城内近一年购买或兑换的商品订单列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-order-detail</td>
      <td>麦麦商城订单详情查询</td>
      <td>查询麦麦商城订单的详细信息，包括支付积分、支付金额和订单状态等</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-party-city</td>
      <td>主题活动城市列表查询</td>
      <td>查询主题活动商品对应的可参与城市列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-party-store</td>
      <td>主题活动门店列表查询</td>
      <td>查询指定城市下主题活动可参与的门店列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-partystore-date</td>
      <td>主题活动可预约日期查询</td>
      <td>查询指定门店下主题活动的可预约日期列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-partystore-session</td>
      <td>主题活动可预约日期场次查询</td>
      <td>查询指定门店、指定日期下主题活动的可预约场次列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">party-order-create</td>
      <td>主题活动订单创建</td>
      <td>创建主题活动订单，当用户选择好城市、门店、日期、场次后使用此工具下单</td>
    </tr>
  </tbody>
</table>

# 4. 版本日志

|    Date    | Version | Description                         |
|:----------:|:-------:|-------------------------------------|
| 2025-12-09 |  1.0.0  | 麦麦日历和麦麦省领券 MCP Server               |
| 2026-01-23 |  1.0.1  | 增加了“餐品营养信息列表”Tool，我们缩短了 URL 以便于大家连接 |
| 2026-02-13 |  1.0.2  | 增加了麦乐送点餐与积分兑换券场景的Tools              |
| 2026-04-02 |  1.0.3  | 增加了到店取餐与团餐场景的Tools              |
| 2026-05-21 |  1.0.4  | 增加了积分兑换实物、商城订单查询等 Tools，并支持得来速车道取餐场景下单及全部点餐场景预约功能              |
| 2026-06-16 |  1.0.5  | 支持更换套餐内商品组合、部分餐品特制              |
| 2026-07-16 |  1.0.6  | 新增历史订单查询工具；支持展示餐品优惠价格；支持随单购买麦金卡和早餐卡              |
| 2026-07-29 |  1.0.7  | 新增麦当劳派对、品鉴会等主题活动查询、预约与下单功能              |
| 2026-08-27 |  1.0.8  | 新增积分抽奖工具：查看活动信息、抽奖、查我的奖品              |
| 2026-09-10 |  1.0.9  | 新增取消订单、餐具选择、麦乐送订单备注功能；堂食外带场景下支持返回取餐柜二维码              |

---

# 5. 注意事项：

- 允许个人以非商业用途复制并使用本仓库中的示例配置、参数、JSON 或示例代码，并仅限用于实现与麦当劳MCP服务的连接与使用。

- 使用 麦当劳MCP 服务须遵守麦当劳中国的《使用条款》及《麦当劳MCP 服务规则》，并在申请MCP Token时同意前述条款。

- 未经书面授权，不得将本仓库内容用于商业售卖、付费分发、引流变现或任何暗示官方背书、误导公众的用途；亦不得用于任何违法、违规或黑灰产相关行为。

- 本仓库内容按“现状”提供，不构成任何形式的保证或承诺。

- 本仓库不构成对麦当劳及其关联方商标的任何授权。

- 请妥善保管您的MCP Token，避免泄露或被他人使用。

<p align="center">© 2026 McDonald’s. All Rights Reserved.</p>
