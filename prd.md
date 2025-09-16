Intentions:
- Learn tools and build an working AI agent
- (nice to have) Try to automate a workflow
- (nice to have) Solve a real problem I have

Problem Statement:
- I want to do my first real estate investment this year
- The problem is that there are so many manual steps involved in doing an investment analysis which include jumping between Zillow, Craiglist, etc to gather real world data
- One key analysis is coming up with a "cap rate" or capitalization rate which is a metric for returns on income-producing property 
- A follow up analysis to "cap rate" is to look at cap rates in the area as a benchmark
- Another key analysis is coming up with "comps" or "comparables" looking at similar properties that have sold in the area to determine the market rate
- I'd like to come up with some AI agent to help automate at least one of these analyses

MVP Solution:
- Real estate investment AI agent 
- Input an address of a residential or commercial real estate and output Investment Note
- Uses some general search API to get output to get financial assumptions
    - Average / Monthly rent for zip code given property configuration (# of bedroom, size, etc)
    - Rule of thumb assumptions via prompt engineering for other costs like insurance and maintanance 
    - Estimated price for the property from Zillow/RedFin search results
- Makes key calculations
    - NOI from Annual Rental Income Estimate Annual Costs
    - Cap Rate from Listing Price and NOI
- Includes a sources and citations 
- (Nice to have) Creates a sensitivity table for Cap Rate based on Price and NOI
- (Nice to have) Mini UI to see under the hood steps and actions (traces UI)
- (Nice to have) UI interface

Constraints & Assumptions:
- Focus on Philadelphia area for now
- Focus on commercial or mixed-use

Technical Tools:
- Python
- OpenAI Agents SDK
    - ComputerTool from OpenAI's Agents SDK 
    - WebSearchTool do deep research + customizations
        - Alternatively can use perplexity or maybe Google Gemini search API, okay to do hallucinations
- OpenAI API for age



Technical Features/Design
- Single agent vs multi-agent
    - Single agent is more doable, if we had more time, would do multi-agent
    - Pros for multi-agent in the future
        Agent for research on rental info and pricing
        Agent for financial analysis and calculations
        Agent for reporting/recommendations.
        Reason: I'm guessing it will be cleaner/easier to manage and smaller context windows for better performance
- Data Pipeline/Schema
    - Single shot prompt, not time for data pipeline
    - If I had time, I would do HTML data + structured output JSON from prompts and tools -> Consolidated schema / JSON blob -> Output in Front-end for future storage
    - Refer to core_data_schema.md file
- Basic Key Error Handling
    - What happens when there are no rent results / good enough rent or comparables results?
        - Cite the source and make a note that it's AI generated 

Agents Workflow
- Real Estate Research and Analysis Agent 
    - Finds rental info and comparable listings and prices with some API for tooling to get structured some structured output
    - Gathers the assumptions and runs calculations
    - Findings overall and writes a short note and recommendations
- Research -> Analysis -> Synthesis and Recommendations paired with some UI and Chat


Technical Workflow
- Imports
- Define Instructions and tools in a separate txt file and reference it
    - Research Agent
        - Instructions:
            You are a real estate research agent. You gather key assumptions to be used in financial and investment analysis for real estate. Your main task is to use tools to research, gather assumptions.
            Once you have gathered all assumptions, then run the calculations
            After you have all of the calculations, do a synthesis / analysis and give you recommendations and thoughts.
        - Tools: WebSearchTools

Out of Scope:
- Success metrics, this is for personal use
- Error handling

Future Roadmap/Vision:
- Real estate investment analyst AI agent
- Input an address of a residential or commercial real estate or URL -> Output Investment Note Webpage
- Top of the webpage has Market Value Price based on cap rate, Calculated Cap Rate, Years to Return on Investment
- Has a sensitivity analysis table of Cap Rate and Price and sensitivity analysis table on Return on Investment and Price
- Has List Price, Target Price and below it a table investment comps with sold price, address, number of bedroom, number of bathrooms, sq ft, price per sq ft, source, and link
- Has table with Calculated Cap Rate and cap rate comps, source, summary note, and link
- Has note summary of City of Philadelphia property history
- Has note summary of general search on property
- Has Investment Summary based on the note and Recommendations