# Quiz 2.

Q1. What do you call the commonly used AI technology for learning input (A) to output (B) mappings?
- [ ] Generative AI
- [ ] Reinforcement learning
- [x] Supervised learning
- [ ] Unsupervised learning

Q2. Which of the following are examples of tasks that could be performed by supervised learning models?
- [x] Determining whether a medical image indicates disease or not
  - If you had a set of medical images, for example X-rays, along with labels from experts indicating the diagnosis, then a supervised learning system could learn to make these diagnoses, like the diabetic retinopathy example that Laurence discussed.
- [x] Deciding if a product review is positive or negative
  - If you could label many product reviews as having either positive or negative sentiment, then these labels along with the input reviews could be used to train a supervised learning system to predict the sentiment of a review.
- [x] Deciding if a user will click on an online advertisement
  - Given a dataset of user characteristics, and labels indicating whether that user clicked an online ad or not, then you could train a supervised learning system to predict whether a given user will click a given image.
- [ ] Writing a reply to an email
  - The response to an email is complex and can’t be summarized with a simple label. So supervised learning would not help here.

Q3. In the example about retinal image classification, Laurence mentioned that a supervised learning model learned to predict additional relationships between data points beyond the disease state, like the sex of the patient. What does this suggest about supervised learning?
- [ ] The model is overfitting the training data by finding unnecessary patterns.
- [ ] The model can only predict the original target labels of the data it was trained on.
- [ ] The model has become sentient and can think for itself.
- [x] The model can identify broader patterns and relationships in the training data.
  - The ability of the model to uncover additional relationships, such as the sex, demonstrates that supervised learning models can generalize beyond the target labels and learn meaningful, broader patterns from the training data itself


Q4. Which of these is the most accurate description of an LLM?

- [ ] It generates text by using supervised learning to carry out web search
- [ ] It generates text by repeatedly predicting the next word or token.
- [ ] It generates text by finding a writing partner to work with you
- [x] It generates text by repeatedly predicting words in random order
  - A Large Language Model (LLM) has been trained to repeatedly predict the next word using 100 billions - trillions of examples of text from the internet.
     
Q5. How does the attention mechanism of a transformer work? 
- [ ] It maps input to output tokens using unsupervised learning
- [ ] It searches existing sources of text to determine the most probable next word
- [x] It adjusts the vector embeddings of tokens to account for the surrounding words
  - The attention mechanism adjusts the vector embeddings of tokens by considering their surrounding context, allowing the model to capture relationships between words.
- [x] It allows the model to focus on specific words when predicting the next word
  - The attention mechanism in transformers helps the model focus on specific words or tokens when predicting the next word, giving more weight to relevant parts of the input.
