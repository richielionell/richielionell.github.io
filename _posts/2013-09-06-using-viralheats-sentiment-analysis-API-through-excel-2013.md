---
layout: post
title: Using Viralheat's Sentiment Analysis API through Excel 2013
---

Microsoft's Excel 2013 comes with some interesting stuff like [PowerMap](http://www.microsoft.com/en-in/download/details.aspx?id=38395), [PowerView](http://cwebbbi.wordpress.com/2012/07/17/building-a-simple-bi-solution-in-excel-2013-part-1/) & [Apps](http://office.microsoft.com/en-us/store/apps-for-excel-FX102804981.aspx).

But in this post I'd like to focus on three new functions that help extract data from webservices.

- **webservice**
- **encodeurl**
- **filterxml**

Let's make use of these functions to extract data from the viralheat sentiment analysis api;

The `url` that is passed would look like this;


    https://viralheat.com/api/sentiment/review.xml?text=happy&api_key=yourapikey

`review.xml` says that the output would be returned in the xml format, `text=` holds the text for which we require the sentiment analysis & `api_key` holds your viralheat api key.

Now let's open an excel 2013 workbook and in cell B5 type the following formula;

 `=webservice("https://viralheat.com/api/sentiment/review.xml?text=happy&api_key=yourapikey")`

Remember to replace "yourapikey" with the viralheat api key.

The following xml output would be returned in cell B5;

    <result>
    <text>happy</text>
    <mood>positive</mood>
    <prob>0.8065489449209308</prob>
    </result>

Now instead of hardcoding the "text" in the url, let's tie it to an Excel cell. Let's assume we are going to paste our text in A6. In that case we will have to url encode whatever is going to be typed in cell A6, like this;

    =webservice("https://viralheat.com/api/sentiment/review.xml?text="&encodeurl(A6)&"&api_key=yourapikey")

Using `filterxml` let's extract information that is necessary from the xml output. In cell C6 you could type;
    
    =filterxml(B5,"result/mood")

and in C7 you could say;

    =filterxml(B5,"result/prob")

Cell B5 holds the xml output that we got using the `webservice` function. C6 would have the text 'positive' and C7 would have '0.8065489449209308'.

Interacting with APIs has become easy now with these Excel 2013 functions.

That is cool! How about trying a 'sentiment analysis' of Robert Frost's 'The Road Not Taken'?

Now try using the `webservice` & `filterxml` functions together in the same cell like this;

![](http://db.tt/N8E6oOpY)

 Since ViralHeat accepts only 360 characters of text for every api call we use the `len()` function to find the number of characters in the cell that holds the text, just to make sure we are sending the right amount of text for analysis. This is how the output looks like;

![](http://db.tt/g3BfvGVf)

eh.. One might disagree with the results though. Robert Frost must be turning in his grave.
