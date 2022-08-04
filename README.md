# Flaming Fuelers Joke Generator!

A quick overview of our NLP Project!

If you have any questions, we probably won't answer them.

This guide covers how our code works and the resources used.

### Setup

Follow the steps below:

`python3 -m pip install -r requirements.txt`

You'll want to edit line 124 of the `main.py` file to either the URL of the cocalc server you are on or `localhost` if you are running it on your own PC.

From there, run `python3 -m main` to start the server on local, most changes while developing will be picked up in realtime by the server. 

Then, on the website, choose between the Dad Joke Generator and the Bar Joke Generator. Once you've made your choice, you must add a prompt so the model can generate a joke.

### AI Development and Testing

The project began with us using a Python tool called <strong>aitextgen</strong>, which is a package that utilizes a Generative Pre Trained Transformer Model to be able to take in data, judge how the data correlates and respond with a text output trained on the data. In our case, we fed it hundreds of thousands of jokes, and eventually it was able to come up with jokes of it's own. Some example code of our AI dev includes:

    !pip3 install aitextgen

    from aitextgen import aitextgen
    from aitextgen.TokenDataset import TokenDataset

    import pandas as pd
    bar_jokes = pd.read_csv(PATH + "/Data sets/bar_jokes.csv")

PATH in this code refers to a Google Drive folder where the data was stored.

```
training_samples_bar = bar_jokes.joke.values.tolist()

training_samples_bar[:5]

train_file_bar = TokenDataset(texts=training_samples_bar, save_cache=True)
```

This section defines the data we want to train.
```
import gc, torch

gc.collect()

torch.cuda.empty_cache()

"""ai.train(train_file_bar,
         line_by_line=False,
         num_steps=2500,
         generate_every=100,
         save_every=100,
         save_gdrive=True,
         batch_size=3,
         output_dir = PATH +'/bar_joke_model')"""
```
Finally, we take the data and train it. In this code, we did it 2500 times.

### Website Development and Deployment
After that, we now had a usable model that could generate jokes. However, we had to make it accessible to the public. Since we had very little time, we went onto <strong>Bootstrap</strong>, a CSS framework that had premade website templates. We modeled the template to our style, and created an interactive interface that would allow the user to generate jokes. You can find it here: https://cocalc12.ai-camp.dev/aebc210b-e912-4df7-91ea-37e0f8451ece/port/43560.

The webpage was made using HTML, CSS, JavaScript and Flask. We used HTML for the forefront of the website, CSS for fonts, styling and additional intricacies.

### Flask(Python) Configuration and Setup
The website needed to have the model attached to it, so we used JavaScript and Flask to get the job done. Flask is a Python web framework that we used to source the code and attach it to the website, and JavaScript filled in a few gaps not viable in Python.

### Tech Stack
Here is a little overview of the resources we used to create this project: 

 - Kaggle: A site where we found the data necessary to train our model.
 - Pandas: Python library (used for data pre-processing).
 - aitextgen: Python package for text-based AI training.
 - GPT-NEO: A Generative Pre-Trained Transformer language model [See AI Dev and Testing].
 - HTML/CSS: Mark-up and stylesheet languages for frontend development.
 - Flask/JS: Web microframework for backend development.

### Datasets

To get the jokes that we needed to train the model on, we sourced our datasets from Kaggle. We used the Walks Into a Bar dataset: (https://www.kaggle.com/datasets/shiladityabasu/walks-into-a-bar-dataset) and the Reddit Dad Jokes dataset: (https://www.kaggle.com/datasets/oktayozturk010/reddit-dad-jokes).

### Libraries
Read the requirements.txt document for required libraries.

### About the Team

Product Manager: Ibrahim Shah

Data Scientists: Aiden Fregoso, Angel Canche

Machine Learning Engineer: Izzy Bunkers

Frontend Engineer: Amanda Chung

Backend Engineer: Abby Hirobe

Instructor: Chase Adams

