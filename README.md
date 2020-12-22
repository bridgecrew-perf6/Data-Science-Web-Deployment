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

1. Create a new environment
  ```
  conda update python
  python3 -m venv worldbankvenv
  source worldbankenv/bin/activate
  ```

2. Pip install libraries that are needed for the web app
  ```
  pip install flask pandas plotly gunicorn
  ```

3. Install the heroku command line tools
  ```
  curl https://cli-assets.heroku.com/install-ubuntu.sh | sh
  https://devcenter.heroku.com/articles/heroku-cli#standalone-installation
  heroku —-version
  ```

4. Log into Heroku
  ```
  heroku login
  ```

5. Heroku asks for (from the terminal)
  - account email address
  - password

6. The next steps involved some housekeeping:
  - remove ```app.run()``` from worldbank.py
  - type cd web_app into the Terminal so that you are inside the folder with your web app code.




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
