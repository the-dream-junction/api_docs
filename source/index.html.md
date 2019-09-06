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
  - update_order
  - cancel_order
  - stock_check
  - errors

search: true
---

# Introduction

Welcome to the Dream Junction API documentation. If you have any questions please contact: <admin@thedreamjunction.com>

# Format

This API supports JSON for requests and responses.

# Authentication

Each request requires an API key in the request header. Each account is assigned an API key. Contact support for your API key.

`Name: Authorization`  
`Value: Token token=<key>`

<aside class="notice">
You must replace <code>key</code> with your personal 16-24 character API key.
</aside>
