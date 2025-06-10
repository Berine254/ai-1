# CryptoBuddy: Your First AI-Powered Financial Sidekick!

crypto_db = {
    "Bitcoin": {
        "price_trend": "rising",
        "market_cap": "high",
        "energy_use": "high",
        "sustainability_score": 3/10
    },
    "Ethereum": {
        "price_trend": "stable",
        "market_cap": "high",
        "energy_use": "medium",
        "sustainability_score": 6/10
    },
    "Cardano": {
        "price_trend": "rising",
        "market_cap": "medium",
        "energy_use": "low",
        "sustainability_score": 8/10
    }
}

def get_most_sustainable():
    recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
    score = int(crypto_db[recommend]['sustainability_score'] * 10)
    return f"{recommend} ({'ADA' if recommend=='Cardano' else recommend}) is super green and scores {score}/10 for sustainability! 🌱"

def get_trending():
    trending = [name for name, data in crypto_db.items() if data["price_trend"] == "rising"]
    if trending:
        return f"{' and '.join(trending)} {'are' if len(trending)>1 else 'is'} both rising! 🚀"
    else:
        return "No cryptocurrencies are trending up right now!"

def get_long_term():
    # Profitability: rising trend & high/medium market cap, and sustainable!
    best = None
    for name, data in crypto_db.items():
        if data["price_trend"] == "rising" and (data["market_cap"] in ["high", "medium"]) and data["sustainability_score"] >= 0.7:
            best = name
    if best:
        return f"{best} (ADA) is trending up and has a top-tier sustainability score! 🚀"
    else:
        return "Consider coins with rising trends and strong sustainability for long-term growth!"

def process_query(query):
    query = query.lower()
    if "sustain" in query or "eco" in query or "green" in query:
        return get_most_sustainable()
    elif "trend" in query or "trending" in query or "up" in query:
        return get_trending()
    elif "long-term" in query or "growth" in query or "should i buy" in query or "invest" in query:
        return get_long_term()
    else:
        return ("I’m CryptoBuddy! Ask me about trending or sustainable cryptos.\n"
                "Example: 'Which crypto is trending up?' or 'What's the most sustainable coin?'")

def main():
    print("👋 Hey, I’m CryptoBuddy! Let’s find you a green and growing crypto! (type 'exit' to quit)")
    while True:
        user_query = input("You: ")
        if user_query.lower() == "exit":
            print("CryptoBuddy: Remember, crypto is risky—always do your own research! 👋")
            break
        advice = process_query(user_query)
        print(f"CryptoBuddy: {advice}")

if __name__ == "__main__":
    main()# ai-1
