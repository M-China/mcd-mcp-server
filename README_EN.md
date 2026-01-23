# Introduction
**What is McDonald's China MCP Server?**

- McDonald's China MCP Server is a data interaction interface service that complies with the Model Context Protocol (MCP) standard, provided by McDonald's China for use in mainland China (excluding Hong Kong, Macau, and Taiwan).
- McDonald's China MCP Server now covers four core business interfaces, providing developers with integration support for McDonald's brand information and member account benefits. Currently supported functions include activity calendar queries, "MaiMaiSheng" coupon queries and claiming. More practical tools are under continuous development and will be launched soon. Stay tuned.

# 1. Apply for MCP Token

## McDonald's Open Platform URL: [McDonald's Open Platform](https://open.mcd.cn/mcp)

- **Step 1:** Click the **[Login]** button in the top right corner.
  <div class="img"><img src="https://img.mcd.cn/gallery/91178777592c9118.jpeg" alt="" width="1000" /></div>
- **Step 2:** Redirect to the login page and verify using your mobile number.
  <div class="img"><img src="https://img.mcd.cn/gallery/c7b5d9e9cdd2c786.png" alt="" width="1000" /></div>
  Upon successful login, you will be redirected to the homepage, and the "Login" button will change to "Console".
  <div class="img"><img src="https://img.mcd.cn/gallery/a854347bb1339ee1.jpeg" alt="" width="1000" /></div>
- **Step 3:** Apply for MCP Token.\
  Click "Console" in the top right corner to open the console popup.\
  Click the "Activate" button to request your MCP Token.
  <div class="img"><img src="https://img.mcd.cn/gallery/37434d0289646b80.png" alt="" width="1000" /></div>
- **Step 4:** Agree to the Service Agreement.
  <div class="img"><img src="https://img.mcd.cn/gallery/62916ae518d0876d.png" alt="" width="1000" /></div>
- **Step 5:** MCP Token application successful. You can copy it with one click.
  <div class="img"><img src="https://img.mcd.cn/gallery/3d14672fe32c8090.png" alt="" width="1000" /></div>

# 2. Quick Start
> The following section describes how to integrate the MCP Server into an MCP Client to start using MCP features.\
> McDonald's provides a remotely hosted MCP Server; users simply need to configure the access address and key in their MCP Client.


## 2.1 Access Address
> Server Access URL: https://mcp.mcd.cn/mcp-servers/mcd-mcp

## 2.2 Protocol and Security
> Connect using the **Streamable HTTP** protocol.\
> To identify user identity and permissions, the **Authorization** field must be included in the request header in the following format:
``` text
Authorization: Bearer YOUR_MCP_TOKEN
```

## 2.3 MCP Configuration JSON Example:
> For convenience, we provide a JSON configuration example.\
> Copy the configuration below, replace **YOUR_MCP_TOKEN** with your actual key, and paste it into the MCP Server configuration of your MCP Client.
``` json
{
  "mcpServers": {
    "mcd-mcp": {
      "type": "streamablehttp",
      "url": "https://mcp.mcd.cn/mcp-servers/mcd-mcp",
      "headers": {
        "Authorization": "Bearer YOUR_MCP_TOKEN"
      }
    }
  }
}
```

## 2.4 Important Notes:
> - ⚠️ The current MCP Server only supports MCP **Version 2025-06-18** and earlier.
> - Each Token allows a maximum of 600 requests per minute. Exceeding this limit will return a 429 error code. Please manage your request frequency reasonably.
> - Please ensure your MCP Client supports the Streamable HTTP protocol.
> - Please keep your MCP Token secure and avoid disclosing it to others.

## 2.5 Integration Tutorials for Different Platforms:
### 2.5.1 Cherry Studio
> **Prerequisites**: You must have applied for a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
> Reference: Cherry Studio Official Documentation: https://docs.cherry-ai.com/advanced-basic/mcp

1. Open Cherry Studio and enter the Settings page.
2. Select the "MCP" tab.
3. Click the "Add" button.
4. In the dropdown menu, select "Import from JSON".

<div class="img"><img src="https://img.mcd.cn/gallery/662175d6e573bb31.png" alt="" width="1000" /></div>

Paste the JSON copied from above, **remember to replace "YOUR_MCP_TOKEN"**, then click the "Confirm" button.

<div class="img"><img src="https://img.mcd.cn/gallery/932b5bea7c9a79eb.png" alt="" width="1000" /></div>

After adding, please toggle the switch to enable it.

<div class="img"><img src="https://img.mcd.cn/gallery/ade1966003d77e3b.png" alt="" width="1000" /></div>

Congratulations! You have successfully set up MCP! Go to the chat window to start using it!
<div class="img"><img src="https://img.mcd.cn/gallery/16721f738e7f631e.png" alt="" width="1000" /></div>


### 2.5.2 Cursor
> **Prerequisites**: You must have applied for a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
> Reference: Cursor Official Documentation: https://cursor.com/cn/docs/context/mcp

Open Cursor, click top menu [Settings] → [Tools & MCP]. Under "Installed MCP Servers", click [Add Custom MCP].

<div class="img"><img src="https://img.mcd.cn/gallery/b4817eeb8c597384.png" alt="" width="1000" /></div>

In the opened `mcp.json` file, fill in the JSON content copied from above. Remember to replace `YOUR_MCP_TOKEN` with your actual key. Click [Close] and select [Save].

<div class="img"><img src="https://img.mcd.cn/gallery/671f20806476f7f7.png" alt="" width="1000" /></div>

Return to the settings page; the McDonald's MCP tool should now appear as available, and the service status should show as [Connected].

<div class="img"><img src="https://img.mcd.cn/gallery/75a3dabf77fac237.png" alt="" width="1000" /></div>

Press CTRL/CMD + L to open the right-side Agent dialog. You can now directly input requests in the dialog and let the AI call the tools for us.

<div class="img"><img src="https://img.mcd.cn/gallery/fed973ae04371908.png" alt="" width="1000" /></div>


### 2.5.3 TRAE
> **Prerequisites**: You must have applied for a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
> Reference: TRAE Official Documentation: https://docs.trae.cn/ide/model-context-protocol

Open Trae, click [Settings] → [MCP] → [Manual Add] to add.

<div class="img"><img src="https://img.mcd.cn/gallery/1b29297767cc5458.png" alt="" width="1000" /></div>
<div class="img"><img src="https://img.mcd.cn/gallery/720beadfcd8c7573.png" alt="" width="1000" /></div>

In the manual configuration page, fill in the JSON content copied from above. Remember to replace `YOUR_MCP_TOKEN` with your actual key, then click [Confirm].

<div class="img"><img src="https://img.mcd.cn/gallery/a532f0555f6d0497.png" alt="" width="1000" /></div>

Return to the MCP page; the McDonald's MCP tool should now appear as available, and the service status should show as [Connected].

<div class="img"><img src="https://img.mcd.cn/gallery/abe84f630677bfd7.png" alt="" width="1000" /></div>

Return to the chat dialog and select [Builder with MCP].

<div class="img"><img src="https://img.mcd.cn/gallery/32970b601e173816.png" alt="" width="1000" /></div>
<div class="img"><img src="https://img.mcd.cn/gallery/68c6f494dfda0627.png" alt="" width="1000" /></div>

You can now directly input requests in the dialog and let the AI call the tools for us.
<div class="img"><img src="https://img.mcd.cn/gallery/4b82125a6902a916.png" alt="" width="1000" /></div>

# 3. Debugging Guide
## 3.1 Recommended MCP Clients


|    Client     |                                 Link                                 |
|:-------------:|:--------------------------------------------------------------------:|
| Cherry Studio |            https://docs.cherry-ai.com/advanced-basic/mcp             |
|    Cursor     |       https://cursor.com/cn/docs/context/mcp#protocol-support        |
|     Kiro      |                      https://kiro.dev/docs/mcp/                      |
|     Trae      |           https://docs.trae.ai/ide/model-context-protocol            |
|    VSCode     | https://code.visualstudio.com/docs/copilot/customization/mcp-servers |

## 3.2 Recommended LLMs

As of December 9, 2025

|    Vendor    |           Model           |
|:--------:|:----------------------:|
|   Qwen   | qwen-plus<br>qwen3-max |
|  Doubao  |    Doubao-Seed-1.6     |
|   Kimi   |           k2           |
|  Zhipu   |        GLM-4.6         |
|  Gemini  |  gemini-3-pro-preview  |
| Deepseek |     DeepSeek-V3.2      |


# 4. Tools
> Tools currently supported by the MCP Server.

## 4.1 Tool List

|     **Tool**      | **Name** |                     **Description**                      |
|:-----------------:|:--------:|:--------------------------------------------------------:|
| campaign-calender | Campaign Calendar Query Tool | Queries McDonald's China monthly marketing campaign calendar. Returns ongoing, past, and future activities. |
| available-coupons | "MaiMaiSheng" Coupon List Query | Queries the list of "MaiMaiSheng" coupons currently available for the user to claim. |
| auto-bind-coupons | One-Click Coupon Claiming | Automatically claims all currently available McDonald's "MaiMaiSheng" coupons. No need to specify coupons or couponIds; the system automatically claims all coupons the user is eligible for. |
|    my-coupons     | My Coupons Query | Queries which coupons I currently have available. Just like opening the "My Coupons" page in the McDonald's App, seeing a list of all coupons valid for ordering. |
|   now-time-info   | Get Current Time Info | Returns complete current time information, allowing the LLM to know the current date and time. |
| list-nutrition-foods | Food Nutrition Information List | Retrieves the nutritional component data of common McDonald's menu items, including information on energy, protein, fat, carbohydrates, sodium, calcium, etc. It is useful when users inquire about the calorie and nutritional content of McDonald's menu items, and when helping users assemble meals with a specified calorie content. |


### 4.1.1 Campaign Calendar Query Tool

**Description:**
> Queries McDonald's China monthly marketing campaign calendar. Returns ongoing, past, and future activities. Suitable for checking campaigns the user is currently participating in or upcoming ones, and can also check the user's subscription status for campaigns.

**Input Parameters:**

|     name      |                              description                               |
|:-------------:|:----------------------------------------------------------------------:|
| specifiedDate | Query activities for a specific date range (Format: yyyy-MM-dd). Returns activities for three days surrounding that date. Optional; defaults to the current month's activities. No parameter needed to query today's activities. |

**Response Content:**

Example:
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

### 4.1.2 "MaiMaiSheng" Coupon List Query

**Description:**
> Queries the list of "MaiMaiSheng" coupons currently available for the user to claim. Returns coupon name, image, status, and promotional tags. Use this tool when the user asks "what discounts are available" or "what coupons can I claim".

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
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

### 4.1.3 One-Click Coupon Claiming

**Description:**
> Automatically claims all currently available McDonald's "MaiMaiSheng" coupons. No need to specify coupons or couponIds; the system automatically claims all coupons the user is eligible for. Use this tool when the user says "help me claim coupons", "auto claim coupons", or "one-click claim".

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
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

### 4.1.4 My Coupons Query

**Description:**
> Queries which coupons I currently have available. Just like opening the "My Coupons" page in the McDonald's App, seeing a list of all coupons valid for ordering. **Includes but not limited to usage scenarios**: - User wants to know what coupons they can use - Checking coupon validity and usage conditions - Viewing coupon quantity and status.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
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

### 4.1.5 Current Time Info Query Tool
**Description:**
> Get current time information - Returns complete current server time information, including: - Timestamp (milliseconds) - Formatted datetime - Year/Month/Day info - Timezone and UTC time. Useful when you don't know the current time but the user requests a campaign calendar query for a specific date.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
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

# 5. Version Log

|    Date    | Version | Description           |
|:----------:|:-------:|-----------------------|
| 2025-12-09 |  1.0.0  | MaiMai Calendar and MaiMaiSheng Coupon MCP Server |
| 2026-01-23 |  1.0.1  | Added the "Food Nutrition Information List" Tool |

---

# 6. Important Notes

- Individual users are permitted to copy and use the sample configurations, parameters, JSON, or example code in this repository for non-commercial purposes only, and solely for establishing connection with and using the McDonald's China MCP Server.

- Use of the McDonald's China MCP Server must comply with McDonald's China's Terms of Use and McDonald's MCP Service Rules, which must be agreed to when applying for an MCP Token.

- Without written authorization, the content of this repository may not be used for:
	- Commercial sale or paid distribution
	- Traffic monetization or revenue generation
	- Any purpose implying official endorsement or misleading the public
	- Any illegal, unauthorized, or gray/black market activities

- The content of this repository is provided "as is" without any form of warranty or commitment.

- This repository does not constitute authorization to use McDonald's or its affiliates' trademarks.

- Please keep your MCP Token secure and avoid disclosure or unauthorized use by others.

<p align="center">© 2026 McDonald’s. All Rights Reserved.</p>
