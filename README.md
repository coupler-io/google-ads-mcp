<div align="center">

# Google Ads MCP Server by Coupler.io

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Transport](https://img.shields.io/badge/Transport-Streamable_HTTP-blue.svg)](#)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.0-green.svg)](#)

Connect Google Ads data to AI with the Coupler.io MCP server. Ask natural-language questions about campaigns, keywords, search terms, spend, conversions, ROAS, audiences, Shopping, and Performance Max data in ChatGPT, Claude, Gemini, Cursor, and other MCP-compatible AI tools. Requires a Coupler.io account.

[Landing page](https://www.coupler.io/mcp/google-ads) · [Documentation](https://docs.coupler.io/ai/mcp) · [All Coupler.io MCP integrations](https://github.com/coupler-io)

</div>

## What you can ask

- Which campaigns had the highest ROAS last month?
- Which keywords are spending money without generating conversions?
- Compare campaign performance by device and location.
- Which search terms should I consider adding as negative keywords?
- How is Performance Max performing compared with Search campaigns?

## How it works

This repository documents the Google Ads integration for the Coupler.io MCP server.

1. Connect Google Ads to Coupler.io.
2. Select your AI tool as the destination.
3. Connect your AI client to Coupler.io MCP.
4. Ask questions about your Google Ads data in natural language.

Coupler.io sits between Google Ads and your AI client. It holds the Google Ads credential, imports the data on a schedule, and exposes the result as a data set the AI can query. Your AI client never calls the Google Ads API itself.

```
  Google Ads
      |        credential held by Coupler.io
      v
  Coupler.io          import, transform, store on a schedule
      |
      v
  MCP server          schema, SQL query execution
      |
      v
  Your AI client      your question, in plain language
```

When you ask a question, the AI reads the data set's schema, writes SQL, and Coupler.io runs that query on its own side. Only the result comes back to the AI, so a large data set does not have to fit into the model's context window.

| | |
|---|---|
| **MCP endpoint** | `https://mcp.coupler.io/mcp` |
| **Transport** | Streamable HTTP |
| **Authentication** | OAuth 2.0 |
| **Query language** | SQL, executed by Coupler.io |
| **Refresh schedule** | From monthly to every 15 minutes, depending on your plan |

## Get started

*Note: You will need to set up a data flow in Coupler.io with Google Ads as a source and the AI tool of your choice as the destination.*

### Claude

Use with Claude Web, Desktop, Chat, Cowork, or Claude Code.

**Via Web/Desktop:** Go to **Customize**->**Connectors**->**Connect your tools**, search for Coupler.io and add it.

**Via Claude Code CLI:**

```bash
claude mcp add coupler-io --transport streamable-http https://mcp.coupler.io/mcp
```

### ChatGPT

Install the [Coupler.io ChatGPT app](https://l.rw.rw/couplerio-chatgpt-app) and complete the authentication. You can also find it by searching for "Coupler.io" in the **Apps** section of **Settings**.

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

## Data you can access

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

Coupler.io imports only the report types and fields you select in the data flow. If a field is missing, add it to the source, or build a **Custom GAQL** source for anything the packaged reports do not cover.

## Example questions

### Performance and trends

- Break down last month's spend and conversions by campaign, and show which campaigns moved the account average.
- Compare cost per conversion for the last 30 days against the previous 30 days.
- Which ad groups have a CTR below the account average but more than 1,000 impressions?

### Keywords and search terms

- List search terms with more than 50 clicks and zero conversions over the last 90 days.
- Which keywords have the highest cost per conversion, and which match types are they using?
- Where am I losing impression share to budget versus to rank?

### Structure and channels

- Compare Performance Max asset group results with my Search campaigns on conversions and ROAS.
- Show performance by device and geographic region for my top five campaigns.
- Which Shopping products generate the most revenue relative to spend?

## Security and permissions

Your AI client never connects to Google Ads directly. Coupler.io holds the Google Ads credential, imports the data, and exposes only the resulting data set over MCP.

- **Your Google Ads data is never modified.** Coupler.io only reads from Google Ads. The AI queries the copy Coupler.io imported and cannot edit, delete, or overwrite it, let alone write anything back to your Google Ads account.
- **Visibility is scoped per AI tool.** An AI client sees only the data sets from data flows that have *that client* set as a destination. Adding Claude as a destination does not expose the data flow to ChatGPT, though one flow can name both.
- **Configuration changes are possible, and confirmed first.** With the full tool set available, the AI can create data flows, add sources and destinations, change a schedule, or trigger a run. Those are real changes to your workspace, so the server instructs the AI to confirm before making one you did not ask for.
- **Nothing else is reachable.** The MCP server exposes the data sets described above and nothing more. It cannot reach your other accounts or your machine.
- **Disconnect at any time** by removing the connector in your AI client, or by deleting the credential or the data flow in Coupler.io.

Coupler.io is SOC 2 certified and compliant with GDPR and HIPAA.

## Troubleshooting

**The AI cannot find my Google Ads data set.**
Usually you have not added that AI tool as a destination yet. Open the data flow in Coupler.io and add your AI client. One data flow can have several AI tools as destinations at the same time, so adding ChatGPT does not displace Claude. Each tool sees only the flows it is named on.

**The numbers look out of date.**
The AI reads the last imported snapshot, not Google Ads live. Check the data flow's refresh schedule, or ask your AI client to run the data flow now.

**A field I need is missing.**
Coupler.io imports only the fields you select in the data flow's source. Add the missing fields and re-run the flow. If no packaged report covers the field, build a **Custom GAQL** source instead.

**The AI misreads a metric.**
Save the business context on the data set: what a metric means, which currency it is in, which rows to exclude. You do not have to leave your AI tool to do it, just tell the assistant to update the data set context and it saves it for you. The AI reads that context before it queries, so the next conversation uses your definitions instead of guessing.

**The connector does not appear in my AI client.**
Availability differs by AI client and subscription plan. Follow the client-specific steps under [Get started](#get-started), and check the [AI destination docs](https://docs.coupler.io/destinations/categories/ai) for that tool.

## Related Coupler.io MCP integrations

- [Facebook Ads MCP](https://github.com/coupler-io/facebook-ads-mcp) — analyze paid social campaign performance
- [Google Analytics 4 MCP](https://github.com/coupler-io/google-analytics-4-mcp) — analyze website traffic, acquisition, and conversions
- [Google BigQuery MCP](https://github.com/coupler-io/google-bigquery-mcp) — analyze advertising and business data stored in BigQuery
- [HubSpot MCP](https://github.com/coupler-io/hubspot-mcp) — connect advertising performance with leads, deals, and CRM data

[Explore all Coupler.io MCP integrations](https://github.com/coupler-io)

## FAQ

### What is the Google Ads MCP server?

It is the Google Ads integration for the Coupler.io MCP server, an endpoint that lets AI clients query your Google Ads data in plain language. Coupler.io imports the data, stores it, and answers the AI's SQL queries on its own infrastructure.

### Do I need a Coupler.io account?

Yes. The MCP server serves data from your Coupler.io workspace, so you need an account with a data flow that has Google Ads as a source and your AI tool as a destination.

### Does this connect directly to my Google Ads account?

No. Coupler.io connects to Google Ads, imports the data, and exposes the resulting data set over MCP. Your AI client talks to Coupler.io, never to Google Ads.

### Which Google Ads data can AI access?

Whatever your data flow imports. See [Data you can access](#data-you-can-access) for the full catalog of report types and fields. The AI reaches only the data sets in flows that name your AI tool as a destination.

### Is the integration read-only?

Yes. Nothing you or your AI client does through Coupler.io changes your Google Ads data. Coupler.io only reads from Google Ads, and the AI only queries the copy Coupler.io imported. It cannot edit, delete, or write anything back to your Google Ads account.

### Which AI assistants can I use?

Claude, ChatGPT, Cursor, Gemini CLI, OpenClaw, Perplexity, and any client that speaks MCP through the Custom MCP destination. Setup steps for the clients above are under [Get started](#get-started); for the rest, see the [AI destination docs](https://docs.coupler.io/destinations/categories/ai).

### Do I need to write SQL or code?

No. You ask in plain language; the AI writes the SQL and Coupler.io runs it. Writing SQL yourself stays an option if you want a specific transformation.

### How fresh is the data?

As fresh as the last data flow run. Schedules range from monthly to every 15 minutes depending on your plan, and you can ask your AI client to refresh the flow on demand.

## Links

- **Landing page:** [Google Ads MCP by Coupler.io](https://www.coupler.io/mcp/google-ads)
- **Documentation:** [Coupler.io MCP](https://docs.coupler.io/ai/mcp)
- **Coupler.io:** [https://coupler.io](https://coupler.io)
- **MCP Server endpoint:** `https://mcp.coupler.io/mcp`
- **All Coupler.io MCP integrations:** [https://github.com/coupler-io](https://github.com/coupler-io)
