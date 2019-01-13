# Cost of Running the Web
  Michael Zelensky

The web has become the global tool used by half of Earth population. Many of us use it every day for many hours. The population is growing, the percentage of users in the population is growing, and the usage of the web during the day is also growing. More and more things become part of the web and computer-defined reality. What does it take to run it? Let's try to find out.

## Costs summary

The annual cost of running the web is:

Item | Amount per year                    | Notes |
------ | -----| ---- |
Energy   | 11.5 TWh (1.15e+10 Kilowatt-hours) |
Storage       | 79 500 4-TB HDD's               | Same amount of hardware servers
Human Resource | 30 million                      | Educated for 5 years |
Maintenance   | 119 500 man-years                |
User experience     |        0.867                      | 23.2 million years of human life time. Explanation below.

## What is calculated

There are many services running on the Internet, and it is extremely difficult to separate them from each other. The goal of this paper to find out how much energy and human resource consumes the web. We can define the web as hypertext web. It mainly consists of websites, each on its own domain of the 2nd, 3rd, and sometimes 4th and rarely 5th and deeper level domains. Websites use Content Management Systems (CMS), and require running a web-server 24x7 in a data center. These webservers must be up and available on any point of the Internet, i.e. any place on Earth that has connectivity.

Websites consist of hypertext html pages, that are retrieved by users from webservers. The pages are then downloaded to the users' client devices and rendered by the browser software. As mentioned above, there are many Internet services which are used widely, like video and audio streaming, data transfer, etc, but we will focus only on the web transferring mainly text, images, and rendering instructions such as HTML, CSS and alike.

Summing up, there are three main parts of the web that consume energy:
- servers
- data transfer
- client-side rendering

If we happen to analyze these groups, we will find out how much energy and resource the web consumes. To do this, first we need to find out the number of pages served. It is not easy, but we can do some approximations.

## Statistics

**Domain names**
There are [342,4 million](https://www.verisign.com/en_US/domain-names/dnib/index.xhtml) 2-level domain names registered by Q3 2018. Annual growth 3.5%.

**Users**
[4,176 bln](https://www.statista.com/statistics/617136/digital-population-worldwide/) as of October 2018. [48% of the global population](https://en.wikipedia.org/wiki/Global_Internet_usage). The guess is that both numbers are growing.

**Websites**
~300 million (3e+8). The number of websites, currently existing, is very important for the estimations below. However, it is difficult to give an exact number, as there can be none, or many websites on each of 2-level domain. Search engines statistics may be a good source of data, or a spiderbot research, but for start a rough approximation would be enough. It is very likely that the number of websites is somewhere around the number of registered 2-nd level domain names. There are a lot of articles available, and many of them claim that there are 2 bln websites. Until we have better statistics, we will rely on our number of 3e+8. When we have better numbers, we can refine our calculations.

Websites are different, there are one-pagers, and on the other side there are social networks, shops, and other data hubs with millions of pages. For simplicity, we can narrow our website definition to a 10-page website enabled by a standard installation of a typical CMS. This is probably what the vast majority of sites are.

[Some more statistics](https://hostingfacts.com/internet-facts-stats/) picked randomly by "educated guess" from the web search result for "Internet statistics" query.

**Content Management Systems**

 CMS | Share | Notes |
 --- | --- | ---- |
Wordpress     | 52% | growing
Droopal       |  5% |
Others       |  43% |

Source: [CMS Usage Top 1M sites](https://trends.builtwith.com/cms)

## Server-side
The principle of work of a typical CMS is in generating an html page dynamically using many elements, such as scripts, text files, and databases. It means that when a browser requests a page from a server, the web server starts up a process of the page generation and then responses to the client with this page. Every time a page is requested, it is generated anew and then sent to the client. So, if there are 1000 clients requesting the same page, it is generated 1000 times.

A web server is a hardware machine that can host one or many websites on it. It requires an operating system (OS) and other software to host websites. This software can take 1 GB of disk space or more.

The typical webserver must be up and running 24x7, ready to serve any client that requests a page any time a day or night.

### Cooling

The physical work that computers do is turning electricity into heat because of electrical resistance. To get rid of that heat, data centers must use cooling of the same power. This adds the 2x coefficient to our formulas below.

E.g. see randomly found [Cisco's whitepaper](https://www.cisco.com/c/en/us/solutions/collateral/data-center-virtualization/unified-computing/white_paper_c11-680202.pdf) which proves the above statement:
> Cooling is a major cost factor in data centers. If cooling is implemented poorly, the power required to cool a data
> center can match or exceed the power used to run the IT equipment itself. Cooling also is often the limiting factor in
> data center capacity (heat removal can be a bigger problem than getting power to the equipment).

### Hardware overhead

There are several components of the server hardware architecture: CPU (50-150 W), RAM (2-6 W), HDD (0.6-9 W), motherboard (20-100 W), power supply, [etc](http://www.buildcomputers.net/power-consumption-of-pc-components.html). We will build our calculations only on CPU and HDD energy consumption, but it is clear that they cannot run on their own. They need the whole set of components, so for the other components overhead we will simply use a coefficient of 2x.

### Storage

Storage, needed for a website, varies greatly. There can be just one website on a dedicated hardware server, or a thousand of websites on a virtual server. If there is only one website on a server, this website requires OS and webserver software, that in total can take from 0.5 GB to 5 GB (2.25GB mean), and actually there is no higher limit. If many websites are served from one OS, then the disk space taken by the OS and webserver software is shared between all websites. Going on the assumption that a webserver serves 10 websites on average in the global scope, one website disk space overhead is 2.25 GB / 10 = 225MB. We will rely on this number until we don't have better statistics.

A fresh installation of the most popular CMS from the above statistics (version 5.0.2) consists of 1709 files and 172 directories that take 40 MB. Adding required MySQL database installation, we probably could roughly round this number up to 50MB, but we can leave 40MB for now, as we already have calculated disk space required for additional software. So, one website requires 225MB + 40MB = 265MB of server disk storage. In total for the web, as if it consisted of 10-pagers without images and other media, used storage would be:

**(1)** 265 MB x 3e+8 sites = **79 500 TB** of space,

or **79 500 4-TB hard drives** (as the most popular) with 25% usage in average (assumption). One HDD consumes 5 W in read/write mode, and we assume that a HDD that contains 1Tb of websites will always be in this mode. This makes the annual consumption of the web storage of **14 million kWh** per year:

**(2)** 2 W x 24 h x 365.25 days x 7.95e+5 HDDs x 1e-3 (kW) x 2 (cooling) x 2 (overhead) = **13 937 940 kWh**.

We will use this as the safe lower limit. Real data storage on the web is of course many times higher.

### Computation

A webpage requested from a CMS-driven website causes the runtime environment (e.g. php) generate a new html page. During the process of the page generation a lot of computational and operational power is used: scripting engine compiles scripts, many files are read, numerous DB connections and data retrievals are done, a lot of string processing of text files are done, numerous function call stacks thousand steps long are invoked. A typical question on CMS forums is how to avoid CPU bandwidth limit overgo. An html page rendering can take in worst cases up to 1s, or 0.1s in average. A CPU consumes 125 W. If an average website is hit as little as 10 times a day, generating the web costs around **15.22 million kWh** of energy per year:

**(3)** 3e+8 sites x 10 hits x 0.1s CPU / 3600 (s to hrs) x 365.25 days x 125 W / 1e+3 (kW) x 2 (cooling) x 2 (overhead) = **15 218 750** kWh / year

## Transfer

Every time a page is requested by the client software, it downloads content (text) mixed with markup (HTML), rendering and interaction instructions (CSS and JS), and all linked resources (fonts, libraries, images, and other media). An average page size is [2MB](https://www.machmetrics.com/speed-blog/website-size-the-average-web-page-size-is-more-than-2mb-twice-the-size-of-the-average-page-just-3-years-ago/) and growing. Transfer of 1GB of data [consumes 5.12 kWh](https://aceee.org/files/proceedings/2012/data/papers/0193-000409.pdf). Quote from the same source, explaining why it takes that much:

>All of the sends and receives at the carrier nodes are brokered by routers, switches, or hubs; each humming with the electronics of their own processers and overhead loads such as cooling, power conditioning, and lighting.  Additionally, when fiber optic, copper-wire, or wireless communication links must span long distances, the signal degrades and must be regenerated periodically by repeaters, each of which adds to the energy footprint of the activities.

Taking our 10 hits per day, we can calculate the annual web transfer energy consumption as **11.22 TWh**.

**(4)** 3e+8 sites * 10 hits * 365.25 days * 5.12 kW * 0.002 GB = **11 220 480 000 kWh**


## Client-side

When a page is downloaded, it has to be rendered by the HTTP client software. Rendering of a html page is a highly energy- and computation-consuming process. First, HTML is parsed and DOM is built, then CSS is parsed and applied to the DOM elements. So, every time a web page is requested, the browser has to render it from the raw HTML and CSS.

There is a big number of research and material on the topic. Here's a quote from [one of them](http://frontendbabel.info/articles/webpage-rendering-101/), although taken randomly, but reflecting the process correctly:

> 1. The DOM (Document Object Model) is formed from the HTML that is received from a server.
> 2. Styles are loaded and parsed, forming the CSSOM (CSS Object Model).
> 3. On top of DOM and CSSOM, a rendering tree is created, which is a set of objects to be rendered (Webkit calls each of those a "renderer" or "render object", while in Gecko it's a "frame"). Render tree reflects the DOM structure except for invisible elements (like the <head> tag or elements that have display:none; set). Each text string is represented in the rendering tree as a separate renderer. Each of the rendering objects contains its corresponding DOM object (or a text block) plus the calculated styles. In other words, the render tree describes the visual representation of a DOM.
> 4. For each render tree element, its coordinates are calculated, which is called "layout". Browsers use a flow method which only required one pass to layout all the elements (tables require more than one pass).
> 5. Finally, this gets actually displayed in a browser window, a process called "painting".

Different browsers and rendering engines implement rendering with different effectiveness. The rendering time and computations involved for the same page can vary greatly. Performance of different pages is different, because validity and optimization of the code affects this process.  Chromium is probably one of the most effective renderers today, and we can use its Audit tool from Chrome Developer Tools to analyze performance of a random page. I used the landing page of developer.mozilla.org website as contentful, and with presumably valid and optimized HTML/CSS which should give result, better than average. The results of running it for several times where between [1.4-1.6s](http://www.myz.ru/webcost/audit.gif), which is again a lower bound, because this page is well-formed and short.

Adding time needed for DNS resolving and data transfer, we will probably get around 3 seconds per page. We should also apply the same coefficients for hardware overhead as for the servers:

**(5)** 3e+8 sites x 10 hits x 3 s / 3600 (s to hrs) x 365.25 days x 125 W / 1e+3 (kW) x 2 (overhead) = **228 281 250 kWh**

## Total Energy

Summing up the above calculations show that the web consumes

**11 477 917 940 kWh** per year, or **11.5 TWh**.

One should take into consideration 18% overhead needed to produce and transfer electricity, which is not covered here.

## Ecology impact

In [greenhouse gas terms](https://www.epa.gov/energy/greenhouse-gas-equivalencies-calculator), 11.5 TWh means:
- 80 million metric tons of CO<sub>2</sub> emission
- 17.3 million cars owned and driven round a year. This is 1/4 of all cars [produced in 2016](http://www.worldometers.info/cars/) globally.
- 199 billion miles of a car driven.
- 1.3 trillion (1.3e+12) trees grown for 10 years to sequester carbon dioxide emissions. This number of trees is equal to 117 million square kilometers of forest, where trees grow in every 3 meters (11,5% of the [whole dry land area](https://en.wikipedia.org/wiki/List_of_countries_and_dependencies_by_area#Countries_and_dependencies_by_area)). Given that the world's forest is shrinking, this amount of CO<sub>2</sub> will be absorbed by the ocean, increasing its acidity and killing its life, though this is rather a bigger problem of the global CO<sub>2</sub> emissions, than our study.

In addition to that, the web needs Internet infrastructure: wires, datacenters, space, buildings, roads for maintenance. Computers turn energy into heat, this is the physical work that they do. To save money on cooling, it is becoming popular to build datacenters in naturally cold regions, which heats them up and harms life balance in these places.

## Non-energy cost

### Human resource

A typical CMS-driven website requires expensive and time-consuming maintenance. A website administrator must be an educated computer specialist, who knows:
- basics of computer fundamentals, like programming, networking, and system design
- web standards and technologies, like HTML, HTTP, SSL, etc.

These skills allow them to do:
- network and OS administration
- database administration
- CMS-specific programming and maintenance

It takes several years to prepare such specialists, and we can assume that an average specialist supervises 10 sites a year. Another assumption: every website administration takes on average 1 man-day per year. This means that we need about 30 mln specialists, and they spend **119.5 thousand man-years** every year:

**(6)** 3e+8 sites / 10 sites per webmaster = **3e+7 (30 million) webmasters**

**(7)** 3e+8 sites x 1 man-day x 10 sites / 251 working days (USA) = **119 522 man-years**

## User experience coefficient

When a user retrieves a webpage, the client software sends an HTTP request to the server after resolving its IP address. The request goes through many network routers, reaching the server. Then the server starts to process this request and generates the response and response body, which consists in most cases of HTML. This response is then sent back to the client software, where it is rendered. Basing on our [above assumption](#client-side), this takes 3 seconds on average.

When the response is rendered and the user sees the painted webpage, the user starts to analyze and learn it to understand how the content is presented and how to navigate the website. In simple terms, it is called usability or user experience (UX). The less time user is required to spend on this step, the better UX is. The greater the user's time losses on waiting and learning, the lower the UX ratio is.

We can speculate on learning time, because UX can be affected by many factors: the user's web operating skills, the user's fatigue, the user's familiarity with a specific webpage. If the user is a skilled computer and web operator, refreshed, and visits the page repeatedly, the page's UX will be very good. If these factors are lower, the UX will fall respectfully. Our speculated UX-time loss on average will be 5 seconds per page.

Judging by Alexa Top-500 sites statistics (site view time divided by page views), a user spends 1 minute on a webpage, and it means that the average UX ratio of the web is **0,867**:

**(8)**  1 - (3 s painting + 5 s UX) /  60 s duration = **0.867**

There are 4.176 billion users (4.176e+9). If their web session was 1 hour per day, they would loose 8 minutes per day (and per hour), or **23,2 million years** of human life time every year:

**(9)**  4,176e+9 users x 1 hour x 365.25 days x 0.133 = **203 371 200 000 hours**

Dividing this number of hours by the number of hours in a year (24 x 365.25) will result in the number of years.

Again, this is as if the average web session duration was 1 hour per user per day. In reality it is probably higher. As well, as learning time is also can be much higher than 5 seconds.

## To the reader

Statistical values for these calculations are often taken from various sources, found mostly on the first page of web search results. Intuitively I would estimate the [measurement error](https://en.wikipedia.org/wiki/Observational_error) as high as 10 (you can also see that I use this number often to be refined later). Applied this measurement error, we can treat the result as being truthful between 0.1x and 10x of the calculated values.

If you have or know non-profit or academic research on any of the numbers used, found errors, or anyhow can provide better data for the calculations, please [let me know](mailto:michaelzelensky@gmail.com). You can also play with the calculations and check how the results change if you change the input: [calculations](http://www.myz.ru/webcost/calculations.html).
