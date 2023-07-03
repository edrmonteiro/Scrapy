# Scrapy Basic commands
## install
sudo apt-get install python3 python3-dev python3-pip libxml2-dev libxslt1-dev zlib1g-dev libffi-dev libssl-dev

inside a virtualenv: pip install scrapy

# 1_first_project
## start project
scrapy startproject projectName<br> 
scrapy startproject quotes_spider

## scrapy url
cd quotes_spider<br> 
scrapy genspider name websiteToScrapy <br>
scrapy genspider quotes quotes.toscrape.com

## show scrapys on the project
scrapy list
### enter into scrapy shell
scrapy shell
### open a site with scrapy, inside the shell:
fetch("quotes.toscrape.com/")

### to inspect the site
response response.css('h1') <br>
response.css('h1::text') <br>
response.xpath('//h1') <br>
response.xpath('//h1/a') <br>
response.xpath('//h1/a/text()') <br>
response.xpath('//h1/a/text()').extract() <br>
response.xpath('//h1/a/text()').extract_first() <br>
response.xpath('//h1/a/text()').extract()[0]

response.xpath('//') <br>
response.xpath('//[@class="tag"]') <br>
response.xpath('//[@class="tag-item"]') <br>
response.xpath('//[@class="tag-item"]').extract() <br>
response.xpath('//*[@class="tag-item"]/a/text()').extract()

## to run python code
outside shell from quotes_spider directory <br>
scrapy crawl quotes

if the website does not have robots.txt file, go to settings.py and change ROBOTSTXT_OBEY to false

# 3_advanced
## scrapy process
scrapy startproject quotes_spider <br>
cd quotes_spider <br>
scrapy genspider quotes quotes.toscrape.com <br>
scrapy shell 'http://quotes.toscrape.com/' <<br>
quotes = response.xpath('//[@class="quote"]') <br>
quote = quotes[0] <br>
quote.extract() <br>
quote.xpath('//a') <br>
quote.xpath('.') br>
quote.xpath('//[@class="text"]/text()').extract() <br>
quote.xpath('//[@class="text"]/text()').extract_first() <br>
quote.xpath('//[@itemprop="author"]/text()').extract_first() <br>
quote.xpath('.//[@itemprop="keywords"]/@content').extract_first() <br>
quote.xpath('.//[@class="tag"]//text()').extract() <br>

next_page_url = response.xpath('//*[@class="next"]/a/@href').extract_first() response.urljoin(next_page_url) <br>

## save project result into file
scrapy crawl quotes -o items.csv scrapy crawl quotes -o items.json scrapy crawl quotes -o items.xml

