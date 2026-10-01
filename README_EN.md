<p align="center">
  <a href="https://open.mcd.cn/mcp" target="_blank">
    <img src="https://img.mcd.cn/gallery/3fa1addc20b6d2d8.jpeg" align="middle" width = "1000" />
  </a>
</p>

<p align="center">
	<a href="README.md">简体中文</a> | English
</p>

# Introduction

**What is McDonald's MCP Service?**
- McDonald's MCP Service is a data interaction interface service that complies with the Model Context Protocol (MCP) standard, provided by McDonald's China for use in mainland China (excluding Hong Kong, Macau, and Taiwan).
- McDonald's MCP Service now covers McDelivery ordering, in-store pickup, group meals, points redemption vouchers, activity calendar queries, and other business scenarios. More practical tools are under continuous development and will be launched soon.
- Official website of the McDonald's MCP Server Open Platform: [https://open.mcd.cn/mcp](https://open.mcd.cn/mcp)

# 1. Apply for MCP Token
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
> McDonald's China provides a remotely hosted MCP Server; users simply need to configure the access address and MCP Token in their MCP Client.


## 2.1 Access Address
> Server Access URL: `https://mcp.mcd.cn`

## 2.2 Protocol and Security
> Connect using the **Streamable HTTP** protocol.\
> To identify user identity and permissions, the **Authorization** field must be included in the request header in the following format:
``` text
Authorization: Bearer YOUR_MCP_TOKEN
```

## 2.3 MCP Configuration JSON Example:
> For convenience, we provide a JSON configuration example.\
> Copy the configuration below, replace **YOUR_MCP_TOKEN** with your actual MCP Token, and paste it into the MCP Server configuration of your MCP Client.
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

## 2.4 Important Notes:
> - Each Token allows a maximum of 600 requests per minute. Exceeding this limit will return a 429 error code. Please manage your request frequency reasonably.
> - Please ensure your MCP Client supports the Streamable HTTP protocol.
> - Please keep your MCP Token secure and avoid disclosing it to others.

## 2.5 Recommended MCP Clients

|    Client     |                                 Link                                 |
|:-------------:|:--------------------------------------------------------------------:|
|   WorkBuddy   | https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Connector |
| Cherry Studio |            https://docs.cherry-ai.com/advanced-basic/mcp             |
|    Cursor     |       https://cursor.com/cn/docs/context/mcp#protocol-support        |
|     Kiro      |                      https://kiro.dev/docs/mcp/                      |
|     Trae      |           https://docs.trae.cn/ide/model-context-protocol            |
|    VSCode     | https://code.visualstudio.com/docs/copilot/customization/mcp-servers |

## 2.6 Integration Tutorials for Different Platforms:
### 2.6.1 Cherry Studio
> **Prerequisites**: Requires application for a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
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

Configuration complete. You can now use MCP features in the chat window.
<div class="img"><img src="https://img.mcd.cn/gallery/16721f738e7f631e.png" alt="" width="1000" /></div>


### 2.6.2 Cursor
> **Prerequisites**: Requires application for a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
> Reference: Cursor Official Documentation: https://cursor.com/cn/docs/context/mcp

Open Cursor, click top menu [Settings] → [Tools & MCP]. Under "Installed MCP Servers", click [Add Custom MCP].

<div class="img"><img src="https://img.mcd.cn/gallery/b4817eeb8c597384.png" alt="" width="1000" /></div>

In the opened `mcp.json` file, fill in the JSON content copied from above. Remember to replace `YOUR_MCP_TOKEN` with your actual token. Click [Close] and select [Save].

<div class="img"><img src="https://img.mcd.cn/gallery/671f20806476f7f7.png" alt="" width="1000" /></div>

Return to the settings page; the McDonald's MCP tool should now appear as available, and the service status should show as [Connected].

<div class="img"><img src="https://img.mcd.cn/gallery/75a3dabf77fac237.png" alt="" width="1000" /></div>

Press CTRL/CMD + L to open the right-side Agent dialog. You can now directly input requests in the dialog and let the AI call the tools for us.

<div class="img"><img src="https://img.mcd.cn/gallery/fed973ae04371908.png" alt="" width="1000" /></div>


### 2.6.3 TRAE
> **Prerequisites**: Requires application for a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
> Reference: TRAE Official Documentation: https://docs.trae.cn/ide/model-context-protocol

Open Trae, click [Settings] → [MCP] → [Manual Add] to add.

<div class="img"><img src="https://img.mcd.cn/gallery/1b29297767cc5458.png" alt="" width="1000" /></div>
<div class="img"><img src="https://img.mcd.cn/gallery/720beadfcd8c7573.png" alt="" width="1000" /></div>

In the manual configuration page, fill in the JSON content copied from above. Remember to replace `YOUR_MCP_TOKEN` with your actual token, then click [Confirm].

<div class="img"><img src="https://img.mcd.cn/gallery/a532f0555f6d0497.png" alt="" width="1000" /></div>

Return to the MCP page; the McDonald's MCP tool should now appear as available, and the service status should show as [Connected].

<div class="img"><img src="https://img.mcd.cn/gallery/abe84f630677bfd7.png" alt="" width="1000" /></div>

Return to the chat dialog and select [Builder with MCP].

<div class="img"><img src="https://img.mcd.cn/gallery/32970b601e173816.png" alt="" width="1000" /></div>
<div class="img"><img src="https://img.mcd.cn/gallery/68c6f494dfda0627.png" alt="" width="1000" /></div>

You can now directly input requests in the dialog and let the AI call the tools for us.
<div class="img"><img src="https://img.mcd.cn/gallery/4b82125a6902a916.png" alt="" width="1000" /></div>

## 2.7 Error Code Description

| code | Reason | Handling Suggestion |
|:----:|:----:|:---------|
| 401 | MCP Token is invalid, expired, or not provided | Check Authorization request header and MCP Token configuration |
| 429 | Rate limit triggered (exceeds 600 requests/minute) | Reduce request frequency and control call intervals appropriately |

# 3. Tool List
> Tools currently supported by the MCP Server.

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
      <td>Food Nutrition Information List</td>
      <td>Retrieves nutritional data for common McDonald's menu items, including energy, protein, fat, carbohydrates, sodium, and calcium. Use this tool when users ask about calories or nutrition, or need help assembling a meal with a specified calorie target.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-query-addresses</td>
      <td>Get User Delivery Address List</td>
      <td>Queries the user's saved delivery addresses for selecting a delivery destination when placing a delivery order.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-create-address</td>
      <td>Add Delivery Address</td>
      <td>Creates a new delivery address when the user has no saved address or needs to add another one.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">delivery-query-stores</td>
      <td>Query Available Delivery Stores</td>
      <td>Queries stores near the user's delivery address that can fulfill a delivery order.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meal-assistance</td>
      <td>Query Meal Assistance Services</td>
      <td>Queries meal assistance services supported by the store for corporate group meal scenarios.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-nearby-stores</td>
      <td>Query Nearby Available Stores</td>
      <td>Queries McDonald's restaurants near the address provided by the user.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-store-coupons</td>
      <td>Query Available Coupons for Current Store</td>
      <td>Queries coupons available at the current store for selecting an applicable discount when ordering.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meals</td>
      <td>Query Currently Available Menu Items</td>
      <td>Queries the current store's available menu, including categories, product codes, and tags, for selecting products when ordering.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-meal-detail</td>
      <td>Query Menu Item Details</td>
      <td>Queries combo composition and available replacement options based on a product code.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">calculate-price</td>
      <td>Calculate Product Price</td>
      <td>Calculates product amounts, delivery fees, discounts, and the total payable for the user's selected products, optionally including coupons.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">create-order</td>
      <td>Create Order</td>
      <td>Creates an order using store information, dining method, and selected products, and returns the order details and payment link.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">cancel-order</td>
      <td>Cancel Order</td>
      <td>Cancels a food order when the user requests order cancellation.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-order</td>
      <td>Query Order Details</td>
      <td>Queries order status, order contents, and delivery information so the user can check progress or confirm order details.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">order-list</td>
      <td>Query Order History</td>
      <td>Queries recent in-store and delivery orders. For MaiMai Mall orders, use mall-order-list instead.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">campaign-calendar</td>
      <td>Campaign Calendar Query</td>
      <td>Queries McDonald's China's monthly marketing campaign calendar, including ongoing, past, and upcoming campaigns.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">available-coupons</td>
      <td>Query MaiMaiSheng Coupon List</td>
      <td>Queries MaiMaiSheng coupons currently available for the user to claim.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">auto-bind-coupons</td>
      <td>Claim All MaiMaiSheng Coupons</td>
      <td>Automatically claims all currently available MaiMaiSheng coupons without requiring a specific coupon or couponId.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-coupons</td>
      <td>Query My Coupons</td>
      <td>Queries all available coupons in the user's account.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-account</td>
      <td>Query My Points</td>
      <td>Queries the user's points account, including available, accumulated, frozen, and expiring points.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-points-products</td>
      <td>Query MaiMai Mall Product List</td>
      <td>Queries MaiMai Mall products available for points redemption or cash purchase, excluding third-party redemption codes obtained with points.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-product-detail</td>
      <td>Query MaiMai Mall Product Details</td>
      <td>Queries product details, including images, points required, validity period, instructions, and descriptions.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-create-order</td>
      <td>Create Points Redemption Order</td>
      <td>Redeems virtual or physical products with points, validates and deducts points, issues vouchers or deducts physical inventory, and returns the redemption order number and voucher information.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">now-time-info</td>
      <td>Get Current Time Information</td>
      <td>Returns the complete current date and time so the LLM has accurate time context.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-lottery-info</td>
      <td>Query Points Lottery Campaign</td>
      <td>Queries the current points lottery campaign, including its status, prizes, draw costs, and the user's available resources.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">draw-lottery</td>
      <td>Draw Points Lottery</td>
      <td>Performs a points lottery draw, consumes points or draw chances, and returns the result and prize information.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-my-prizes</td>
      <td>Query My Prizes</td>
      <td>Queries the user's points lottery prize history with pagination, ordered by winning time in descending order.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-order-list</td>
      <td>Query MaiMai Mall Orders</td>
      <td>Queries MaiMai Mall purchase and redemption orders from the past year.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">mall-order-detail</td>
      <td>Query MaiMai Mall Order Details</td>
      <td>Queries MaiMai Mall order details, including points paid, amount paid, and order status.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-party-city</td>
      <td>Query Themed Event Cities</td>
      <td>Queries cities participating in a themed event associated with a product.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-party-store</td>
      <td>Query Themed Event Stores</td>
      <td>Queries stores participating in a themed event within a selected city.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-partystore-date</td>
      <td>Query Available Themed Event Dates</td>
      <td>Queries available reservation dates for a themed event at a selected store.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">query-partystore-session</td>
      <td>Query Available Themed Event Sessions</td>
      <td>Queries available themed event sessions for a selected store and date.</td>
    </tr>
    <tr>
      <td style="white-space: nowrap; text-align: center;">party-order-create</td>
      <td>Create Themed Event Order</td>
      <td>Creates a themed event order after the user selects a city, store, date, and session.</td>
    </tr>
  </tbody>
</table>

# 4. Version Log

|    Date    | Version | Description |
|:----------:|:-------:|-------------|
| 2025-12-09 |  1.0.0  | Launched the MaiMai Calendar and MaiMaiSheng coupon features for the MCP Server |
| 2026-01-23 |  1.0.1  | Added the Food Nutrition Information List tool and shortened the URL for easier connection |
| 2026-02-13 |  1.0.2  | Added tools for McDelivery ordering and points redemption vouchers |
| 2026-04-02 |  1.0.3  | Added tools for in-store pickup and corporate group meal ordering |
| 2026-05-21 |  1.0.4  | Added points redemption for physical goods and MaiMai Mall order queries; added Drive-Through ordering and reservations for all ordering scenarios |
| 2026-06-16 |  1.0.5  | Added support for replacing items in combos and customizing selected menu items |
| 2026-07-16 |  1.0.6  | Added order history queries, discounted-price display, and McGold Card and Breakfast Card add-on purchases |
| 2026-07-29 |  1.0.7  | Added themed-event browsing, reservations, and ordering for McDonald's parties, tasting events, and similar activities |
| 2026-08-27 |  1.0.8  | Added points lottery tools for viewing campaign information, drawing, and checking prizes |
| 2026-09-10 |  1.0.9  | Added order cancellation, tableware selection, and McDelivery order notes; added pickup-locker QR codes for dine-in and takeaway scenarios |

---

# 5. Important Notes

- Individual users may copy and use the sample configurations, parameters, JSON, or example code in this repository for non-commercial purposes only, and solely to connect to and use the McDonald's MCP Service.

- Use of the McDonald's MCP Service must comply with McDonald's China's Terms of Use and McDonald's MCP Service Rules, which users must accept when applying for an MCP Token.

- Without written authorization, this repository's content may not be used for commercial sale, paid distribution, traffic monetization, or any purpose implying official endorsement or misleading the public; nor may it be used for illegal, non-compliant, or illicit/gray-market activities.

- This repository's content is provided "as is" without any form of warranty or commitment.

- This repository does not grant any authorization to use McDonald's or its affiliates' trademarks.

- Keep your MCP Token secure and prevent disclosure or unauthorized use by others.

<p align="center">© 2026 McDonald’s. All Rights Reserved.</p>
