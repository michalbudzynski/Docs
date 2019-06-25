## 1) Create Makefile to run steps clearly:

> ##### Command to install dependencies
> 

    deps:
    	pip install -r test_requirements.txt

> 
> ##### Command to run tests

    test:
    PYTHONPATH= py.test

## 2) Create test_requirements.txt file

    selenium


## 3) Create a .travis.yml file

> ##### Command to define language, and python version (https://docs.travis-ci.com/user/languages/python/)
> 

    language: python
    python:
    - "3.7-dev"

> ##### Command to install google chrome

    addons:
      apt:
        packages:
          - google-chrome-stable

> 
> ##### Command to install dependencies pip install -r test_requirements.txt

    install:
    - make deps

> 
> ##### command to download and unzip chromedriver to travis local folder

    before_script:
    - wget https://chromedriver.storage.googleapis.com/75.0.3770.90/chromedriver_linux64.zip
    - unzip chromedriver_linux64.zip -d /home/travis/virtualenv/python3.7-dev/bin/
    - export CHROME_BIN=chromium-browser

> 
> ##### command to run tests define in Makefile PYTHONPATH= py.test
> 

    script:
    - make test

> 
> ##### command to check chrome browser version
> 

     - google-chrome-stable --version

## .travis.yml

    language: python
    python:
    - "3.7-dev"
    addons:
      apt:
        packages:
          - google-chrome-stable
    install:
    - make deps
    before_script:
    - wget https://chromedriver.storage.googleapis.com/75.0.3770.90/chromedriver_linux64.zip
    - unzip chromedriver_linux64.zip -d /home/travis/virtualenv/python3.7-dev/bin/
    - export CHROME_BIN=chromium-browser
    script:
    - make test

## Makefile

    deps:
    pip install -r test_requirements.txt
    test:
    PYTHONPATH= py.test
## test_requirements.txt

    selenium





