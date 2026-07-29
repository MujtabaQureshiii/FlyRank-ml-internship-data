## Voice Card

Direct, clear, practical, honest, no buzzwords.

---

# Structured Content Archetype Clustering
### FlyRank AI Internship Capstone

## The Problem

FlyRank's content inventory has a large number of pages, and reviewing them one by one to understand performance is slow. Going page by page also makes it hard to notice patterns across the inventory. Reviewers can end up spending time on pages that are already performing fine, while groups of pages with the same underlying issue go unnoticed.

The goal of this project is to see whether content pages naturally form groups based on how they perform in search, so that content reviewers and SEO analysts can look at the inventory in groups instead of one page at a time. The intended use is to make the first step of a content review more organized: reviewers would look at what a group has in common and decide where to focus first, rather than starting from scratch on every page.

This is not meant to replace reviewer judgment. It is meant to support it.

## What I Did and Decided

**Framed it as an unsupervised clustering task.** There is no existing label that tells us which performance archetype a page belongs to, so this isn't a classification or scoring problem. The research question — what performance archetypes exist across the content inventory — is exploratory by nature, which is why clustering fit better than a predefined structure.

**Defined the unit of analysis as one content page**, working with an anonymized dataset of roughly 30,000 pages.

**Started with two features: impressions_90d and CTR.** Impressions represent visibility (how often a page shows up in search), and CTR represents engagement (how often people click when they see it). I chose to start with just these two instead of adding more variables right away — features like average position or clicks could be useful later, but clicks in particular overlap heavily with impressions and CTR. I wanted a small, understandable baseline I could actually inspect before adding complexity.

**Chose clustering over fixed rules.** A rule-based approach (something like flagging pages with low CTR and high impressions) would require picking thresholds before understanding how the data is actually distributed. Those thresholds are arbitrary, and pages sitting close to a cutoff could land in different buckets even though their performance is nearly identical. Clustering lets the groups come from the actual relationship between impressions and CTR instead of a guess at where the lines should be.

**Selected silhouette score as the initial technical metric**, using 0.40 as an initial benchmark — though I decided that the final judgment can't rest on that number alone. A cluster with a good score that reviewers can't understand or use isn't actually useful.

**Worked through the data risks before modeling.** I identified several issues I need to handle: impressions may be heavily skewed, which I will confirm during data exploration, with a small number of pages getting far more visibility than the rest, which may call for a log transformation. CTR is unstable for low-impression pages, since a handful of clicks can make CTR look unusually high or low. And there's a tradeoff between the number of clusters and how easy the result is to explain — different cluster counts may produce better technical scores while making the groups harder to explain.

## What Came of It

As of now, this project is still in progress. The clustering model has not been trained or evaluated yet, so I'm not claiming any results from it.

What I can say honestly is that I've taken a broad, hard-to-manage content review problem and turned it into a clearly defined machine learning task: I know who it's for, what one row represents, what features I'm starting with and why, why clustering is the right approach for this stage, and what "useful" needs to look like beyond just a good score. I've also reviewed the dataset structure and thought through the main data risks in advance, so the modeling stage isn't starting blind.

Next steps are to inspect the data for missing values, duplicates, and the shape of the impressions distribution; scale the features; run K-Means across a range of cluster counts using silhouette score and the elbow method to narrow it down; and then check whether the resulting groups actually make sense in terms of average impressions and CTR, not just the score. After that, I'll test whether adding another feature improves the clusters without making them harder to explain, then name the clusters, check their stability, and document the limitations.

I'm not claiming final archetypes, a specific silhouette score, or any improvement to reviewer efficiency or search performance — those would be getting ahead of the work that's actually been done.

---

## Short Bio

I'm a software development student completing a machine learning internship at FlyRank AI. My background is in Core PHP, ASP.NET Core MVC, SQL, databases, Flutter, and web development. Through this internship, I'm learning how to take a real, messy problem and frame it as a machine learning task — deciding what data to use, what approach fits the question, and what a model's output actually needs to do for the people using it. I'm still early in this process and treat each project as a chance to build that judgment, not just to apply a technique.

---

## Contact / CTA

I'm looking for internships, junior development roles, and practical machine learning projects where I can keep building on this kind of work. If you're looking for someone who takes the time to frame a problem properly before jumping into a solution, feel free to reach out.

---

## Before and After

**Generic AI line:**
"I leveraged advanced machine-learning techniques to unlock actionable insights and optimize content performance."

**Edited version:**
"I used impressions and CTR to explore whether content pages form useful performance groups."

The edited version is better because it says exactly what was used and what was actually being tested, instead of relying on vague phrases that could describe any project and don't tell the reader anything real.
