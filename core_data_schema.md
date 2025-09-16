Data Schema Structure for Data Pipeline

# Core Property Schema
  # Redfin URL output from parsing
  {
    "property_id": "addr_hash_or_uuid",
    "address": {
      "street": "123 Main St",
      "city": "Philadelphia",
      "state": "PA",
      "zip": "19101"
    },
    "analysis_timestamp": "2025-01-10T15:30:00Z",

    # RE Research Agent Output
    "rental_data": {
      "comparables": [
        {
          "source": "craigslist|zillow|apartments",
          "monthly_rent": 1200,
          "bedrooms": 2,
          "bathrooms": 1,
          "sqft": 800,
          "distance_miles": 0.3,
          "listing_url": "...",
          "confidence_score": 0.85
        }
      ],
      "estimated_monthly_rent": 1150, # calculate weighted average based on confidence_score
      "rent_per_sqft": 1.44 #calculate weighted average based on monthly rent / sq ft per rental unit
    },
    "valuation_data": {
      "sources": [
        {
          "source": "zillow_estimate",
          "price": 185000,
          "confidence": 0.7 # confident score based on prompt + LLM vibes
        },
        {
          "source": "phila_assessment",
          "price": 165000,
          "confidence": 0.6 # based on browsing and scraping property.phila.gov
        },
        {
          "source": "listing_price",
          "price": 195000,
          "confidence": 0.9 # actual listing price
        }
      ],
      "weighted_market_value": 183000,
      "comps": [
        {
          "address": "125 Main St",
          "sold_price": 180000,
          "sold_date": "2024-11-15",
          "sqft": 850,
          "similarity_score": 0.92
        }
      ]
    },

    # RE Analysis Agent Output
    "financial_analysis": {
      "annual_rental_income": 13800,
      "annual_costs": {
        "taxes": 2200,
        "insurance": 800,
        "maintenance": 1380,
        "reserves": 1380,
        "total": 5760
      },
      "noi": 8040,
      "cap_rate": 0.044,
      "years_to_roi": 22.8,
      "sensitivity_analysis": {
        "price_scenarios": [175000, 183000, 195000],
        "noi_scenarios": [7500, 8040, 8500],
        "cap_rates_matrix": [[0.043, 0.046, 0.049], ...]
      }
    },

    # Metadata for traces/debugging
    "processing_metadata": {
      "agents_used": ["researcher", "analyzer", "recommender"],
      "data_sources_accessed": ["craigslist", "zillow", "phila_gov"],
      "errors": [],
      "warnings": ["low_confidence_rental_data"]
    }
  }