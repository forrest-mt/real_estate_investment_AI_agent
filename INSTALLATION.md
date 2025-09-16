# Installation Guide

This guide will help you set up the Real Estate Investment Analyst AI Agent on your local machine.

## Prerequisites

- Python 3.8 or higher
- Internet connection for web searches
- OpenAI API key

## Step-by-Step Installation

### 1. Clone the Repository

```bash
git clone [repository-url]
cd real_estate_investment_analyst_AI_agent
```

### 2. Install UV Package Manager

UV is a fast Python package manager that we use for dependency management.

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows:**
```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**Alternative (using pip):**
```bash
pip install uv
```

### 3. Install Dependencies

```bash
uv sync
```

This will:
- Create a virtual environment
- Install all required dependencies from `pyproject.toml`
- Set up Jupyter notebook environment

### 4. Set Up Environment Variables

```bash
# Copy the example environment file
cp .env.example .env

# Edit the .env file and add your OpenAI API key
echo "OPENAI_API_KEY=your_actual_api_key_here" > .env
```

**To get an OpenAI API key:**
1. Go to [OpenAI API](https://platform.openai.com/api-keys)
2. Create an account or sign in
3. Generate a new API key
4. Copy the key to your `.env` file

### 5. Verify Installation

```bash
# Activate the virtual environment
source .venv/bin/activate  # macOS/Linux
# or
.venv\Scripts\activate     # Windows

# Start Jupyter
jupyter notebook
```

This should open Jupyter in your browser at `http://localhost:8888`

### 6. Open and Run the Notebook

1. In Jupyter, click on `re_research_agent.ipynb`
2. Run all cells (Cell → Run All)
3. When prompted, enter a Philadelphia property address like:
   ```
   1834 E Allegheny Ave, Philadelphia, PA 19134
   ```

## Troubleshooting

### Common Issues

**"OPENAI_API_KEY not found" error:**
- Make sure your `.env` file exists in the project root
- Verify the API key is correct (no extra spaces or quotes)
- Restart the Jupyter kernel after adding the key

**Import errors for 'agents' module:**
- Make sure you ran `uv sync` successfully
- Check that you're in the project directory
- Try restarting Jupyter

**WebSearchTool not working:**
- Ensure you have an internet connection
- Check if your firewall is blocking requests
- Verify your OpenAI API key has sufficient credits

**Jupyter not starting:**
- Try: `python -m jupyter notebook`
- Or install Jupyter separately: `pip install jupyter`

### Getting Help

If you encounter issues:

1. Check that all prerequisites are installed
2. Ensure your OpenAI API key is valid and has credits
3. Try running in a fresh terminal window
4. Verify your Python version: `python --version`

## Project Structure

```
real_estate_investment_analyst_AI_agent/
├── re_research_agent.ipynb    # Main notebook
├── .env                       # Your API keys (create this)
├── .env.example              # Template for environment variables
├── pyproject.toml            # Dependencies and project config
├── README.md                 # Project overview
├── CLAUDE.md                 # Development guidance
└── .venv/                    # Virtual environment (created by uv)
```

## Next Steps

Once installed:
1. Run the notebook and test with a Philadelphia address
2. Review the agent's research process in the output
3. Examine the investment calculations and recommendations
4. Try different properties to see how the analysis varies

The system is designed specifically for Philadelphia properties and uses local tax rates and market assumptions.