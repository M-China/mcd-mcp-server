<p align="center">
  <a href="https://open.mcd.cn/mcp" target="_blank">
    <img src="https://img.mcd.cn/gallery/3fa1addc20b6d2d8.jpeg" align="middle" width = "1000" />
  </a>
</p>

<p align="center">
	<a href="README.md">简体中文</a> | English
</p>

# Introduction
**What is McDonald's China MCP Server?**
- McDonald's China MCP Server is a data interaction interface service that complies with the Model Context Protocol (MCP) standard, provided by McDonald's China for use in mainland China (excluding Hong Kong, Macau, and Taiwan).
- McDonald's China MCP Server now covers five core business interfaces, providing developers with integration support for McDonald's brand information and member account benefits. Currently supported functions include McDelivery ordering, points redemption vouchers, activity calendar queries, and "MaiMaiSheng" coupon queries and claiming. More practical tools are under continuous development and will be launched soon. Stay tuned.

# News
- **[2026-02] `Feature`:** We have added "McDelivery Ordering" and "Points Redemption Vouchers" feature modules, supporting complete food delivery and points redemption services. [View Tool Details](#4-tools)
- **[2026-01] `Feature`:** We have added the "Food Nutrition Information List" tool, allowing users to query nutritional data for common McDonald's menu items, including calories and nutrition information. [View Tool Details](#4-tools)
- **[2025-12] `Release`:** We released McDonald's MCP Server version 1.0.0, providing activity calendar queries and MaiMaiSheng coupon claiming features. Try it now! See the [Quick Start](#2-quick-start) section below for integration tutorials.

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
> Server Access URL: https://mcp.mcd.cn

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
      "url": "https://mcp.mcd.cn",
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
> **Prerequisites**: Requires a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
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
> **Prerequisites**: Requires a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
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
> **Prerequisites**: Requires a McDonald's China MCP Token. Tutorial: [Apply for MCP Token](#1-apply-for-mcp-token)\
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

As of February 12, 2026

|  Vendor  |         Model          |
|:--------:|:----------------------:|
|   Qwen   | qwen-plus<br>qwen3-max |
|  Doubao  |    Doubao-Seed-1.6     |
|   Kimi   |          k2.5          |
|  Zhipu   |         GLM-5          |
|  Gemini  | gemini-3-flash-preview |
| Deepseek |     DeepSeek-V3.2      |


# 4. Tools
> Tools currently supported by the MCP Server.

## 4.1 Tool List

|         **Tool**         |             **Name**              |                                                                                                                                                              **Description**                                                                                                                                                              |
|:------------------------:|:---------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|   list-nutrition-foods   |  Food Nutrition Information List  | Retrieves the nutritional component data of common McDonald's menu items, including information on energy, protein, fat, carbohydrates, sodium, calcium, etc. It is useful when users inquire about the calorie and nutritional content of McDonald's menu items, and when helping users assemble meals with a specified calorie content. |
| delivery-query-addresses |  Get User Delivery Address List   |                                                                           Queries the user's created delivery address list, used for selecting delivery addresses when ordering food delivery, and obtains corresponding store information (storeCode, beCode).                                                                           |
| delivery-create-address  |       Add Delivery Address        |                                                                                                          Used when the user has no delivery address or needs to add a new delivery address, for creating a new delivery address.                                                                                                          |
|   query-usable-coupons   | Query Available Coupons at Store  |                                                                                                              Queries the list of coupons available at the current store, used for selecting available coupons when ordering.                                                                                                              |
|       query-meals        |       Query Store Menu List       |                                                                                                   Queries the menu of meals available at the current store (categories, meal codes, tags, etc.), used for meal selection when ordering.                                                                                                   |
|       meal-detail        |        Query Meal Details         |                                                                                                          Queries meal details based on meal code (combo composition, default selections, etc.), used for viewing combo contents.                                                                                                          |
|     calculate-price      |       Calculate Item Price        |                                                                                                    Calculates item amount, delivery fee, discount amount, and total payable based on user's selected item list (may include coupons).                                                                                                     |
|       create-order       |       Create Delivery Order       |                                                                                                       Creates a delivery order based on store information, delivery address, and item list, returns order details and payment link.                                                                                                       |
|       query-order        |        Query Order Details        |                                                                                                   Queries order status, order content, delivery information, etc., used for users to check order progress or confirm order information.                                                                                                   |
|    campaign-calendar     |   Campaign Calendar Query Tool    |                                                                                                                Queries McDonald's China monthly marketing campaign calendar. Returns ongoing, past, and future activities.                                                                                                                |
|    available-coupons     |  "MaiMaiSheng" Coupon List Query  |                                                                                                                              Queries the list of "MaiMaiSheng" coupons currently available for the user to claim.                                                                                                                               |
|    auto-bind-coupons     |     One-Click Coupon Claiming     |                                                                       Automatically claims all currently available McDonald's "MaiMaiSheng" coupons. No need to specify coupons or couponIds; the system automatically claims all coupons the user is eligible for.                                                                       |
|        my-coupons        |         My Coupons Query          |                                                                                     Queries which coupons I currently have available. Just like opening the "My Coupons" page in the McDonald's App, seeing a list of all coupons valid for ordering.                                                                                     |
|     query-my-account     |          My Points Query          |                                                                                                        Queries user points account information, including available points, accumulated points, frozen points, points about to expire, etc.                                                                                                        |
|   mall-points-products   |  Points Redemption Product List   |                                                                                            Queries meal vouchers that can be redeemed with points in MaiMai Mall (does not include physical items or third-party codes redeemed with points).                                                                                             |
|   mall-product-detail    | Points Redemption Product Details |                                                                                                Queries detailed information of specified points redemption product vouchers (images, points, validity period, description, details, etc.).                                                                                                |
|    mall-create-order     |  Points Redemption Product Order  |                                                                                       Uses points to redeem specified meal vouchers, completes points deduction and voucher issuance, returns redemption order number and voucher code information.                                                                                       |
|      now-time-info       |       Get Current Time Info       |                                                                                                                      Returns complete current time information, allowing the LLM to know the current date and time.                                                                                                                       |


## 4.2 Ordering

### 4.2.1 Food Nutrition Information List

**Description:**
> Retrieves nutritional component data for common McDonald's menu items, including energy, protein, fat, carbohydrates, sodium, calcium, etc. Useful when users inquire about calorie and nutritional content of McDonald's menu items, and when helping users assemble meals with a specified calorie target.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
``` json
{
    "success": true,
    "code": 200,
    "message": "Request succeeded",
    "datetime": "2026-01-23 09:32:44",
    "data": "[1]{productName,nutritionDescription,energyKj,energyKcal,protein,fat,carbohydrate,sodium,calcium}:\n  Sausage McMuffin,null,1288,308,16,16,24,781,213\n "
}
```
### 4.2.2 Get User Delivery Address List

**Description:**
> Queries the user's created delivery address list. Use this tool when the user has a McDonald's ordering need.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 14:29:28",
  "traceId": "f2a0d969353467c957fd6728166eb430",
  "data": {
    "addresses": [
      {
        "addressId": "1",
        "contactName": "<name>",
        "phone": "152****6666",
        "fullAddress": "xx Province xx City xxx Community x Building x Unit xxx Room",
        "storeCode": "12345",
        "storeName": "xxx",
        "beCode": "12345"
      }
    ]
  }
}
```
### 4.2.3 Add Delivery Address

**Description:**
> Used when the user has no delivery address or the current list does not contain the desired delivery address, allowing the user to add a new delivery address.

**Input Parameters:**

| name | description |
|------|-------------|
| city | City name, required. e.g. `Nanjing` |
| contactName | Contact name, required. e.g. `Li Ming` |
| gender | Gender, optional. e.g. `Mr.`, `Ms.` |
| phone | Contact phone number, required. 11-digit mobile number, e.g. `16666666666` |
| address | Delivery address, required. e.g. `Qingzhuyuan Building 9` |
| addressDetail | Delivery address unit/room number, required. e.g. `Unit 2, Room 508` |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 14:29:28",
  "traceId": "f2a0d969353467c957fd6728166eb430",
  "data": {
    "addressId": "1",
    "contactName": "<name>",
    "phone": "152****6666",
    "fullAddress": "xx Province xx City xxx Community x Building x Unit xxx Room",
    "storeCode": "12345",
    "storeName": "xxx",
    "beCode": "12345"
  }
}
```
### 4.2.4 Query Available Coupons at Store

**Description:**
> Queries coupons available to the user at the current store. Use this tool when the user asks what coupons are currently available.

**Input Parameters:**

| name | description |
|------|-------------|
| storeCode | Store code, required |
| beCode | BE code (Business Entity Code), required |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 14:32:41",
  "traceId": "0f694a844e393e6cb0717455d9229a24",
  "data": [
    {
      "title": "Delivery coupon secondary voucher",
      "couponId": "xxxxxxxxxx",
      "couponCode": "xxxxxx",
      "tradeDateTime": "2025-04-21 23:23:00-2026-07-01 23:59:59",
      "products": [
        {
          "productCode": "xxxxxxxxx",
          "productName": "Sweet Snack 1+1"
        }
      ]
    }
  ]
}
```
### 4.2.5 Query Store Menu List

**Description:**
> Queries the list of meals available at the current store. Use this tool when the user wants to view the store menu or place an order.

**Input Parameters:**

| name | description |
|------|-------------|
| storeCode | Store code, required |
| beCode | BE code (Business Entity Code), required |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 09:47:35",
  "traceId": "4b2b4de1d772dad2dc498597c65cf3af",
  "data": {
    "categories": [
      {
        "name": "Popular",
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
              "Half price for 2nd item"
            ]
          }
        ],
        "daypart": 8
      }
    ],
    "meals": {
      "920215": {
        "name": "Bacon Angus Thick Beef Burger Large Combo",
        "currentPrice": "55.5"
      },
      "9900008139": {
        "name": "DC Combo Test",
        "currentPrice": "14"
      },
      "9900008169": {
        "name": "Double Deep Sea Cod Burger",
        "currentPrice": "25"
      }
    }
  }
}
```
### 4.2.6 Query Meal Details

**Description:**
> Queries meal details based on the meal code returned from the menu list, including combo composition and other information. Use this tool when viewing meal details.

**Important Note:**
> Changing default selections is not supported in this version. More features will be available in future updates.

**Input Parameters:**

| name | description |
|------|-------------|
| code | Meal code, required |
| storeCode | Store code |
| beCode | BE code (Business Entity Code), required |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 14:37:19",
  "traceId": "21de60d22eea026cae0428f714359e2c",
  "data": {
    "code": "9900008139",
    "price": "14",
    "rounds": [
      {
        "id": 1,
        "name": "Hamburger",
        "quantity": 1,
        "maxQuantity": 1,
        "minQuantity": 1,
        "choices": [
          {
            "code": "1000",
            "name": "Hamburger-pool1",
            "quantity": 1,
            "maxQuantity": -1
          }
        ]
      }
    ]
  }
}
```
### 4.2.7 Calculate Item Price

**Description:**
> Calculates the price of items and discounts for the user's purchase. Use this tool when the user asks about the price of an item or a combination of items.

**Input Parameters:**

| name | description |
|------|-------------|
| storeCode | Store code (obtained from `deliveryQueryAddresses`) |
| beCode | BE code (Business Entity Code, obtained from `deliveryQueryAddresses`) |
| items | Item list (array) |

`items` field structure:

| name | description |
|------|-------------|
| productCode | Product code, required (if the user uses a coupon, productCode is the coupon product code) |
| quantity | Product quantity, required |
| couponId | Coupon ID, optional (if the user wants to use a coupon) |
| couponCode | Coupon code, optional (if the user wants to use a coupon) |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
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
        "productName": "DC Combo Test",
        "quantity": 1,
        "originalSubtotal": 1600,
        "subtotal": 1600
      }
    ]
  }
}
```
### 4.2.8 Create Delivery Order

**Description:**
> Creates a delivery order. Use this tool when the user wants to place an order.

**Input Parameters:**

| name | description |
|------|-------------|
| storeCode | Store code (obtained from `deliveryQueryAddresses`) |
| beCode | BE code (Business Entity Code, obtained from `deliveryQueryAddresses`) |
| items | Item list (array) |

`items` field structure:

| name | description |
|------|-------------|
| productCode | Product code, required (if the user uses a coupon, productCode is the coupon product code) |
| quantity | Product quantity, required |
| couponId | Coupon ID, optional (if the user wants to use a coupon) |
| couponCode | Coupon code, optional (if the user wants to use a coupon) |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 14:42:51",
  "traceId": "80572509920e2e1e4a4373ee9eeca070",
  "data": {
    "orderId": "1030938730000733964700499858",
    "payId": "11940981078137585664",
    "payH5Url": "https://m-sit.mcdchina.net/mcp/scanToPay?orderId=1030938730000733964700499858",
    "orderDetail": {
      "orderStatus": "Pending Payment",
      "storeName": "xxxxxx Store",
      "storeAddress": "xxxxx",
      "orderProductList": [
        {
          "productName": "DC Combo Test",
          "quantity": 1,
          "price": "16",
          "comboItemList": [
            {
              "itemName": "Hamburger-pool1 with extra cream (add)",
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
        "deliveryType": "Deliver Now",
        "deliveryAddress": "xxxx Community - xx Building",
        "addressDetail": "xxx Room",
        "customerNickname": "<name>",
        "mobilePhone": "152****6666",
        "expectDeliveryTime": ""
      },
      "createTime": "2026-02-09 14:42:51",
      "deliveryPrice": "6",
      "realDeliveryPrice": "6",
      "productPrice": "16"
    }
  }
}
```
### 4.2.9 Query Order Details

**Description:**
> Queries order details. Use this tool when the user wants to check order status, order progress, or other order information.

**Input Parameters:**

| name | description |
|------|-------------|
| orderId | Order ID, required |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request succeeded",
  "datetime": "2026-02-09 14:44:29",
  "traceId": "341e2dce2af4a61497b52097125a8a77",
  "data": {
    "orderId": "1030938730000733964700499858",
    "orderStatus": "Pending Payment",
    "storeName": "xxxxx Store",
    "orderProductList": [
      {
        "productName": "DC Combo Test",
        "quantity": 1,
        "price": "16",
        "comboItemList": [
          {
            "itemName": "Hamburger-pool1 with extra cream (add)",
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
      "deliveryType": "Deliver Now",
      "deliveryAddress": "xxxx Community - xx Building",
      "addressDetail": "xxx Room",
      "customerNickname": "<name>",
      "mobilePhone": "152****6666",
      "expectDeliveryTime": ""
    },
    "createTime": "2026-02-09 14:42:51",
    "deliveryPrice": "6",
    "realDeliveryPrice": "6",
    "productPrice": "16"
  }
}
```

---

## 4.3 MaiMai Calendar

### 4.3.1 Campaign Calendar Query Tool

**Description:**
> Queries McDonald's China monthly marketing campaign calendar. Returns ongoing, past, and future activities. Suitable for viewing ongoing and upcoming activities users can participate in, and can also query user subscription status for activities.

**Input Parameters:**

|     name      |                              description                               |
|:-------------:|:----------------------------------------------------------------------:|
| specifiedDate | Query activities for a specified date range (format: yyyy-MM-dd). Returns activities for three days around that date. Optional; defaults to querying current month's activities. No parameter needed to query today's activities. |

**Response Content:**

Example:
``` markdown
### Current Time: 2025-12-09 14:48:42
### Activity List:
#### December 8 Past Review
-   **Activity Title**: Powerpuff Girls Sofa! Coming to MaiMai Mall on December 12! ⏰\
    **Activity Content**: ❗️Super cute Powerpuff Girls heart sofa is here
    😍Powerpuff Girls + hamburger embroidery + pink color scheme
    ✨Full of hero power and happy energy!
    💥On sale December 12 at 14:00 sharp
    👇Pre-order now, don't miss out!\
    **Activity Image**:\
    <img src="https://cms-cdn.mcd.cn/img/short-content/86a849ae4b9528e53ac595ffa1b39cf9.png" alt="" height="300" width="auto">
#### December 9 Today
-   **Activity Title**: ⏳Countdown! Super popular "Cheese Ham Patty Burger" is coming back!\
    **Activity Content**: 🍔Soft cheese ham patty burger paired with fresh brewed coffee
    💥One burger + one coffee! Still only ¥9.9 every day!
    ☀One bite to energize your morning!
    ⏰Starting December 15, super value low price, go for it!\
    **Activity Image**:\
    <img src="https://cms-cdn.mcd.cn/img/short-content/39bb241887869bca544b67a355cb616f.jpg" alt="" height="300" width="auto">
```

---

## 4.4 MaiMaiSheng Coupons

### 4.4.1 MaiMaiSheng Coupon List Query

**Description:**
> Queries the list of "MaiMaiSheng" coupons currently available for the user to claim. Returns coupon name, image, status, and promotional tags. Use this tool when users ask about available deals or what coupons they can claim.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
``` markdown
### MaiMaiSheng Coupon List:
- Coupon Title: 11.9 Yuan McNuggets \
  Status: Claimed \
  Coupon Image:\
    <img src="https://img.mcd.cn/cms/images/077b86c9268d33a0.png" height="auto" width="300">
- Coupon Title: 9.9 Yuan Sweet Fries \
  Status: Not Claimed \
  Coupon Image:\
    <img src="https://img.mcd.cn/cms/images/0853e0f8882dc66e.png" height="auto" width="300">
- Coupon Title: North African Egg McMuffin \
  Status: Cannot Claim \
  Coupon Image:\
    <img src="https://img.mcd.cn/cms/images/6714e5753b475d96.png" height="auto" width="300">
```

### 4.4.2 MaiMaiSheng One-Click Coupon Claiming

**Description:**
> Automatically claims all currently available McDonald's coupons from MaiMaiSheng. No need to specify specific coupons or couponId; the system will automatically claim all coupons available to the user. Use this tool when users say "help me claim coupons", "automatically claim coupons", or "one-click claim".

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
``` markdown
### 🎉 Coupon Claiming Result

**Total**: 1 coupon
**Success**: 1
**Failed**: 0

---

#### ✅ Successfully Claimed Coupons:

- **9.9 Yuan Sweet Fries**
  - couponId: 8ED8D8BEBEBDEF26B615682E92EFAC86
  - couponCode: MCDD60T892ST5EV00N1090
  - Image: <img src="https://img.mcd.cn/cms/images/0853e0f8882dc66e.png" alt="9.9 Yuan Sweet Fries" height="200" width="auto">
```

### 4.4.3 My Coupons Query

**Description:**
> Queries what available coupons I have. Like opening the "My Coupons" page in the McDonald's APP, you can see all the coupon lists that can be used for ordering. **Including but not limited to use cases**: - Users want to know what coupons they can use - Check coupon validity period and usage conditions - View coupon quantity and status

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
``` markdown
# Your Coupon List

Total 1 available coupon

## 9.9 Yuan Sweet Fries
- **Discount**: ¥9.9 (price with coupon)
- **Valid Period**: 2025-12-09 00:00-2026-02-12 23:59
- **Claimed Time**: Received today
- **Tags**: In-store only, Delivery only

<img src="https://mcd-portal-prod-cos1-1300270282.cos.ap-shanghai.myqcloud.com/campaign/prod/campaign-offer/coupon/66f226e438714697b9f15d1a753d91ba/%E5%A4%A7%E8%96%AF%E6%9D%A1.jpg?sign=q-sign-algorithm%3Dsha1%26q-ak%3DAKIDCD6mEcX25tVrjNxiPvEICas0uXyBKIBs%26q-sign-time%3D1763363214%3B1921043214%26q-key-time%3D1763363214%3B1921043214%26q-header-list%3D%26q-url-param-list%3D%26q-signature%3D59b757fb6a863e8debfcdce8e595bf268d9c0cb9" alt="Wukong Premium Drink Free Coupon 0411" height="300" width="auto">

```

---

## 4.5 MaiMai Mall

### 4.5.1 My Points Query

**Description:**
> Queries the user's points account information, including historical accumulated points, available points, expired points, etc. Use this tool when users inquire about their account points balance.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request successful",
  "datetime": "2026-02-09 13:58:34",
  "traceId": "713a18de45735089a3b8a0e8a7cf3e36",
  "data": {
    "availablePoint": "7592",
    "accumulativePoint": "141760.94",
    "currency": "McDonald's Points",
    "currentMouthExpirePoint": "0",
    "expiredPoint": "0",
    "frozenPoint": "30",
    "lastMouthExpirePoint": "0",
    "nextMouthExpirePoint": "0",
    "usedPoint": "115474.14"
  }
}
```

### 4.5.2 Points Redemption Product List

**Description:**
> Queries meal vouchers that can be redeemed with points in the MaiMai Mall (excluding physical items or third-party codes redeemable with points). Use this tool when users inquire about what product vouchers can be redeemed with points.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request successful",
  "datetime": "2026-02-09 13:59:12",
  "traceId": "43d1d331b103b29bd07a93d441409804",
  "data": [
    {
      "spuName": "Medium Latte/Americano 500 Points",
      "spuId": 542,
      "skuId": 10997,
      "spuImage": "https://cdn-test.mcdchina.net/ecs/b6e0616d94c1f733.png",
      "point": "500",
      "shopId": 2,
      "selling": "",
      "upTime": "2026-02-02 00:00:00",
      "downTime": "2026-04-30 23:59:59"
    }
  ]
}
```

### 4.5.3 Points Redemption Product Details

**Description:**
Queries detailed information about product vouchers that can be redeemed with points.
Use this tool when users want to learn more about a specific product voucher (such as usage method, validity period, etc.).

**Input Parameters:**

| name | description |
|------|-------------|
| skuId   | The product skuId selected by the user from the points redemption product list, representing the specific specification ID of this product. Required, Long type. |
| count   | Indicates the quantity of vouchers the user wants to redeem. Optional, Integer type, default=1. |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request successful",
  "datetime": "2026-02-09 14:03:20",
  "traceId": "801b027a09821d95f8a8d26337245ea7",
  "data": {
    "spuName": "Medium Latte/Americano 500 Points",
    "spuId": 542,
    "skuId": 10997,
    "images": [
      "https://cdn-test.mcdchina.net/ecs/b6e0616d94c1f733.png"
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

### 4.5.4 Points Redemption Product Order

**Description:**
> Supports users redeeming product vouchers with points, completing points verification, points deduction, and voucher issuance. Use this tool when users need to redeem a product voucher with points.

**Input Parameters:**

| name | description |
|------|-------------|
| skuId | The product skuId selected by the user from the points redemption product list, representing the specific specification ID of this product. Required, Long type. |
| count | Indicates the quantity of vouchers the user wants to redeem. Optional, Integer type, default=1. |

**Response Content:**

Example:
```json
{
  "success": true,
  "code": 200,
  "message": "Request successful",
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

## 4.6 General Utilities

### 4.6.1 Current Time Information Query Tool

**Description:**
> Gets current time information - Returns complete current server time information, including: - Timestamp (millisecond level) - Formatted date and time - Year, month, day information - Timezone and UTC time. Useful when you don't know the current time and the user needs to specify a date to query the activity calendar.

**Input Parameters:**
> No parameters required.

**Response Content:**

Example:
``` json
{
  "success": true,
  "code": 200,
  "message": "Request successful",
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

# 5. Version Log

|    Date    | Version | Description                                                                                              |
|:----------:|:-------:|----------------------------------------------------------------------------------------------------------|
| 2025-12-09 |  1.0.0  | MaiMai Calendar and MaiMaiSheng Coupon MCP Server                                                        |
| 2026-01-23 |  1.0.1  | Added the "Food Nutrition Information List" Tool, we shortened the URL for easier access and integration |
| 2026-02-13 |  1.0.2  | Added McDelivery ordering and points redemption voucher scenario tools                                   |

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
