# ISR System Evaluation

## Objective
Evaluate retrieval quality of the SQLite-based IR system on historical graphics/design records.

## Dataset
- Collection size: 50 records
- Domain: graphics and design from different origins and periods

## Query Set (example)
1. geometric islamic pattern
2. bauhaus germany poster
3. renaissance italy print
4. japanese woodblock wave
5. art deco typography france
6. afrocentric modern symbols
7. gothic illumination manuscript
8. swiss style grid typography
9. baroque calligraphy ornament
10. digital minimalism interface

## Relevance Judgement
For each query, manually mark top-10 as relevant (1) / non-relevant (0) or graded relevance (0-3).

## Metrics
- Precision@10 = relevant_in_top10 / 10
- Recall@10 = relevant_in_top10 / total_relevant_in_collection
- F1 = 2 * (P * R) / (P + R)
- MRR = mean(1 / rank_of_first_relevant)
- nDCG@10 for graded relevance

## Efficiency
Track per query:
- `tookMs` from `/api/search`
- mean, median, max latency

## Error Analysis
Document failure types:
- vocabulary mismatch (synonyms)
- ambiguous periods
- sparse tags
- metadata inconsistency

## Improvement Plan
- synonym expansion map (e.g., pharaonic->egyptian)
- normalized controlled vocabulary for period/style
- field boosting for title and tags
- typo tolerance layer (optional)
