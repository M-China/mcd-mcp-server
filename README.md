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

# 新闻
- **[2026-04] `功能`:** 我们上线了"到店取餐"与"团餐"场景的点餐能力，新增了附近门店查询工具，并对多个点餐工具进行了升级以支持多场景下单。[查看工具详情](#4-工具)
- **[2026-02] `功能`:** 我们新增了"麦乐送点餐"与"积分兑换券"功能模块，支持完整的外送点餐与积分兑换服务。[查看工具详情](#4-工具) 
- **[2026-01] `功能`:** 我们新增了“餐品营养信息列表”工具，用户可以查询麦当劳常见餐品的营养成分数据,咨询麦当劳餐品的热量、营养。[查看工具详情](#4-工具)
- **[2025-12] `发布`:** 我们发布了麦当劳 MCP Server 1.0.0 版本，提供了活动日历查询和麦麦省领券功能，快来试试吧！接入教程请看下文[快速开始](#2-快速开始)部分

---

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
> - ⚠️MCP Server 当前仅支持 MCP **Version 2025-06-18** 及之前的版本。
> - 每个 Token 每分钟最多允许 600 次请求，超过限制会返回 429 错误码，请合理控制请求频率。
> - 请确保 MCP Client 支持 Streamable HTTP 协议。
> - 请妥善保管 MCP Token，避免泄露给他人。

## 2.5 各平台接入教程：
### 2.5.1 Cherry Studio
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


### 2.5.2 Cursor
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


### 2.5.3 TRAE
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

## 2.6 错误码说明

| code | 原因 | 处理建议 |
|:----:|:----:|:---------|
| 401 | MCP Token 无效、已过期或未提供 | 检查 Authorization 请求头和 MCP Token 配置 |
| 429 | 触发限流（超过 600 次/分钟） | 降低请求频率，合理控制调用间隔 |

# 3. 调试指南
## 3.1 MCP Client  推荐


|    Client     |                                 Link                                 |
|:-------------:|:--------------------------------------------------------------------:|
| Cherry Studio |            https://docs.cherry-ai.com/advanced-basic/mcp             |
|    Cursor     |       https://cursor.com/cn/docs/context/mcp#protocol-support        |
|     Kiro      |                      https://kiro.dev/docs/mcp/                      |
|     Trae      |           https://docs.trae.cn/ide/model-context-protocol            |
|    VSCode     | https://code.visualstudio.com/docs/copilot/customization/mcp-servers |

## 3.2 LLM 推荐

截至 2026 年 2 月 12 日

|    厂商    |           型号           |
|:--------:|:----------------------:|
|   Qwen   | qwen-plus<br>qwen3-max |
|  Doubao  |    Doubao-Seed-1.6     |
|   Kimi   |          k2.5          |
|  Zhipu   |         GLM-5          |
|  Gemini  | gemini-3-flash-preview |
| DeepSeek |     DeepSeek-V3.2      |


# 4. 工具
> MCP Server 目前所支持的 Tools

## 4.1 工具列表

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
      <td>查询用户已创建的配送地址列表，用于外送点餐时选择配送地址，并获取对应门店信息（storeCode、beCode）</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-create-address</td>
      <td>新增配送地址</td>
      <td>当用户无可配送地址或需新增收货地址时使用，用于创建新的可配送地址</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-nearby-stores</td>
      <td>查询附近门店</td>
      <td>查询用户提供地址附近的麦当劳餐厅</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-store-coupons</td>
      <td>查询用户在当前门店可用券</td>
      <td>查询用户在当前门店下可使用的优惠券列表，用于点餐时选择可用优惠</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meals</td>
      <td>查询当前门店可售卖的餐品列表</td>
      <td>查询当前门店可售卖的餐品菜单（分类、餐品编码、标签等），用于点餐选品</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meal-detail</td>
      <td>查询餐品详情</td>
      <td>根据餐品编码查询餐品详情（套餐组成、默认选择等），用于查看套餐包含内容</td>
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
      <td style="white-space: nowrap; text-align: center;">query-order</td>
      <td>查询订单详情</td>
      <td>查询订单状态、订单内容、配送信息等，用于用户查看订单进度或确认订单信息</td>
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
      <td>查询我有哪些可用的优惠券。就像打开麦当劳App的"我的优惠券"页面，能看到所有可以用来点餐的优惠券列表</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-account</td>
      <td>我的积分查询</td>
      <td>查询用户积分账户信息，包括可用积分、累计积分、冻结积分、即将过期积分等</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-points-products</td>
      <td>积分兑换商品列表</td>
      <td>查询麦麦商城内可以用积分兑换的餐品券（不包含积分兑换的实物或者积分兑换的第三方码）</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-product-detail</td>
      <td>积分兑换商品详情</td>
      <td>查询指定积分兑换商品券的详细信息（图片、积分、有效期、说明、详情等）</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-create-order</td>
      <td>积分兑换商品下单</td>
      <td>使用积分兑换指定餐品券，完成积分扣减并发放券码，返回兑换订单号与券码信息</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">now-time-info</td>
      <td>获取当前时间信息</td>
      <td>返回当前的完整时间信息，以便于 LLM 知道当前的时间和日期</td>
    </tr>
  </tbody>
</table>

## 4.2 点餐

### 4.2.1 餐品营养信息列表

**描述：**
> 获取麦当劳常见餐品的营养成分数据，包括能量、蛋白质、脂肪、碳水化合物、钠、钙等信息。当用户咨询麦当劳餐品的热量、营养，或需要帮助用户搭配指定热量套餐时使用此工具。

**入参：**
> 无需入参

**响应内容：**
> 注意：为优化 LLM Token 消耗，营养信息采用紧凑格式（toon 格式）返回，而非标准 JSON 数组格式。

示例：
``` json
{
    "success": true,
    "code": 200,
    "message": "请求成功",
    "datetime": "2026-01-23 09:32:44",
    "data": "[1]{productName,nutritionDescription,energyKj,energyKcal,protein,fat,carbohydrate,sodium,calcium}:\n  猪柳麦满分,null,1288,308,16,16,24,781,213\n "
}
```
### 4.2.2 获取用户可配送地址列表

**描述：**   
> 查询用户已创建的配送地址列表。当用户有麦当劳外送（麦乐送）、团餐需求时使用该工具查询用户可配送的地址列表。仅用于包括麦乐送、企业团餐在内的外送场景。

**入参：**  
| name | description |
|------|-------------|
| beType | 必填，麦乐送(beType=2)，团餐(beType=6) |

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:29:28",
  "traceId": "f2a0d969353467c957fd6728166eb430",
  "data": {
    "addresses": [
      {
        "addressId": "1",
        "contactName": "张三",
        "phone": "152****6666",
        "fullAddress": "xx省xx市xxx小区 x栋x单元xxx室",
        "storeCode": "12345",
        "storeName": "xxx",
        "beCode": "12345"
      }
    ]
  }
}
```

### 4.2.3 新增配送地址

**描述：**
>用户无可配送地址或者当前列表内无用户期望的配送地址时，可以使用该工具新增配送地址。仅用于包括麦乐送、企业团餐在内的外送场景。

**入参：**

| name | description |
|------|-------------|
| city | 城市名称，必填，必须从用户输入中获取实际城市名称，如"南京市" |
| contactName | 联系人姓名，必填，必须从用户输入中获取实际联系人姓名，如"李明" |
| gender | 性别，非必填，如"先生"、"女士" |
| phone | 联系人电话号码，必填，必须从用户输入中获取实际电话号码，类型为11位纯数字，如"16666666666" |
| address | 配送地址，必填，必须从用户输入中获取实际地址，如"清竹园9号楼" |
| addressDetail | 配送地址门牌号，必填，必须从用户输入中获取实际门牌号，如"2单元508" |
| beType | 必填，麦乐送(beType=2)，团餐(beType=6) |

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:29:28",
  "traceId": "f2a0d969353467c957fd6728166eb430",
  "data": {
    "addressId": "1",
    "contactName": "张三",
    "phone": "152****6666",
    "fullAddress": "xx省xx市xxx小区 x栋x单元xxx室",
    "storeCode": "12345",
    "storeName": "xxx",
    "beCode": "12345"
  }
}
```
### 4.2.4 查询附近可用门店

**描述：**  
> 查询用户提供地址附近的麦当劳餐厅。当用户希望想要到店取餐、堂食或希望寻找麦当劳餐厅时可以使用该工具查找位置附近的麦当劳门店

**入参：**

| name | description |
|------|-------------|
| searchType | 必填，1：查询收藏，2：按位置搜索，默认选中1 |
| beType | 必填，默认1，到店 |
| city | 城市，仅在searchType=2时必填 |
| keyword | 位置关键词，仅在searchType=2时必填 |

**响应内容：**

示例：
```json
{
    "success": true,
    "code": 200,
    "message": "请求成功",
    "datetime": "2026-02-09 14:44:29",
    "traceId": "341e2dce2af4a61497b52097125a8a77",
    "data": [
        {
            "storeCode": "1",
            "storeName": "xxxx",
            "beCode": "",
            "address": "",
            "distance": ""
        },
        {
            "storeCode": "2",
            "storeName": "xxxx",
            "beCode": "",
            "address": "",
            "distance": ""
        }
    ]
}
```
### 4.2.5 查询用户当前门店下可用的优惠券列表

**描述：**  
> 查询用户在当前门店、当前取餐方式可用的优惠券。当用户询问当前门店、取餐方式有哪些可以使用的优惠券时，可以使用该工具进行查询。


**入参：**

| name | description |
|------|-------------|
| storeCode | 门店编码，必填 |
| beCode | BE编码  |
| orderType | 必填，到店：orderType=1，外送：orderType=2 |

>到店取餐场景: orderType=1 && beCode=null\
>外送场景: orderType=2 && beCode 为 delivery-query-address 中的 beCode

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:32:41",
  "traceId": "0f694a844e393e6cb0717455d9229a24",
  "data": [
    {
      "title": "外送优惠券二次券",
      "couponId": "xxxxxxxxxx",
      "couponCode": "xxxxxx",
      "tradeDateTime": "2025-04-21 23:23:00-2026-07-01 23:59:59",
      "products": [
        {
          "productCode": "xxxxxxxxx",
          "productName": "甜蜜小食1+1"
        }
      ]
    }
  ]
}
```
### 4.2.6 查询当前可售卖的餐品列表

**描述：**  
> 查询当前门店可售餐品列表。当用户希望获取门店菜单或者点单时，可以调用这个工具获取当前门店可售的餐品。


**入参：**

| name | description |
|------|-------------|
| storeCode | 门店编码，必填 |
| beCode | BE编码 |
| orderType | 必填，到店：orderType=1，外送：orderType=2 |

>到店取餐场景: orderType=1 && beCode=null\
>外送场景: orderType=2 && beCode 为 delivery-query-address 中的 beCode

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 09:47:35",
  "traceId": "4b2b4de1d772dad2dc498597c65cf3af",
  "data": {
    "categories": [
      {
        "name": "人气热卖",
        "meals": [
          {
            "code": "9900008139",
            "tags": []
          },
          {
            "code": "9900008169",
            "tags": []
          },
          {
            "code": "920215",
            "tags": [
              "第二份半价"
            ]
          }
        ],
        "daypart": 8
      }
    ],
    "meals": {
      "920215": {
        "name": "培根安格斯厚牛堡大套餐",
        "currentPrice": "55.5"
      },
      "9900008139": {
        "name": "DC套餐测试",
        "currentPrice": "14"
      },
      "9900008169": {
        "name": "双层深海鳕鱼堡",
        "currentPrice": "25"
      }
    }
  }
}
```
### 4.2.7 查询餐品详情

**描述：**
> 根据餐品列表中返回的餐品编码，可以查看套餐的组成等信息。当用户需要查看餐品详情时使用此工具。 

**重点注意：**
>当前版本（v1.0.3）暂不支持更换套餐内的单品，该功能将在后续版本中提供。

**入参：**

| name | description |
|------|-------------|
| code | 餐品编码，必填 |
| storeCode | 门店 code |
| beCode | BE编码 |
| orderType | 必填 |
>到店取餐场景: orderType=1 && beCode=null\
>外送场景: orderType=2 && beCode 为 delivery-query-address 中的 beCode

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:37:19",
  "traceId": "21de60d22eea026cae0428f714359e2c",
  "data": {
    "code": "9900008139",
    "price": "14",
    "rounds": [
      {
        "id": 1,
        "name": "汉堡包",
        "quantity": 1,
        "maxQuantity": 1,
        "minQuantity": 1,
        "choices": [
          {
            "code": "1000",
            "name": "汉堡包-pool1",
            "quantity": 1,
            "maxQuantity": -1
          }
        ]
      }
    ]
  }
}
```
### 4.2.8 商品价格计算

**描述：**  
> 计算用户购买商品及优惠价格。当用户询问商品或商品组合的价格时，可以使用此工具获取订单价格信息。


**入参：**

| name | description |
|------|-------------|
| storeCode | 门店编码, 必填 |
| beCode | BE编码 |
| orderType | 必填，到店：orderType=1，外送（麦乐送&团餐）：orderType=2 |
| items | 商品列表（数组） |

`items` 字段结构：

| name | description |
|------|-------------|
| productCode | 餐品编码，必填（如果用户使用优惠券，则productCode为券商品code） |
| quantity | 商品数量，必填 |
| couponId | 优惠券ID，当用户要使用优惠券时必填） |
| couponCode | 优惠券编码，当用户要使用优惠券时必填 |

>到店取餐场景: orderType=1 && beCode=null\
>外送场景: orderType=2 && beCode 为 delivery-query-address 中的 beCode

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:39:50",
  "traceId": "1f90ace087d33bdabd3b8c27da4e7b0a",
  "data": {
    "productOriginalPrice": 1600,
    "productPrice": 1600,
    "deliveryOriginalPrice": 600,
    "deliveryPrice": 600,
    "originalPrice": 2200,
    "discount": 0,
    "price": 2200,
    "productList": [
      {
        "productCode": "xxxxxxx",
        "productName": "DC套餐测试",
        "quantity": 1,
        "originalSubtotal": 1600,
        "subtotal": 1600
      }
    ],
    "takeWayList": [],
    "mealAssistanceList": []
  }
}
```
### 4.2.9 创建订单

**描述：**  
> 创建订单。当用户希望下单/购买选中商品时可以使用该工具进行下单。


**入参：**

| name | description |
|------|-------------|
| storeCode | 门店编码 |
| beCode | BE编码|
| addressId | 外送场景下必填 |
| takeWayCode | 到店场景下必填, 需要从 calculate-price 的价格计算工具中获取 |
| orderType | 必填，到店：orderType=1，外送（麦乐送&团餐）：orderType=2 |
| items | 商品列表（数组） |

`items` 字段结构：

| name | description |
|------|-------------|
| productCode | 餐品编码，必填（如果用户使用优惠券，则productCode为券商品code）|
| quantity | 商品数量，必填 |
| couponId | 优惠券ID，当用户使用优惠券时必填 |
| couponCode | 优惠券编码，当用户使用优惠券时必填 |

>到店取餐场景: orderType=1 && beCode=null\
>外送场景: orderType=2 && beCode 为 delivery-query-address 中的 beCode


**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:42:51",
  "traceId": "80572509920e2e1e4a4373ee9eeca070",
  "data": {
    "orderId": "1030938730000733964700499858",
    "payId": "11940981078137585664",
    "payH5Url": "https://m.mcd.cn/mcp/scanToPay?orderId=1030779030000000000000000",
    "orderDetail": {
      "orderStatus": "待支付",
      "storeName": "xxxxxx门店",
      "storeAddress": "xxxxx",
      "orderProductList": [
        {
          "productName": "DC套餐测试",
          "quantity": 1,
          "price": "16",
          "comboItemList": [
            {
              "itemName": "汉堡包-pool1 加一份奶油(加)",
              "itemQuantity": 1
            }
          ]
        }
      ],
      "totalAmount": "22",
      "realTotalAmount": "22",
      "totalDiscountAmount": "0",
      "couponList": [],
      "deliveryInfo": {
        "deliveryType": "立即送出",
        "deliveryAddress": "xxxx小区-xx栋",
        "addressDetail": "xxx号房间",
        "customerNickname": "张三",
        "mobilePhone": "152****6666",
        "expectDeliveryTime": ""
      },
      "createTime": "2026-02-09 14:42:51",
      "deliveryPrice": "6",
      "realDeliveryPrice": "6",
      "productPrice": "16",
      "takeWay": "locker-in",
      "pickupCode": "",
      "lockerCode": "",
      "mealAssistance": {
        "code": "",
        "name": "",
        "items": [
          {
            "name": ""
          }
        ]
      }
    }
  }
}
```
### 4.2.10 查询订单详情

**描述：**  
>查询订单详情。当用户希望查询订单状态、订单进度等信息时，可以使用该工具获取。

**入参：**

| name | description |
|------|-------------|
| orderId | 订单号，必填 |

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:44:29",
  "traceId": "341e2dce2af4a61497b52097125a8a77",
  "data": {
    "orderId": "1030938730000733964700499858",
    "orderStatus": "待支付",
    "storeName": "xxxxx门店",
    "orderProductList": [
      {
        "productName": "DC套餐测试",
        "quantity": 1,
        "price": "16",
        "comboItemList": [
          {
            "itemName": "汉堡包-pool1 加一份奶油(加)",
            "itemQuantity": 1
          }
        ]
      }
    ],
    "totalAmount": "22",
    "realTotalAmount": "22",
    "totalDiscountAmount": "0",
    "couponList": [],
    "deliveryInfo": {
      "deliveryType": "立即送出",
      "deliveryAddress": "xxxx小区-xx栋",
      "addressDetail": "xxx号房间",
      "customerNickname": "张三",
      "mobilePhone": "152****6666",
      "expectDeliveryTime": ""
    },
    "createTime": "2026-02-09 14:42:51",
    "deliveryPrice": "6",
    "realDeliveryPrice": "6",
    "productPrice": "16",
    "takeWay": "locker-in",
    "pickupCode": "",
    "lockerCode": "",
    "mealAssistance": {
      "code": "",
      "name": "",
      "items": [
        {
          "name": ""
        }
      ]
    }
  }
}
```

---

## 4.3 麦麦日历

### 4.3.1 活动日历查询工具

**描述：**
> 查询麦当劳中国当月的营销活动日历，返回进行中、往期和未来日期的活动。适用于查看用户进行中和即将到来的可参与活动，还可查询用户对活动的订阅状态。

**入参：**

|     name      |                              description                               |
|:-------------:|:----------------------------------------------------------------------:|
| specifiedDate | 查询指定日期范围的活动(格式: yyyy-MM-dd)，返回该日期附近一共三天的活动，非必传，默认查询当前月的活动，查询今天的活动不需要入参 |

**响应内容：**
> 注意：活动内容为营销文案，可能包含表情符号等营销元素。

示例：
``` markdown
### 当前时间：2025-12-09 14:48:42
### 活动列表：
#### 12月8日 往期回顾
-   **活动标题**：小女警沙发！12月12日麦麦商城见！⏰\
    **活动内容介绍**：❗️超萌酷小女警爱心沙发来袭
    😍小女警+汉堡刺绣+粉嫩配色
    ✨满满英雄力和快乐能量！
    💥12月12日14:00准时发售
    👇提前预约，心动别错过！\
    **活动图片介绍**：\
    <img src="https://cms-cdn.mcd.cn/img/short-content/86a849ae4b9528e53ac595ffa1b39cf9.png" alt="" height="300" width="auto">
#### 12月9日 今日
-   **活动标题**：⏳倒计时！超人气「芝芝火腿扒堡」即将回归！\
    **活动内容介绍**：🍔松软芝芝火腿扒堡搭配鲜萃咖啡
    💥一堡+一咖啡！还是天天￥9.9！
    ☀一口下去给元气满满的早晨充能！
    ⏰12月15日起，超值低价闭眼冲！\
    **活动图片介绍**：\
    <img src="https://cms-cdn.mcd.cn/img/short-content/39bb241887869bca544b67a355cb616f.jpg" alt="" height="300" width="auto">
```

---

## 4.4 麦麦省领券

### 4.4.1 麦麦省券列表查询

**描述：**
> 查询用户当前可领取的麦麦省的优惠券列表。返回券名称、图片、状态和促销标签。当用户询问有什么优惠、可以领什么券时使用此工具。

**入参：**
> 无需入参

**响应内容：**

示例：
``` markdown
### 麦麦省优惠券列表：
- 优惠券标题：11.9元麦乐鸡 \
  状态：已领取 \
  优惠券图片：\
    <img src="https://img.mcd.cn/cms/images/077b86c9268d33a0.png" height="auto" width="300">
- 优惠券标题：9.9元薯你最甜 \
  状态：未领取 \
  优惠券图片：\
    <img src="https://img.mcd.cn/cms/images/0853e0f8882dc66e.png" height="auto" width="300">
- 优惠券标题：北非蛋风味麦满分 \
  状态：不可领取 \
  优惠券图片：\
    <img src="https://img.mcd.cn/cms/images/6714e5753b475d96.png" height="auto" width="300">
```

### 4.4.2 麦麦省一键领券

**描述：**
> 自动领取麦麦省所有当前可用的麦当劳优惠券。无需指定具体的优惠券和couponId，系统会自动领取用户可领的所有券。当用户说"帮我领券"、"自动领取优惠券"、"一键领券"时使用此工具。

**入参：**
> 无需入参

**响应内容：**

示例：
``` markdown
### 🎉 领券结果

**总计**: 1 张优惠券
**成功**: 1 张
**失败**: 0 张

---

#### ✅ 成功领取的优惠券：

- **9.9元薯你最甜**
  - couponId：8ED8D8BEBEBDEF26B615682E92EFAC86
  - couponCode：MCDD60T892ST5EV00N1090
  - 图片：<img src="https://img.mcd.cn/cms/images/0853e0f8882dc66e.png" alt="9.9元薯你最甜" height="200" width="auto">
```

### 4.4.3 我的优惠券查询

**描述：**
> 查询我有哪些可用的优惠券。就像打开麦当劳App的"我的优惠券"页面，能看到所有可以用来点餐的优惠券列表。 **包括但不限于使用场景**： - 用户想知道自己有哪些优惠券可以用 - 检查优惠券的有效期和使用条件 - 查看优惠券数量和状态

**入参：**
> 无需入参

**响应内容：**

示例：
``` markdown
# 您的优惠券列表

共 1 张可用优惠券

## 9.9元薯你最甜
- **优惠**: ¥9.9 (用券价格)
- **有效期**: 2025-12-09 00:00-2026-02-12 23:59
- **领取时间**: 今日收到
- **标签**: 到店专用、外送专用

<img src="https://mcd-portal-prod-cos1-1300270282.cos.ap-shanghai.myqcloud.com/campaign/prod/campaign-offer/coupon/66f226e438714697b9f15d1a753d91ba/%E5%A4%A7%E8%96%AF%E6%9D%A1.jpg?sign=q-sign-algorithm%3Dsha1%26q-ak%3DAKIDCD6mEcX25tVrjNxiPvEICas0uXyBKIBs%26q-sign-time%3D1763363214%3B1921043214%26q-key-time%3D1763363214%3B1921043214%26q-header-list%3D%26q-url-param-list%3D%26q-signature%3D59b757fb6a863e8debfcdce8e595bf268d9c0cb9" alt="悟空加价特调免费券0411" height="300" width="auto">

```
---


## 4.5 麦麦商城
### 4.5.1 我的积分查询

**描述：**
>查询用户的积分账户信息，包含历史积分累计、可用积分数量、过期积分数量等；当用户询问账户下积分数量情况时使用此工具。

**入参：**
>无需入参

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 13:58:34",
  "traceId": "713a18de45735089a3b8a0e8a7cf3e36",
  "data": {
    "availablePoint": "7592",
    "accumulativePoint": "141760.94",
    "currency": "麦当劳积分",
    "currentMouthExpirePoint": "0",
    "expiredPoint": "0",
    "frozenPoint": "30",
    "lastMouthExpirePoint": "0",
    "nextMouthExpirePoint": "0",
    "usedPoint": "115474.14"
  }
}
```
### 4.5.2 积分兑换商品列表

**描述：**
>查询麦麦商城内，可以用积分兑换的餐品券（不包含积分兑换的实物或者积分兑换的第三方码）。 当用户询问可以用积分兑换哪些商品券时使用此工具。

**入参：**
> 无需入参

**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 13:59:12",
  "traceId": "43d1d331b103b29bd07a93d441409804",
  "data": [
    {
      "spuName": "中杯拿铁/美式500积分",
      "spuId": 542,
      "skuId": 10997,
      "spuImage": "https://img.mcd.cn/gallery/b6e0616d94c1f733.png",
      "point": "500",
      "shopId": 2,
      "selling": "",
      "upTime": "2026-02-02 00:00:00",
      "downTime": "2026-04-30 23:59:59"
    }
  ]
}
```
### 4.5.3 积分兑换商品详情

**描述：**  
查询可用积分兑换的商品券详细信息。  
当用户想了解某个商品券的详细信息（如使用方式、有效期等）时，可以使用此工具。

**入参：**

| name | description |
|------|-------------|
| spuId | 用户在积分兑换商品列表中选择的商品spuId，表示这个商品的 id，必传，Long 类型|


**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:03:20",
  "traceId": "801b027a09821d95f8a8d26337245ea7",
  "data": {
    "spuName": "中杯拿铁/美式500积分",
    "spuId": 542,
    "skuId": 10997,
    "images": [
      "https://img.mcd.cn/gallery/b6e0616d94c1f733.png"
    ],
    "points": "500",
    "shopId": 2,
    "extTradePrice": "7",
    "selling": "",
    "note": "note",
    "detail": "detail",
    "upDate": "2026-02-02 00:00:00",
    "downDate": "2026-04-30 23:59:59"
  }
}
```
### 4.5.4 积分兑换商品下单

**描述：**
>支持用户使用积分兑换商品券，完成积分检验、积分扣减以及发券。当用户需要使用积分兑换某种商品券时使用此工具。

**入参：**

| name | description |
|------|-------------|
| skuId | 用户在积分兑换商品列表中选择的商品skuId，表示这个商品具体的规格 id，必传，Long 类型 |
| count | 表示用户要兑换券的数量，非必传，Integer 类型，默认=1 |


**响应内容：**

示例：
```json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2026-02-09 14:04:51",
  "traceId": "da02dd48f941d934e4765627acdc27f4",
  "data": {
    "orderId": "ECS1202144786604392448",
    "coupons": [
      {
        "couponId": "2BCEFFB7E1CEA6BD32A43C45A1CE80B3",
        "orderItemId": "202144786647384064",
        "couponCodes": [
          "MCDD6E08N9100KC050F087"
        ],
        "orderItemStatus": 1
      }
    ],
    "orderStatus": 30,
    "status": 1
  }
}
```

---

## 4.6 通用

### 4.6.1 当前时间信息查询工具

**描述：**
> 获取当前时间信息 - 返回当前服务器的完整时间信息，包括： - 时间戳（毫秒级） - 格式化的日期时间 - 年月日信息 - 时区和UTC时间 在你不知道当前时间，并且用户需要指定日期查询活动日历的时候有用

**入参：**
> 无需入参

**响应内容：**

示例：
``` json
{
  "success": true,
  "code": 200,
  "message": "请求成功",
  "datetime": "2025-12-11 17:57:05",
  "traceId": "7b7255e6b4682f35dc0b4df39ffcf02d",
  "data": {
    "timestamp": 1765447025424,
    "datetime": "2025-12-11T17:57:05.424",
    "formatted": "2025-12-11 17:57:05",
    "date": "2025-12-11",
    "year": 2025,
    "month": 12,
    "day": 11,
    "dayOfWeek": "THURSDAY",
    "timezone": "GMT+08:00",
    "offset": "+08:00",
    "utc": "2025-12-11T09:57:05.425Z"
  }
}
```
---

# 5. 版本日志

|    Date    | Version | Description                        |
|:----------:|:-------:|------------------------------------|
| 2025-12-09 |  1.0.0  | 麦麦日历和麦麦省领券 MCP Server              |
| 2026-01-23 |  1.0.1  | 增加了“餐品营养信息列表”Tool，我们缩短了URL 以便于大家连接 |
| 2026-02-13 |  1.0.2  | 增加了麦乐送点餐与积分兑换券场景的Tools             |
| 2026-04-02 |  1.0.3  | 增加了到店取餐与团餐场景的Tools              |

---

# 6. 注意事项：

- 允许个人以非商业用途复制并使用本仓库中的示例配置、参数、JSON 或示例代码，并仅限用于实现与麦当劳MCP服务的连接与使用。

- 使用 麦当劳MCP 服务须遵守麦当劳中国的《使用条款》及《麦当劳MCP 服务规则》，并在申请MCP Token时同意前述条款。

- 未经书面授权，不得将本仓库内容用于商业售卖、付费分发、引流变现或任何暗示官方背书、误导公众的用途；亦不得用于任何违法、违规或黑灰产相关行为。

- 本仓库内容按“现状”提供，不构成任何形式的保证或承诺。

- 本仓库不构成对麦当劳及其关联方商标的任何授权。

- 请妥善保管您的MCP Token，避免泄露或被他人使用。

<p align="center">© 2026 McDonald’s. All Rights Reserved.</p>

