---
title: API Reference

language_tabs:
  - json
  - xml
  - markdown : csv

toc_footers:
  - <a href='mailto:support@adthena.com'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Adthena API! You can use our API to access Adthena API endpoints, in order to programmatically retrieve data for your Adthena account(s).

Use the "json", "xml" and "csv" tabs on the right to show example response data in those formats.

# FAQ

### How do I access the API?
Accessing the API requires you to have the unique authentication key for each Adthena account. Speak to you Adthena contact for further information.

### Is there a way to test my credentials?
One simple way is to use a free tool such as onlinecurl.com

1. Enter your URL beginning https://
2. Click Add Option, select Header, enter adthena-api-key:my-api-key
3. Click Start Your Curl

### At what time can I download yesterday’s data?
Yesterday’s data is available by 9am local time for that country

### How can I better understand the data I am downloading or filters I am applying?
Try our Knowledge Base, which has descriptions and screengrabs: https://adthena.zendesk.com/hc/en-us 

### I discovered an issue what shall I do?
Email the details to <a href='mailto:support@adthena.com'>support@adthena.com</a> and we will investigate

# Authentication

> To authorize, use this code:

```
curl -i "api_endpoint_here" -H "adthena-api-key: my-api-key"
```

> Make sure to replace `my-api-key` with your API key.

Adthena uses API keys to allow access to the API. You can register <a href='mailto:support@adthena.com'>here</a> for a new Adthena API key.

Adthena expects for the API key to be included in all API requests to the server in a header that looks like the following:

`adthena-api-key: my-api-key`

<aside class="notice">
You must replace <code>my-api-key</code> with your account's API key. If you have multiple accounts then you will need to ensure that you are using the key specific to that account.
</aside>

# Market Share

> The response has the following structure:

```json
[{
    "Competitor": "competitor1.com",
    "RelevantSearchTerms": 49,
    "EstimatedImpressions": 3421,
    "AveragePosition": 2.1,
    "ShareOfClicks": "16.17%",
    "ShareOfSpend": "15.24%"
}, {
    "Competitor": "competitor2.com",
    "RelevantSearchTerms": 13,
    "EstimatedImpressions": 2395,
    "AveragePosition": 3.1,
    "ShareOfClicks": "12.97%",
    "ShareOfSpend": "14.12%"
}]
```
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<DesktopMarketShare>
  <Item>
    <Competitor>competitor1.com</Competitor>
    <RelevantSearchTerms>49</RelevantSearchTerms>
    <EstimatedImpressions>3421</EstimatedImpressions>
    <AveragePosition>2.1</AveragePosition>
    <ShareOfClicks>16.17%</ShareOfClicks>
    <ShareOfSpend>15.24%</ShareOfSpend>
  </Item>
  <Item>
    <Competitor>competitor2.com</Competitor>
    <RelevantSearchTerms>13</RelevantSearchTerms>
    <EstimatedImpressions>2395</EstimatedImpressions>
    <AveragePosition>3.1</AveragePosition>
    <ShareOfClicks>12.97%</ShareOfClicks>
    <ShareOfSpend>14.12%</ShareOfSpend>
  </Item>
</DesktopMarketShare>
```
```markdown
Competitor,RelevantSearchTerms,EstimatedImpressions,AveragePosition,ShareOfClicks,ShareOfSpend
competitor1.com,49,3421,2.1,"16.17%","15.24%"
competitor2.com,13,2395,3.1,"12.97%","14.12%"
```

### Curl Request

`curl -i 'https://api.adthena.com/wizard/{id}/desktop-market-share/all?periodstart=2016-08-17&periodend=2016-08-18' -H 'adthena-api-key: my-api-key' -H 'accept: application/json'`

### HTTP Request

`GET /wizard/{id}/desktop-market-share/all?periodstart=2016-08-17&periodend=2016-08-18 HTTP/1.1`<br>
`Host: api.adthena.com`<br>
`Adthena-api-key: my-api-key`<br>
`Accept: application/json`<br>

# Market Trends

> The response has the following structure:

```json
[{
  "Competitor" : "competitor1.com",
  "Data" : [{
    "Date" : "2016-08-17",
    "Value" : 0.20252793391991963
  }, {
    "Date" : "2016-08-18",
    "Value" : 0.17226717371649275
  }]
}, {
  "Competitor" : "competitor2.com",
  "Data" : [{
    "Date" : "2016-08-17",
    "Value" : 0.1251964689111161
  }, {
    "Date" : "2016-08-18",
    "Value" : 0.1525691616591276
  }]
}]
```
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ShareOfClicksTrends>
  <Item>
    <Competitor>competitor1.com</Competitor>
    <Point>
      <Date>2016-08-17</Date>
      <Value>0.20252793391991963</Value>
    </Point>
    <Point>
      <Date>2016-08-18</Date>
      <Value>0.17226717371649275</Value>
    </Point>
  </Item>
  <Item>
    <Competitor>competitor2.com</Competitor>
    <Point>
      <Date>2016-08-17</Date>
      <Value>0.1251964689111161</Value>
    </Point>
    <Point>
      <Date>2016-08-18</Date>
      <Value>0.1525691616591276</Value>
    </Point>
  </Item>
</ShareOfClicksTrends>
```
```markdown
Competitor,2016-08-17,2016-08-18
competitor1.com,0.20252793391991963,0.17226717371649275
competitor2.com,0.1251964689111161,0.1525691616591276
```

There are six different Market Trend reports and each is called from a different API endpoint:

Report Type | Endpoint
----------- | --------
Market Trends - Share of Clicks | /desktop-share-of-clicks-trend
Market Trends - Share of Impressions | /desktop-impression-share-trend
Market Trends - Frequency | /desktop-frequency-trend
Market Trends - Average Position | /desktop-average-position-trend
Market Trends - Share of Spend | /desktop-share-of-spend-trend
Market Trends - Average CPC | /desktop-average-cpc-trend


### Curl Request

`curl -i 'https://api.adthena.com/wizard/{id}/desktop-share-of-clicks-trend/all?periodstart=2016-08-17&periodend=2016-08-18' -H 'adthena-api-key: my-api-key' -H 'accept: application/json'`

### HTTP Request

`GET /wizard/{id}/desktop-share-of-clicks-trend/all?periodstart=2016-08-17&periodend=2016-08-18 HTTP/1.1`<br>
`Host: api.adthena.com`<br>
`Adthena-api-key: my-api-key`<br>
`Accept: application/json`<br>

# Search Term Detail

> The response has the following structure:

```json
[{
  "SearchTerm": "my first search term",
  "Competitors": 12,
  "EstimatedClicks": 253,
  "AveragePosition": 3.5504277823493,
  "TopCompetitor": "competitor1.com",
  "EstimatedCPC": 3.8611486814916
},
{
  "SearchTerm": "my second search term",
  "Competitors": 10,
  "EstimatedClicks": 176,
  "AveragePosition": 3.3850404530201,
  "TopCompetitor": "competitor2.com",
  "EstimatedCPC": 4.8769243528258
}]
```
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<SearchTermDetail>
  <Item>
    <SearchTerm>my first search term</SearchTerm>
    <Competitors>12</Competitors>
    <EstimatedClicks>253</EstimatedClicks>
    <AveragePosition>3.5504277823492885</AveragePosition>
    <TopCompetitor>competitor1.com</TopCompetitor>
    <EstimatedCPC>3.8611486814916134</EstimatedCPC>
  </Item>
  <Item>
    <SearchTerm>my second search term</SearchTerm>
    <Competitors>10</Competitors>
    <EstimatedClicks>176</EstimatedClicks>
    <AveragePosition>3.3850404530201317</AveragePosition>
    <TopCompetitor>competitor2.com</TopCompetitor>
    <EstimatedCPC>4.876924352825813</EstimatedCPC>
  </Item>
</SearchTermDetail>
```
```markdown
SearchTerm,Competitors,EstimatedClicks,AveragePosition,TopCompetitor,EstimatedCPC
"my first search term",12,253,3.5504277823492885,competitor1.com,3.8611486814916134
"my second search term",10,176,3.3850404530201317,competitor2.com,4.876924352825813
```

### Curl Request

`curl -i 'https://api.adthena.com/wizard/{id}/search-term-detail/all?periodstart=2016-08-17&periodend=2016-08-18' -H 'adthena-api-key: my-api-key' -H 'accept: application/json'`

### HTTP Request

`GET /wizard/{id}/search-term-detail/all?periodstart=2016-08-17&periodend=2016-08-18 HTTP/1.1`<br>
`Host: api.adthena.com`<br>
`Adthena-api-key: my-api-key`<br>
`Accept: application/json`<br>

# Search Term Opportunities

> The response has the following structure:

```json
[{
  "SearchTerm": "my first search term",
  "Competitors": 12,
  "EstimatedClicks": 253,
  "AveragePosition": 3.5504277823493,
  "TopCompetitor": "competitor1.com",
  "EstimatedCPC": 3.8611486814916
},
{
  "SearchTerm": "my second search term",
  "Competitors": 10,
  "EstimatedClicks": 176,
  "AveragePosition": 3.3850404530201,
  "TopCompetitor": "competitor2.com",
  "EstimatedCPC": 4.8769243528258
}]
```
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<SearchTermOpportunities>
  <Item>
    <SearchTerm>my first search term</SearchTerm>
    <Competitors>12</Competitors>
    <EstimatedClicks>253</EstimatedClicks>
    <AveragePosition>3.5504277823492885</AveragePosition>
    <TopCompetitor>competitor1.com</TopCompetitor>
    <EstimatedCPC>3.8611486814916134</EstimatedCPC>
  </Item>
  <Item>
    <SearchTerm>my second search term</SearchTerm>
    <Competitors>10</Competitors>
    <EstimatedClicks>176</EstimatedClicks>
    <AveragePosition>3.3850404530201317</AveragePosition>
    <TopCompetitor>competitor2.com</TopCompetitor>
    <EstimatedCPC>4.876924352825813</EstimatedCPC>
  </Item>
</SearchTermOpportunities>
```
```markdown
SearchTerm,Competitors,EstimatedClicks,AveragePosition,TopCompetitor,EstimatedCPC
"my first search term",12,253,3.5504277823492885,competitor1.com,3.8611486814916134
"my second search term",10,176,3.3850404530201317,competitor2.com,4.876924352825813
```

### Curl Request

`curl -i 'https://api.adthena.com/wizard/{id}/search-term-opportunities/all' -H 'adthena-api-key: my-api-key' -H 'accept: application/json'`

### HTTP Request

`GET /wizard/{id}/search-term-opportunities/all HTTP/1.1`<br>
`Host: api.adthena.com`<br>
`Adthena-api-key: my-api-key`<br>
`Accept: application/json`<br>

# Top Adverts

> The response has the following structure:

```json
[{
  "Competitor": "competitor1.com",
  "Title": "First ad title",
  "Description": "First ad Description",
  "DisplayUrl": "www.competitor1.com/ad",
  "EstimatedImpressions": 10715,
  "AveragePosition": "3.5",
  "BestPosition": "T1",
  "SearchTerms": 6,
  "Frequency": "86.39%",
  "DisplayLength": 31,
  "FirstSeen": "2016-08-21",
  "LastSeen": "2016-09-20"
},
{
  "Competitor": "competitor2.com",
  "Title": "Second ad title",
  "Description": "Second ad Description",
  "DisplayUrl": "www.competitor2.com/ad",
  "EstimatedImpressions": 8804,
  "AveragePosition": "3.5",
  "BestPosition": "T1",
  "SearchTerms": 11,
  "Frequency": "66.48%",
  "DisplayLength": 31,
  "FirstSeen": "2016-08-21",
  "LastSeen": "2016-09-20"
}]
```
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<TopDesktopAds>
  <Item>
    <Competitor>competitor1.com</Competitor>
    <Title>First ad title</Title>
    <Description>First ad Description</Description>
    <DisplayUrl>www.competitor1.com/ad</DisplayUrl>
    <EstimatedImpressions>10715</EstimatedImpressions>
    <AveragePosition>3.5</AveragePosition>
    <BestPosition>T1</BestPosition>
    <SearchTerms>6</SearchTerms>
    <Frequency>86.39%</Frequency>
    <DisplayLength>31</DisplayLength>
    <FirstSeen>2016-08-21</FirstSeen>
    <LastSeen>2016-09-20</LastSeen>
  </Item>
  <Item>
    <Competitor>competitor2.com</Competitor>
    <Title>Second ad title</Title>
    <Description>Second ad Description</Description>
    <DisplayUrl>www.competitor2.com/ad</DisplayUrl>
    <EstimatedImpressions>8804</EstimatedImpressions>
    <AveragePosition>3.5</AveragePosition>
    <BestPosition>T1</BestPosition>
    <SearchTerms>11</SearchTerms>
    <Frequency>66.48%</Frequency>
    <DisplayLength>31</DisplayLength>
    <FirstSeen>2016-08-21</FirstSeen>
    <LastSeen>2016-09-20</LastSeen>
  </Item>
</TopDesktopAds>
```
```markdown
Competitor,Title,Description,DisplayUrl,EstimatedImpressions,AveragePosition,BestPosition,SearchTerms,Frequency,DisplayLength,FirstSeen,LastSeen
competitor1.com,"First ad title","First ad description","www.competitor1.com/ad",10715,3.5,T1,6,"86.39%",31,2016-08-21,2016-09-20
competitor2.com,"Second ad title","Second ad description","www.competitor2.com/ad",8804,3.5,T1,11,"66.48%",31,2016-08-21,2016-09-20
```

### Curl Request

`curl -i 'https://api.adthena.com/wizard/{id}/top-desktop-adverts/all' -H 'adthena-api-key: my-api-key' -H 'accept: application/json'`

### HTTP Request

`GET /wizard/{id}/top-desktop-adverts/all HTTP/1.1`<br>
`Host: api.adthena.com`<br>
`Adthena-api-key: my-api-key`<br>
`Accept: application/json`<br>

# Query parameters

These parameters can be applied in the query string section of the request URI, eg:

`https://api.adthena.com/wizard/{id}/desktop-share-of-clicks-trend?periodstart=2016-08-17&periodend=2016-08-18&searchterm=one&searchterm=two`

For parameters that support multiple values (arrays), repeat the parameter for each value. For example, to specify a list of competitors using the competitor parameter:

`competitor=competitor1.com&competitor=competitor2.com&competitor=competitor3.com`

Parameter | Required | Default | Multiple | Description
--------- | ------- | ---------|--------|------------
periodstart | <span class="tick"></span> | | | Start date for data in format yyyy-mm-dd. If the date is more than 30 days in the past, then weekly data (Monday - Sunday) will be returned.
periodend | <span class="tick"></span> | | | End date for data in format yyyy-mm-dd
traffictype | | paid | | paid/organic/total
wholemarket | | false | | Results will be taken from “whole of market” or “my search terms”
competitor | | | <span class="tick"></span> | Includes competitors in results
searchterm | | | <span class="tick"></span> | Includes search terms in results
exclude-competitor | | | <span class="tick"></span> | Excludes competitors from results
exclude-searchterm | | | <span class="tick"></span> | Excludes search terms from results
cg | | | <span class="tick"></span> | Includes competitor groups in results
kg | | | <span class="tick"></span> | Includes search term groups in results
exclude-cg | | | <span class="tick"></span> | Excludes competitor groups from results
exclude-kg | | | <span class="tick"></span> | Excludes search term groups from results
exclude-brand-terms | | false | | Exclude brand terms
adtext | | | <span class="tick"></span> | Include only adverts containing specific text string. Note: Only applicable to Top Adverts end point. Unlike other parameters, multiple values will be treated as an AND, so adverts containing both ‘$’ and ‘less than
exclude-text | | | <span class="tick"></span> | Exclude any adverts containing specific text string. Note: Only applicable to Top Adverts end point

# Content Negotiation

All Adthena endpoints return data in JSON, XML or CSV form. In order to return the appropriate content type, use one of the following accept headers:

`Accept: application/json`<br>
`Accept: application/xml`<br>
`Accept: text/csv`

# Errors

The Adthena API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request - Something is wrong with the request format
401 | Unauthorized - API key not found or account disabled 
403 | Forbidden - The API key does not allow access to this endpoint
404 | Not Found
405 | Method Not Allowed - Endpoint does not support the supplied HTTP method
406 | Not Acceptable - the requested format isn’t supported (see [Content Negotiation](#content-negotiation))
429 | Too Many Requests - Slow down your request rate
500 | Internal Server Error - We had a problem with our server. Try again later.
503 | Service Unavailable - We're temporarially offline for maintanance. Please try again later.