---
title: "Reverse Image Search Automation for Booru Images"
description: "Automate reverse image searches across SauceNAO, IQDB, and booru sites. Find where your images are reposted and track attribution."
---

# Reverse Image Search Automation

Tracking where your watermarked images end up across booru platforms is essential for attribution monitoring. Automated reverse image search makes this scalable.

## Available APIs

| Service | Free Tier | Rate Limit |
|---------|-----------|------------|
| SauceNAO | 200 queries/day | 30s between queries |
| IQDB | Unlimited | 5s between queries |
| Google Images | Rate-limited | Via browser automation |

## Python Automation

```python
import httpx

async def search_iqdb(image_path):
    async with httpx.AsyncClient() as client:
        with open(image_path, 'rb') as f:
            files = {'file': f}
            resp = await client.post('https://iqdb.org/', files=files)
        # Parse HTML for result links
        return extract_matches(resp.text)
```

For more tools, check the [rule34.ink](https://rule34.ink) image management ecosystem.

## Attribution Tracking

When you find reposted images, record the source URLs and check if your watermark or domain link is present. Automated credit detection can flag uncredited reposts for follow-up.
