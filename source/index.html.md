---
title: DreamJunction API

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - new_order
  - order_status
  - multiple_order_status
  - stock_check
  - errors

search: true
---

# Format

This API supports only JSON for requests and responses.

# Authentication

Each request requires an API key in the request header. Each user is assigned an API key. Contact support for your API key.

    `Name: Authorization`  
    `Value: Token token=<key>`

<aside class="notice">
You must replace <code>key</code> with your personal 16-24 character API key.
</aside>
