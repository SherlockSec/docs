---
layout: default
title: HackTheBox API
nav_order: 3
permalink: /docs/htb-api
published: true
---

# HackTheBox API
{: .no_toc }

Unofficial documentation for the HackTheBox API. Feel free to PR and add to this on [GitHub](https://github.com/SherlockSec/docs).

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

___

## Introduction
First things first, for most of the API queries, you need an **API Key**. To find your API Key, navigate to the `https://www.hackthebox.eu/home/settings`, as seen below.  

![api_key](https://raw.ratelimited.me/H0j2bwgj0rBr.png)  

To use the API Key, add it a URL parameter like so:

```https://example.com/api/endpoint?api_token=<API KEY GOES HERE>```

Next, you'll need a way to make the API requests. MOst, if not all programming languages have a capacity to make HTTP Requests, but when testing a query it's nice to have a standalone tool. Therefore, I recommend the following tools (based on my experience):  
* Postman (Windows)
* curl/wget (*nix)

___

# Endpoints

___

## Global Stats  
  
| ----------------- | ------------------------------------------ |  
| URL               | https://www.hackthebox.eu/api/stats/global |  
| Requires API Key? | No                                         |  
| Request Type      | POST                                       |  

Response:
```json
{
    "success": "1",
    "data": {
        "sessions": 1349,
        "vpn": 1112,
        "machines": 123,
        "latency": "1.05"
    }
}
```

___

## Hall Of Fame  
  
|-------------------|---------------------------------------------------|  
| URL               | https://www.hackthebox.eu/api/charts/users/scores |  
| Requires API Key? | Yes                                               |  
| Request Type      | GET                                               |  

Response:
```json
{
    "status": 1,
    "chartData": [
        {
            "name": "snowscan",
            "timeline": [
                {
                    "x": "22:02:33 06 Aug",
                    "y": 1768
                },
                <!--Repeated Data Omitted-->
            ],
            "color": "9acc14"
        },
        <!--Repeated Data Omitted-->
    ]
}
```

___

