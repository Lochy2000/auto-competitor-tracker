<!-- {
  "$schema": "http://json-schema.org",
  "title": "CompetitorIntelligencePayload",
  "type": "object",
  "properties": {
    "competitor_name": { "type": "string" },
    "analysis_timestamp": { "type": "string", "format": "date-time" },
    "strategic_updates_detected": { "type": "boolean" },
    "insights": {
      "type": "object",
      "properties": {
        "pricing_changes": {
          "type": "string",
          "description": "Details of any new tiers, discounts, or price hikes. Enter 'None' if unchanged."
        },
        "product_launches": {
          "type": "array",
          "items": { "type": "string" },
          "description": "List of newly discovered features, products, or service offerings."
        },
        "marketing_shift": {
          "type": "string",
          "description": "Changes in messaging, target audience focus, or homepage copywriting."
        }
      },
      "required": ["pricing_changes", "product_launches", "marketing_shift"]
    },
    "recommended_action": { "type": "string" }
  },
  "required": ["competitor_name", "analysis_timestamp", "strategic_updates_detected", "insights", "recommended_action"]
} -->
