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

___

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
| Extra Parameters? | No                                         |  

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
| Extra Parameters? | No                                                |  

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

## Get User ID  
  
|-------------------|---------------------------------------|  
| URL               | https://www.hackthebox.eu/api/user/id |  
| Requires API Key? | Yes                                   |  
| Request Type      | POST                                  |  
| Extra Parameters? | Yes                                   |  

### Parameters
{: .no_toc }

| Parameter  | Example Value               | Description                 |
|------------|-----------------------------|-----------------------------|
| `username` | `SherlockSec`               | HTB Username for given user |

Response:
```json
{
    "username": "SherlockSec",
    "id": 50344
}
```

___

## Machines List  
  
|-------------------|---------------------------------------------------|  
| URL               | https://www.hackthebox.eu/api/machines/get/all    |  
| Requires API Key? | No                                                |  
| Request Type      | GET                                               |  
| Extra Parameters? | No                                                |  

Response:
```json
[
    {
        "id":1,"name":"Lame",
        "os":"Linux",
        "ip":"10.10.10.3",
        "avatar_thumb":"https://www.hackthebox.eu/storage/avatars/fb2d9f98400e3c802a0d7145e_thumb.png",
        "points":20,"release":"2017-03-14",
        "retired_date":"2017-05-26",
        "maker":{
            "id":1,"name":"ch4p"
        },
        "maker2":null,
        "ratings_pro":2261,
        "ratings_sucks":216,
        "user_owns":7459,
        "root_owns":7792,
        "retired":true,
        "free":false
    }
    <!--Repeated Data Omitted-->
]
```

___
