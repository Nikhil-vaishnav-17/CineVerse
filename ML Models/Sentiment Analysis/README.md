# Sentiment Analysis Model

A machine learning-based sentiment analysis system that classifies movie reviews as positive or negative using text preprocessing, TF-IDF vectorization, and star ratings.

*Second Year End Project*

## Overview

This sentiment analysis model combines natural language processing with machine learning to predict the sentiment (positive/negative) of movie reviews. It uses both textual content and star ratings to improve classification accuracy.

### Key Features

- **Text Processing**: Uses spaCy for lemmatization, tokenization, and stopword removal
- **Feature Engineering**: Combines TF-IDF features with star ratings
- **Model Interpretability**: Provides feature importance rankings
- **Probability Scoring**: Returns confidence scores for predictions
- **Model Persistence**: Save and load trained models

## Tech Stack

- **scikit-learn**: ML algorithms and preprocessing
- **spaCy**: NLP processing and text preprocessing
- **pandas**: Data manipulation
- **NumPy**: Numerical computing
- **Pickle**: Model serialization

## Installation

1. Install dependencies:
```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

2. Ensure your training data is in CSV format with columns:
   - `review`: Text content of the review
   - `sentiment`: 'positive' or 'negative' labels
   - `stars`: Star rating (optional, will be generated if missing)

## Usage

### Training the Model

```python
from Sentiment_model import IMDBSentimentAnalyzer

# Initialize analyzer
analyzer = IMDBSentimentAnalyzer(star_weight=0.0048)

# Prepare data
prepared_data = analyzer.prepare_data(
    reviews=train_df['review'].values,
    stars=train_df['stars'].values
)

# Train model
analyzer.fit(prepared_data, train_df['sentiment'].values)
```

### Making Predictions

```python
# Single prediction
result = analyzer.predict(['Great movie!'], [9])

# Probability prediction
probabilities = analyzer.predict_proba(['Great movie!'], [9])
# Returns: [[negative_prob, positive_prob]]
```

### Model Evaluation

```python
results = analyzer.evaluate_model(
    test_df[["review", "stars"]], 
    test_df["sentiment"]
)

print(f"Accuracy: {results['accuracy']:.4f}")
print(f"F1-Score: {results['f1_score']:.4f}")
```

### Feature Importance

```python
importance_df = analyzer.get_feature_importance()
print(importance_df.head(20))
```

### Model Persistence

```python
# Save model
analyzer.save_model('sentiment_model.pkl')

# Load model
analyzer.load_model('sentiment_model.pkl')
```

## Model Details

- **Algorithm**: Logistic Regression
- **Features**: TF-IDF vectorization with star ratings
- **Max Features**: 50,000 text features
- **N-gram Range**: Unigrams and bigrams
- **Star Weight**: 0.0048 (configurable)

## Data Format

### Input CSV Structure
```
review,sentiment,stars
"This movie was amazing!",positive,9
"Terrible waste of time",negative,2
```

### Sentiment Labels
- `positive`: 1
- `negative`: 0

### Star Ratings
- Scale: 1-10 (higher for positive reviews, lower for negative)
- Auto-generated if missing

## File Structure

```
Sentiment Analysis/
├── Sentiment.ipynb           # Training notebook
├── Sentiment_model.pkl       # Trained model
├── requirements.txt          # Python dependencies
├── data/
│   └── review.csv           # Training dataset
└── README.md                # This file
```

## Integration with CineVerse

This sentiment analysis model integrates with the CineVerse Flask API to analyze user-submitted reviews in real-time and provide sentiment predictions.

## License

This project is part of CineVerse.
