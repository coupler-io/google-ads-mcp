<div align="center">

# Google Ads MCP Server by Coupler.io

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Transport](https://img.shields.io/badge/Transport-Streamable_HTTP-blue.svg)](#)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.0-green.svg)](#)

Coupler.io Google Ads MCP server for Claude, ChatGPT, Gemini, Cursor, n8n, OpenClaw, and other MCP clients. Query and analyze Google Ads data with natural language. Requires the Coupler.io account.

</div>

## Data Access

Access 30+ report types — campaign performance, keyword analysis, audience demographics, geographic breakdowns, Shopping and video campaigns, and more.

<details>
<summary><strong>Report types</strong></summary>

#### Frequently used reports

| Report type | What it contains | When to use it |
|---|---|---|
| **Campaign performance** | Spend, clicks, impressions, conversions, and other metrics at the campaign level | Overall campaign analysis, budget tracking, performance dashboards |
| **Keywords performance** | Keyword-level metrics for search campaigns | Analyzing which keywords drive traffic and conversions |
| **Ad group performance** | Performance metrics at the ad group level | Comparing ad groups within campaigns |
| **Ad performance** | Individual ad creative performance | Identifying top-performing ads and creative variations |
| **Asset group performance** | Performance data for asset groups (Performance Max) | Evaluating Performance Max campaign components |
| **Custom GAQL** | Any data available via Google Ads Query Language | Advanced users who need custom report structures |

#### Additional reports

| Report type | What it contains |
|---|---|
| **Account performance** | Account-level aggregate metrics |
| **Ad group audience performance** | Performance by audience segment at the ad group level |
| **Age range performance** | Performance by age demographic |
| **Gender performance** | Performance by gender demographic |
| **Geographic performance** (by country, state, region) | Performance by geographic location at the ad group or campaign level |
| **Campaign audience performance** | Performance by audience segment at the campaign level |
| **Campaign performance by ad network type** | Performance split by Search, Display, YouTube, etc. |
| **Campaign performance with conversion actions** | Campaign data with named conversion actions |
| **Campaign performance with unique user stats** | Campaign data including unique reach metrics |
| **Click performance** | Individual click-level data |
| **Display keyword performance** | Performance for Display network keywords |
| **Display topics performance** | Performance by topic targeting on the Display network |
| **Landing page / Expanded landing page** | Performance by destination URL |
| **Search query performance** | Actual search terms that triggered your ads |
| **Shopping performance** | Product-level performance for Shopping campaigns |
| **Responsive search ad performance** | Performance of responsive search ad combinations |
| **Video campaign performance** | Performance for video (YouTube) campaigns with conversions |
| **User location performance** | Performance by user's physical location |
| **Placement performance** | Performance by website placement on the Display network |

#### Structural data (Core Components)

| Report type | What it contains | When to use it |
|---|---|---|
| **Accounts** | Account details and settings | Auditing account configuration |
| **Campaigns** | Campaign structure, status, type, and settings | Monitoring campaign setup and status changes |
| **Ad groups** | Ad group structure, status, and settings | Reviewing ad group organization |
| **Ads** | Individual ad details and approval status | Checking ad review status and configuration |

</details>

<details>
<summary><strong>Key metrics by category</strong></summary>

| Category | Example metrics |
|---|---|
| **Budget** | Content budget lost IS, Search budget lost absolute top IS, Search budget lost IS, Search budget lost top IS |
| **Clicks** | CTR, Active view CTR, Invalid click rate, Invalid clicks, Relative CTR |
| **Conversions** | Conversions, All conversions, Conversions value, Cross device conversions, View through conversions, Cost per conversion, Conversions by conversion date |
| **Cost** | Amount spend, CPC, CPM, CPV, CPE, Active view CPM, Cost per conversion |
| **Performance** | Impressions, Clicks, Bounce rate, Search impression share, Content impression share, Absolute top impression %, Top impression % |
| **Cross sell / Sales** | Revenue, Cost of goods sold, Gross profit, Units sold, Orders, Average order value |
| **Video** | Video views, Video view rate, Plays at 25/50/75/100% rate |
| **Phone** | Phone calls, Phone impressions, Phone through rate |

</details>


## Supported Clients

*Note: You will need to set up a data flow in Coupler.io with Google Ads as a source and the AI tool of your choice as the destination.*

### Claude

Use with Claude Web, Desktop, Chat, Cowork, or Claude Code.

**Via Web/Desktop:** Go to **Customize**->**Connectors**->**Connect your tools**, search for Coupler.io and add it.

**Via Claude Code CLI:**

```bash
claude mcp add coupler-io --transport streamable-http https://mcp.coupler.io/mcp
```

### ChatGPT

Install from the **ChatGPT Apps** directory — search for "Coupler.io" in the **Apps** section of **Settings**.

### Cursor

Find it on the [Cursor Directory](https://cursor.directory/mcp/coupler-io-official-remote-mcp).

### Gemini CLI

Go to the **AI integrations** -> **Gemini CLI** page in your Coupler.io account to copy the correct command (unique to each account). It will look like this:

```bash
gemini mcp add coupler --transport=http https://mcp.coupler.io/mcp/xxxxx
```

### OpenClaw

Use the **mcporter** skill to connect, or install the **coupler-io** skill from ClawHub.
Directly ask your OpenClaw agent to add the skill and execute it.

## Links

- **Landing page:** [Google Ads MCP by Coupler.io](https://www.coupler.io/mcp/google-ads)
- **Coupler.io:** [https://coupler.io](https://coupler.io)
- **MCP Server endpoint:** `https://mcp.coupler.io/mcp`