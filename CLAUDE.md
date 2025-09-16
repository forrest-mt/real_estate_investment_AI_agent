# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Instructions
- Keep implementation simple and minimal
- Primary development is in the Jupyter notebook `re_research_agent.ipynb`
- Focus on helping with the notebook-based approach rather than complex infrastructure

## Project Overview

This is a **real estate investment analyst AI agent** system designed to automate Philadelphia property analysis. The system uses a single Jupyter notebook with a simple agent that uses WebSearchTool to research properties and calculate investment metrics.

**Current Status**: Implemented as a single notebook (`re_research_agent.ipynb`) with one agent that handles research, calculation, and recommendations.

## Quick Start

```bash
# 1. Environment setup
cp .env.example .env  # Add your OpenAI API key
pip install uv
uv sync

# 2. Run the notebook
jupyter notebook re_research_agent.ipynb
```

## Architecture Overview

### Simplified Notebook Architecture
The system is implemented as a single Jupyter notebook with:

1. **Real Estate Agent** - Uses WebSearchTool for property research and analysis
2. **Simple workflow**: Property Address → Web Search → Financial Calculations → Investment Recommendation

### Data Flow
```
User Input (Address) → WebSearchTool → Agent Analysis → Investment Report
```

### Core Components
- **Agent Instructions**: Detailed prompts for property research and analysis
- **WebSearchTool**: Handles all external data gathering
- **Manual Calculations**: Philadelphia-specific investment metrics

### Philadelphia-Specific Configuration
The system uses these Philadelphia market assumptions:
- Vacancy rate: 8%
- Maintenance: 10% of rental income
- Capital reserves: 10% of rental income

## Financial Calculations

The agent calculates key investment metrics:
- **NOI**: (Annual Rent × 0.92) - (Taxes + Insurance + Maintenance + Reserves)
- **Cap Rate**: NOI / Property Value
- **Blended Property Value**: Weighted average of Zillow, assessments, and comps

## Environment Setup

### Required Environment Variables (.env)
```bash
OPENAI_API_KEY=your_key_here
```

## Usage

1. Open `re_research_agent.ipynb` in Jupyter
2. Run all cells to set up the agent
3. Enter a Philadelphia property address when prompted
4. The agent will:
   - Search for property details (bedrooms, bathrooms, square footage, value)
   - Find comparable rental properties
   - Calculate investment metrics (NOI, cap rate)
   - Generate an investment recommendation

## Key Features

- **Real-time web search** for property and rental data
- **Philadelphia-specific analysis** with local tax rates and assumptions
- **Investment calculations** including cap rate and NOI
- **Detailed tracing** to see the agent's research process

## Important Notes

- Designed specifically for Philadelphia properties
- Uses real web search data (not synthetic)
- Requires OpenAI API key for operation
- All calculations follow standard real estate investment principles