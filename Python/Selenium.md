# Selenium

## 목차

## 목표
selenium 을 이용한 Chrome Control

### Install
python 3 를  이용하여 설치
~~~ruby
pip3 install selenium
~~~

### selenium 위치 확인
~~~ruby
brew install geckodriver
which geckodriver
 /usr/local/bin/geckodriver
~~~ 

### Chrome을 이용한 selenium 이용
chromeDriver 설치 필요
~~~ruby
brew install chromedriver
~~~

### Chrome 버전 정보 확인
설정(cmd + ,) -> Chrome 정보 -> 버전정보 확인
[ChromeDriverDownloadLink](https://chromedriver.chromium.org/downloads) 접속 Chrome버전에 맞는 드라이버 다운로드

### Google Login
보안으로 인해 Login이 우횔 위해 selenium-stealth 설치
~~~ruby
 pip3 install selenium-stealth
~~~
 
 stealth 기능 이용하여 가상환경 구성
 ~~~python
from selenium_stealth import stealth

#Optional argument, if not specified will search path
driver = webdriver.Chrome('/usr/local/bin/chromedriver')

stealth(driver,
        languages=["en-US", "en"],
        vendor="Google Inc.",
        platform="Win32",
        webgl_vendor="Intel Inc.",
        renderer="Intel Iris OpenGL Engine",
        fix_hairline=True,
        )
 ~~~

### Python 명령어 작성

~~~python

import time
from selenium import webdriver

driver = webdriver.Chrome('/usr/local/bin/chromedriver')
driver.get('http://www.google.com/')
time.sleep(5)

search_box = driver.find_element_by_name('q')
search_box.send_keys('search something')
search_box.submit()
time.sleep(5)

driver.quit()

~~~

