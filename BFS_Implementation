from urllib.request import urlopen
from urllib import parse
from html.parser import HTMLParser

urlmain="https://www.pec.ac.in"
crawled1=open('crawled.txt','w')
crawled1=""
#i=0

class link_parser(HTMLParser):
    def __init__(self, url):
        super().__init__()
        self.url = url
        self.links = []

    def handle_starttag(self, tag, attrs):
        # print("Length = ", str(len(self.links)))
        if tag == 'a':
            for name, value in attrs:
                if name == 'href':
                    newurl = parse.urljoin(self.url, value)
                    if newurl not in self.links:
                        self.links.append(newurl)

    def get_links(self):
        return self.links

def crawl(url):
 try:
    response = urlopen(url)
    html_bytes = response.read()
    html_string = html_bytes.decode("utf-8")
    finder=link_parser(url)
    finder.feed(html_string)
    return finder.get_links()
 except:
     print("exception")

crawl(urlmain)
queue=set()
tu=(urlmain,1)
queue.add(tu)
crawled1=open('crawled.txt','a')
crawled1.write(urlmain+'\n')
while queue:
    variable=queue.pop()
    #print(variable)
    var=variable[0]
    index=variable[1]
    crawled1= open('crawled.txt', 'a')
    if index<=6:
     crawled1.write(var+'\n')
     print(var)
     setnew=crawl(var)
     setnew2=set()
     print(index)
     if setnew is not None:
      for x in setnew:
            tu=(x,index+1)
            setnew2.add(tu)
      print(setnew)
      queue.update(setnew2)

     p=0
     for indtest in range(1,7):
       if indtest in queue:
           p=p+1

     if p>0:
         break



