# Real Estate Investment Analyst AI Agent

A simple Jupyter notebook-based system for Philadelphia real estate investment analysis using AI agents and web search.

## Demo

https://www.loom.com/share/c090fc0be275462ca6b3d59ad4e010b6

## Screenshot

<img width="1157" height="814" alt="image" src="https://github.com/user-attachments/assets/d32069e3-fc5b-459b-bb00-d817c369cf54" />

## Features:

Input an address of a residential or commercial real estate ->  output Investment Memo
Uses OpenAI's Agents SDK WebSearchTool to do research on rental rates, comparables, etc
Rule of thumb assumptions via prompt engineering for assumptions for costs like insurance and maintanance
Agents key investment calculations 
NOI from Annual Rental Income Estimate Annual Costs
Cap Rate from Listing Price and NOI
Includes a sources and citations

## Problem Statement 
I'm running a real estate business as a side gig. The problem is that there are so many manual steps involved in doing an investment analysis, which include jumping between Zillow, Craiglist, etc to gather real world data and takes a few hours
One key analysis is coming up with a "cap rate" or capitalization rate which is a metric for returns on income-producing property which takes hours per property
I'd like to come up with some AI agent to help automate the analyses

## My Thoughts

I used one of a my manual calculations of NOI to evaluate the effectiveness of the agent, I did a manual feedback loop to improve  
I struggled  with implementation. As you can see from my PRD.md and implementation_plan.md I had a lot of lofty goals but I ended up running out of time to implement
This single agent single shot approach is a really buggy, a lot of randomness when it comes to the quality and consistency of the output
Still the agent came somewhat close in terms of "investment vibes" sometimes and the time it took went from 2 hours to 2 mins
One time it gave a really completely off result

If I had more time, I would do 

- Multi-agent setup to potentially reduce hallucinations and improve quality
- Create more structured outputs or JSON outputs to reduce hallucination and quality check
- Create helper functions for the calculations to improve quality and reduce hallucinations
- Create UI to make it easier to visualize the analysis and ask more questions


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

- Vacancy rate: 8%
- Maintenance: 10% of rental income
- Capital reserves: 10% of rental income

## Requirements

- Python 3.8+
- OpenAI API key
- Jupyter notebook environment
- Internet connection for web searches
