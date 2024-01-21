# Predictive modeling for credit card offer acceptance

In this project we build a machine learning solution for analyzing customer behavior for credit card offer acceptance.

# The Problem

This initiative is undertaken to delve into the trends in customer acceptance of credit card offers from financial institutions.
Our aim is to enhance our comprehension of the factors influencing offer acceptances and to develop predictive insights into whether a customer is more inclined to accept or decline the offer.

# The Data

More information on the problem and the data used for this project can be found [here](https://www.kaggle.com/datasets/thedevastator/unlocking-credit-card-offer-acceptance-trends-in)

# The model
We used two models
* Logistic Regression
* Decision Tree
The best model was Logistic Regression

## How to Run The Project
Please note that these steps are to be carried out in a terminal window like command prompt or git bash<br>
  - Clone the repository to your computer using:  <br>
  ```bash
  git clone [https://github.com/Fozan-Talat/credit_card_ml.git]
  ```
  <br>
  
  - Navigate to the directory where you cloned the repo and cd into the cloned repo by running: <br>
  ```bash
  cd credit_card_ml
  ```
  <br>
  You should now be in the project folder
  
  - The libraries used in this project can be found in the [requirements.txt](https://github.com/Fozan-Talat/credit_card_ml/blob/main/requirements.txt) file. It is advisable to run this project in a virtual environment to avoid issues with your system configuration. To create a virtual environment with venv <br>
  ```bash
  python -m venv credit-env
  ```
  
   Activate credit-env with: <br>
   ```bash
   credit-env\Scripts\activate.bat
   ```
   <br>
   
   Now install the libraries from the requirements.txt file by running:<br>
   
   ```bash
   pip install -r requirements.txt
   ```
   
   As we saw earlier, the model was already trained and saved in the train.py file. However, you may want to retrain the model for some reason. You do this by executing the file. In terminal, run:<br>
   ```bash 
   python train.py
   ```
   
  Now deploy the flask app locally by running the predict.py file. It is recommended to do this with a production server like waitress(windows OS) or gunicorn(UNIX).<br>
  You can still run it directly, with:   <br>
  ```bash
  python predict.py
  ```
  
  with waitress: <br>
 
  ```bash
  waitress-serve --listen=0.0.0.0:9090 predict:app
  ```
  
   with gunicorn: <br>
 
  ```bash
  gunicorn --bind 0.0.0.0:9090 predict:app
  ```
  
  Now the prediction service should be running locally on "http://0.0.0.0:9090"
  
  Finally, you send a POST request to the service. You can do this by running the request.py file or use the file to understand the format in which the request will be sent, and then create your own request. This is how you run it:<br>
  ```bash
  python request.py
  ```
  
  You can also decide to build and run the Dockerfile for the project. To build this locally:
  ```bash
  docker build -t credit_card_project .
  ```
  
  Then to run it:<br>
  ```bash
  docker run -it --rm -p 9090:9090 credit_card_project:latest
