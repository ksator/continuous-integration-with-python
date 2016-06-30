# continuous-integration
[![Build Status](https://travis-ci.org/ksator/continuous-integration.svg?branch=master)](https://travis-ci.org/ksator/continuous-integration)
[![Coverage Status](https://coveralls.io/repos/github/ksator/continuous-integration/badge.svg?branch=master)](https://coveralls.io/github/ksator/continuous-integration?branch=master)


### introduction to CI with Travis   
https://www.youtube.com/watch?v=buXwBr9H3VY  

### introduction to pytest
https://www.youtube.com/watch?v=LdVJj65ikRY 

### what to find on this repo
CI with Travis and pytest. And test coverage using Coveralls.   
inpired by:      

automated tests with pytest   
https://ilovesymposia.com/2014/10/01/continuous-integration-0-automated-tests-with-pytest/  

Measuring test coverage  
https://ilovesymposia.com/2014/10/02/continuous-integration-1-test-coverage/  

Setting up test configuration files  
https://ilovesymposia.com/2014/10/13/continuous-integration-in-python-3-set-up-your-test-configuration-files/  

Using Travis-CI to run your tests automatically with each git push  
https://ilovesymposia.com/2014/10/15/continuous-integration-in-python-4-set-up-travis-ci/  

continuously check your test coverage using Coveralls (https://coveralls.io/)  
https://ilovesymposia.com/2014/10/15/continuous-integration-in-python-5-report-test-coverage-using-coveralls/ 

badge your repo  
https://ilovesymposia.com/2014/10/17/continuous-integration-in-python-6-show-off-your-work/  


### requirements
to test python code locally, sudo pip install pytest pytest-cov coveralls  
to test with Travis CI, you need a github account. you can sign in to Travis and coveralls with your github account.       

###usage for this repo  
git clone https://github.com/ksator/continuous-integration.git  
cd continuous-integration/ 
Github has a webhook with Travis CI.   
Travis CI runs tests every time you push to your GitHub repository.   
Travis pushes the coverage report to Coveralls every time Travis is run.  


### how does it work
maths.py has some function definitions.  
tests/test_multiple.py has the tests for math.py  

This git repo has a webhook with Travis.   
.travis.yml has the Travis CI details.  
requirements.txt has the list of python packages Travis installs.  

Travis tests with py.test the repo every time you push to your GitHub repository.   
Travis pushes the coverage report to Coveralls every time Travis is run, i.e., every time you push to your GitHub repository.   


### run python tests locally  
py.test
py.test -v
py.test --cov maths.py
py.test --cov maths.py -v
py.test --cov-report term-missing --cov=maths.py
py.test --cov-report term-missing --cov=maths.py -v
py.test --cov-report term-missing  
py.test --cov-report term-missing --ignore maths2.py  
you can use a setup.cfg file at the root of the project with configuration options (ignore maths2.py, cov-report term-missing, ....) to then invoke your tests with a simple call to py.test.  
more details:   
https://ilovesymposia.com/2014/10/13/continuous-integration-in-python-3-set-up-your-test-configuration-files/  
http://pytest.org/latest/customize.html  
http://coverage.readthedocs.io/en/latest/config.html  









