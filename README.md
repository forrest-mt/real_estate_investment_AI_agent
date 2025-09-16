# Real Estate Investment Analyst AI Agent

A simple Jupyter notebook-based system for Philadelphia real estate investment analysis using AI agents and web search.

## Quick Start

```bash
# 1. Clone and setup environment
git clone [repo-url]
cd real_estate_investment_analyst_AI_agent

# 2. Install dependencies
pip install uv
uv sync

# 3. Setup OpenAI API key
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY

# 4. Run the notebook
jupyter notebook re_research_agent.ipynb
```

## How It Works

1. **Input**: Enter a Philadelphia property address
2. **Research**: Agent searches web for property details and comparable rentals
3. **Calculate**: Computes NOI, cap rate, and investment metrics
4. **Report**: Generates investment recommendation and analysis

## Key Features

- **Real-time web search** for property and rental data
- **Philadelphia-specific** tax rates and market assumptions
- **Investment calculations**: Cap rate, NOI, ROI analysis
- **Interactive notebook** with step-by-step execution
- **Detailed tracing** to see agent decision-making process

## Example Usage

```python
# In the notebook, simply run all cells and enter:
1834 E Allegheny Ave, Philadelphia, PA 19134
```

The agent will automatically:
- Find property details (bedrooms, bathrooms, value)
- Search comparable rental properties
- Calculate investment metrics
- Generate investment recommendation

## Philadelphia Market Assumptions

- Property tax rate: 0.6138%
- Vacancy rate: 8%
- Maintenance: 10% of rental income
- Capital reserves: 10% of rental income
- Insurance: 15% of rental income

## Requirements

- Python 3.8+
- OpenAI API key
- Jupyter notebook environment
- Internet connection for web searches