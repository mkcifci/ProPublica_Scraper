## ProPublica-scraper

```python
from selenium import webdriver
from bs4 import BeautifulSoup
import re

browser = webdriver.Chrome(executable_path = r'/chromedriver')

browser.get(r'https://projects.propublica.org/represent/statements/search')
browser.find_element_by_class_name('next_page').click()

soup = BeautifulSoup(browser.page_source,'html')

tables = soup.find_all('table')
table = str(tables[0])


links = re.findall('>Title</b>.*?</a></span></td>', table)
for line in links:
    link = re.search('(?P<url>https?://[^\s]+)', line)
    print(link.group("url"))

# conda install -c anaconda json
import json
with open('/file.json') as f:
  df = json.load(f)
  
df = df['results']

import pandas as pd
dataset = pd.DataFrame(df)

# extract text from url
# conda install -c anaconda urllib2
# conda install -c anaconda urllib

from bs4 import BeautifulSoup 
import re 
import urllib.request as urllib2

# read urls of websites from text file 
list_open = open("web list.txt") 
read_list = list_open.read() 
line_in_list = read_list.split("\n") 
 
for url in dataset.url: 
    soup = BeautifulSoup(urllib2.urlopen(url).read(), 'html') 
    # parse something special in the file 
    paragraph = soup.find_all('p')
    paragraphs = (' '.join(paragraph))
    statement = []
    paragraphtext = []
    for p in paragraphs:
        text = print(str(p.get_text()))
        paragraphtext.append(text)
   
    statement.append(paragraphtext)
    myarticle.append(statement) 
    
    print(myarticle[0])
```
