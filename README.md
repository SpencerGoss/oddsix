# Oddsix

A multi-sport data and prediction platform, live at **[oddsix.app](https://oddsix.app)**.
Designed, built and run by Spencer Goss. The source code is private; this repository documents the project.

<a href="https://oddsix.app"><img src="https://raw.githubusercontent.com/SpencerGoss/SpencerGoss.github.io/master/public/images/projects/oddsix-home.png" width="49%" alt="Oddsix home page"></a>
<a href="https://oddsix.app"><img src="https://raw.githubusercontent.com/SpencerGoss/SpencerGoss.github.io/master/public/images/projects/oddsix-team.png" width="49%" alt="Oddsix team page"></a>
<a href="https://oddsix.app"><img src="https://raw.githubusercontent.com/SpencerGoss/SpencerGoss.github.io/master/public/images/projects/oddsix-shotchart.png" width="49%" alt="Oddsix shot chart"></a>

## Features

- Live scores, standings and game pages for the NBA, NFL, MLB, NHL and soccer
- Team pages with strength ratings, recent form and advanced stats
- Career stats and game logs for about 57,000 players
- Historical record books for each league
- Model predictions for every game: win probability and projected score

## Architecture

```mermaid
flowchart LR
    A[League and odds<br/>data feeds] --> B[Ingestion and<br/>validation]
    B --> C[Feature<br/>engineering]
    C --> D[Prediction models<br/>per sport]
    D --> E[Data products<br/>and grading]
    B --> E
    E --> F[Static site build]
    F --> G[oddsix.app<br/>on Cloudflare]
```

- **Data:** league APIs and public odds feeds, ingested and validated continuously through the day
- **Storage:** relational databases and versioned data files, with large archives on Cloudflare R2
- **Models:** a separate model per sport, validated on seasons they were not trained on, with calibrated
  probabilities; predictions are graded publicly after each game
- **Front end:** Astro static site on Cloudflare Pages, with a single template serving the player pages
- **Quality:** thousands of automated tests run on every change

A new generation of models is being evaluated live this season.

## Stack

Python (pandas, scikit-learn, LightGBM) · SQL · Astro · TypeScript · Cloudflare Pages and R2

---

For information and entertainment only.
