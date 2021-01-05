# Data Science Web App Deployment

Deployment is needed that anyone can see the web app work. For this reason an external server with a web address is needed.

- [Heroku](https://www.heroku.com/)
  - Platfrom as a Service
  - One of the easiest Platforms
  - Does not need much configuration


- [Amazon's Lightsail](https://aws.amazon.com/lightsail/)
- [Microsoft's Azure](https://azure.microsoft.com/en-us/resources/samples/python-docs-hello-world/)
- [Google Cloud](https://cloud.google.com/appengine/docs/standard/python/getting-started/python-standard-env)
- [IBM Cloud](https://www.ibm.com/blogs/bluemix/2015/03/simple-hello-world-python-app-using-flask/)

#### Working with Heroku

1. Create a new folder and put all files needed for the web app into this folder, e.g.
  ```
  mkdir web_app
  mv -t web_app data worldbankapp wrangling_scripts worldbank.py
  ```

2. Create a new environment
  ```
  conda update python 
  python3 -m venv worldbankvenv 
  source worldbankenv/bin/activate 
  ```
  Now besides the folder ```web_app``` there is a folder ```worldbankvenv``` with a Python installation inside (folders like bin, include, lib, lib64, etc.).

3. Pip install libraries that are needed for the web app
  ```
  pip install flask pandas plotly gunicorn
  ```
  Those libraries are installed in the virtuasl environment instead of the regular Python environment.

4. Install the heroku command line tools

  Ubuntu
  ```
  curl https://cli-assets.heroku.com/install-ubuntu.sh | sh
  ```
  
  Mac OS
  ```
  curl https://cli-assets.heroku.com/install.sh | sh
  ```

  Other OS
  ```
  https://devcenter.heroku.com/articles/heroku-cli#standalone-installation 
  ```
  
  Check the installation
  ```
  heroku —-version 
  ```

5. Log into Heroku
  - Go to Heroku web page
  - Create an account
  ```
  heroku login
  ```

6. Heroku asks for (from the terminal)
  - account email address
  - password
 

7. The next steps involved some housekeeping:
  - remove ```app.run()``` from worldbank.py
  - type ```cd web_app``` into the terminal (be inside the folder with the web app code)


8. Create a proc file
  ```
  touch Procfile
  ```
  A proc file tells Heroku what to do when starting the web app.

9. Then open the Procfile and type:
  ```
  web gunicorn worldbank:app
  ```

  If you stored ```worldbank.py``` in a folder like ```app``` then use
  ```
  web gunicorn cd app && worldbank:app
  ```

  Tells Heroku, when starting the web app call the gunicorn library and runt the wordbank app.

10. Next, create a requirements file, which lists all of the Python library that your app depends on
  ```
  pip freeze > requirements.txt
  ```

11. Initialize a git repository in the ```web_app``` folder and make a commit
  ```
  git init
  git add .
  git commit -m ‘first commit’
  ```
  
  Eventually you have to add an email address and user name:
  ```
  git config user.email "something@example.com"
  git config user.name "Andy"
  ```

12. Now, create a heroku app
  ```
  heroku create my-app-name
  ```
  The ```heroku create``` command should create a git repo on Heroku and a web address for accessing the web app.
  The name must be unique, e.g. 'dsnd-udacity-webapp'

13. Check if the remote repo was added to your git repo with the following terminal command
  ```
  git remote -v
  ```

14. Next, push the git repo to the remote heroku repo with this command
  ```
  git push heroku master
  ```

15. Type the web app's address in the browser to see the results


## Databases fot a web app
This app does not need a database. All data is within one csv file.
However, it is possible to include a database as part of a Flask app. One common use case would be to store user login information such as username and password.
Flask is database agnostic meaning Flask can work with a number of different database types.

Here are some resources how to include a database as part of a Flask app:

- [Flask Mega Tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database)
- [Heroku - Provision a Database](https://devcenter.heroku.com/articles/getting-started-with-python#provision-a-database)


## Setup Instructions

The following is a brief set of instructions on setting up a cloned repository.

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites: Installation of Python via Anaconda and Command Line Interaface
- Install [Anaconda](https://www.anaconda.com/distribution/). Install Python 3.7 - 64 Bit
- If you need a good Command Line Interface (CLI) under Windowsa you could use [git](https://git-scm.com/). Under Mac OS use the pre-installed Terminal.

- Upgrade Anaconda via
```
$ conda upgrade conda
$ conda upgrade --all
```

- Optional: In case of trouble add Anaconda to your system path. Write in your CLI
```
$ export PATH="/path/to/anaconda/bin:$PATH"
```

### Clone the project
- Open your Command Line Interface
- Change Directory to your project older, e.g. `cd my_github_projects`
- Clone the Github Project inside this folder with Git Bash (Terminal) via:
```
$ git clone https://github.com/ddhartma/Data-Science-Web-Development.git
```

- Change Directory
```
$ cd web_app
```

- Create a new Python environment, e.g. ds_dashboard. Inside Git Bash (Terminal) write:
```
$ conda create --name ds_dashboard
```

- Install the following packages (via pip or conda)
```
numpy = 1.17.4
pandas = 0.24.2
plotly = 4.6.0
Flask = 1.1.2
```

- Check the environment installation via
```
$ conda env list
```

- Activate the installed spotify_analysis environment via
```
$ conda activate ds_dashboard
```
