---
layout: post
title: Job Recommendation Chatbot 
categories: [content, demo]
---
### What does it do? 
## Purpose
## Advantages
### Skills 
---
layout: post
title: Simplify Your Data Science Job Search with Reverse CV Matching
[![Github][2.2]][2]

[2.2]:(https://github.com/joycechungyt/Job-Recommendation-Chatbot)

Introduction:
Searching for data science jobs online can be a time-consuming process. With countless job postings to sift through, it's easy to feel overwhelmed. That's where our innovative chatbot comes in. By leveraging the power of reverse CV matching and utilizing cutting-edge technologies such as Selenium, Scrapingdog, Python, and sentence transformers, our chatbot saves you up to 80% of the time typically spent searching for data science jobs. Say goodbye to manual job hunting and let our chatbot do the work for you.

How It Works:
Our chatbot employs web scraping techniques to gather job data from various online job portals and stores it in CSV files. We utilize Selenium, Scrapingdog, and Python to automate the process and ensure accurate and up-to-date job listings. Once the data is collected, we take it a step further by employing sentence transformers to tokenize the job context and generate embeddings. This enhances the chatbot's understanding of the job requirements and allows for more accurate matching.

Reverse CV Matching:
Traditional job search platforms require you to manually search for jobs based on keywords and filters. Our chatbot takes a different approach with reverse CV matching. Instead of you searching for jobs, the chatbot analyzes your skills and preferences and matches them with the job requirements listed in the collected data. By using reverse CV matching, we ensure that you receive personalized job recommendations tailored to your unique skill set.

Accurate Job Recommendations:
With the power of reverse CV matching and cutting-edge technologies, our chatbot excels at providing accurate job recommendations for data scientist roles. Simply input your query, and the chatbot will analyze your skills and preferences to present you with a curated list of job opportunities that align with your expertise. No more wasting time sifting through irrelevant listings.

Benefits:
Using our chatbot for your data science job search offers several benefits:

1. Time Savings: Our chatbot saves you up to 80% of the time typically spent searching for jobs online. With automated web scraping and reverse CV matching, you can focus on preparing for interviews and enhancing your skills.
2. Personalized Recommendations: Our chatbot understands your skills and preferences and delivers job recommendations tailored to you. You'll receive opportunities that align with your expertise, increasing your chances of finding the perfect job.
3. Accurate Matching: By utilizing sentence transformers and embeddings, our chatbot ensures accurate matching between your skills and the job requirements. This means you'll receive relevant job recommendations that closely match your capabilities.

Conclusion:
Streamline your data science job search with our innovative chatbot. By harnessing the power of reverse CV matching, web scraping, and cutting-edge technologies, we save you time and deliver accurate job recommendations tailored to your skills. Say goodbye to manual job hunting and let our chatbot simplify your job search journey. Stay tuned for updates and enhancements as we continue to improve and refine our chatbot for an even better user experience.

### Here's a snippet of the main code after importing all relevant libraries, gathering the web-scraped context, and setting up the chatbot interface in Gradio. 

{% highlight c %}
# Main code
print("Welcome to the Job Recommendation Chatbot!")

while True:
    user_input = input("Enter your query or type 'recommend' to get a job recommendation: ")

    if user_input.lower() == "recommend":
        inputs = gr.Textbox(label="Enter your job preferences")
        outputs = gr.Textbox(label="Job Recommendation")
        gr.Interface(fn=chatbot_interface, inputs=inputs, outputs=outputs, title="Job Recommendation Chatbot", theme='freddyaboulton/dracula_revamped').launch()

# user_query = input("Enter your job preferences: ")
#         job = recommend_job(user_query)
#         context = "\n".join(job)

#         input_text = f"Answer the question to the best of your ability strictly from the context.\n\nContext:{context}\n\nQuestion:{user_query}
#         outputs = model.generate(**input_ids, max_new_tokens=200)
#         print(tokenizer.decode(outputs[0]))
    else:
        query = user_input
{% endhighlight %}
