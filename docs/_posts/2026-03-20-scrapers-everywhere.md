---
category: Software
---

I always felt a little something when I heard the term web scraping, I wanted to get into it but never had the time. School, work, or a f pandemic and sickness that I thought was going to kill me, anyhow the moment finally came.

I had to work on a project where I would fix a tool that generated insights for the hospitality industry, and that's when I realized 95% of tutorials about web scraping are irrelevant, at least for industry purposes they simply don't work, and here I will tell you why and what does normally, but not always, work, and especially how web scraping is a mix of everything, so if you have a friend that is getting serious with learning software fundamentals, tell them to scrape Amazon, if they can.

Before that, a warning, this is for people that are interested in learning the technical side behind or to at least realize why the data guy I hire charges me so much when I ask him for a full house solution to scrape data from the web, but because the idea of this blog is to put in simpler terms the tech stuff, here a brief:
you need to reverse engeneer the site you want to scrape , prepare for  an armamentistic war were you create spies  and they anty spy methods, and after that manage the hole storage cleanning and probably presenting of the data, so it combines knowing automation , a little of ciber security, network protocols, proxies, some  web development tecnologies, data bases orchestraition with containers probably  and to keep updating the system. IT'S A LOT OF WORK.End of the brief. 

First you want to enter the main page of the portal you want to scrape, and add this to the URL "/robots.txt", this is normally for crawlers but it can give you a perspective of the mission you are about to embark on.

When it tells that specific user agents are disallowed, now you know they monitor user agents and will spot you if your user agent makes no sense.

User agent string: is information about your system and is sent in the user agent header when you send an HTTP request.

robots.txt also specifies sensitive endpoints, when you see they are disallowed, and the sitemaps that are safe to just scrape with no use of UI.
If they say something like crawl-delay 3, that can mean you can only send a request every 3 seconds.
It also tells you how complex the site is, depending on how many tracking endpoints, disallows, user agents, and sitemaps.
More complex sites, more strict anti-bot measures.

You have to infer other things from the names of those sensitive endpoints:
/tracking/: have anti-bot systems with behavior tracking
/js_tracking: telemetry and performance tracking and detection of headless browsers
/fragment.: the site is dynamic, so the HTML is partial and it probably uses AJAX
/anysearch.: the results on a search are also loaded dynamically
/event: it tracks user action logic
/xfg: or weird names like that could be an anti-bot system, do they have many user agents blocked?

Now you want to go again to your main page and put a lot of attention to:

How you are interacting with it, so you can then replicate that behavior (clicks, scrolls, searches, idle times, mouse movements).
Use the developer tools to find out how the structure that renders the info you are interested in is built (HTML, CSS, XPath), and maybe go to the network section, if you are in luck you can find a hidden API that will make everything much easier, but from here we will presuppose you did not find it.

As we have established, this is warfare, so your scraper needs to be maintainable and robust, because changes will be needed as the website changes their UI or updates their anti-bot measures, this is why I will suggest you use a layered-based approach and a modular architecture thinking, where you define a core module from which you can import for your specific scrapers, if there is a better way you guys are encouraged to contact me via LinkedIn and tell me.

layers:

Orchestrator: the idea is that here you decide how and when to split in batches the scraper jobs, when and how the scraper will run, and for this here you will connect all the instances of your other layers, and handle failures, concurrency, and rate limits (how much to scrape in one run).

Automation driver: all the interaction that a human will do to get to the URL you want to scrape, this module is responsible for that, if you are using Playwright or Camoufox, or decided to build  the  user behavior controller  yourself using playwrigth or selenium .

Network/fingerprint/proxy: Services from IP Royal or Bright Data will be useful, especially the ones that allow you to rotate in residential proxies, because if the server sees you (your IP) too often you are blocked. You also want to rotate your session, you know, that thing that is built with which cookies you are using and the data of the hardware and browser you use to navigate to a page, I think Bright Data has something called secure browser that helps with that.

Parsing/extraction: here you use the selectors you previously found using the developer tools to know what to extract and actually do it, all the cleaning, normalization, and validation of the data goes here. Beautiful Soup is one of the standards here.

Storage: I don't have much experience here, still, not only a SQL database will be needed, an entire data pipeline is in order where you do data quality functions like normalization, validation, deduplication, idempotency, you need to decide if the data pipeline will process the data in a stream or in batches, I think this depends on how much RAM is available and how much data you have, or you can just dump the data in a CSV, your call.

Infrastructure: where and how the system runs. Docker is a must here, you can put it in a GitHub runner or an EC2, you want a way to handle logging and monitoring protocols, and maybe a way to destroy and create instances of your scraper system dynamically to better handle fingerprinting if you do so by yourself, and I haven't talked about concurrency or observability because, being honest, I don't really understand how that works yet, I just do a logging config, where I manage logs in files with the handlers it has by default and try not to let them grow too much.

As you can see, the anti-bot strategies are specially distributed in the network, automation, infrastructure, and orchestration modules or layers of your core.

Implementation will take its time, I hope there were a library or framework that had all these modules and I could just import and use out of the box, like scikit-learn for machine learning, but the closest thing I found is Scrapy and it falls short in some aspects apparently, but still a good thing to use.

Because you will have to implement a lot of this yourself, it is a good idea to have the next concepts clear:

interface: this is a template that is standardized for what a file should have in terms of behaviors (methods and functions), does not provide implementation
factory pattern: imagine a super machine (class) that creates entire lines of production (other classes that actually create objects)
strategy pattern: the idea is that it is a decision-maker algorithm, you give it a context (arguments to a function) and based on that it decides the best tool for the job
abstract class: a mental group that is normally only used to gather classes that have some similarity between them. Humans, dogs, and whales (classes) are all mammals (abstract class), and inside there can be implementations of methods or variables that all classes inside of mammals have, like breathing or number of eyes
difference between instance, static, and class methods: an instance method only makes sense if there is an object to perform it (to talk only can be done if a person exists and knows how to). A static method can be used even if there is no instance of the class (imagine a validation strategy to check if it's a person that is not performed by another person). And finally, a class method is pretty similar to a static method but can edit variables that are part of the class, not the individuals in that class (number of persons in the world).

Now my  dear spy, go and  scrape the world. 