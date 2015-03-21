# AP-what?
Today, we turn our focus towards APIs. Chances are you've already used some of them, quite a lot, without even knowing about them:

* ever clicked on a Twitter "Share this" button?
* ever opened Facebook or Twitter?
* **other examples**

Well, you've used an API!

In short, APIs are a way to interact with an Internet service. A magnificent and powerful one. They can be used to:

* fetch data from a provider (that is what third-party Twitter clients do when tweets appear on your screen),
* or send data to a service (that's what you do when you don't write tweets on Twitter.com directly, you send a message to Twitter saying "I wrote this tweet").

Interacting with an API can be done in a number of way. Some of them are transparent to the user, and you interact with a third-party service which handles talking to the main service you want to reach through a graphical user interface (GUI).

Some others are more artisanal, geekier, and require you to write the queries manually, filling out a bunch of fields. These can even be used programmatically, with a script written in your language of choice, or your beloved command line.

For this tutorial, we are going to use the *BBC linked data API*. For a more clear definition of linked data, please refer [here](). But let's just say that linked data expresses relationships between concepts present in content. For example, a BBC article mentioning "David Cameron" will be considered by the machine as being *about* David Cameron, our Prime minister. You could then ask the service "show me all articles *about* David Cameron *and* Nigel Farage," for example.

# API keys and rate limiting
A quick word about security here: quite often, content providers restrict the use of their APIs. First, they'd rather only have approved developers using them, and not crackers, botnets, or spammers. On Twitter, you need an account associated with a phone number to obtain an API key, giving you access to some of their content. I say "some of it" because there is another (very exclusive) Twitter API, called *the firehose*, which gives you access to all the tweets posted, in real time.

Second, the number of queries you can send to the servers are quite often limited as well. The reason for this is that the provider has to pay for the bandwidth and calculations, and they don't want to be swamped by requests, or simply DDoSed. That is called "rate limiting." Should you exceed this limit, the server will stop replying to you for a while and invite you to chill out for a moment.

# What you will find in the BBC API
We call this API "the Juicer." It has been developed by BBC News Labs, and here is how it works:

* The Juicer scrapes news articles from the BBC and roughly 150 other news organisations, automatically. It ingests them in its database, identifying the title, the authors, the source, images, external links.
* It then performs entity extraction: in the articles' bodies, it will recognises some concepts ("David Cameron", "smoking", "Leicester", "Apple Inc"...), which can be people, places, organisations, or intangibles.
* It will match these concepts with a unified concepts base containing information about these concepts, this providing some consistency.
* Finally, it will draw relationships between the concepts: how often they co-occur together, with which other concepts they appear, their frequency over time...

Every step of the way can be interrogated by talking to the API directly. You might only be interested by reading articles about the geographic zone 15 miles around your current gps position, for example. Or you might just want to know what are the other politicians co-occurring with Nigel Farage in the last two months, and in which proportions. Or, you might be curious to know who is mentioned the most alongside Adolf Hitler in news articles.

Now, it might seem all a bit silly and broad, but you can use these APIs for quite nice purposes. If you have downloaded the new BBC News smartphone app (available on Android and iOS), you probably noticed that you can *follow* topics, such as your constituency or geographical area, major news developments ( *Islamic State crisis*, *counter-terrorism*, *Jeremy Clarkson*, *Cymru*, *Election 2015*...). These pages are aggregated automatically by the APIs, served to you by them - with probably a certain dose of human curation that I must admit not knowing about.

# Tools
You don't need much to talk to an API. Although some tools are nicer than the others.
To understand how a request works, we will use Google Chrome extension Postman, which is a pretty tool to make requests clear to humans. Go ahead and install it!
Once we're familiar with the requests and their responses, ...

# Making requests
There are important elements in the formulation of API queries that you will need to identify each time by reading the API documentation given by the provider. As a rule of thumb, you will need the url of the API server, a query, and an API key.
Then you will need to build your query following the available options (refer to the documentation).

# Getting a response
After you've sent your query, the server will reply in a certain format. One of the most common is JSON (which stands for *JavaScript Obect Notation*). This format is very standard and easy to parse in any language, and though it can be a bit bigger than flat CSV datasets, it is quite good at expressing relationships and hierarchy. JSON is also the format returned by the Juicer, and thus the one that we will use for this tutorial.
