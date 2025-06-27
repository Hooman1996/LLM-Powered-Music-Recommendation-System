🎵 LLM-Powered Music Recommendation System
Discover songs tailored to your mood using hybrid embeddings (text + audio features)!

📌 Overview: 

This project uses categorized audio features (e.g., "high-energy", "low-acousticness") embedded into a structured text template, combined with sentence-transformers/all-mpnet-base-v2 embeddings, to build a music recommender.

🛠️ Key Features

    - Natural Language Feature Encoding: Numerical features (BPM, Energy, etc.) are converted to descriptive categories (e.g., "fast tempo") and injected into a text template.

    - Textualized Audio Features

    - FAISS Indexing: Efficient similarity search for real-time recommendations.

    - Semantic Search: LLM embeddings understand nuanced queries (e.g., "upbeat workout songs with low acousticness").


📂 Dataset: Top50MusicFrom2010-2019 from Spotify.

![image](https://github.com/user-attachments/assets/38242b46-86f2-40a2-b147-462e8a8a8c3a)



✒️ template = 

        "a {popularity_cat} and {loudness_cat} {speechiness_cat} music titled: {title}, by : {artist} released in : {year}, {genre} Genre {tempo_cat} Tempo, {energy_cat} Energy and {dancability_cat} Dancability . it has {liveness} Liveness and {valence_cat} Mood. {length_cat} Length and {acousticness_cat} acousticness"
    

Feature Injected Template Example : 

        "A very popular and loud speech-heavy music titled: 'Blinding Lights', by: The Weeknd released in: 2020, Pop Genre with fast tempo, high energy, and very danceable. It has studio-like liveness and happy mood. Average length and low acousticness."


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

Example Usage : 
search("a music about Drugs and in genre of hip hop", index_all, texts_artist_genre_year, 10)


        index	texts	distance
        0	a music titled: Your Love Is My Drug, by : Kesha released in : 2010, Genre : dance pop	        0.8068172931671143
        1	a music titled: Overdose, by : Ciara released in : 2013, Genre : dance pop	                0.8073247671127319
        2	a music titled: Drip (feat. Migos), by : Cardi B released in : 2018, Genre : pop	        0.9020224809646606
        3	a music titled: Me, Myself & I, by : G-Eazy released in : 2016, Genre : hip hop	                0.9145728349685669
        4	a music titled: Lemon, by : N.E.R.D released in : 2018, Genre : hip hop	                        0.9183028936386108
        5	a music titled: Fancy, by : Iggy Azalea released in : 2014, Genre : australian hip hop	        0.9416817426681519
        6	a music titled: Rock That Body, by : The Black Eyed Peas released in : 2010, Genre : dance pop	0.9535823464393616
        7	a music titled: TiK ToK, by : Kesha released in : 2010, Genre : dance pop	                0.954178512096405
        8	a music titled: Love The Way You Lie, by : Eminem released in : 2010, Genre : detroit hip hop	0.9603129625320435
        9	a music titled: Starships, by : Nicki Minaj released in : 2012, Genre : dance pop

Flexible: Modify thresholds or templates without retraining.
