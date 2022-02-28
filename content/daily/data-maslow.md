+++
title="Maslow's Heirarchy of Data Needs"
date=2022-02-27
extra.tldr=""
+++

You've heard of Maslow's Heirarchy of Needs. But what are `Data Needs`?

This Heirarchy helps outline the foundation any organization needs to lay out if they want to actually "Leverage Big Data™" or "Disrupt the Industry with AI®". So here she is, in all her glory. It took me about 5 minutes to come up with, but honestly I think it's pretty good.

<div class="columns is-centered">
    {{ img(path="/assets/images/daily/data-maslow/heirarchy.jpg") }}
</div>

### The Heirarchy

So in reverse order, starting at the bottom is **Capital**. In other words, funding, money, gwala, cheddar, pork, clams, dough, dollars, bucks, racks, skrilla. It almost feels stupid to say this, but you need money to operate a business. Why? Well that gets us to our next level.

**Labor**. In other words, employees (and hopefully not a "family"). Without human labor, businesses can't exist. But, as it turns out these so called "employees" apparently have needs like shelter, food, power, water, etc, etc. Which is pretty inconvenient. So until we have reached the top of this `Data Needs Heirarchy` and replace those meatbags, I mean employees, with robots and AI, we have to pay them with money.

**Operations**. If you run a business destined to make money, then your employees should be doing something useful, ideally not filing TPS reports 9-5. These operations should really be the engine of your business. This is what brings home the bacon. If all of your operations happened to seize due to say, a worker strike or perhaps a nuclear strike, then you would be a sad capitalist, and/or irradiated (depending on how extreme those employees are!). For example, on a farm these operations would include the planting of seeds, the monitoring of crop health, the harvest of said crops, and the packaging, transport, and sale of those crops to paying customers. In this hypothetical scenario, all of these operations are manual. But you aspire to  automate them so you can rob jobs, I mean increase efficiency. This will then maximize our return to our beloved shareholders! (hallowed be thy names). So how can we increase our efficiency?

**Data**. To be more specific, Data Collection. Let's say for example you are currently employing people to manually weed your fields. We want to build a machine that can do this, but we need to build some way to recognize the difference between crop and weed. A good starting point would be to employ these people to collect photos of crops and weeds, and label them for us. This would build up a large repository of examples that our robot overlords can reference when making the decisions themselves. And of course we'll need to organize it in a logical and easily accessible way. Perhaps we would build a database to store the metadata for these images? Just a thought. 

**Analysis** and algorithms. This is typically where the nerds come in. If you have a BS in CS, it's your time to shine. Data is pretty much worthless until you start making it do jigs for you. And by that I mean using it to train machine learning models. The goal here is to squeeze out the underlying information that is stored in the data. Why did _Employee #871_ decide to call this a weed and not a crop? Was it an accident? Beats me, but hopefully by using lots of linear algebra, Python, and over-priced Nvidia GPUs, we can train the machine to sniff it out for us.

**Visualization**. We've all heard the phrase that "A picture is worth a thousand words". And with a word going for 14.8¢ on the open market, that adds up quick. Dashboards are a great way to convey massive amounts of information in a pretty succinct way. As it turns out 100K rows in a database table printed out like a CVS receipt doesn't help make business decisions. So turning this information into something digestible is massively important. Oftentimes, this is where business intelligence tools like Tableau are wielded by ex-frat/sorority types to point out obvious things, I mean deep insights. Only once we have achieved these insights, can we move onto the next, and final stage of the pyramid.

**Decisions**. In the Maslow's Heirarchy of Needs, this is the Self-Actualization step. Once this has been achieved the birds come out to sing, the sun comes out from behind the clouds, and Warren Buffet awards you the Berkshire Hathaway Medal of Synergy. In our previous analogy of the automated farm weeding, a decision may to be to actually allow certain types of weeds because they pose no threat to the crop, but choke out other weeds. Or in another example, you learn that making a small tweak to the fertilizer composition increases crop yield by 22.4%. 


### Conclusion

All businesses today that market themselves as tech companies hope to achieve the top of this `Data Heirarchy of Needs`. But, it is important to remember that in order to get to this point, each previous level of the pyramid must be built out in a robust fashion. If you are hoping to actually leverage large quantities of data and cheap compute, then make sure you focus on the really boring aspects of this pyramid. 

* Make sure you find the right investors who understand that returns won't be immediate if you just "add machine learning".
* Make sure you hire the right people to collect your data, and that you create and iterate on robust methods for collecting data.
* Make sure your business is not doomed to fail due to too much bureaucracy or complete lack of leadership.
* Make sure you give engineers room to experiment to improve ML models, but not so much that they aren't held accountable for delivering business value.
* Make sure you develop concise methods for boiling down the vast quantities of data in an easily digestible way.
* Finally, make sure you make the best decision possible given your judgement and the data presented to you.