#### to create and prepare the project
scrapy startproject quotes_login_spider

ROBOTSTXT_OBEY = False

scrapy genspider login quotes.toscrape.com

changes on login.py

#### to run the project
scrapy crawl login 

#### to find the csrf_token value
scrapy shell 'http://quotes.toscrape.com/login'
response.xpath('//*[@name="csrf_token"]/@value').extract_first()


