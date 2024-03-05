import tweepy
import time

# Substitua pelos seus próprios valores das chaves de acesso da API do Twitter
api_key = 'SUA_API_KEY'
api_secret_key = 'SUA_API_SECRET_KEY'
access_token = 'SEU_ACCESS_TOKEN'
access_token_secret = 'SEU_ACCESS_TOKEN_SECRET'

# Autenticação com a API do Twitter
auth = tweepy.OAuthHandler(api_key, api_secret_key)
auth.set_access_token(access_token, access_token_secret)
api = tweepy.API(auth, wait_on_rate_limit=True)

# Palavras-chave para buscar e dar RT
keywords = ["Python", "Programming", "Coding"]

# Função para buscar e dar RT
def retweet_tweets_with_keywords():
    for keyword in keywords:
        print(f"Buscando por tweets contendo a palavra-chave: {keyword}")
        for tweet in tweepy.Cursor(api.search_tweets, q=keyword, lang="en", tweet_mode='extended').items(10):
            try:
                # Verifica se o tweet já foi retweetado pela conta para evitar duplicatas
                if not tweet.retweeted:
                    api.retweet(tweet.id)
                    print(f"Retweetado: {tweet.full_text}")
                    time.sleep(10)  # Pausa entre retweets para evitar spam
            except tweepy.TweepError as e:
                print(e.reason)
            except StopIteration:
                break

# Roda a função em um loop
while True:
    retweet_tweets_with_keywords()
    time.sleep(900)  # Espera por 15 minutos antes de buscar e retweetar novamente
