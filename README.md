# Bright Data의 Twitter (X) Data Scraper

[![Promo](https://github.com/luminati-io/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/web-scraper/twitter)

이 리포지토리는 Twitter 데이터를 수집하기 위한 두 가지 상이한 방법을 제공합니다:
1. **무료 Twitter Scraper**: 소규모 프로젝트 및 학습용
2. [**Enterprise Twitter Scraper API**](https://brightdata.co.kr/products/web-scraper/twitter): 프로덕션급 데이터 추출용

## Table of Contents
1. [Free Twitter Scraper](#free-twitter-scraper)
    - [Profile Scraping](#1-profile-scraping)
    - [Post Scraping](#2-post-scraping)
    - [Limitations](#limitations)
2. [Twitter Scraper API](#twitter-scraper-api)
    - [Key Features](#key-features)
    - [Quick Start Guide](#quick-start-guide)
    - [Scrape Posts by URL](#1-scrape-posts-by-url)
    - [Scrape Profile Data](#2-scrape-profile-data)
    - [Date-Range Tweet Collection](#3-date-range-tweet-collection)
3. [No-Code Scraper Option](#no-code-scraper-option)
4. [Data Collection Approaches](#data-collection-approaches)
5. [Support & Resources](#support--resources)


## Free Twitter Scraper
소규모 프로젝트, 실험, 학습 목적에 이상적입니다.

### 1. Profile Scraping
이름, 팔로워 수, 트윗 수 등 Twitter의 공개 프로필 데이터를 추출합니다.

#### Input Requirements:
| Parameter  | Type  | Required | Description                          |
|------------|-------|----------|--------------------------------------|
| usernames  | list  | Yes      | 스크레이핑할 Twitter 핸들의 목록입니다   |

#### Implementation:
```python
# free_scraper/twitter_profiles.py
usernames = [
    "satyanadella",
    "BillGates", 
    "elonmusk"
]
```

#### Sample Output (CSV):
<img width="700" alt="twitter_profiles_data" src="https://github.com/luminati-io/twitter-scraper/blob/main/Images/408877618-450d920a-4760-463b-9670-8ac1264b6409.png" />

### 2. Post Scraping
특정 트윗에 대한 참여(engagement) 지표를 수집합니다.

#### Input Requirements:

| Parameter  | Type  | Required | Description                        |
|------------|-------|----------|------------------------------------|
| tweet_ids  | list  | Yes      | 스크레이핑할 Twitter 게시물 ID 목록입니다 |

#### Implementation:
```python
# free_scraper/twitter_posts.py
TWEET_IDS = [
    "1882412972414214544",
    "1879604491764297992",
    "1869427646368792599"
]
```

#### Sample Output (JSON):
```json
{
  "tweet_id": "1882412972414214544",
  "author": "MongoDB",
  "content": "We're excited to announce...",
  "engagement": {
    "likes": 29,
    "retweets": 10,
    "views": 3417
  }
}
```

### Limitations
무료 방식은 Twitter의 엄격한 앤チ봇(anti-bot) 보호로 인해 대규모 スクレイピング에는 권장되지 않습니다. 주요 제한 사항은 다음과 같습니다:
- **レート制限:** 몇 번 スクレイピング한 후 Twitter가 リクエスト를 차단합니다.
- **IPアドレス 차단:** 동일한 IP에서 빈번히 スクレイピング하면 차단(밴)될 수 있습니다.
- **제한된 확장성:** 대용량 데이터 수집에 적합하지 않습니다.
- **제한된 데이터 필드:** 기본 프로필 및 트윗 데이터만 제공하며, 고급 필터링 옵션은 제공되지 않습니다.

## Twitter Scraper API
대규모 Twitter 데이터 추출을 위한 강력하고 확장 가능하며 신뢰할 수 있는 솔루션입니다. 인프라 부담 없이 고품질의 실시간 데이터가 필요한 기업 및 개발자를 위해 설계되었습니다.

### Key Features
- **확장 가능 & 신뢰성:** 대용량 및 실시간 데이터 수집에 최적화되어 있습니다.
- **차단 방지:** 내장된 [プロキシ 로ーテ이션](https://brightdata.co.kr/solutions/rotating-proxies) 및 [CAPTCHA 해결](https://brightdata.co.kr/products/web-unlocker/captcha-solver)
- **법적 준수:** GDPR 및 CCPA를 완전히 준수합니다.
- **글로벌 커버리지:** 어떤 지역 또는 언어의 데이터에도 접근할 수 있습니다.
- **실시간 데이터:** 최소한의 지연으로 최신 데이터를 제공합니다.
- **고급 필터링:** 정밀한 필터로 데이터 추출을 사용자 지정할 수 있습니다.
- **종량제(Pay-as-You-Go):** 성공한 レスポンス에 대해서만 비용을 지불합니다.
- **무료 체험:** 시작을 위한 무료 API 호출 20회를 포함합니다.
- **전담 지원:** 24/7 기술 지원을 제공합니다.

👉 **자세히 알아보기:** [Bright Data Twitter Scraper API](https://brightdata.co.kr/products/web-scraper/twitter)

### Quick Start Guide
- **가입:** [Bright Data 계정](https://brightdata.co.kr/)을 생성합니다.
- **API Token 받기:** 대시보드에서 [API key](https://docs.brightdata.com/general/account/api-token)를 발급받습니다.
- **엔드포인트 선택:** 아래에서 제공되는 API 엔드포인트 중 하나를 선택합니다.

### 1. Scrape Posts by URL
URL을 사용하여 특정 트윗에 대한 상세 참여 지표 및 콘텐츠를 추출합니다.

<img width="700" alt="twitter-posts-scraper" src="https://github.com/luminati-io/twitter-scraper/blob/main/Images/409213804-9d07a475-2e3b-45fc-ae8e-ebcd7cef367b.png" />


#### Request Parameters:
| Field | Type   | Required | Description            |
|-------|--------|----------|------------------------|
| `url`   | string | Yes      | 전체 Twitter 게시물 URL입니다 |

#### Example Request:
```python
# twitter_api/twitter_posts.py
posts = [
    {"url": "https://x.com/OpenAI/status/1885406586136383634"},
    {"url": "https://x.com/CNN/status/1796673270344810776"}
]
```

#### Response Schema:
```json
{
    "post": {
        "author": {
            "name": "OpenAI",
            "followers": 3930255,
            "profileImage": "https://pbs.twimg.com/profile_images/1885410181409820672/ztsaR0JW_normal.jpg",
            "bio": "OpenAI's mission is to ensure that artificial general intelligence benefits all of humanity. We're hiring: https://t.co/dJGr6Lg202",
        },
        "content": {
            "text": "OpenAI o3-mini is now available in ChatGPT and the API.\n\nPro users will have unlimited access to o3-mini and Plus & Team users will have triple the rate limits (vs o1-mini).\n\nFree users can try o3-mini in ChatGPT by selecting the Reason button under the message composer.",
            "postedAt": "2025-01-31T19:15:33.000Z",
            "id": "1885406586136383634",
        },
        "engagement": {
            "replies": 1004,
            "reposts": 1997,
            "likes": 13420,
            "views": 2858777,
            "quotes": 684,
            "bookmarks": 1546,
        },
    }
}
```
👉 여기에는 핵심 필드만 표시되어 있습니다. 모든 세부 사항은 [full JSON response](https://github.com/luminati-io/Twitter-Scraper/blob/main/twitter_data/twitter_posts.json)를 확인하시기 바랍니다. 지금 전용 [Twitter Posts Scraper](https://brightdata.co.kr/products/web-scraper/twitter/posts)를 사용해 보시기 바랍니다.

### 2. Scrape Profile Data
최근 게시물과 참여 지표를 포함하여 포괄적인 프로필 정보를 추출합니다.

<img width="600" alt="twitter-profile-scraper" src="https://github.com/luminati-io/twitter-scraper/blob/main/Images/409214197-3b3e2f0f-30bc-45d9-b9bc-13358b22a55a.png" />

#### Request Parameters:

| Field      | Type   | Required | Description                     |
|------------|--------|----------|---------------------------------|
| `url`        | string | Yes      | Twitter 프로필 URL입니다       |
| `max_number_of_posts`  | number | No       | 가져올 최근 게시물 수입니다 |

#### Example Request:
```python
# twitter_api/twitter_profile_posts.py
profiles = [
    {"url": "https://x.com/satyanadella", "max_number_of_posts": 50},
    {"url": "https://x.com/BillGates", "max_number_of_posts": 35}
]
```

#### Response Schema:
```json
{
    "profile": {
        "name": "Satya Nadella",
        "handle": "satyanadella",
        "role": "Chairman and CEO at Microsoft",
        "isVerified": true,
        "profileImage": "https://pbs.twimg.com/profile_images/1221837516816306177/_Ld4un5A_normal.jpg",
        "website": "http://www.microsoft.com/ceo",
        "joinedDate": "2009-02-11T04:45:34.000Z",
        "stats": {"following": 286, "followers": 3356268, "postsCount": 1859},
    },
    "posts": [
        {
            "id": "1807114709499523208",
            "content": "What a final!!! Congrats, India, and well played, South Africa. Super World Cup... let us have more cricket in the West Indies and USA!!",
            "postedAt": "2024-06-29T18:11:35.000Z",
            "engagement": {
                "replies": 712,
                "reposts": 10785,
                "likes": 133591,
                "views": 2029775,
            },
        },
        {
            "id": "1726509045803336122",
            "content": "We remain committed to our partnership with OpenAI and have confidence in our product roadmap, our ability to continue to innovate with everything we announced at Microsoft Ignite, and in continuing to support our customers and partners. We look forward to getting to know Emmett",
            "postedAt": "2023-11-20T07:53:28.000Z",
            "engagement": {
                "replies": 4524,
                "reposts": 14480,
                "likes": 89773,
                "views": 41675720,
            }
        },
    ],
}
```
👉 여기에는 핵심 필드만 표시되어 있습니다. 모든 세부 사항은 [full JSON response](https://github.com/luminati-io/Twitter-Scraper/blob/main/twitter_data/twitter_profile_posts.json)를 확인하시기 바랍니다. 지금 전용 [Twitter Profile Scraper](https://brightdata.co.kr/products/web-scraper/twitter/profile)를 사용해 보시기 바랍니다. 

### 3. Date-Range Tweet Collection
특정 날짜 범위 내의 게시물을 가져옵니다.

#### Request Parameters:

| Parameter  | Type   | Required | Description                   |
|------------|--------|----------|-------------------------------|
| `url`        | string | Yes      | Twitter 프로필 URL입니다          |
| `start_date` | string | Yes      | 시작 날짜(ISO 형식)입니다       |
| `end_date`   | string | Yes      | 종료 날짜(ISO 형식)입니다         |


#### Example Request:
```python
# twitter_api/twitter_posts_date_range.py
profiles = [
    {
        "url": "https://x.com/satyanadella",
        "start_date": "2025-01-15T09:00:00.000Z",
        "end_date": "2025-01-31T23:00:00.000Z",
    },
    {"url": "https://x.com/cnn", "start_date": "2025-01-01", "end_date": "2025-01-15"},
    {"url": "https://x.com/fabrizioromano", "start_date": "", "end_date": ""},
]
```

#### Response Schema:
```json
{
    "post": {
        "author": {
            "name": "Satya Nadella",
            "handle": "satyanadella",
            "role": "Chairman and CEO at Microsoft",
            "isVerified": false,
            "profileImage": "https://pbs.twimg.com/profile_images/1221837516816306177/_Ld4un5A_normal.jpg",
            "followers": 3356282,
            "following": 286,
        },
        "content": {
            "text": "For me, cricket is maybe the only thing that could possibly come close to watching the Excel World Champ on ESPN!",
            "images": ["https://pbs.twimg.com/media/GiF4nePaEAAHQg5.jpg"],
            "externalUrl": "https://techcommunity.microsoft.com/blog/excelblog/congrats-to-the-winners-of-this-years-mewc--mecc/4355651",
            "postedAt": "2025-01-24T22:29:46.000Z",
            "id": "1882918743409676719",
        },
        "engagement": {
            "replies": 102,
            "reposts": 208,
            "likes": 3416,
            "views": 286901,
            "quotes": 39,
            "bookmarks": 127,
        },
    }
}
```
👉 여기에는 핵심 필드만 표시되어 있습니다. 모든 세부 사항은 [full JSON response](https://github.com/luminati-io/Twitter-Scraper/blob/main/twitter_data/twitter_date_range_posts.json)를 확인하시기 바랍니다.

## No-Code Scraper Option
그래픽 인터페이스를 선호하는 사용자를 위해, 컨트롤 패널을 통해 노코드 솔루션을 제공합니다:

- 몇 분 안에 스크레이퍼를 구성할 수 있습니다.
- 전체 데이터 수집 프로세스를 자동화합니다.
- 결과를 직접 다운로드할 수 있습니다(다양한 형식 지원).

노코드 스크레이퍼 사용에 대한 자세한 안내는 [Getting Started guide](https://github.com/luminati-io/Twitter-Scraper/blob/main/no-code-scraper.md)를 방문하시기 바랍니다.


## Data Collection Approaches
다음 パラメータ를 사용하여 결과를 세밀하게 조정할 수 있습니다:
| **Parameter**       | **Type**   | **Description**                                            | **Example**                  |
|---------------------|------------|------------------------------------------------------------|------------------------------|
| `limit`             | `integer`  | 입력당 최대 결과 수                                   | `limit=10`                   |
| `include_errors`    | `boolean`  | 문제 해결을 위한 오류 리포트를 가져옵니다                     | `include_errors=true`        |
| `notify`            | `url`      | 완료 시 알림을 받을 Webhook 알림 URL입니다  | `notify=https://notify-me.com/` |
| `format`            | `enum`     | 출력 형식(예: JSON, NDJSON, JSONL, CSV)         | `format=json`                |

💡 **Pro Tip:** 데이터를 [external storage](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-deliver-to-external-storage)로 전달할지 또는 [webhook](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-webhook)으로 전달할지도 선택할 수 있습니다.

## Support & Resources
- **API Documentation:** [Bright Data Docs](https://docs.brightdata.com/scraping-automation/web-scraper-api/trigger-a-collection)
- **스크레이핑 모범 사례:** [차단을 피하는 방법](https://brightdata.co.kr/blog/web-data/web-scraping-without-getting-blocked)
- **기술 지원:** [Contact Us](mailto:support@brightdata.com)

---

**다른 스크레이퍼에도 관심이 있으신가요? 아래 목록을 확인하시기 바랍니다:**

- [LinkedIn Scraper](https://github.com/luminati-io/LinkedIn-Scraper)
- [Google News Scraper](https://github.com/luminati-io/Google-News-Scraper)
- [Google Maps Scraper](https://github.com/luminati-io/Google-Maps-Scraper)
- [Amazon Scraper](https://github.com/luminati-io/Amazon-scraper)