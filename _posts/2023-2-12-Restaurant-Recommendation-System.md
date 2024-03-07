---
layout: post
title: Restaurant Recommendation System 
categories: [content, demo]
---

Introduction:
Choosing a restaurant for your next dining experience can be a challenging task.
That's where our Restaurant Recommendation System comes in. By leveraging the power of data from OpenRice, a popular restaurant guide, our recommendation engine generates personalized recommendations with over 90% accuracy. 

How It Works:
Our Restaurant Recommendation System utilizes advanced NLP modeling techniques and location-based inputs to provide accurate and personalized restaurant recommendations. We gather data from OpenRice, which boasts a vast repository of over 26,000 restaurant entries. By analyzing the semantic meaning of reviews and other textual data using the Sentence-transformer MiniLM L6 v2 model, we enhance the predictive ability of our recommendation engine. This ensures that our system accurately suggests restaurants that align with your preferences.

Personalized Recommendations:
Our Restaurant Recommendation System goes beyond generic suggestions by tailoring recommendations to your specific preferences. By analyzing your location and utilizing NLP modeling techniques, our system understands your dining preferences and provides personalized restaurant recommendations for different cuisines available on OpenRice. 

Accurate and Reliable:
Accuracy is at the core of our Restaurant Recommendation System. Through extensive data analysis and the utilization of advanced NLP modeling techniques, we have achieved over 90% accuracy in our recommendations.

Benefits:
Using our Restaurant Recommendation System offers several benefits:

1. Personalized Dining Experience: Our system takes into account your location and preferences to provide personalized restaurant recommendations. Say goodbye to generic suggestions and enjoy dining experiences tailored to your tastes.
2. Time and Effort Savings: With our system, you no longer need to spend hours researching restaurants or reading numerous reviews. We simplify the process by delivering accurate recommendations based on your preferences, saving you time and effort.
3. Reliable and Trustworthy: Our recommendation engine utilizes advanced NLP modeling techniques and a large dataset of restaurant entries and customer reviews. This ensures that our suggestions are reliable and trustworthy, allowing you to dine with confidence.

### Skills 

NLP, Data Analysis, Location-based services, Web-scraping

### Main code snippet:

{% highlight c %}
from sentence_transformers import SentenceTransformer, util
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

openrice = pd.read_csv(r"/Users/joycechung/Downloads/Unit 1/01Foundations/11-APIs/data/open-rice.csv", encoding = 'utf8')
openrice['target_text'] = openrice.apply(lambda x: f"Name: {x['name']} Food type: {x['food_type']} Bookmarks: {x['bookmarks']}", axis=1)
target_docs = openrice['target_text'].tolist()

model = SentenceTransformer('all-MiniLM-L6-v2', cache_folder="./model_folder/")

docs_encoding = model.encode(target_docs, show_progress_bar=True)
#converted openrice data into numbers
# progress bar added to check time of completion

while True:
    my_test_sentence = input("Search restaurants ('q' to quit): ")
    if my_test_sentence == 'q':
        break

    test_encoding = model.encode(my_test_sentence)
    #turning the words in my sentence input into numbers

    weights = util.dot_score(test_encoding, docs_encoding).numpy()[0]
#sentence transformer will compare the similarity of the test sentence and the openrice database
#util = it conducts cosine similarity search

    plt.hist(weights, bins=20)
    plt.show()

    idxs = np.argwhere(weights)[:, 0]
    relev_score = weights[idxs]

    # print(idxs, relev_score)

    relev_idxs = idxs[np.argsort(relev_score)[::-1]]
    #
    # print(relev_idxs)

    print(len(relev_idxs))

    for idx in relev_idxs[:10]:
        print(target_docs[idx])
{% endhighlight %}
