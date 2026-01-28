# Stock Recommender & Advisor

A comprehensive stock analysis and financial advisory tool built with Streamlit, featuring real-time stock data analysis, interactive visualizations, and AI-powered financial advice.

## Features

### Stock Analysis
- **Multi-Stock Comparison**: Analyze multiple stocks simultaneously
- **Interactive Charts**: 
  - Price history with currency conversion
  - Trading volume analysis
  - Moving averages (50-day & 200-day)
  - Candlestick charts for detailed price movements
- **Key Financial Metrics**:
  - Current price and price changes
  - 52-week high/low
  - Market cap, P/E ratio, dividend yield
  - Revenue, net income, ROE
  - Debt-to-equity ratio
- **Multi-Currency Support**: USD, INR, EUR, AUD
- **Exchange Support**: NSE, BSE, and US markets

### Financial Advisor Chat
- AI-powered financial advice using open-source LLMs
- Answers questions about:
  - Personal finance
  - Investment strategies
  - Retirement planning
  - Financial terms and concepts

## Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd stock-advisor-ai
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Dependencies

- **streamlit**: Web application framework
- **pandas**: Data manipulation and analysis
- **numpy**: Numerical computing
- **plotly**: Interactive visualizations
- **yfinance**: Real-time stock data from Yahoo Finance
- **requests**: HTTP library for API calls
- **transformers**: Hugging Face transformers for LLM
- **torch**: PyTorch for model inference
- **accelerate**: Model acceleration library
- **sentencepiece**: Tokenization library
- **huggingface_hub**: Access to Hugging Face models

## Usage

### Running the Application

Start the Streamlit app:
```bash
streamlit run app.py
```

The application will open in your default web browser at `http://localhost:8501`

### Stock Analysis Page

1. **Enter Stock Tickers**: Input one or more ticker symbols separated by commas
   - Examples: `AAPL`, `RELIANCE`, `TSLA, MSFT, GOOGL`

2. **Select Exchange**:
   - `None`: For US stocks (NASDAQ, NYSE)
   - `NSE`: National Stock Exchange (India)
   - `BSE`: Bombay Stock Exchange (India)

3. **Choose Time Period**: 1M, 3M, 6M, 1Y, 2Y, 5Y, YTD, Max

4. **Select Currency**: USD, INR, EUR, or AUD for all financial data

5. **View Analytics**:
   - Price history comparison
   - Volume analysis
   - Moving averages (for periods ≥ 200 days)
   - Individual candlestick charts
   - Financial metrics comparison
   - Company information

### Financial Advisor Chat

1. Navigate to the "Financial Advisor Chat" page
2. Ask questions about personal finance, investing, or financial concepts
3. The AI advisor will provide guidance using a local language model

**Example Questions**:
- What is a Roth IRA?
- How much should I save for retirement?
- What's a good investment strategy for beginners?
- Should I pay off debt or invest?
- What is an ETF?

## Project Structure

```
stock-advisor-ai/
├── app.py                  # Main application file
├── requirements.txt        # Python dependencies
├── README.md              # Project documentation
├── .gitignore             # Git ignore rules
├── config.py              # Configuration settings
├── tests/                 # Test files
│   └── test_stock_data.py
└── docs/                  # Additional documentation
    ├── USAGE.md
    └── API.md
```

## 🔧 Configuration

### Currency Exchange Rates
The app uses the Open Exchange Rates API for real-time currency conversion. Fallback rates are provided if the API is unavailable.

### Rate Limiting
- yfinance requests are rate-limited with exponential backoff
- Default delay: 1.5 seconds between requests
- Max retries: 3 attempts with backoff

### LLM Models
The application uses TinyLlama for financial advice, with automatic fallback to distilgpt2 if unavailable.

## Data Sources

- **Stock Data**: Yahoo Finance via yfinance
- **Currency Rates**: Open Exchange Rates API
- **LLM**: Hugging Face transformers (TinyLlama/distilgpt2)

## Important Notes

### Limitations
- The AI advisor uses a small language model and may have limitations
- Not a replacement for certified financial advice
- Stock data depends on Yahoo Finance API availability
- Currency conversion uses approximate rates when API is unavailable

### Rate Limits
- Yahoo Finance may rate-limit requests for high-frequency queries
- The app implements retry logic and exponential backoff
- Consider the rate limits when analyzing many stocks simultaneously

### Data Accuracy
- Historical data is sourced from Yahoo Finance
- Some stocks may have incomplete financial data
- Always verify critical information from official sources

## Troubleshooting

### Common Issues

**"No data available for ticker"**
- Verify the ticker symbol is correct
- Check if the exchange is properly selected
- Some tickers may require specific suffixes (.NS for NSE, .BO for BSE)

**"Rate limited" errors**
- Wait a few minutes before retrying
- Reduce the number of stocks analyzed simultaneously
- The app will automatically retry with exponential backoff

**LLM not loading**
- Ensure all dependencies are installed
- Check internet connection for model download
- The app will automatically fall back to a smaller model

**Currency conversion issues**
- The app uses fallback rates if the API is unavailable
- Rates are approximate and updated periodically

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This project is open source and available under the MIT License.

## Credits

Created by Gurleen

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Contact the development team

## Future Enhancements

- [ ] Portfolio tracking and management
- [ ] Advanced technical indicators (RSI, MACD, Bollinger Bands)
- [ ] News sentiment analysis
- [ ] Price prediction using ML models
- [ ] Stock screener with custom filters
- [ ] Real-time alerts for price movements
- [ ] Export reports as PDF
- [ ] Integration with more exchanges globally
- [ ] Enhanced AI chat with conversation memory
- [ ] Comparison with market indices

---

**Disclaimer**: This tool is for educational and informational purposes only. It is not financial advice. Always consult with a qualified financial advisor before making investment decisions.
