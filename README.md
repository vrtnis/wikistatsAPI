

<h1>wikistats</h1>


<h2>Random Quotes API with statistics from Wikipedia</h2>


wikistats is a free and open source API that provides statistics-related sentences (or quotes) from the Simple English version of Wikipedia.\
\
This API has been built as a side-project (as an alternative to conventional quote APIs). The raw quote data is stored in the "Data" folder.

<br>

## API Endpoint

```
https://api.statistron.xyz/v1/wikistats
```


<br>

[![Run in Postman](https://run.pstmn.io/button.svg)](https://elements.getpostman.com/redirect?entityId=26982513-8fb164dd-eebf-441a-99ff-21ea675410b4&entityType=collection&workspaceId=a547849a-d103-4bad-aaa7-00ff8e0dd146)

<br>



## API Reference <!-- omit in toc -->

- [Get Random Quotes](#get-random-quotes)
- [Search Quotes (beta)](#search-quotes-beta)

<br>

## CodePen Examples <!-- omit in toc -->


- [Random Quotes](https://codepen.io/statistron/pen/KKGgNXM)

[<img src="assets/screenshot_bulk_quotes_15-40-11.png"  width="700" height="750">](https://codepen.io/statistron/pen/KKGgNXM)



<br>

## Get Random Quote(s)

```HTTP
GET /?q=random&limit=your_integer_value
```

Returns one or more random quote(s) from the database as an array of JSON objects.  You must specify the limit parameter.  The limit parameter must be less than 50.
                                   
<br>

**Sample response for one quote**

```ts
{
  quote: string,
  // The text of the statistical quote 
  //(e.g., An iron carbon alloy is only considered steel if the carbon level is between 0.01% and 2.00%.)
  source: string,
  // The source which includes the formatted Wikipedia article name followed by Wikipedia (e.g., Materials Science | Wikipedia)
  article: string
  // The slugified title of the Wikipedia article (e.g., materials_science)
}
```
<br>

[Try it in your browser](https://api.statistron.xyz/v1/wikistats?q=random&limit=1)

<br>

[Codepen](https://codepen.io/statistron/pen/JjmRbyL)


<br>


---

<br>

**Sample response for 10 quotes**



**Response**

```ts
[{
  quote: string,
  // The text of the statistical quote 
  //(e.g., An iron carbon alloy is only considered steel if the carbon level is between 0.01% and 2.00%.)
  source: string,
  // The source which includes the formatted Wikipedia article name followed by Wikipedia (e.g., Materials Science | Wikipedia)
  article: string
  // The slugified title of the Wikipedia article (e.g., materials_science)
},
{
  quote: string,
  // The text of the statistical quote 
  //(e.g., It has a spectrum similar to the Sun, but is only 78% of the Suns mass.)
  source: string,
  // The source which includes the formatted Wikipedia article name followed by Wikipedia (e.g., Tau Ceti | Wikipedia)
  article: string
  // The slugified title of the Wikipedia article (e.g., tau_ceti)
 
},

{...}
// ...and so on
//10 JSON objects total

]



```

<br>




[Try it in your browser](https://api.statistron.xyz/v1/wikistats?q=random&limit=10)

<br>

[Codepen](https://codepen.io/statistron/pen/KKGgNXM)


<br>

---


<br>

## Search Quotes (beta)

```HTTP
GET /?q=your_search_string
```

This endpoint allows you to search through quotes.  It uses OpenSearch.  It returns an array of a single object or multiple objects depending on the number of results.


**Examples**

Search for "catalyst" [try in browser](https://api.statistron.xyz/v1/wikistats?q=catalyst)

```HTTP
GET /search/quotes?query=catalyst
```
<br>
Results:

```ts
[{"quote": "Use of an iron catalyst, however, resulted in only 30% methane in the product; the rest consisted of short-chain hydrocarbons.", "source": "Fischer-tropsch Process | Wikipedia", "article": "fischer-tropsch_process"}]

```

<br>

Search for quotes with the keywords "earth" or "mars" [try in browser](https://api.statistron.xyz/v1/wikistats?q=earth+mars)

```HTTP
GET /search/quotes?query=earth+mars
```
<br>

Results:

```ts
[{"quote": "The surface gravity on Mars is 38% of that on Earth.", "source": "Colonization Of Mars | Wikipedia", "article": "colonization_of_mars"}, {"quote": "The Sun as seen from Mars is about as large as seen from Earth, and shines 40% of the light, approximately the brightness of a slightly cloudy afternoon on Earth.", "source": "Extraterrestrial Sky | Wikipedia", "article": "extraterrestrial_sky"}, {"quote": "Mars mantle makes up 74–88% of its mass.", "source": "Mantle (geology) | Wikipedia", "article": "mantle_(geology)"}, {"quote": "About 60% of the surface of Mars shows a record of impacts from that era.", "source": "Mars | Wikipedia", "article": "mars"}, {"quote": "The planet is also 1.52 times as far from the Sun as Earth, resulting in just 43% of the amount of sunlight.", "source": "Mars | Wikipedia", "article": "mars"}, {"quote": "During a poles winter, it lies in continuous darkness, chilling the surface and causing the deposition of 25–30% of the atmosphere into slabs of CO2 ice (dry ice).", "source": "Mars | Wikipedia", "article": "mars"}, {"quote": "It made the smooth Borealis Basin that covers 40% of the planet.", "source": "Mars | Wikipedia", "article": "mars"}, {"quote": "This salty water makes up about 97% of all Earths water.", "source": "Earth | Wikipedia", "article": "earth"}, {"quote": "Mars has only 0.1% by volume, with the other planets having less than that.", "source": "Oxygen | Wikipedia", "article": "oxygen"}, {"quote": "Each has at least 1% of all languages on Earth:", "source": "Language Family | Wikipedia", "article": "language_family"}]

```
<br>

---

<br>

### Rate Limit

There is a rate limit of **100 requests per minute**, per IP address. Exceeding this can result in a `429` error. 

---


### Credits

Inspired by popular quote APIs such as [Quotable](https://github.com/lukePeavey/quotable) and [Animechan](https://github.com/rocktimsaikia/anime-chan)
