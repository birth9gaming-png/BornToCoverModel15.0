# Born to Cover — Prototype 15

Your weekly list now shows up to **four distinct games per league**. It ranks usable, current projections by historical probability support and the lower win estimate with/without live adjustments. Negative EV does not automatically exclude a pick. Both spread and total remain visible, with the preferred market highlighted.

This is a reliability and data correction. The model has not demonstrated a 65–70% live win rate. The supplied cached CFB slate produces conservative estimates around 52–53%; those are limited model edges, not locks.

## Install

1. Extract `football_dashboard_prototype15.zip`.
2. Replace your app files with **every file inside `football_dashboard/`**, including the five new Python modules, requirements, config and preloaded artifacts.
3. Keep existing Streamlit Secrets, the app entry path and private cloud data. Reboot.
4. Confirm **Prototype 15** in the sidebar. Connected workspaces using the old NFL adapter receive a current-season refresh. Allow that background job to finish before treating NFL projections or scorer data as current.

Your trained recipe and historical datasets remain preloaded. There is no manual Apply Model step or ten-season training download. Artifact filenames retain `v14` because their fitted coefficients are unchanged.

## Review a game

Click **Review assumptions** or **View game and inputs** directly under its game card. The weekly list also has a **Review game** button for each pick.

The panel shows current and sensitivity-tested win estimates, final forecasts with/without the listed adjustments, injury players/statuses/sources/timestamps, wind, divisional context and matchup reasons.

- **Use forecast without these adjustments** saves a reversible choice for this game. It removes the injury/wind/unlearned-spot/fixed-division effects included in the sensitivity check. It does not remove every modeling assumption or certify a wager.
- **Restore automatic inputs** reverses that choice.
- **Refresh current game inputs** runs the current-season update and retains the other league and your historical models.
- **Correct a player status from a dated report** requires an actual source and publication time. Automatic corrections preserve existing player importance/role calculations, including defensive effects on the opponent. They are scoped to the game and expire after 24 hours or a newer report. Confirming a fact does not validate its assumed point value.

## Best available weekly picks

There is no minimum EV in the new shortlist. Current prices, a usable projection, current NFL statistics and a win estimate above 50% both with/without checked live adjustments are required. Fewer than four places remain unfilled if those checks fail; the exclusions explain why.

Reported recipe probability checks that beat the market comparator receive priority over weaker targets. Within that tier, the lower with/without win estimate ranks picks. Applied weekly corrections that pass later-week checks can gain that priority too. These historical comparisons precede production refitting and do not establish a live betting record.

On a Monday window spanning two NFL weeks, the list uses the next substantial upcoming slate instead of trying to fill four positions from one remaining Monday game. The board still exposes the Monday game, and the shortlist caption identifies its official week.

Buying points uses actual DraftKings/FanDuel alternate offers, on the same side selected from the main lines. Default limits are **three bought points** and **−150 or better**. Setup has an optional −150/−200/−300 price choice and an on/off control. No prices are invented. Alternate lines do not alter the model's consensus market reference. Up to eight provisional weekly games receive an event-level alternate-price lookup during a normal live refresh; source access and API quota apply.

The first displayed live weekly list is frozen and tracked separately in **Results & Learning**. Its actual prices determine hypothetical unit returns. Later reruns cannot rewrite that record after a result. The current board can change as new data arrives; the recorded first list remains identifiable.

## Anytime touchdowns

The NFL loader no longer lets a pending Monday game's week cutoff exclude completed Sunday games from later matchups. Statistics and player inputs use verified completed games available at the forecast time; completed cards keep their pregame inputs.

A snap sheet without completed game play-by-play cannot manufacture zero targets or zero TDs. Missing later-game coverage disables recency rules instead of treating an older zero-TD game as a new bounce-back opportunity. Byes and confirmed inactive games still skip correctly.

Featured scorers require current coverage, at least three recent active games, recent observed opportunities, recent and latest-game offensive snap shares, an eligible role and a current price. They rank by **market-implied TD chance and verified usage**. Market-implied chance includes sportsbook margin; it is not a calibrated model probability.

The existing xTD, red-zone and recency calculations remain in an explicitly exploratory section. They have not been validated as a TD pricing model, so their formula EV cannot rank the featured list or be advertised as a +100% betting edge. Out/doubtful players remain excluded, and final availability still matters. Every loaded upcoming NFL game is searched; there is no high-total gate.

## Saved data and validation

Your saved history, models, settings and frozen cards remain. Live CFB refreshes reuse known saved historical context instead of requesting those past annual responses again; current-season statistics and prices still refresh. Incomplete saved years retain their coverage limits.

Missing CFB season metadata is supplied on loaded games. Older frozen records can resolve a season from their pregame date for matching final scores; their predictions, picks and prices are not rewritten. Weekly learning still requires the existing sample-size and later-period checks.

See `audit_report_v15.md` for findings and practical limits, and earlier audit/validation files for the unchanged fitted recipe.

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
python -m unittest discover -s tests
```

**263 tests passed.** Real-browser checks covered the per-game review, reversible action, all six tabs and a 390-pixel mobile view. These checks verify software behavior, not betting accuracy.
