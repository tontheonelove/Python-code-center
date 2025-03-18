## 1. Install the required libraries

- First, you need to install the required libraries: Flask and feedparser:
```
pip install Flask feedparser
```


## 2. Python code to fetch RSS Feed and display it on Web Server

```
from flask import Flask, render_template_string
import feedparser

app = Flask(__name__)

# ฟังก์ชันดึงข้อมูล RSS Feed
def get_rss_feed(url):
    feed = feedparser.parse(url)
    return feed.entries

# หน้าเว็บหลัก
@app.route('/')
def index():
    rss_url = 'https://cointelegraph.com/rss'  # ใส่ URL ของ RSS feed ที่คุณต้องการ
    entries = get_rss_feed(rss_url)

    # HTML Template สำหรับแสดงผล
    template = '''
    <!DOCTYPE html>
    <html lang="th">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>RSS Feed</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                padding: 20px;
            }
            h1 {
                text-align: center;
            }
            .rss-item {
                margin-bottom: 20px;
                border-bottom: 1px solid #ccc;
                padding-bottom: 10px;
            }
            .rss-item a {
                font-size: 18px;
                text-decoration: none;
                color: #007bff;
            }
            .rss-item a:hover {
                text-decoration: underline;
            }
        </style>
    </head>
    <body>
        <h1>RSS Feed</h1>
        <div>
            {% for entry in entries %}
                <div class="rss-item">
                    <h2><a href="{{ entry.link }}" target="_blank">{{ entry.title }}</a></h2>
                    <p>{{ entry.summary }}</p>
                </div>
            {% endfor %}
        </div>
    </body>
    </html>
    '''

    # ส่งข้อมูลไปแสดงในหน้าเว็บ
    return render_template_string(template, entries=entries)

if __name__ == '__main__':
    app.run(debug=True)
```
