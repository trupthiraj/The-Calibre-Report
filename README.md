# ⌚ The Calibre Report

> *What 280,000 luxury watch listings reveal about brand power, price architecture, and market positioning*

---

## The Hook

There is a particular kind of rabbit hole that opens up when you spend enough time with luxury watch data. It starts innocently — a dataset, a question, a curiosity about whether prestige is actually measurable. And then somewhere around the third hour of reading about the difference between a Patek Philippe grand complication and an Audemars Piguet Royal Oak, you realise you've developed opinions. Strong ones. About brands you couldn't have named a month ago.

This project is an attempt to do something the watch world has never done: put a number on prestige. Not the price tag — anyone can read a price tag. The *architecture* behind it.

---

## What Makes This Different

Most watch data analyses do three things: average price by brand, a histogram, maybe a price prediction model. That's the entire ceiling of what's out there.

This project does something different. It builds a **Prestige Index from scratch** — a composite scoring system that ranks brands not just by price, but by price consistency, market scarcity, and price ceiling. Then it uses that index to answer questions nobody else has asked of this dataset:

- Which brands use their price range as a velvet rope — and which use it as a ladder?
- Does scarcity actually drive prestige, or do we just assume it does?
- What does it actually cost to get in the door of each brand on the resale market?
- Which brands are punching above their weight — and which are coasting on name recognition?

---

## Key Findings

1. **Richard Mille scores 0.9437 on the Prestige Index** — the next closest brand, A. Lange & Söhne, scores 0.300. That 0.6437 gap between first and second place is not a rounding error. It reflects a brand that has made a deliberate, decades-long decision to occupy a category of one. Their median resale price is $287,000. Their 90th percentile is $547,100. They have 750 listings on the world's largest watch marketplace. Every one of those numbers is a choice.

2. **Rolex lands in Accessible Luxury — and that's the most interesting finding in the dataset.** The most recognised luxury watch brand on earth sits in the third tier of the Prestige Index, below Sinn, Vacheron Constantin, and Hublot. Not because Rolex isn't prestigious, but because the data captures something the watch world already knows and rarely admits: Rolex built the most powerful collector on-ramp in horology. A $5,000 entry price. A $14,670 median. 68,798 resale listings. Being accessible at that scale isn't a weakness — it's the entire strategy, executed over decades, working exactly as intended.

3. **Cartier sits in the Aspirational tier** despite being one of the most recognised luxury names on earth. The secondary market is honest in a way that brand marketing is not. Cartier sells a lot of watches to a lot of people at a lot of price points. Their median resale price is $5,768 and their prestige score is 0.1183. The market has priced in that breadth. This isn't a criticism of Cartier — it's a description of their strategic choice to be a luxury brand for many rather than an exclusive brand for few.

4. **Patek Philippe and Audemars Piguet both run deliberate ladder strategies.** Their violin plots show a characteristic shape: a fuller body in the mid-range with a long right tail reaching into the stratosphere. Entry complications anchor the accessible end. Grand complications and iconic models — the Nautilus, the Royal Oak — anchor the prestigious end. The shape of their price distribution is the shape of a promise: give collectors somewhere to start, and somewhere to aspire to.

5. **Sinn scores Ultra Luxury with a median price of $2,731.** This is the finding that will surprise people most — and it's defensible. The Prestige Index rewards price consistency and market discipline, not just expense. Sinn's obsessively controlled pricing and minimal secondary market volume put it in the same tier as Patek Philippe and Audemars Piguet. The data is saying: being deliberate about positioning matters as much as being expensive. That's a lesson every luxury brand strategist should read twice.

6. **The entry price for a Richard Mille on the resale market is approximately the median price of a Patek Philippe.** The 10th percentile Richard Mille listing costs more than the typical Patek Philippe. At some point, the price stops being about the watch and starts being about what owning it communicates. The data doesn't judge that. It just shows you where the line is — and exactly how far above everyone else that line sits.

7. **Prestige and scarcity are related but not the same thing.** Patek Philippe has 10,645 listings and a prestige score that most brands would restructure their entire business to achieve. Sinn has 671 listings and a price point that won't retire anyone early. The bubble chart makes this argument visually — two very different paths to the same tier, two very different brand philosophies, the same data-driven conclusion.

---

## What a Luxury Business Should Do With This

**Pricing teams** should be tracking price consistency scores across competitors — not just median prices. A brand with erratic pricing is leaking positioning signals it almost certainly doesn't intend to send. Consistency is a prestige signal the market reads whether or not you're aware you're broadcasting it.

**Marketplace platforms** like Chrono24, Watchfinder, or WatchBox should be using prestige tier segmentation to personalise the discovery experience. A customer browsing Richard Mille and a customer browsing Longines are not the same customer having the same moment. Treating them identically is a missed opportunity the data makes embarrassingly obvious.

**Brand strategists** entering or repositioning in the luxury watch space should study the entry-to-median gap obsessively. The brands with the longest collector ladders — the widest gap between entry price and median price — have the most durable customer relationships. Getting someone into the brand at $5,000 and giving them somewhere to go at $50,000 is not a pricing strategy. It is a retention strategy disguised as a pricing strategy. Rolex figured this out. Everyone else is still catching up.

---

## Project Structure
```
calibre-report/
│
├── calibre_report_analysis.ipynb    ← Full analysis notebook
├── TheCalibreReport.html            ← Standalone HTML export
│
├── chart1_price_architecture.png    ← Price range by brand
├── chart2_prestige_leaderboard.png  ← Prestige Index rankings
├── chart3_price_violin.png          ← Price distribution shapes
├── chart4_entry_point.png           ← Entry price vs median
├── chart5_scarcity_prestige.png     ← Scarcity vs prestige bubble chart
└── chart6_model_families.png        ← Model family price positioning

```
---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core analysis |
| pandas | Data manipulation and cleaning |
| Plotly | Interactive charts |
| Seaborn | Statistical visualisation |
| scikit-learn | K-means clustering and normalisation |
| Jupyter Notebook | Development environment |

---

## Data Source

**Luxury Watch Listings** — 280,000+ listings scraped from Chrono24, the world's largest luxury watch marketplace.

🔗 [Dataset on Kaggle](https://www.kaggle.com/datasets/philmorekoung11/luxury-watch-listings)

---

## What I Learned

Building a custom scoring metric is harder than it looks — and more interesting than anything a pre-built model would have given me.

The first version of the Prestige Index put Sinn above Patek Philippe and Rolex in Aspirational. That was wrong — and figuring out *why* it was wrong taught me more about the data than the correct version did. The issue was that scarcity was doing too much work. A brand with 671 listings was being rewarded the same way a brand with genuine ultra-high pricing was. Three iterations of weight adjustments later — shifting from listing count as a primary signal to a supporting one, and switching from median price to 90th percentile price as the ceiling measure — the leaderboard made intuitive sense. That process of questioning why the model was wrong, understanding the mechanics well enough to fix it, and being honest about the assumptions baked into every weight — that was the most valuable part of this project.

I also learned that missing data tells its own story. Movement type was missing in 69% of rows — not because the data was poorly scraped, but because marketplace sellers fill in what they feel like filling in. A seller listing a $400,000 Richard Mille doesn't need to tell you it's mechanical. You already know. The absence of data in luxury contexts is often a signal, not a gap.

The 14,259 "Price on request" listings were the most interesting exclusion. Each one represents a watch too expensive — or too exclusive — to list publicly. Removing them was analytically necessary. But it also means every price figure in this analysis is conservative. The real ceiling of this market is higher than what the data shows. That's worth sitting with.

Finally: the Prestige Index is one framework, not the framework. A different weighting would produce a different leaderboard. That's not a flaw — that's what makes it a conversation starter rather than a verdict. The goal was never to settle the debate about which brand is most prestigious. The goal was to make that debate more interesting than a bar chart of average prices. I think it did that.

---

## About

Built by **Trupthi Raj** 

📁 [GitHub](https://github.com/trupthiraj)
📊 [Tableau Public](https://public.tableau.com/app/profile/trupthi.raj/vizzes)
