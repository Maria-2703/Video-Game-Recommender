# Video-Game-Recommender

# 🎮 Video Game Recommendation System: Lexical vs. Semantic Approach

## 📌 Project Overview
This project implements and evaluates a Content-Based Filtering recommendation system for video games. It compares a traditional lexical approach (TF-IDF) against a modern semantic approach using dense vector representations (Transformer-based embeddings). 

## 📊 Dataset Used
The project utilizes a synthetic video game dataset containing both categorical metadata (e.g., Platform, Genre, Developer, Age Group) and natural language text (User Reviews). *Note: Due to the randomized nature of the synthetic metadata, this dataset serves as an excellent stress-test for evaluating if the models blindly follow text patterns or get confused by statistical noise.*

## ⚙️ Dependencies
To run this notebook, the following Python libraries are required:
- `pandas`
- `numpy`
- `scikit-learn`
- `sentence-transformers`

*You can install the required models via pip: `pip install sentence-transformers pandas scikit-learn`*

## 🚀 Execution Instructions
1. Ensure the dataset CSV file is placed in the same directory as the notebook (or properly uploaded if using Google Colab).
2. Run the notebook cells sequentially.
3. **Important:** The embedding generation step (`Step 5`) utilizes the `all-MiniLM-L6-v2` model. This process runs on the CPU by default and may take a few minutes depending on your hardware. A progress bar will indicate the estimated time.
4. The notebook includes a fully automated offline evaluation protocol that will output the final performance metrics (Precision & Diversity).

## 🏆 Summary of Results
- **Baseline (TF-IDF):** Showed strong keyword-matching capabilities but suffered heavily from "lexical overfitting." It tended to create a "developer bubble," repeatedly recommending games from the same studio simply because the studio's name was a statistically rare token in the corpus.
- **Modern Embeddings (MiniLM):** Outperformed the baseline across all metrics. It successfully bypassed the superficial vocabulary, capturing the underlying contextual meaning of the games (Genre, Vibe, Review Sentiment). It provided a much richer **Diversity@5**, proving to be a more robust and useful recommendation engine for end-users.
- **Offline Metrics:** The semantic model achieved higher **Precision@5** (accurate genre matching) and **Diversity@5** (unique developers) compared to the classical lexical baseline.