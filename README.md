🎵 LLM-Powered Music Recommendation System
Discover songs tailored to your mood using hybrid embeddings (text + audio features)!

📌 Overview: 

This project uses categorized audio features (e.g., "high-energy", "low-acousticness") embedded into a structured text template, combined with sentence-transformers/all-mpnet-base-v2 embeddings, to build a music recommender.

🛠️ Key Features

Natural Language Feature Encoding: Numerical features (BPM, Energy, etc.) are converted to descriptive categories (e.g., "fast tempo") and injected into a text template.

Textualized Audio Features:

FAISS Indexing: Efficient similarity search for real-time recommendations.






Semantic Search: LLM embeddings understand nuanced queries (e.g., "upbeat workout songs with low acousticness").


📂 Dataset: Top50MusicFrom2010-2019 from Spotify.

Dataset & Feature Categories
Source: Top50 Spotify Tracks (2010-2019)
data = {
    "title": "Blinding Lights",
    "artist": "The Weeknd",
    "tempo_cat": "fast", 
    "energy_cat": "high",
    # ... other features
}

template = """
A {popularity_cat} and {loudness_cat} {speechiness_cat} music titled: {title}, 
by: {artist} released in: {year}, {genre} Genre with {tempo_cat} tempo, 
{energy_cat} energy and {danceability_cat} danceability.
"""

Feature Injected Template Example : 

"A very popular and loud speech-heavy music titled: 'Blinding Lights', by: The Weeknd released in: 2020, Pop Genre with fast tempo, high energy, and very danceable. It has studio-like liveness and happy mood. Average length and low acousticness."

🔢 Numerical Features → Text Categories
Feature	Example Categories Thresholds :

BPM :	"slow", "moderate", "fast"	Fast: >140 BPM

Energy : "low", "medium", "high"	High: >0.7

Valence :	"sad", "neutral", "happy"	Happy: >0.6

Acousticness : "low", "mixed", "high"	High: >0.7

(Full thresholds in jupyter file)



🧠 How It Works
Feature Categorization:

Numerical features (e.g., Energy=0.8) → descriptive labels ("high energy").

Text Template Injection:

Labels are inserted into a structured template to create a natural language description.

LLM Embedding:

all-mpnet-base-v2 converts descriptions into embeddings.

FAISS Search:

Queries are embedded and matched against the index.


📊 Why This Approach?
LLM-Friendly: Text descriptions allow the model to understand audio features semantically.

Interpretable: Categories (e.g., "high energy") are more intuitive than raw numbers for users.

Flexible: Modify thresholds or templates without retraining.
