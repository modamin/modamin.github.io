# Designing a Lakehouse That Teams Actually Use

*Published: 12 September 2026 — by Mohamed Amin*

A lakehouse is easy to stand up and hard to keep useful. The technology decisions
are rarely what make or break the platform; the operating model around it is.

## Start from the questions, not the tables

Before modelling anything, write down the handful of business questions the
platform has to answer in its first six months. Everything in the bronze, silver
and gold layers should trace back to one of them. If a dataset cannot be linked
to a question someone is waiting on, it can wait too.

## Keep the layers honest

- **Bronze** — raw, append-only, no business logic. It should be reproducible
  from the source system alone.
- **Silver** — cleaned, conformed, de-duplicated. This is where data quality
  rules live and where lineage matters most.
- **Gold** — business-facing models shaped for consumption, owned by the teams
  who use them.

The most common failure mode is business logic leaking into bronze, which makes
reprocessing history impossible.

## Govern early, lightly

Access control, classification and ownership are much cheaper to apply while the
platform is small. Assign an owner to every gold dataset, document what it means
in one paragraph, and make that paragraph discoverable from the tool people
actually query with.

## Measure adoption, not volume

Rows ingested is a vanity metric. Track how many distinct people query the gold
layer each week, and how many reports were retired because the platform replaced
them. Those two numbers tell you whether the investment is landing.

---

*This is a sample post. More writing coming soon.*
