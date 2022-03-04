## Description 

Forecasting Irish house / real estate prices using advanced machine learning.

Forecasting Irish house / real estate prices using Ordinary Least Squares-, XGBoost-, KNN-, Lasso-, Ridge-, Polynomial-, Random Forest-, and Neural Network MLP Regression (via scikit-learn)

---

## Approach:

- load Pandas DataFrame containing (Dec-17) housing data, supplemented with longitude and latitude coordinates mapped to zip code (via [GeoPy](https://geopy.readthedocs.io/en/1.10.0/#)
- do some simple data exploration / visualisation
- remove non-numeric data, NaNs, and outliers (everything above 3 x standard dev of y)
- define explanatory variables (surface,latitude,and longitude) and independent variable (price EUR)
- split the data in train and test sets (+ normalise independent variables where required)
- find the optimal model parameters using [scikit-learn](http://scikit-learn.org/stable/)'s GridSearchCV
- fit the model using GridSearchCV's optimal parameters
- evaluate estimator performance by means of 5 fold 'shuffled' nested cross-validation
- predict cross validated estimates of y for each data point and plot on scatter diagram vs true y

---

# Development

Developed using Python / Django,

---

## Developer Notes

Please always use `pipenv install` instead of `pip3 install` when adding dependencies.

Also ensure to keep the `requirements.txt` up-to-date by runnging the following command wheneve dependencies are added/removed.

`$ pipenv lock -r > requirements.txt`

---

## Environment & Application setup

Step 1: Download & install Python 3 -

The easiest way to setup a Python Environment on Windows is to download Anaconda - https://www.anaconda.com/download/

If on macOS, you can use `brew`

To setup homebrew, open the terminal and run the command

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Then install Python by running the following command

`$ brew install python`

Step 2: Install Pipenv

To setup & use isolated Virtual Environments, install pipenv

`$ pip3 install pipenv`

Step 3: Open the terminal & cd into project directory -

`$ cd /path/to/project`

Step 4: Activate/Create Virtual Environment

`$ pipenv shell`

Step 5: Run the following command to install all the dependencies -

`$ pipenv install`

Alternatively, you can run -

`$ pip3 install -r requirements.txt`

Step 6: Done!

---

## Run Locally:

Step 1: Open the terminal & cd into project directory -

`$ cd /path/to/project`

Step 2: Run the following command to run the application -

`$ python <script>.py`

Done!

---

## Scores (5 fold nested 'shuffled'cross-validation - Rsquared)

**1. XGBoost Regression**

- Parameters: max_depth: 5, min_child_weight: 6, gamma: 0.01, colsample_bytree: 1, subsample: 0.7
- Score: 0.887

**2. Random Forest Regression**

- Parameters: max_depth: 6, max_feat: None, n_estimators: 10
- Score: 0.839

**3. Polynomial Regression**

- Parameters: degrees: 2
- Score: 0.731

**4. Neural Network MLP Regression**

- Parameters: act: relu, alpha: 0.01, hidden_layer_size: (10,10), learning_rate: invscal
- Score: 0.715

**5. KNN Regression**

- Parameters: n_neighbours: 10
- Score: 0.711

**6. Ordinary Least-Squares Regression**

- Parameters: None
- Score: 0.694

**7. Ridge Regression**

- Parameters: alpha: 0.01
- Score: 0.694

**8. Lasso Regression**

- Parameters: alpha 0.01
- Score: 0.693

---

### Sample data input (Pandas DataFrame)

```
   surface  rooms_new  zipcode_new  price_new   latitude  longitude
0    138.0        4.0         1060     420000  40.804672 -73.963420
1    130.0        5.0         1087     550000  52.355590   5.000561
2    116.0        5.0         1061     425000  52.373044   4.837568
3     92.0        5.0         1035     349511  52.416895   4.906767
4    127.0        4.0         1013    1050000  52.396789   4.876607
```

---

#### Scatter plot - Surface vs. Asking Price (EUR)

#### XGBoost - Predicted prices vs. True price (EUR)

#### Random Forest - Predicted prices vs. True price (EUR)

#### Polynomial - Predicted prices vs. True price (EUR)

#### Neural Network MLP - Predicted prices vs. True price (EUR)

#### KNN - Predicted prices vs. True price (EUR)

#### OLS - Predicted prices vs. True price (EUR)

#### Lasso - Predicted prices vs. True price (EUR)

#### Ridge - Predicted prices vs. True price (EUR)
