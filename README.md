# Extract Historical Twitter Data
___

`getTwitterData.ipynb`

- Extracts Twitter meta-data for a given timeline and a search query (one or multiple words) in most of the known languages.
- Makes an API POST call to SNScrape with a formatted body.
- No need for an API key.
```
API Payload:
start date, end date, search query

Output Attributes:
- date: Tweet timestamp
- tweet: Tweet content
- lang: Language classifer used by parent API
- retweetCount: Tweet retweeted count
- likeCount: Tweet like count
- replyCount: Number of replies to the original tweet
- username: Author profile
- user_followersCount: Number of followers the Author has (tells you about the popularity index for tweets)
- user_friendsCount: Number of friends the Author has
- verifiedStatus: If the Author has been Verified or not (i.e. pays 8 bucks every month!)
- tweet_url: URL of the original tweet
- hastags: If any hastags were used (hastags are important for search and information retrieval, works like an anchor-text founded by Wikipedia)
- chr_count: Count of English characters in the original tweet
- topic: Keywords you used for searching tweets (aka. labels)
```

`NLP_basics_preprocessing_vectorization_similarity.ipynb`
- Basic and Advanced pre-processing units for general text cleaning in English language. Works well with short-text as well as a big corpus (inspired by practical experience and fine-tuned considering the pipeline used in Open.Ai's GPT-3 series).
- Contains general vectorizer pipeline streamlined for most of the vectorizers like _Word2Vec, WMD, Glove, Google, BERT, FastText, Google USE_.
- You would need to store and load your own embedding models in-order to run this.
- Contains an intricate comparison of various syntactic and semantic similarity estimation industrial techniques.

Advised/Supervised by:
- Dr. Hyuckchul Jung (Principal Data Science Lead, Meta, Alma: University of Southern California, Ph.D, CS Machine Learning)
- Dr. Jason Li (Data Science Lead, Morgan Stanley)

### Setup
```
pip install git+https://github.com/JustAnotherArchivist/snscrape.git 
```

### Directory Structure

```yaml
└── data
    ├── Resources
        ├── chatwords.txt
        ├── ...
└── models
    ├── ...
    └── en_core_web_lg
        ├── __init__.py
        ├── meta.json
        └── en_core_web_lg-2.2.5
            ├── config.cfg
            ├── meta.json
            └── ...
└── Requirements.txt
└── Conda_env_python38forTextAnalytics.yml
└── getTwitterData.ipynb
└── NLP_basics_preprocessing_vectorization_similarity.ipynb
```

### Model Path Setting

```bash
# PATH:
root_dir = os.path.abspath("./")
data_dir = os.path.join(root_dir, "data")
output_dir = os.path.join(root_dir, "outputs")
PATH_SPACY_MODEL = os.path.join(os.path.join(os.path.join(root_dir, "models"), "en_core_web_lg”), “en_core_web_lg-2.2.5”)
PATH_RES_DIR = os.path.join(data_dir, "resources")
PATH_BERT_MODEL = os.path.join(os.path.join(root_dir, "models"), "finbert_v1")
```

### Model Loading

```bash
# 1. Load Spacy Model:
import spacy
spacy_model_data_path = PATH_SPACY_MODEL
nlp = spacy.load(spacy_model_data_path, disable=['ner'])
from spacy import displacy
from spacy.matcher import Matcher
from spacy.lang.en import English
print("Spacy loaded.")
```

```bash
# 2. Load NLP Resources:
resources_dir_path = PATH_RES_DIR
```

```bash
# 3. Load sent.BERT model:
bert_model_fp = PATH_BERT_MODEL
```

**Credits:**
- Authors of SNScrape 
- Awesome social media mining tool SNScrape (https://github.com/JustAnotherArchivist/snscrape)
