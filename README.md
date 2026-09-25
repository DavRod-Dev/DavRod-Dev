# David Rodriguez

I build financial data processes in SQL and Python — pipelines that load
public market and filing data, models that make it queryable and correct,
and analytics that say something true about it. I work with Claude Code
and treat it the way I'd treat a strong pair: it types and drafts, I decide
what to build, check every number, and own what ships.

Four repositories, each written from scratch for this profile, each with
tests and continuous integration you can inspect:

| repository | what it does | what it shows |
|---|---|---|
| [**market-data-warehouse**](https://github.com/davrod-dev/market-data-warehouse) | SEC EDGAR company facts → DuckDB, with dbt-style SQL layers, a point-in-time `facts_as_of(date)` macro, and 13 SQL quality assertions | data engineering: idempotent loads, versioned facts, restatement tracking, the discipline of asserting on real data |
| [**equity-fundamentals-sql**](https://github.com/davrod-dev/equity-fundamentals-sql) | the SEC bulk Financial Statement Data Sets — every US filer — loaded as four relational tables, with twelve analytical queries: Piotroski, Altman Z″, DuPont, sector percentiles, quarters derived from year-to-date filings, restatements, a no-look-ahead screen | SQL depth: window functions, QUALIFY, UNPIVOT, NULL-safe ranking, and twelve design notes on what 14 million real values taught the models |
| [**portfolio-risk-report**](https://github.com/davrod-dev/portfolio-risk-report) | daily prices → returns, drawdowns, three VaR estimators, Euler risk contributions, benchmark statistics → one self-contained HTML report with inline SVG charts | Python: pure, tested numerics (35 hand-computed cases), a bond total-return proxy from a yield series, no plotting dependency |
| [**finance-dashboards-powerbi**](https://github.com/davrod-dev/finance-dashboards-powerbi) | Power BI over the three repos above: a star-schema semantic model and a four-page report (fundamentals screen, company detail, portfolio risk, correlation/calendar), generated as a TMDL + PBIR project, exported as `.pbix` and PDF | BI: dimensional modelling, 54 documented DAX measures, pages that refuse to show a misleading aggregate, and CI that validates every visual's fields against the model |

[![market-data-warehouse ci](https://github.com/davrod-dev/market-data-warehouse/actions/workflows/ci.yml/badge.svg)](https://github.com/davrod-dev/market-data-warehouse/actions)
[![equity-fundamentals-sql ci](https://github.com/davrod-dev/equity-fundamentals-sql/actions/workflows/ci.yml/badge.svg)](https://github.com/davrod-dev/equity-fundamentals-sql/actions)
[![portfolio-risk-report ci](https://github.com/davrod-dev/portfolio-risk-report/actions/workflows/ci.yml/badge.svg)](https://github.com/davrod-dev/portfolio-risk-report/actions)
[![finance-dashboards-powerbi ci](https://github.com/davrod-dev/finance-dashboards-powerbi/actions/workflows/ci.yml/badge.svg)](https://github.com/davrod-dev/finance-dashboards-powerbi/actions)

## How I work

- **Real data before done.** Each repository was finished and green on a
  synthetic fixture first, then run against the real source — and every
  one of them broke somewhere. Those breaks are written up as numbered
  *design notes* in each README: a `segments` column that turned Walmart's
  gross profit negative, an 8-K comparative that erased Apple's 2013
  balance sheet, a capture ratio that compounded 1,300 up-days into
  nonsense. Fixed in the model, never by loosening the test.
- **Assertions over assumptions.** Data-quality checks are SQL files that
  return the rows that violate an expectation; zero rows passes, and a
  failure shows you exactly which company-year is wrong.
- **Explicit over clever.** Annualisation takes a periods-per-year, the
  risk-free rate is compounded not divided, and "latest" versus "as of a
  date" is a query the reader can see, not a default hidden in a loader.
- **Nothing hidden.** Every repository has a `CLAUDE.md` that states the
  conventions the tool follows and a plain account of what the tool did
  and what I did.

## Stack

SQL (DuckDB; standard enough to move to Postgres), Python 3.11+ (pandas,
numpy, requests, pytest), Power BI (TMDL, PBIR, DAX), GitHub Actions. Sources used here: SEC EDGAR
APIs and bulk data sets, FRED.

## Looking for

Roles building financial data processes — data engineering, analytics
engineering, or quantitative tooling — where correctness on messy real
data is the job. Open to conversations; the best way to reach me is
through the contact details on this profile.
