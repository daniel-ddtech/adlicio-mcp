# Adlicio MCP server: Reddit, Amazon reviews, Meta Ad Library and Google Maps reviews in Claude and ChatGPT

Adlicio is a hosted (remote) MCP server for customer research. Connect it once and Claude, ChatGPT, Cursor, Codex or Claude Code can read Reddit threads, Amazon reviews, Google Maps reviews, Trustpilot pages, YouTube, TikTok and Instagram comments, and ads in the Meta Ad Library, then answer with quotes and links you can check.

- **MCP URL:** `https://mcp.tryadlicio.com/mcp`
- **Transport:** streamable HTTP
- **Auth:** OAuth 2.1 with dynamic client registration. There is no API key to paste; the first tool call opens a sign-in for your Adlicio account.
- **Sources:** Reddit, Amazon, Google Maps, Trustpilot, G2, App Store, Google Play, YouTube, TikTok, Instagram, Facebook, LinkedIn, Etsy, Walmart, Sephora, Ulta, Steam, Hacker News, forums and more: 30+ sources in all.

[Website](https://tryadlicio.com) · [MCP overview](https://tryadlicio.com/mcp) · [Docs](https://tryadlicio.com/docs) · [Every tool and its price](https://tryadlicio.com/docs/tools) · [Pricing](https://tryadlicio.com/pricing)

This repository holds setup notes and client configs only. The server is hosted by Adlicio and its source is not published.

## Connect

**Claude (web and desktop):** Customize > Connectors > + Add > Add custom connector, paste the MCP URL and sign in. Claude Free allows one custom connector. [Step by step](https://tryadlicio.com/docs/connect/claude)

**ChatGPT:** add Adlicio as a custom MCP plugin with the MCP URL. [Step by step](https://tryadlicio.com/docs/connect/chatgpt)

**Claude Code:**

```bash
claude mcp add --transport http adlicio https://mcp.tryadlicio.com/mcp
```

**Codex:**

```bash
codex mcp add adlicio --url https://mcp.tryadlicio.com/mcp
```

**Cursor, VS Code and other clients:** add the URL to the client's MCP config. [`.mcp.json`](.mcp.json) in this repository is a ready config. [All clients](https://tryadlicio.com/docs/connect/other-clients)

## Reddit MCP server

Search Reddit, read whole threads with every reply, and get the answer back with quotes. No Reddit API key.

- **Tools:** `search_reddit`, `research_topic` (searches and reads the top threads for a keyword), `scrape_url` (one thread)
- **Cost:** 1 credit per Reddit search or thread on paid plans
- **Plan:** every plan. A free account gets 3 runs to try it.
- **Ask:** "Find Reddit threads where people ask if a Ridge wallet is worth it, and list the main objections with quotes."
- [Reddit MCP page](https://tryadlicio.com/mcp/reddit)

## Amazon reviews MCP server

Paste a product link and Claude pulls the reviews with star ratings, then groups the complaints and praise.

- **Tool:** `scrape_url` with an Amazon product link
- **Cost:** 0 to 2 credits per product, by the tier that delivers (stored reviews 0, a public teaser 1, live reviews 2)
- **Plan:** Starter and up
- **Ask:** "Read the reviews on this Amazon product and give me the top five complaints, each with a quote."
- [Amazon reviews MCP page](https://tryadlicio.com/mcp/amazon-reviews)

## Meta Ad Library MCP

Search the public Meta Ad Library for a brand or a niche. Claude reads the ads' copy, offers and landing pages, and the scripts of video ads.

- **Tools:** `find_competitor_ads`, `get_ad_transcript`, `inspect_landing_page`, `find_competitor_brands` (Scale)
- **Cost:** 1 credit per search, 1 more per video ad transcript
- **Plan:** Growth and Scale
- **Ask:** "Find the Facebook and Instagram ads AG1 is running now and list the hooks and offers."
- [Meta Ad Library MCP page](https://tryadlicio.com/mcp/meta-ad-library)

## Google Maps reviews MCP

Paste a place link (or a maps.app.goo.gl share link) and Claude reads the Google reviews of that business.

- **Tool:** `scrape_url` with a Google Maps place link
- **Cost:** 4 credits for a full pull of up to about 200 reviews, 3 credits for 50 reviews or fewer
- **Plan:** Starter and up
- **Ask:** "Pull the Google reviews for this dentist and tell me what patients complain about most."
- [Google Maps MCP page](https://tryadlicio.com/mcp/google-maps)

## Trustpilot, YouTube, TikTok, Instagram, LinkedIn and more

| Source | What Claude gets | Cost | Plan | Page |
| --- | --- | --- | --- | --- |
| Trustpilot | A company's reviews | 1 credit | Starter and up | [Trustpilot MCP](https://tryadlicio.com/mcp/trustpilot) |
| YouTube | Comments on a video, video search, a channel's uploads | 0 credits | Starter and up | [YouTube MCP](https://tryadlicio.com/mcp/youtube) |
| TikTok | Comments on a video | 1 credit | Starter and up | [TikTok MCP](https://tryadlicio.com/mcp/tiktok) |
| Instagram | Comments on a post or reel | 1 credit | Every plan; Free and Pro read 5 posts a week at 0 credits | [Instagram MCP](https://tryadlicio.com/mcp/instagram) |
| LinkedIn | Comments on a public post | 1 credit | Starter and up | [LinkedIn MCP](https://tryadlicio.com/mcp/linkedin) |
| Video transcripts | The spoken words of a TikTok, Instagram, YouTube or LinkedIn video | 1 credit | Growth and Scale | [Docs](https://tryadlicio.com/docs/tools) |

The full list of sources and their prices is in [the docs](https://tryadlicio.com/docs/sources).

## All tools

Research: `research_topic`, `scrape_url`, `search_reddit`, `search_youtube`, `search_hackernews`, `search_blind`, `find_forum_threads`, `start_deep_scrape`, `get_deep_scrape`, `get_video_transcript`, `get_linkedin_profile`, `scrape_facebook_group`, `get_extension_job`, `start_instagram_followers`, `get_instagram_followers`.

Ads and creative: `find_competitor_ads`, `find_competitor_brands`, `find_tv_ads`, `get_ad_transcript`, `inspect_landing_page`, `find_scroll_stoppers`, `find_creators`, `find_products`, `find_early_products`, `save_script`.

Brands and reports: `create_brand`, `start_brand_research`, `get_brand_research`, `get_audience`, `start_voc_report`, `get_voc_report`, `save_evidence`, `add_tracked_source`, `list_tracked_sources`.

Reddit Radar: `create_radar`, `update_radar`, `check_radar`, `list_radar_posts`, `set_radar_post_status`.

Account and history: `whoami`, `list_history`, `get_history_item`, `search_history`.

What each tool does, its inputs and its credit price: [tryadlicio.com/docs/tools](https://tryadlicio.com/docs/tools). The machine-readable server card is at [tryadlicio.com/.well-known/mcp.json](https://tryadlicio.com/.well-known/mcp.json).

## Plans

| Plan | Price | Research credits | In short |
| --- | --- | --- | --- |
| Free | $0 | 3 Reddit runs and 5 Instagram pulls a week | Try it |
| Pro | $9.99 a month | 10 Reddit pulls a month | The Chrome extension plan |
| Starter | $49 a month | 250 a month | All 30 sources in Claude and ChatGPT |
| Growth | $99 a month | 600 a month | Adds competitor ads, viral hooks, transcripts |
| Scale | $199 a month | 1,200 a month, 3 seats | Adds top advertisers, TV ads, export API |

Quarterly and yearly billing cost less. [Current prices](https://tryadlicio.com/pricing).

## What it does not do

Adlicio reads public pages only. It never posts, likes, follows or sends messages, and it never asks for your login on Reddit, Amazon or any other site. The one exception you opt into is `scrape_facebook_group`, which reads a Facebook group through your own logged-in Chrome extension.

## Support

[tryadlicio.com/contact](https://tryadlicio.com/contact)
