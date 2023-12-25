# Sentiment Analysis Service

This microservice provides a sentiment analysis for text data passed into it via a REST API. It's built using FastAPI and NLTK so has a high throughput and is suprisingly rapid once running.

## Getting Started

### Prerequisites
- Docker (yup this is the only prerequisite)

### Installation and running the service

1. Build the image i.e. `docker build -t sentiments:1.0.0 .`
2. Run the image i.e. `docker run -d --name sentiments -p 8080:8080 sentiments:1.0.0`
3. Point your browser at http://localhost:8080 and you should see `"Service is running!"`

### Analyse Sentiments via the RestAPI

- **Endpoint**: `POST /`
- **Payload**:
```json
{
 "text": "string"
}
```

You can call this via CURL or via postman or whatever service you like e.g.

```bash
$ curl -X POST http://localhost:8080/ \
-H "Content-Type: application/json" \
-d '{"text": "I love this new service! It works wonderfully."}'

{
  "sentiment": "positive",
  "sentiment_score": {
    "compound": 0.8553,
    "neg": 0.0,
    "neu": 0.373,
    "pos": 0.627
  },
  "text": "I love this new service! It works wonderfully.",
}
```

## Understanding Sentiment Scores

The sentiment analysis returns several scores that represent different aspects of sentiment:

- **Positive Score (`pos`)**: Proportion of the text that falls into the positive category. Higher scores indicate more positive sentiments.
- **Neutral Score (`neu`)**: Proportion of the text that is neutral. High scores are often found in factual or objective statements.
- **Negative Score (`neg`)**: Proportion of the text that is negative. Higher scores indicate more negative sentiments.
- **Compound Score (`compound`)**: A normalized, weighted composite score of the positive, neutral, and negative scores. Ranges from -1 (extremely negative) to +1 (extremely positive). It provides an overall sentiment of the text.

## Contributing

Contributions to the Sentiment Analysis Service are welcome! If you have suggestions for improvements or encounter any issues, please feel free to contribute. Here's how you can contribute:

1. **Fork the Repository:** Create your own fork of the project on GitHub.
2. **Create a Branch:** Make your changes in a new branch in your fork.
3. **Submit a Pull Request:** After making your changes, submit a pull request to the main repository. Please describe your changes and the reason for them.
4. **Code Review:** Your pull request will be reviewed and, if accepted, merged into the project.

For major changes, please open an issue first to discuss what you would like to change. Please ensure to update tests as appropriate.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

If you have any questions or encounter issues with the Sentiment Analysis Service, please file an issue in the [GitHub Issues](https://github.com/GizzmoAsus/sentiment-analysis-service/issues) section of the repository.
