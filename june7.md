June 7 ~ Request/Response
============================

The Internet  

<video playsinline="true" src="https://media.wired.com/clips/603054d5d5aeee948f9055a6/720p/pass/security_internetmapping4k.mp4"></video>

---

<img src="https://hcwebdev.netlify.app/bboard.jpg">


---

<div class="audiodiv"><audio controls>
<source src="https://oona.windytan.com/blogfiles/dialup.mp3" />
[HTML5 audio: In-line recording of the beginning of a telephone call made by a modem.]
</audio></div>
  

![](https://oona.windytan.com/posters/dialup-final.png)
[More on modems](http://www.windytan.com/2012/11/the-sound-of-dialup-pictured.html)

---

<img src="https://hcwebdev.netlify.app/dns-via-home-router2.jpg">

---

## Berkeley Sockets
Berkeley sockets is an industry standard Application Programming Interface (API) to create and use sockets. It was initially used as an API for the Unix operating system and was later adopted by TCP/IP.

Berkeley defines 18 standard function names for this purpose.
![](https://microchip.wikidot.com/local--files/tcpip:berkeley-sockets/berkeley.JPG)

The __socket()__ function creates a socket on the host.
The __bind()__ function is typically used on the server side and assigns a socket to its local IP address and port number. Connect() is typically used on the client side. It creates a socket and also attempts to establish a TCP or UDP connection with a server.
Send(),recv() and write(),read() are used to send and receive the messages to and from the socket. [(source)](https://microchipdeveloper.com/com4104:berkeley-sockets)

---

Sockets are connections between two computers.  
Python [sockets library](https://docs.python.org/3/library/socket.html) 

```python
import socket

mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
mysock.connect(('info.cern.ch', 80))
cmd = 'GET http://info.cern.ch/hypertext/WWW/TheProject.html HTTP/1.0\r\n\r\n'.encode()
mysock.send(cmd)

while True:
    data = mysock.recv(512)
    if len(data) < 1:
        break
    print(data.decode(),end='')

mysock.close()
``` 
[(src)](https://www.dj4e.com/code/http/client1.py)  
[AF_INET?](https://docs.python.org/2/library/socket.html) A single string is used for the AF_UNIX address family. A pair (host, port) is used for the AF_INET address family, where host is a string representing either a hostname in Internet domain notation like 'daring.cwi.nl' or an IPv4 address like '100.50.200.5', and port is an integer.


---

![](https://mdn.mozillademos.org/files/13687/HTTP_Request.png)

```html
GET http://info.cern.ch/hypertext/WWW/TheProject.html HTTP/1.0
```

---


![](https://mdn.mozillademos.org/files/13691/HTTP_Response.png)

[Status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

---

More on sockets:   
  
https://docs.python.org/3/howto/sockets.html  
https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview    

## Requests 



<hr>
<h4>GET vs. POST</h4>
<p>The following table compares the two HTTP methods: GET and POST.</p>
<div class="w3-responsive">
<table class="w3-table-all notranslate">
  <tr>
    <th style="width:30%">&nbsp;</th>
    <th style="width:35%">GET</th>
    <th>POST</th>
  </tr>
  <tr>
    <td>BACK button/Reload</td>
    <td>Harmless</td>
    <td>Data will be re-submitted (the browser should alert the user that the data are about to be re-submitted)</td>
  </tr>
  <tr>
    <td>Bookmarked</td>
    <td>Can be bookmarked</td>
    <td>Cannot be bookmarked</td>
  </tr>
  <tr>
    <td>Cached</td>
    <td>Can be cached</td>
    <td>Not cached</td>
  </tr>
  <tr>
    <td>Encoding type</td>
    <td>application/x-www-form-urlencoded</td>
    <td>application/x-www-form-urlencoded or multipart/form-data. Use multipart encoding for binary data</td>
  </tr>
  <tr>
    <td>History</td>
    <td>Parameters remain in browser history</td>
    <td>Parameters are not saved in browser history</td>
  </tr>
  <tr>
    <td>Restrictions on data length</td>
    <td>Yes, when sending data, the GET method adds the data to the URL; and the length of a URL is limited (maximum URL length is 2048 characters)</td>
    <td>No restrictions</td>
  </tr>
  <tr>
    <td>Restrictions on data type</td>
    <td>Only ASCII characters allowed</td>
    <td>No restrictions. Binary data is also allowed</td>
  </tr>
  <tr>
    <td>Security</td>
    <td>GET is less secure compared to POST because data sent is part of the URL<br>
 <br>
 Never use GET when sending passwords or other sensitive information!</td>
    <td>POST is a little safer than GET because the parameters are not stored in browser history or in web server logs</td>
  </tr>
  <tr>
    <td>Visibility</td>
    <td>Data is visible to everyone in the URL</td>
    <td>Data is not displayed in the URL</td>
  </tr>
  </table>
</div>
<a href="https://www.w3schools.com/tags/ref_httpmethods.asp">src</a>
<hr>


The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.

__simple request__ 
```python
import requests
response = requests.get("http://www.gutenberg.org/cache/epub/250/pg250.txt")
if response.status_code == 200: 
    headers = response.headers
    text = response.text
    binary = response.content 
    json = response.json()
```

__request with argument__ 
```python
response = requests.get(
    'https://api.github.com/search/repositories',
    params={'q': 'requests+language:python'},
)
response.json()
```

same as get request in the browser [`https://api.github.com/search/repositories?q=requests+language:python`](https://api.github.com/search/repositories?q=requests+language:python)


The POST method is used to submit an entity to the specified resource, often causing a change in state or side effects on the server.

https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

```python
requests.post('https://httpbin.org/post', data={'key':'value'})
requests.put('https://httpbin.org/put', data={'key':'value'})
requests.delete('https://httpbin.org/delete')
requests.head('https://httpbin.org/get')
requests.patch('https://httpbin.org/patch', data={'key':'value'})
requests.options('https://httpbin.org/get')
```

---

<iframe style="width:100%;height:400px" src="https://httpbin.org/"></iframe>

---


More on Requests   

https://realpython.com/python-requests/  



# Types of Response 

---

## [Response](https://fastapi.tiangolo.com/advanced/custom-response/#response)
The main Response class, all the other responses inherit from it.

`content - A str or bytes.`  
`status_code - An int HTTP status code.`  
`headers - A dict of strings.`  
`media_type - A str giving the media type. E.g. "text/html".`  

```python
from fastapi import FastAPI, Response

app = FastAPI()


@app.get("/legacy/")
def get_legacy_data():
    data = """<?xml version="1.0"?>
    <shampoo>
    <Header>
        Apply shampoo here.
    </Header>
    <Body>
        You'll have to use soap here.
    </Body>
    </shampoo>
    """
    return Response(content=data, media_type="application/xml") 
```

[full list of media types](https://www.iana.org/assignments/media-types/media-types.xhtml)

---


## PlainTextResponse
Takes some text or bytes and returns an plain text response.

```python
from fastapi import FastAPI
from fastapi.responses import PlainTextResponse

app = FastAPI()

@app.get("/", response_class=PlainTextResponse)
async def main():
    return "Hello World"
```

---

## HTMLResponse

```python
from fastapi import FastAPI
from fastapi.responses import HTMLResponse

app = FastAPI()


@app.get("/items/", response_class=HTMLResponse)
async def read_items():
    return """
    <html>
        <head>
            <title>Some HTML in here</title>
        </head>
        <body>
            <h1>Look ma! HTML!</h1>
        </body>
    </html>
    """
```

---

## [HTML Templates](https://fastapi.tiangolo.com/advanced/templates/)

While it is possible to write the HTML by hands, more often, we create a template that is automatically updated.  
This provides
- consistent styling and formatting
- allows use of a templating language such as [Jinja](https://jinja.palletsprojects.com/en/2.11.x/)

```html
<title>{% block title %}{% endblock %}</title>
<ul>
{% for user in users %}
  <li><a href="{{ user.url }}">{{ user.username }}</a></li>
{% endfor %}
</ul>
```
`{% ... %}` is a programming statement  
`{{ ... }}` is a variable expression  
`{{ foo.bar }}` or `{{ foo['bar'] }}` accesses an attribute of the data passed to the template  

---

You can add conditions: `{% if foo %}<p>Foo!</p>{% endif %}`  
You can add loops: `{% for fish in fishes%}<p>{{ fish }}</p>{% endfor %}`  

1. `pip install Jinja2`  
2. create a `templates` directory 
3. in `templates` create a `base.html` and `index.html` template

---

**main.py**

```python
from fastapi import FastAPI, Request
from fastapi.responses import HTMLResponse
from fastapi.staticfiles import StaticFiles
from fastapi.templating import Jinja2Templates

app = FastAPI()

app.mount("/static", StaticFiles(directory="static"), name="static")

templates = Jinja2Templates(directory="templates")

@app.get("/greeting/{name}", response_class=HTMLResponse)
async def read_item(request: Request, name: str):
    context = {}
    context['request'] = request
    context['greeting'] = f"Hello {name}!"
    return templates.TemplateResponse("index.html", context)
```

---

**index.html**
```html
 <html>
        <head>
            <title>The Title</title>
        </head>
        <body>
            <h1>{{ greeting }}</h1>
        </body>
    </html>
```

