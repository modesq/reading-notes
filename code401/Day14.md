# class 14

## web scraping

Web scraping, web harvesting, or web data extraction is data scraping used for extracting data from websites. Web scraping software may directly access the World Wide Web using the Hypertext Transfer Protocol or a web browser. While web scraping can be done manually by a software user, the term typically refers to automated processes implemented using a bot or web crawler. It is a form of copying in which specific data is gathered and copied from the web, typically into a central local database or spreadsheet, for later retrieval or analysis.

## how to do it  right

Web scraping is a task that has to be performed responsibly so that it does not have a detrimental effect on the sites being scraped. Web Crawlers can retrieve data much quicker, in greater depth than humans, so bad scraping practices can have some impact on the performance of the site. While most websites may not have anti-scraping mechanisms, some sites use measures that can lead to web scraping getting blocked, because they do not believe in open data access.

If a crawler performs multiple requests per second and downloads large files, an under-powered server would have a hard time keeping up with requests from multiple crawlers. Since web crawlers, scrapers or spiders (words used interchangeably) don’t really drive human website traffic and seemingly affect the performance of the site, some site administrators do not like spiders and try to block their access.

## Web Scraping best practices to follow to scrape without getting blocked

1. Respect Robots.txt
2. Make the crawling slower, do not slam the server, treat websites nicely
3. Do not follow the same crawling pattern
4. Make requests through Proxies and rotate them as needed
5. Rotate User Agents and corresponding HTTP Request Headers between requests
6. Use a headless browser like Puppeteer, Selenium or Playwright
7. Beware of Honey Pot Traps
8. Check if Website is Changing Layouts
9. Avoid scraping data behind a login
10. Use Captcha Solving Services
11. How can websites detect web scraping?
12. How do you find out if a website has blocked or banned you?
