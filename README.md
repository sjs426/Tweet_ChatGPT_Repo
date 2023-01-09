# Twitter Bot Detection Model
On April 14th of 2022, Elon Musk announced to the world via his social media that he was initiating the process to acquire the social media giant, Twitter. One of the main concerns raised by Musk, the now CEO of Twitter, was the percentage and number of bots present in Twitter’s platform. Since then, the internet began debating the actual percentage of Twitter's mDAU, monetizable daily active users, who are bots. The percentage is estimated to be betwee 5% and 20%. A research study conducted by SimilarWeb determined that 20.8% and 29.2% of the content posted on Twitter was generated by bots, meaning that bots post x1.57 more content than a regular user.

Bots are defined as automated Twitter accounts that are programmed to behave like real Twitter users to achieve specific goals at a larger scale. Social media experts divide bots into two major categories: (a) “good” bots that provide useful content to users such as daily weather forecasts and stock prices, and (b) “bad” bots that spread misinformation, scams, span and devalue Twitter’s platform. 

##### The goal of this project is to detect a Twitter bot regardless of their activity on the platform. 

### Folder Structure
| Name                | Description                                                                                |
|---------------------|--------------------------------------------------------------------------------------------|
| Final_Project.ipynb | Fine-tuned Google BERT model code to detect Twitter bot Tweets from original, real Tweets. |
| Tweet_Repo.csv      | Main dataset used as training data for our Bot Detection model.                            |

***Note:*** *Our fine-tuned model is available on the huggingface hub as : Generic-usernam3/Tweet_Chatgpt*

## Dataset
The main dataset in the Twitter Bot Detection Repository is the *Tweet_Repo.csv*, which contains approximately 7,000 data samples. The dataset is composed of real, original tweets written by verified Twitter users and bot-like Tweets generated by OpenAI's ChatGPT. It additionally indicates which label do each Tweet belongs to. The designed purpose of this dataset is to be used as training data for a model to detect original Tweets from bot-generated Tweets. These data samples were collected by our team through two data sources:
- Twitter - We used Twitter API to scrap off data from verified user and their tweets.
- ChatGPT - We asked ChatGPT to generate us a couple thousand tweets.

| Column | Description                                                                                                                                                                 |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Text]      | Contains the text of the Tweets generated by both bots and real Twitter users. The text is not yet clean.                                                                   |
| [Type]      | Labels the source of the [Text] column as "Not a bot" if it was written by a real, verified Twitter user or "bot" if it was generated by ChatGPT assimilated a Twitter bot. |
## Literature Review
According to researchers in the field (Feng, Tan, Wan, et al. 2022), feature based models, text based models and graph based models as well as hybrid models are the primary ways used today for bot detection. In order to make the best possible choice for our project we will explore all these options as possibilities. For the first type, feature based models, features are extracted from: metadata, tweets, descriptions, temporal patterns and follow relationships. With this information, more traditional prediction methods are often used to reach the conclusion of whether or not a twitter user is a bot or not. These methods include Logistic regression models and Support vector machines. The second method, the text based model, uses Natural language processing for the detection of bots by using text from tweets and user descriptions. Some models additionally use user features along with text.  This kind of model performs rather well, but sometimes can be fooled by bots that occasionally steal real tweets and use them as their own. Finally, graph based models interpret users as "nodes" and the relationships between them are called "edges". These models  learn to predict from the many relationships between nodes what each node is. In our case, bot or not. Recent research has shown that graph-based approaches achieve state-of-the-art performance, are capable of detecting novel Twitter bots, and are better at addressing various challenges facing Twitter bot detection" but unfortunately are quite difficult to build. (Feng, Tan, Wan, et al. 2022). 

## Methodology
The approach chose for the Twitter Bot Detection project was using a pre-trained Bert model for sequence classification. This is mainly due to the fact that Bert models are readily available and not especially complicated to use. In the fine-tuning process, we used a basic bert-base-cased model. We trained the model on 1 epoch and received a training loss of more or less  0.26. Upon evaluation of the model on the testing data set we received an **evaluation loss of 0.22** and **accuracy score of 0.95**.


