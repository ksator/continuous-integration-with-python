[![Build Status](https://travis-ci.org/ksator/continuous-integration-with-python.svg?branch=master)](https://travis-ci.org/ksator/continuous-integration-with-python)
[![Coverage Status](https://coveralls.io/repos/github/ksator/continuous-integration/badge.svg?branch=master)](https://coveralls.io/github/ksator/continuous-integration?branch=master)  

## About this repo: 
- How to test python code with pytest.  
- How to mesure test coverage with pytest-cov (Pytest plugin for measuring coverage).
- How to automate tests using pytest with TravisCI.   
- Automatic coverage reporting with Coveralls.  

## Inpired by:  
- introduction to CI with Travis: https://www.youtube.com/watch?v=buXwBr9H3VY  
- introduction to pytest: https://www.youtube.com/watch?v=LdVJj65ikRY 
- python doctest module: https://docs.python.org/2/library/doctest.html
- automated tests with pytest: https://ilovesymposia.com/2014/10/01/continuous-integration-0-automated-tests-with-pytest/
- Measuring test coverage: https://ilovesymposia.com/2014/10/02/continuous-integration-1-test-coverage/  
- Setting up test configuration files: https://ilovesymposia.com/2014/10/13/continuous-integration-in-python-3-set-up-your-test-configuration-files/  
- Using Travis-CI to run your tests automatically with each git push: https://ilovesymposia.com/2014/10/15/continuous-integration-in-python-4-set-up-travis-ci/  
- continuously check your test coverage using Coveralls (https://coveralls.io/): https://ilovesymposia.com/2014/10/15/continuous-integration-in-python-5-report-test-coverage-using-coveralls/ 
- badge your repo: https://ilovesymposia.com/2014/10/17/continuous-integration-in-python-6-show-off-your-work/  

## Requirements: 

### To test python code locally: 
```
sudo pip install pytest pytest-cov coveralls  
```
Actually, coveralls installation is not required locally. it is used by Travis CI  to push coverage report to the Coveralls service.     

### Travis CI:  
to test with Travis CI, you need a github account.  
Github supports webhook with Travis CI.   
Travis CI runs tests every time you push to your GitHub repository.   

### Coveralls:   
Travis pushes the coverage report to Coveralls every time Travis is run.   
You can sign in to Travis and coveralls with your github account.  

## Usage for this repo:   
```
git clone https://github.com/ksator/continuous-integration.git  
cd continuous-integration/  
```

## How does it work: 

### pytest:    
This is a testing tool for python.   
By default, pytest discovers tests by looking at files that have these patterns test_*.py and *_test.py  
Type py.test on the command line at your project root directory: Pytest will traverse all your subdirectories, gather up all the test files, run your tests, and provide an output.  

pytest installation: 
```
pip install pytest
```

**maths.py** has some function definitions. **tests/test_multiple.py** has the tests for math.py  

### doctest:    
The doctest module searches for pieces of text that look like interactive Python sessions, and then executes those sessions to verify that they work exactly as shown.  
https://docs.python.org/2/library/doctest.html  
Pytest supports doctests with the **--doctest-modules** flag.  

**maths3.py** is using doctests. the tests are in the code comment.  

### coverage reporting:   
testing is important, measuring coverage is also important.   
Pytest can measure coverage for you with the coverage plugin, found in the pytest-cov package. pytest-cov is a Pytest plugin for measuring coverage.  

pytest-cov installation: 
```
pip install pytest-cov
```

use the option **--cov** to mesure coverage.  
with the option **--cov-report term-missing**, we can see which lines are not covered.   

### Travis CI:  
to make these tests and reports automatic, we use a github webhook with Travis CI.   
Travis tests with py.test the repo every time you push to your GitHub repository.  
The file **.travis.yml** has the Travis CI details.  
The file **requirements.txt** has the list of python packages Travis installs.  

### Coveralls:  
Our **.travis.yml** file use the service Coveralls: Travis pushes the coverage report to Coveralls every time it runs, i.e., every time you push something to your GitHub repository.  
 
## run python tests locally:   
```
py.test  
py.test -v  

py.test --cov .  
py.test --cov . -v  

py.test --cov maths.py  
py.test --cov maths.py -v  

py.test --cov-report term-missing --cov .  
py.test --cov-report term-missing --cov . -v  

py.test --cov-report term-missing --cov=maths.py  
py.test --cov-report term-missing --cov=maths.py -v  

py.test --doctest-modules -v  

py.test --doctest-modules --cov .  
py.test --doctest-modules --cov . -v  

py.test --doctest-modules --cov . --cov-report term-missing  
py.test --doctest-modules --cov . --cov-report term-missing -v  

py.test --doctest-modules --cov=maths3.py  
py.test --doctest-modules --cov=maths3.py -v   

py.test --doctest-modules --cov=maths3.py --cov-report term-missing  
py.test --doctest-modules --cov=maths3.py --cov-report term-missing -v  
```
##  setup.cfg file:   
you can use a setup.cfg file at the root of the project with configuration options (ignore maths2.py, cov-report term-missing, ....) to then invoke your tests with a simple call to py.test.  
more details:   
https://ilovesymposia.com/2014/10/13/continuous-integration-in-python-3-set-up-your-test-configuration-files/  
http://pytest.org/latest/customize.html  
http://coverage.readthedocs.io/en/latest/config.html  

## python syntax check: 
you can use the module py_compile to validate the syntax of a python script.  
```
python -m py_compile maths.py  
```

