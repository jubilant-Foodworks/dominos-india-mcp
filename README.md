# 🍕 Domino's MCP Server

**Order pizza, customize your meal, and manage your cart—right from your AI assistant.**

A [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) server that connects Domino's India ordering services to AI-powered clients like Cursor, Claude and Amp. Browse menus, build your cart, and place orders using natural language—no app switching required.

---

## Table of Contents

- [Ordering Features](#ordering-features)
- [Technical Details](#technical-details)
- [Supported Clients](#supported-clients)
- [Quick Start](#quick-start)
- [Installation](#installation)
  - [Cursor](#cursor)
  - [Manual configuration](#manual-configuration)
- [OTP Based Login](#otp-based-login)
- [Example Workflows](#example-workflows)
- [Support](#support)

---

## Ordering Features

Everything you need to browse, build, and place your order from your AI assistant.

| Feature | Description |
|:--------|:------------|
| **Menu browsing** | Explore full menus with prices, item details, and categories (pizzas, sides, beverages). Filter by veg/non-veg, size, and budget. |
| **Cart management** | Add, update, or remove items. View item-wise and total bill breakdown before checkout. |
| **Customization** | Choose size (regular/medium/large), crust, toppings, and extras (e.g. extra cheese, jalapeños). Build your pizza your way. |
| **Sides & combos** | Add garlic bread, dips, cold drinks, and combos. Get recommendations for combos. |
| **Order placement** | Place delivery orders in natural language. Confirmation and order ID returned for tracking. |
| **Payment options** | *Currently supports* **Cash on Delivery (COD)** and **UPI through QR Code**. Select at checkout. |
| **Order tracking** | Check status of your placed orders. Get updates on preparation and delivery. |

> **Domino's India** — *Food you love, on time. Powered by MCP.*

---

## Technical Details

Integration, transport, and security for developers and MCP clients.

| Feature | Description |
|:--------|:------------|
| **Multi-client support** | One server, many clients. Use from Cursor, Claude, or Amp with the same configuration. |
| **HTTP transport** | Connect remotely via URL. No local binary to install; add the endpoint to your MCP client and go. |
| **Natural language** | Use conversational prompts—no commands to learn. Ask for suggestions, compare options, or describe what you want. |

---

## Supported Clients

This MCP server is tested and supported on:

- **Cursor** — AI-first code editor
- **Claude** — Claude Pro Desktop and Claude.ai
- **Amp** — VS Code–based AI environment

Other MCP-compatible clients may work with the same HTTP configuration; we officially support the clients listed above.

---

## Quick Start

1. Choose your client (Cursor, Claude, or Amp).
2. Use one of the **Install** buttons in [Installation](#installation), or add the server manually (see [Manual configuration](#manual-configuration)).
3. Restart your client and start with a prompt like: *"Show me Domino's veg pizzas"* or *"Add a medium Margherita to my cart."*

---

## Installation

### Cursor

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en-US/install-mcp?name=dominos-ordering-assistant&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vZ2VuYWktcHJvZC1leHQuZG9taW5vcy5jby5pbi9vcmRlci1tY3AvbWNwIn0=)

Click the badge above to add the Domino's MCP server to Cursor in one step.

---

### Manual configuration

### Cursor

Add the server to your Cursor MCP config manually.

**Config file location:** `~/.cursor/mcp.json` (Cursor) or your client’s MCP config path.

```json
{
  "mcpServers": {
    "dominos-ordering-assistant": {
      "type": "http",
      "url": "https://genai-prod-ext.dominos.co.in/order-mcp/mcp"
    }
  }
}
```

Save the file and restart your client to load the Domino's MCP server.

### Claude Pro Desktop

1. Open **Claude Desktop**.
2. Go to **Settings → Connectors → Add custom connector**.
3. Enter any **Name** (e.g. `dominos-ordering-assistant`).
4. Set **URL** to: `https://genai-prod-ext.dominos.co.in/order-mcp/mcp`
5. Save and restart Claude.

**Note:** If you experience a slow response, select "Always Allow" to permit Claude to use these tools without prompting each time.


### Amp

1. Open the Amp extension in your IDE.
2. Go to **Settings → MCP Servers & Toolboxes → Add**.
3. Enter a **Name** (e.g. `dominos-ordering-assistant`).
4. Set **Command or URL** to: `https://genai-prod-ext.dominos.co.in/order-mcp/mcp`
5. Click **Add** or **Save**.
6. Restart your IDE to apply the changes.


### Antigravity - Gemini

1. Open `~/.gemini/antigravity/mcp_config.json` in your Antigravity.
2. Locate or create the `"mcpServers"` object within the JSON file.
3. Add the following configuration block:

```json
{
  "mcpServers": {
    "dominos-ordering-assistant": {
      "type": "http",
      "url": "https://genai-prod-ext.dominos.co.in/order-mcp/mcp"
    }
  }
}
```

4. Save the file.
5. Restart your AI assistant or IDE to apply the changes.


---

## OTP Based Login

Once the Domino's MCP server is added, you will be prompted to log in before proceeding.

---

## Example Workflows

Use these example prompts in your AI assistant after installing the MCP server. Copy as-is or adapt to your situation.

---

#### Team lunch  
*Group orders and office delivery*

> 1. `"Order two large pizzas—one veg, one non-veg—for the team."`  
> 2. `"We need lunch for 6 people. Suggest a mix of pizzas and sides and add them to the cart."`  
> 3. `"Add three medium pizzas: one Margherita, one Pepper Barbecue Chicken, and one Veggie Paradise."`  
> 4. `"Set up an order for the office—two large pizzas and two garlic breads. Show me the bill before placing."`

---

#### Quick dinner  
*Single or small orders*

> 1. `"Add a medium Margherita and garlic bread to my cart."`  
> 2. `"I want a personal pizza and a cold drink for tonight. What do you recommend?"`  
> 3. `"Order one large pizza and one regular garlic bread for delivery. I'll pay by UPI."`  
> 4. `"Add a veggie pizza (medium) and a bottle of Pepsi to my order."`

---

#### Explore menu  
*Browsing and discovery*

> 1. `"What veg pizzas does Domino's have? Show prices."`  
> 2. `"List all non-veg pizzas with their sizes and prices."`  
> 3. `"What sides and beverages are available? I need something under ₹200."`  
> 4. `"Show me the full menu for today. I'm looking for combos or deals."`

---

#### Cart & bill  
*Review and modify cart*

> 1. `"What's in my cart and what's the total?"`  
> 2. `"Show me the bill breakdown—item-wise and total amount."`  
> 3. `"Remove the garlic bread from my cart and tell me the new total."`  
> 4. `"I want to add one more medium pizza. What's my updated cart total?"`

---

#### Custom pizza & extras  
*Toppings, sides, combos*

> 1. `"Add a large pizza with extra cheese and jalapeños."`  
> 2. `"I need a medium pizza, thin crust, with double cheese and olives."`  
> 3. `"Add a large pizza with my choice of toppings—suggest something spicy and cheesy."`  
> 4. `"Put two garlic breads (regular) and one cheesy dip in the cart."`

---

#### Place & track order  
*Checkout and tracking*

> 1. `"Place my order for delivery. I'll pay cash on delivery."`  
> 2. `"Confirm the order and pay via UPI. Send me the order ID."`  
> 3. `"Where is my order? I want to track the last order I placed."`

---

---

## Support

- **Domino's India:** [dominos.co.in](https://www.dominos.co.in)

For issues or feature requests related to this MCP server, open an issue in this repository or contact Domino's India support.

---

<p align="center">
  <sub>Domino's MCP Server · Order with your AI assistant</sub>
</p>
