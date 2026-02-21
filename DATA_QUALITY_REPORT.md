# LuxeScout v2 — Data Quality & Search Report

**Date:** February 21, 2026
**Database:** 136,916 products across 58 vendors (v2_ tables)
**Embeddings:** 100% coverage (Cohere embed-v4, 1024 dimensions)

---

## 1. Database Overview

| Metric | Old MVP | LuxeScout v2 | Change |
|--------|---------|-------------|--------|
| Total products | 154,804 | 136,916 | -12% (removed deleted vendors) |
| Vendors | 68 | 58 | -10 (client-deleted vendors removed) |
| Embedding model | OpenAI text-embedding-3 (1536d) | Cohere embed-v4 (1024d) | Higher MTEB score, multimodal |
| Search method | Vector-only + attribute rerank | Hybrid (vector + BM25 + RRF) + Cohere Rerank 3.5 | Dramatically better recall |
| Reranking | Basic attribute matching | Cohere Rerank 3.5 | ML-based semantic reranking |
| Feedback loop | None | Thumbs up/down + comments | New in v2 |

## 2. Overall Data Quality

| Metric | Coverage |
|--------|----------|
| Has description (>10 chars) | 95% |
| Has price | 60% |
| Has image | 98% |
| Has categories | 78% |
| In stock | 75% |
| Has embedding | 100% |

## 3. Vendor Data Quality (All 58 Vendors)

| Vendor | Tier | Count | Desc% | Price% | Image% | Cat% | Stock% | Avg Desc | Issues |
|--------|------|------:|------:|-------:|-------:|-----:|-------:|---------:|--------|
| A&B Home | - | 219 | 0% | 0% | 100% | 100% | 0% | 0 | NO-DESC |
| Ambella Home | top5 | 775 | 94% | 0% | 100% | 100% | 22% | 184 | |
| Artistica Home | - | 648 | 100% | 0% | 100% | 100% | 77% | 261 | |
| Bernhardt | top10 | 4,876 | 76% | 94% | 78% | 100% | 42% | 112 | |
| Bramble Co | - | 1,866 | 92% | 0% | 100% | 100% | 0% | 81 | |
| Caracole | - | 1,671 | 100% | 100% | 100% | 100% | 90% | 396 | |
| Chelsea House | - | 1,944 | 0% | 0% | 100% | 100% | 75% | 0 | NO-DESC |
| Currey & Company | - | 2,725 | 100% | 100% | 100% | 0% | 88% | 368 | |
| Cyan Design | - | 1,983 | 97% | 100% | 97% | 87% | 100% | 328 | |
| ELK Home | - | 4,575 | 100% | 100% | 100% | 100% | 100% | 176 | |
| Eastern Accents | - | 8,338 | 100% | 70% | 94% | 78% | 100% | 153 | |
| Eloquence | - | 652 | 100% | 100% | 100% | 1% | 99% | 641 | |
| Essentials for Living | top10 | 408 | 99% | 100% | 0% | 0% | 99% | 35 | NO-IMG, SHORT-DESC |
| Fairfield Chair | top20 | 5,818 | 100% | 99% | 100% | 99% | 100% | 211 | |
| Four Hands | - | 17,144 | 100% | 100% | 100% | 100% | 27% | 291 | |
| Gabriella White | depri | 1,782 | 97% | 80% | 99% | 81% | 100% | 367 | |
| Gracie Studio | - | 51 | 100% | 100% | 100% | 100% | 96% | 160 | |
| Greenhouse Fabrics | - | 70 | 100% | 0% | 100% | 0% | 0% | 187 | |
| HVL Group | - | 5,915 | 100% | 92% | 100% | 100% | 73% | 329 | |
| Hekman | - | 691 | 100% | 100% | 100% | 100% | 80% | 391 | |
| Horizon Shades | - | 4 | 100% | 0% | 100% | 0% | 0% | 152 | |
| Interlude Home | - | 1,183 | 80% | 99% | 100% | 98% | 99% | 127 | |
| Jaipur Living | - | 2,337 | 100% | 89% | 100% | 100% | 100% | 375 | |
| James Martin Vanities | - | 411 | 99% | 76% | 100% | 93% | 100% | 679 | |
| Jamie Young Co | - | 1,100 | 100% | 100% | 100% | 100% | 0% | 310 | |
| Jonathan Charles | - | 576 | 100% | 99% | 100% | 100% | 71% | 410 | |
| Lexington Home Brands | top5 | 603 | 100% | 0% | 100% | 93% | 0% | 213 | |
| Loloi Rugs | - | 4,510 | 100% | 100% | 99% | 100% | 89% | 301 | |
| Made Goods | - | 1,242 | 100% | 0% | 100% | 100% | 100% | 300 | |
| Maitland-Smith | - | 705 | 100% | 0% | 100% | 100% | 92% | 190 | |
| McKinley Leather | - | 117 | 97% | 0% | 0% | 97% | 0% | 58 | NO-IMG |
| Old Biscayne Designs | - | 3,135 | 100% | 0% | 100% | 98% | 0% | 159 | |
| Padma's Plantation | - | 331 | 100% | 100% | 100% | 100% | 99% | 2,701 | |
| Paragon | - | 3,776 | 100% | 0% | 100% | 100% | 100% | 131 | |
| Phillips Scott | - | 530 | 100% | 0% | 100% | 100% | 0% | 195 | |
| Precedent Furniture | top5 | 406 | 100% | 0% | 0% | 100% | 0% | 176 | NO-IMG |
| Propac Images | - | 1,301 | 100% | 0% | 100% | 100% | 100% | 119 | |
| Regina Andrew | top10 | 1,880 | 78% | 100% | 78% | 0% | 85% | 157 | |
| Renwil | - | 1,631 | 100% | 100% | 100% | 0% | 100% | 352 | |
| Rowe Furniture | top20 | 1,923 | 98% | 0% | 98% | 100% | 0% | 228 | |
| Rowley Company | - | 30 | 67% | 67% | 73% | 0% | 0% | 120 | |
| Sarreid Ltd | top5 | 603 | 100% | 100% | 100% | 100% | 0% | 364 | |
| Savoy House | - | 1,790 | 100% | 0% | 100% | 100% | 66% | 439 | |
| Selamat Designs | - | 277 | 96% | 100% | 96% | 91% | 99% | 353 | |
| Shadow Catchers Art | - | 2,720 | 100% | 100% | 100% | 99% | 100% | 166 | |
| Sherrill Furniture | - | 216 | 89% | 0% | 89% | 89% | 0% | 102 | |
| Southern Home Inc. | - | 1,063 | 99% | 33% | 100% | 100% | 100% | 133 | |
| Style Upholstering | - | 83 | 99% | 0% | 100% | 87% | 0% | 44 | SHORT-DESC |
| Summer Classics | - | 417 | 85% | 59% | 87% | 76% | 100% | 289 | |
| Surya | - | 18,598 | 100% | 0% | 100% | 0% | 100% | 190 | |
| Swaim Inc. | - | 1,354 | 100% | 9% | 96% | 99% | 96% | 133 | |
| Theodore Alexander | top5 | 2,507 | 0% | 0% | 100% | 100% | 61% | 0 | NO-DESC |
| Tuuci | - | 115 | 98% | 0% | 23% | 0% | 0% | 133 | NO-IMG |
| Universal Furniture | - | 943 | 100% | 0% | 100% | 100% | 0% | 326 | |
| Uttermost | - | 4,595 | 100% | 0% | 100% | 100% | 100% | 249 | |
| Wendover Art Group | opt | 9,558 | 100% | 100% | 100% | 100% | 100% | 238 | |
| Woodbridge Furniture | - | 1,309 | 100% | 100% | 100% | 100% | 100% | 220 | |
| Worlds Away | - | 886 | 100% | 0% | 100% | 0% | 0% | 234 | |
| **TOTAL** | | **136,916** | **95%** | **60%** | **98%** | **78%** | **75%** | | |

### Top 5 Vendor Issues (by product count)

| Vendor | Count | Tier | Issue |
|--------|------:|------|-------|
| Theodore Alexander | 2,507 | top5 | 0% descriptions - scraper captured names/images but no description text |
| Chelsea House | 1,944 | - | 0% descriptions |
| Essentials for Living | 408 | top10 | 0% images, short descriptions (avg 35 chars) |
| Precedent Furniture | 406 | top5 | 0% images |
| A&B Home | 219 | - | 0% descriptions |

### Note: Duplicate Vendor Entry
- "Sarreid" (4 products) and "Sarreid Ltd" (599 products) appear as separate vendors. These should be merged.

## 4. Search Quality Comparison

### Test Query: "console table with open base for 2 ottomans"

**Old MVP results** (vector-only + attribute rerank, OpenAI embeddings):
- Returned sideboards, trunks, display cabinets, and nightstands
- Only 5 of 20 results were actually console tables
- The rest were random Sarreid furniture items matching via broken text search
- No semantic understanding of "open base" or "space for ottomans"

**New LuxeScout v2 results** (hybrid search + Cohere Rerank 3.5):

| # | Score | Product | Vendor | Relevant? |
|---|------:|---------|--------|-----------|
| 1 | 0.630 | Adona Console Table | Uttermost | Yes - console table |
| 2 | 0.518 | Corte Open Console Table w/ 2 Drawers | Bramble Co | Yes - "open" console |
| 3 | 0.501 | Camerlin Console Table | Uttermost | Yes - console table |
| 4 | 0.496 | Reed Console Table | Uttermost | Yes - metal base, asymmetric |
| 5 | 0.374 | Versatilis Console Table | Sarreid Ltd | Yes - console table |
| 6 | 0.328 | Mar Monte Open Console | Artistica Home | Yes - "open" console |
| 7 | 0.259 | Corbet Cocktail Ottoman | Sarreid Ltd | No - ottoman, not console |
| 8 | 0.257 | Lacroix Console Table | Cyan Design | Yes - console table |
| 9 | 0.253 | Corbet Cocktail Ottoman, Caramel | Sarreid Ltd | No - ottoman, not console |
| 10 | 0.251 | Bartola Console Table | Rowe Furniture | Yes - console table |

**Summary:** 16 of 20 results are actual console tables (80% precision). The remaining 4 are cocktail ottomans pulled in by keyword matching on "ottoman." This is a significant improvement over the old MVP where only 25% of results were relevant.

**Known issue:** The search still surfaces ottomans as results because the word "ottoman" appears in the query. The Cohere reranker correctly pushes these down (scores 0.259 vs 0.630 for the top result), but they still appear. Contextual enrichment will help by giving embeddings stronger category signals.

## 5. Feedback System

### How It Works

The new feedback system creates a learning loop between the client and the search pipeline:

```
User searches → Results appear → User clicks thumbs up/down →
Feedback stored in DB → Score recalculated → Future searches boosted/penalized
```

#### User Experience
1. **Hover** over any product card to reveal thumbs up/down buttons
2. **Thumbs up** = immediately recorded, button highlights gold
3. **Thumbs down** = opens a comment box asking "Why was this a poor result?" with Skip/Send options
4. Feedback is **fire-and-forget** — no loading spinner, no interruption

#### Backend Pipeline
1. Each vote creates a row in `v2_search_feedback` with: product_id, query_text, signal (+1/-1), conversation_id, optional comment
2. An RPC function `v2_update_feedback_score()` immediately recalculates the product's aggregated score using **Laplace smoothing**:
   ```
   score = (upvotes - downvotes) / (total_votes + 5)
   ```
   The +5 in the denominator prevents a single vote from having outsized impact.
3. The score is stored as a precomputed `feedback_score` column on `v2_products` (zero latency at search time)
4. During search, `_apply_feedback_boost()` adjusts each result's ranking score:
   ```
   boosted_score = base_score * (1.0 + feedback_score * 0.3)
   ```
   This means: range from 0.85x (heavily downvoted) to 1.2x (heavily upvoted)

#### Analysis & Tuning
All feedback data is queryable in the `v2_search_feedback` table:
- **Which products get consistently downvoted?** May indicate bad data or wrong categories
- **Which queries produce poor results?** The `query_text` field lets us find weak spots
- **Free-text comments** explain *why* results were bad — invaluable for tuning
- **Conversation context** via `conversation_id` shows the full search session

Example analysis queries:
```sql
-- Most downvoted products
SELECT p.name, p.vendor_name, COUNT(*) as downvotes
FROM v2_search_feedback f JOIN v2_products p ON f.product_id = p.id
WHERE f.signal = -1 GROUP BY p.name, p.vendor_name ORDER BY downvotes DESC;

-- Queries with most negative feedback
SELECT query_text, COUNT(*) as votes,
       SUM(CASE WHEN signal = 1 THEN 1 ELSE 0 END) as up,
       SUM(CASE WHEN signal = -1 THEN 1 ELSE 0 END) as down
FROM v2_search_feedback GROUP BY query_text ORDER BY down DESC;

-- Comments for review
SELECT query_text, comment, signal, created_at
FROM v2_search_feedback WHERE comment IS NOT NULL ORDER BY created_at DESC;
```

## 6. Remaining Work

### Data Quality Fixes (Priority Order)
1. **Theodore Alexander** (top5, 2,507 products) — Re-scrape to capture descriptions
2. **Precedent Furniture** (top5, 406 products) — Re-scrape to capture image URLs
3. **Essentials for Living** (top10, 408 products) — Re-scrape to capture images
4. **Chelsea House** (1,944 products) — Scrape descriptions
5. **Merge "Sarreid" + "Sarreid Ltd"** — Deduplicate vendor entries

### Search Quality Improvements
1. **Contextual enrichment** — Run LLM-generated descriptions for all products (especially those with NO-DESC). This dramatically improves embedding quality.
2. **Re-embed after enrichment** — Products with better descriptions will produce better embeddings
3. **Query intent extraction** — Have Claude identify the primary item type before searching, to avoid the "ottoman" keyword pollution issue
4. **Deduplication** — The Bramble Co "Kraton" console appears twice with different category tags
