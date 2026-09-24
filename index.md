# PDXMenusBot


**Before publishing, the owner fills in:**
- `<food-find>`: the public name of the service.
- `<andy@goautolane.com>`: an inbox that someone reads.

---

## What is PDXMenusBot?

PDXMenusBot collects public menus and prices for `<service name>`. The service tells people what Portland, Oregon restaurants, cafes, bars, bakeries, and food carts serve and what it costs. Voice assistants use it, for example to answer "where can I get pho under fifteen dollars near Division?".

It identifies itself as:

```
PDXMenusBot/1.0 (+<this page's address>)
```

## What it reads

- Menu pages, menu PDFs, and menu images on restaurants' own websites.
- Public menu pages on the restaurant's online-ordering provider. It reads only what an anonymous visitor sees.

It never reads delivery marketplaces, review sites, search engines, or social networks. It never logs in, fills in forms, or keeps cookies.

## What it keeps

It keeps only facts:
- item names and prices, and sizes;
- dietary labels that the menu itself states;
- ingredient words;
- service charges printed on the menu;
- opening hours.

It doesn't republish photos or long descriptions, and every menu we show links back to your site.

## How often it visits

- It checks known menu pages about once a night, around midnight Pacific time.
- It asks your server whether the page changed (`If-None-Match` and `If-Modified-Since`). An unchanged menu usually costs one small request.
- Once a month or so, it looks for new menu pages, with at most six page requests per site.

## How it behaves

- It obeys `robots.txt`, both rules for `PDXMenusBot` and rules for `*`. It re-reads the file at most once a day. If your `robots.txt` returns a server error, it leaves your site alone that night.
- It makes one request at a time to your site, at least 2 seconds apart, or longer if your `Crawl-delay` asks. It makes at most 20 requests to your site per night.
- It honors `Retry-After`.
- A 403, a 429, or a challenge page makes it stop for the night. After three such nights in a row it stops visiting.

## How to opt out

Any of these works:
- **Block it in `robots.txt`:**

  ```
  User-agent: PDXMenusBot
  Disallow: /
  ```
- **Ask to be removed:** email `<contact email>` with your restaurant's name and address. Once we remove you, we never fetch your site or show your menu again.

## Data sources and attribution

Place names and locations come from Overture Maps Foundation (CDLA Permissive 2.0) and Foursquare OS Places (Apache 2.0). Area boundaries come from City of Portland open data.
