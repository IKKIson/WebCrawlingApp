# Study Note

## Class 01. Setting IDE for Web Crawling

### 크롤링 하고 싶은 데이터 확인해보기
- 파이어폭스, 크롬 등 웹브라우저를 사용하여 찾고자하는 데이터가 있다면 해당 웹의 요소에서 마우스 우클릭 후 '요소검사' or '검사'를 클릭하면 HTML에서 어떻게 데이터가 구성됬는지 확인 할 수 있다.(개발자모드 F12의 Elements)
- 해당 강의에서는 Ubuntu14/Python2.7 환경에서 개발하였지만 본 Repository는 Windows10/Pycharm/Python3.6으로 진행한다.

### 개발환경 구축하기
- Python, Pycharm 설치(과정 생략)

#### 1. 파이썬 가상환경 구축 - No PyCharm(VirtualEnv - Python Virtual Environment)
1. 가상환경이란?
    - VitualEnv란 파이썬을 이용하여 여러가지 프로그램을 여러개 개발할 때, 각각 독립된 파이썬 개발환경을 만들도록 도와준다.
    - 즉, 내가 원하는 폴더에 특정 파이썬, 라이브러리들을 설치하여 실행하는것이다.
    - 필요한 라이브러리가 있을 때 바로 다른 폴더에 설치해 사용할 수 있다.
    - 개인폴더에 설치하는 것이기 때문에 관리자 권한이 필요하지 않게 된다.
    - 본설명은 Win콘솔, Linux터미널에서 개발하는 상황을 고려한 방법이다.

2. 설치 방법
    - 다운로드 및 설치
    ```markdown
    pip install virtualenv
    ```
    - 사용 방법
    ```markdown
    virtualenv "파이썬을 설치할 폴더경로"
    ex) virtualenv C:\MyPython(독립된 파이썬 환경을 만들고 싶은 곳)
    ```
    - 바로 다음 DLLs 폴더를 복사해준다.(?)
    - 파이썬 프로그램 or  설치하는 라이브러리 실행하기
    ```markdown 
    "파이썬 설치된 폴더경로"의 script 폴더로 이동
    cd C:\MyPython\Script
    실행 명령어
    activate
    ```
    - 파이썬 프로그램 or  설치하는 라이브러리 실행종료
    ```markdown 
    "파이썬 설치된 폴더경로"의 script 폴더로 이동
    cd C:\MyPython\Script
    실행 명령어
    deactivate
    ```
3. 가상환경의 오류
    - 원하는 라이브러리를 소스코드에서 import 할 시 오류가 생기는 경우가 있는데, 그중 하나는 원래 파이썬이 설치된 폴더에서의 lib폴더에서 사용할 라이브러리의 폴더를 그대로 자신의 가상환경 폴더에 복사해주면된다.
    - 이러한 원인은 virtualenv 상에서 몇몇 c extension 파일을 복사힞 않는 문제이다.
    
#### 2. 파이썬 가상환경 구축 - Using PyCharm(VirtualEnv - Python Virtual Environment)
- 파이참의 경우 pip와 같은 명령어를 사용하지 않고 필요한 라이브러리나 모듈 등을 추가할 수 있다.
- VirtualEnv의 경우 파이참에서 파이썬프로젝트 생성 시 자신이 프로젝트가 생성될 폴더에 자동으로 생성해준다.
1. 프로젝트 생성 시 자동 생성
2. Setting에서 설정하기


#### 3. 파이참에서 라이브러리 Import 하기(No pips.... etc)
- 설치방법
    1. 상단메뉴의 File 메뉴 클릭
    2. File메뉴의 Settings 클릭 (단축기 : Ctrl + Alt + S)
    3. 좌측 메뉴에서 Project:'나의프로젝트명'클릭
    4. 하위의 Project Interpreter 클릭
    5. 가장 우측의 초록색의 + 버튼 클릭
    6. Available Packages 창이 뜬다. 원하는 라이브러리를 검색
    7. 원하는 라이브러리가 검색됬으면 클릭 후 하단의 Install Packge 버튼을 클릭한다.

- 설치 오류
    1. pip 버전문제로 새당 폴더의 파이썬에서 pip업그레이드 하기
        ```markdown
        python -m pip install --upgrade pip
        ```    
    2. 파이썬 버전에 따른 라이브러리 지원
        - 자신이 사용하는 파이썬2와 파이썬3을 확인하여 지원하는 라이브러리나 라이브러리버전을 확인해준다.
        - BeautifulSoup의 경우 BeautifulSoup기존 버전으로 파이썬3에 사용할 수 없으며, BeautifulSoup4를 사용해야된다.
    
#### 4. 파이참에 beautifulsoup 라이브러리 Import 하기(No pips.... etc)
1. About BeautifulSoup
    - The current release is Beautiful Soup 4.6.0 (May 7, 2017). You can install Beautiful Soup 4 with pip install beautifulsoup4.
    - [About beautifulsoup](https://www.crummy.com/software/BeautifulSoup/#Download)
    - [Download Page](https://www.crummy.com/software/BeautifulSoup/bs4/download/)
2. Install 
    - Install in the same way as in 3(above)
    
#### 5. 파이참에 scrapy 라이브러리 Import 하기(No pips.... etc)
1. Aboud scrapy
    - A Fast and Powerful Scraping and Web Crawling Framework
    - The current release is Scrapy 1.5.
    - [Scrapy Home](https://scrapy.org/)
    - [Download Page](https://scrapy.org/download/)

2. Install 
    - Install in the same way as in 3(above)

<hr/>

## Class 02. BeautifulSoup & Scrapy 

### 웹크롤링을 위한 라이브러리
- 가장 많이 사용되는 웹 크롤링 라이브러리이다.
- beautifulsoup도 scrapy처럼 여러 기능을 사용할 수 있지만 직접 구현해야된다. 

#### BeautifulSoup
- 인터넷의 문서을 가져와 그 정보를 가져오는, 파싱을 하는 역할이다.(파서)
- html문서에서 원하는 정보를 손쉽게 가져올 수 있는 방법을 제공.(사용자를 위한 네비게이션역할이 잘되어있다.)
- 자동으로 인코딩을 유니코드로 변환해서 UTF-8로 출력.(이 기능이 강력함. -> 한국어 특성상)
- lxml, html5lib 파서를 이용함

#### Scrapy
- 웹에서 데이터를 들고와 처리하는 전체적인 내용을 프레임워크형태로 제작한 라이브러리이다.
- 기능이 굉장히 많고 다양하다.
- web scraper framework
- 다양한 selector지원
- 파이프 라인(가져온 데이터를 후처리하기 좋다.)
- 로깅(데이터가 잘 들어오고 잘 처리되는지 알 수 있다.)
- 이메일


## Class 03. Web Data's Copyright and Site Policies

### 웹크롤링을 위한 라이브러리