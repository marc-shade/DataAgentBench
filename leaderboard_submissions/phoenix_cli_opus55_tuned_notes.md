# Phoenix-CLI tuned: every note in the prompt

Each run's system prompt is the base prompt of our untuned entry #114 (sha256 prefix `b03507acbcf5`), then `common.md`, then its dataset's note (`<dataset>.md`) if one exists, then its query's note (`<dataset>/queryN.md`) if one exists, each separated by a blank line. A query gets no note written for any other query. Every run's `isolation.json` lists the files it received with their sha256, and its `system_prompt_sha256` reproduces from the published runner and these files.

These are the v2 notes, used for all 270 runs. Earlier versions and an unused v3 candidate are in `runner_tools.tar.gz` in the release.

## `common.md` (every query), sha256 `8d37196e27692cfd5bfb0da9a1be0e70a0d3e46178caa61ec9935604f7641791`

```text
ANSWER DISCIPLINE
- Run every command in the foreground and wait for its result. Write the FINAL ANSWER
  only after all computation has finished.
- The FINAL ANSWER line carries the complete answer: every item of a requested list,
  each with every field the question asks for. Do not shorten a list to examples.
- Before concluding that an entity has no data, confirm it: a table or collection
  listing can be long, so count it or look the entity up by name directly.
```

## `stockmarket.md` (dataset stockmarket), sha256 `ad07770f1e2771d02650e3ec103aaf2143115b8089f431c8686225692be7375b`

```text
PRICE DATA
- Each security's daily prices are a table named by its symbol in the trading
  database. Get the complete table list, or query a candidate symbol's table directly;
  never treat a partial listing as the set of securities that have prices.
```

## `agnews/query2.md` (agnews query2), sha256 `593ced4afae0e318d58dfe8ea28ac7ebbe77e21e49f4e7074640b35ae8206e1d`

```text
CATEGORY LABELS (this dataset stores no category; you assign one per article)
- Label articles one at a time by reading each title and description yourself. Do not
  use keyword rules or a trained classifier for the articles the answer depends on.
- Every article gets exactly one of World, Sports, Business, Science/Technology, chosen
  by the story's main subject:
  - Business: companies as businesses (earnings, deals, mergers, layoffs, executives,
    lawsuits, share prices, IPOs), markets, the economy, trade, oil and prices. This
    holds when the company is a technology company: a story about a tech firm's
    results, deal or stock is Business.
  - Science/Technology: the technology or science itself: computing, software, the
    internet, products and how they work, security flaws and viruses, space, research
    and discoveries, health and medical science.
  - World: international affairs, politics, government, elections, conflict, crime and
    disasters, outside sport.
  - Sports: athletes, teams, games, leagues and sporting events.
- Label each of the qualifying articles in three independent passes (do not consult an
  earlier pass while labeling) and count each article under its majority label; if all
  three passes differ, re-read the article and decide.
```

## `agnews/query3.md` (agnews query3), sha256 `31876e5b209161183e3cb144a8dd2e06aec2d0f3fd4f2cbd6679616c530256c3`

```text
This question covers thousands of articles. Choose a method that finishes inside the
time budget; an answer computed on all qualifying articles is required.
```

## `crmarenapro/query12.md` (crmarenapro query12), sha256 `5ae4a5a48233616af0670afc3b0e46b546d4881c3d19aa7a4341efae3a52cc51`

```text
- An opportunity "closes" on its contract's company signed date (the end point the
  sales cycle policy defines). "In April 2023" selects opportunities whose company
  signed date falls in April 2023. Turnaround = days from the opportunity's created
  date to that signed date; average per owner (agent).
```

## `crmarenapro/query2.md` (crmarenapro query2), sha256 `4ce53fe077ed0ccab21df5a85bec06d843ea144d6f19f8b9bf5642635ca36d2d`

```text
- "Cost and setup" means the quote's pricing (line discounts) and its installation or
  setup terms. Which products a quote bundles is not what this question checks.
- The tiers in the Volume-Based Discounts article are unit quantities per line item,
  not dollar amounts: compare each line's discount with the tier its quantity reaches.
```

## `crmarenapro/query3.md` (crmarenapro query3), sha256 `3cde7b4991c5f6a3289119264a416c5f6dbdc47f059dd17badfdce841cf17d48`

```text
- The stage an opportunity's tasks represent is the stage of its most advanced task
  (stage order: Qualification, Discovery, Quote, Negotiation, Closed), counting every
  task on the opportunity whether or not it has started.
```

## `crmarenapro/query7.md` (crmarenapro query7), sha256 `14107cb7e484f6e7f3a8239305ee026d5b5b66b6770c20d0871ce4af71d8b4c7`

```text
- When the agent recommended a solution that a knowledge article covers, first check the
  conditions that article sets for offering it (eligibility, timing and validity
  windows). Breaking those conditions is the breach this question asks about.
```

## `crmarenapro/query8.md` (crmarenapro query8), sha256 `e2a44d7ca575cbb04ed6c96c991feac3a70e386cbadacec7ff175340ef40c0e1`

```text
- "Fewest transfer counts among agents who handled cases" ranks the agents that
  transferred at least one case in the window. An agent with zero transfers made no
  transfers to count and is not a candidate.
```

## `DEPS_DEV_V1/query1.md` (DEPS_DEV_V1 query1), sha256 `b41e1d0b1a6be66eef8841258ead825c96a753b376f128fba80b37fce4f86bb3`

```text
- A package name can contain ">" (a nested dependency path). Each distinct stored name
  is its own package; keep such names whole and in the ranking.
- When several packages tie at a rank, still name one concrete package (with its
  version) for that rank, and say that it is tied.
```

## `GITHUB_REPOS/query1.md` (GITHUB_REPOS query1), sha256 `face8387edbb12552c58c1cddbee3f6d84f2b1a5511b4a3afb39ad9d0a952a6f`

```text
- The repository's README.md files are the rows of the files table whose path is
  README.md (at any folder depth). A file's text is the contents row with the same id:
  join files.id = contents.id. Do not identify README files from contents.sample_path.
- Give the proportion as a decimal fraction (for example 0.25), followed by the
  numerator and denominator.
```

## `GITHUB_REPOS/query2.md` (GITHUB_REPOS query2), sha256 `66263b8e82a97dbed102d314bc28fcb06d5355df70a20ab0ac7bbec6ce4ff8d3`

```text
- Only files whose id appears in the files table qualify, as the question says; a
  Swift file found only in contents is not a candidate.
- The answer names the repository AND the file: its path, its id and its copy count.
```

## `googlelocal/query2.md` (googlelocal query2), sha256 `1b6e20acb779ebbbe6e2ee206321efa380e0a1963963a31f27fb1f148bc66f11`

```text
- A massage therapy business is any business whose name, category, description or
  reviews show that it provides massage or bodywork, whether or not its name contains
  the word "massage".
```

## `PANCANCER_ATLAS/query1.md` (PANCANCER_ATLAS query1), sha256 `6f1a3823d81663a91541abc7f842f618876d5b973fe13891effc9cd41dacc73c`

```text
- Report one average per histology type, keyed by the histology code as stored in the
  clinical data (the ICD-O-3 morphology code of the form NNNN/N), not by a type name.
```

## `PATENTS/query2.md` (PATENTS query2), sha256 `fa0d81612b44fbc8f4b1f4a8686883b3a71ea710d55c179be3808af9c3ffe406`

```text
- Exponential moving average per CPC group over consecutive filing years (years with
  no filings count as zero): the first year's value is that year's count, then
  EMA = 0.1 x count + 0.9 x previous EMA. If several years share the highest EMA,
  report the earliest.
```

