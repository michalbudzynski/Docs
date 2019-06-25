Create Makefile to run steps clearly:

# command to install dependencies
deps:
	pip install -r test_requirements.txt

# command to run tests
test:
PYTHONPATH= py.test



Create test_requirements.txt file

selenium


Create a .travis.yml file

# command to define language, and python version
https://docs.travis-ci.com/user/languages/python/

language: python
python:
- "3.7-dev"
# command to install google chrome
addons:
  apt:
    packages:
      - google-chrome-stable

# command to install dependencies pip install -r test_requirements.txt
install:

- make deps

# command to download and unzip chromedriver to travis local folder
before_script:
- wget https://chromedriver.storage.googleapis.com/75.0.3770.90/chromedriver_linux64.zip
- unzip chromedriver_linux64.zip -d /home/travis/virtualenv/python3.7-dev/bin/
- export CHROME_BIN=chromium-browser

# command to run tests define in Makefile PYTHONPATH= py.test

script:
- make test

# command to check chrome browser

- google-chrome-stable --version

# command to check version chromedriver
