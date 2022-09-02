+++
title="Amazon Auto Purchaser Bot Challenge"
date=2022-08-24
extra.thumbnail="/assets/images/projects/amazon-auto-purchaser/snail.jpg"
extra.status="Done"
extra.description="A coding challenge to automatically purchase items from Amazon using code."
extra.tools=["TypeScript", "Chrome/Firefox DevTools"]
extra.toc = true
+++

{{ img(path="/assets/images/projects/amazon-auto-purchaser/snail.jpg", center="True") }}

A customer's garage full of 93 Playstation 5's purchased via this company's software.


### What is this? 

This was a coding challenge from a retail item scalping company, (think GPUs, PS5's, Xboxs, etc) used to assess my skills as a developer. This was the first of two challenges.   

The first challenge I was given was to create a script that could automatically purchase an item from Amazon.

### Ethics

Before I talk about this project, I would like to note that at the time I was working on this assignment I was unsure of whether or not this was a good thing to be working on. I was blinded by work dissatisfaction as well as an eye catching email that said the salary range was $150k-$300k. I now have come to conclude that I do not believe that scalping is the type of work I want to spend my time and talents on, regardless of the potential financial gains.

With that being said, I would still like to present the results of this coding assignment with the following things in mind:

1. I believe that this project has professional value as it demonstrates that I have a solid understanding of web automation, HTTP, cookies and sessions, async javascript, and other skills relevant to being a web developer.

2. I am deliberately excluding the name of the company that this coding challenge came from. 

3. I did not sign any NDAs or license these assignments in such a way that I cannot share them. The code I wrote is entirely my IP.


---

## The Assignment

#### Requirements

1. Write a program in Typescript/Node.js that periodically checks for in-stock status of two Amazon.com (US) products:
   1. An out-of-stock product of your choosing.
   2. An in-stock product of your choosing.
2. The two products should be checked concurrently.
3. The program should purchase the product if it detects it's in stock (feel free to manually cancel the order after). The program may exit after a successful purchase.

#### Notes

1. You may only use HTTP requests. Webdrivers like Selenium, Puppeteer, etc are not permitted.
2. You may install any other dependencies you find useful.
3. You may provide cookies to the program so you don't have to add login logic.
4. You can use your personal Amazon account for testing. Nothing bad will happen to your account, and Amazon doesn't care about repeated order cancellations.
5. Most checkout endpoints require you to have a shipping and payment address defaulted on your Amazon account, so make sure to do that manually before testing.

## My Submission

---

### Zach Bellay -- Crawler / Purchase Bot Submission

#### Demo Video!
**Audio Warning** : Keystrokes are a loud, be warned if using headphones.

{{ video(path="/assets/images/projects/amazon-auto-purchaser/demo.mp4")}}

[Link to Video](https://zbellay.sfo3.cdn.digitaloceanspaces.com/demo.mp4)

#### How it works

This program generates the same requests to view, add to cart, and purchase a product on Amazon as a browser. There are 5 steps:

1. Generate a new cookie by logging into Amazon and grabbing the new cookie. Copy this into the `.env` file and set `AMAZON_COOKIE` equal to this value.

{{ img(path="/assets/images/projects/amazon-auto-purchaser/cookie.png", center="True") }}


2. GET the product page and check that the item is in stock.

{{ img(path="/assets/images/projects/amazon-auto-purchaser/product_page.png", center="True") }}

- If the product is in stock, simulate clicking the "Add to Cart" button by sending a HTTP POST request. The data for this POST request is scraped and filtered from all `<input>` tags on the product page.

3. Now that we have the product in our cart, we want to proceed to checkout. In order to do so, we send an HTTP GET request simulating clicking on the "Proceed to checkout" button.

{{ img(path="/assets/images/projects/amazon-auto-purchaser/added_to_cart.png", center="True") }}

4. We are now in the checkout page. To check out we send an HTTP POST request that simulates clicking the "Place your order" button. The body of the POST request is again generated by scraping all `<input>` tags and then filtering down by elements we know will produce a successful outcome (observed via Chrome developer tools network tab).

{{ img(path="/assets/images/projects/amazon-auto-purchaser/checkout_page.png", center="True") }}

5. If successful, the POST request will return a redirect to a page that thanks the customer for purchasing the item. 

{{ img(path="/assets/images/projects/amazon-auto-purchaser/purchased.png", center="True") }}

{{ img(path="/assets/images/projects/amazon-auto-purchaser/console.png", center="True") }}


#### Time Allocation

Estimated Time Spend by Day: 

- Monday, Jan 3 - 2 hours

- Tuesday, Jan 4 - 3 hours

- Friday, Jan 7 - 3 hours

- Saturday, Jan 8 - 6 hours

- Sunday, Jan 9 - 10 hours

- Monday, Jan 10 - 6 hours

- Tuesday, Jan 11 - 3 hours

- Total time spent: 33 hours


Estimated Time Spent by Task:

- Screwing around with Postman (5 hours)
- Debugging weird Typescript issues (5 hours)
- Debugging GET/POST requests not resulting in what I wanted (15 hours)
- Writing code and refactoring (5 hours)
- Writing submission (2 hours)
- Writing tests (1 hour)

#### Thought Process/Challenges

I immediately reached for Postman Interceptor to capture and replay HTTP requests when beginning this project. But unfortunately it didn't really work properly so I ended up abandoning the tool. 

From there I began trying to replicate the HTTP requests I was seeing in the Chrome developer tools network tab. Replicating the requests weren't too difficult, but I was having issues with the proceed to checkout not actually proceeding to checkout, and instead asking me to confirm my address or if I wanted gift wrapping.

I narrowed down the issue to the add to cart POST request. I was adding all elements in `<input>` tags to the body of the post request. However, I was sending a lot of extraneous information. So, I found success by adding a filter by cross referencing the body of the POST request in Chrome developer tools network tab.

That was my main breakthrough moment. That and realizing I needed to URL encode the body of my POST requests (duh!). 

---

### Conclusion

I learned a lot technically and morally from this project. This was a really interesting and fun project to work on, that I later realized was one of those things that just because you can do it doesn't mean you should.

