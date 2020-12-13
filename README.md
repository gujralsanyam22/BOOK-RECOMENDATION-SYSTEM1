# BOOK-RECOMENDATION-SYSTEM1

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspect](#technical-aspect)
  * [Installation](#installation)
  * [Run](#run)
  * [Deployement on Heroku](#deployement-on-heroku)
  * [Directory Tree](#directory-tree)
  * [To Do](#to-do)
  * [Bug / Feature Request](#bug---feature-request)
  * [Technologies Used](#technologies-used)
  * [Team](#team)
  * [Credits](#credits)

## Overview
This repository contains all the files related to the final project for the Master in Data Science, VI Edition, held by Kschool Madrid. The objective of this project is the implementation of a book recommender system, using the data made available by Goodreads, a website where users can register and rate the books they have read, sharing their ratings and opinions with other readers. The approach chosen is to generate a system that recommends books using the information inherent in users' ratings. So, rather than predicting the ratings that each user would give to all the books included in this analysis that he hasn’t read yet (and hence trying to reduce the error in those predictions), I have chosen instead to generate a system that give relevant recommendations to each user based on a certain measure of similarity between the books he has already read and rated and the books he hasn't read but other users do.  In order to successfully run the code, please download all the .csv files included in this repository and place them in your own working directory and hence change the path at the beginning of each script (os.chdir("/Users/678094/Desktop/Goodreads")) so it will be pointing at your own working directory where the files have just been saved. I have replicated this part at the beginning of each notebook because in order to build the recommender system it is not compulsory to run all three notebooks: notebooks 01. and 02. are facultative, they serve to scrape from the Goodreads website additional data used in the analysis. But the same data is saved as .csv file and loaded again in notebook .03. So the logical sequence of the code consists in running notebook 01, 02 and 03 respectively, but in case you want to skip the scraping part and go directly to the recommender system, you can run notebook 03. independently, changing the working directory accordingly as indicated above.

## Motivation
What could be a perfect way to utilize unfortunate lockdown period? Like most of you, I spend my time in cooking, Netflix, coding and reading some latest research papers on weekends. The idea of classifying indian currency struck to me when I was browsing through some research papers. I couldn't find any relevant research paper (and of course dataset!) associated with it. And that led me to collect the images of Indian currency to train a deep learning model using [this](https://github.com/hardikvasa/google-images-download) amazing tool.

## Technical Aspect
This project is divided into two part:
1. Training a machine learning model learning using seaborn,matplotlib. (_Not covered in this repo. I'll update the link here once I make it public._)
    - A user can choose image from a device or capture it using a pre-built camera.
    - Used __Amazon S3 Bucket__ to store the uploaded image and predictions.
    - Used __CSRF Token__ to protect against CSRF attacks.
    - Used __Sentry__ to catch the exception on the back-end.
    - After uploading the image, the predictions are displayed on a __Bar Chart__.
    
    ## Installation
The Code is written in Python 3.7. If you don't have Python installed you can find it [here](https://www.python.org/downloads/). If you are using a lower version of Python you can upgrade using the pip package, ensuring you have the latest version of pip. To install the required packages and libraries, run this command in the project directory after [cloning](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/) the repository:
```bash
pip install -r requirements.txt
```
## Run
> STEP 1
#### Linux and macOS User
Open `.bashrc` or `.zshrc` file and add the following credentials:
```bash
export AWS_ACCESS_KEY="your_aws_access_key"
export AWS_SECRET_KEY="your_aws_secret_key"
export ICP_BUCKET='your_aws_bucket_name'
export ICP_BUCKET_REGION='bucket_region'
export ICP_UPLOAD_DIR='bucket_path_to_save_images'
export ICP_PRED_DIR='bucket_path_to_save_predictions'
export ICP_FLASK_SECRET_KEY='anything_random_but_unique'
export SENTRY_INIT='URL_given_by_sentry'
```
Note: __SENTRY_INIT__ is optional, only if you want to catch exceptions in the app, else comment/remove the dependencies and code associated with sentry in `app/main.py`

#### Windows User
Since, I don't have a system with Windows OS, here I collected some helpful resource on adding User Environment Variables in Windows.

__Attention__: Please perform the steps given in these tutorials at your own risk. Please don't mess up with the System Variables. It can potentially damage your PC. __You should know what you're doing__. 
- https://www.tenforums.com/tutorials/121855-edit-user-system-environment-variables-windows.html
- https://www.onmsft.com/how-to/how-to-set-an-environment-variable-in-windows-10

> STEP 2

To run the app in a local machine, shoot this command in the project directory:
```bash
gunicorn wsgi:app
```
## Directory Tree 
```
├── app 
│   ├── __init__.py
│   ├── main.py
│   ├── model
│   ├── static
│   └── templates
├── config
│   ├── __init__.py
├── processing
│   ├── __init__.py
├── requirements.txt
├── runtime.txt
├── LICENSE
├── Procfile
├── README.md
└── wsgi.py
```

## To Do
1. Convert the app to run without any internet connection, i.e. __PWA__.
2. Add a better vizualization chart to display the predictions.

## Bug / Feature Request
If you find a bug (the website couldn't handle the query and / or gave undesired results), kindly open an issue [here](https://github.com/gujralsanyam/Book-Recommendation-Sytem/issues/new) by including your search query and the expected result.

If you'd like to request a new function, feel free to do so by opening an issue [here](https://github.com/gujralsanyam/Book-Recommendation-System/issues/new). Please include sample queries and their corresponding results.
