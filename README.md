# API Used
- <a href="https://developer.api.nhs.uk/nhs-api" target="_blank">NHS</a> (might be replaced by health.gov)
- <a href="https://health.gov/our-work/national-health-initiatives/health-literacy/consumer-health-content/free-web-content/apis-developers" target="_blank">Health.gov</a>

# Setup
```bash
cp .env.example .env
```

# Installation


```bash
py -m venv .venv
```

```bash
.\.venv\Scripts\Activate
```

```bash
pip install fastapi nltk numpy pydantic python-dotenv requests setuptools sumy uvicorn beautifulsoup4 lxml    
```

# Run
```bash
uvicorn main:app --reload
```

# Summarizer
### methods
`LSA`
`text-rank`
`lex-rank` 
`edmudson` 
`luhn`
`kl-sum`
`random`
`reduction`

### inputType
`text` `URL`
 
### sample api call - Summarizer

```bash
function summarizeText(
  method: string, 
  language: string, 
  sentenceCount: number 
  inputType: string, 
  inputText: string
): void {
  const apiUrl = 'http://localhost:5000/summarize';
  const data = {
    data: [method, language, sentenceCount, inputType, inputText]
  };
  
  fetch(apiUrl, {
    method: 'POST', 
    headers: {
      'Content-Type': 'application/json' 
    },
    body: JSON.stringify(data) 
  })
    .then(response => response.text()) 
    .then(summary => {
      console.log('Summary:', summary);
    })
    .catch(error => {
      console.error('Error:', error); 
    });
}

// Sample
summarizeText('lex-rank', 'english', 5, 'URL', 'https://www.nhs.uk/live-well/alcohol-advice/calculating-alcohol-units/');

```
