# Keisaku changelog

What changed in each version of Keisaku, newest first.

<!-- For the developer: the version lives in keisaku/VERSION, and
`packaging/release.py bump` adds a section here. `release.py publish` copies the
top section into the GitHub release notes (testers see it in the update pill)
and puts this whole file on the release repo, so every line is written for the
trader: what changed for you, not which function moved. -->

## 0.1.6 — 2026-09-30

- **Keisaku is now installed as compiled code.** The program files in the
  Keisaku folder are no longer readable scripts. Nothing changes in how it
  works: the same dashboard, alerts, Coach, locks, Tape and reports, and every
  setting you've saved is kept.
- **Notifications have a new name inside Windows.** Keisaku now registers
  itself as "Keisaku". If you had turned Keisaku's notifications off or down in
  Windows Settings, check them once after this update. If you pinned Keisaku
  to the taskbar, pin it again from the Start menu.
- **Your early tell, week by week.** Trading History › Your early tell now
  draws how much worse the rest of your day went on the tell's side, as a
  rolling four weeks stepped each week, instead of one bar per calendar month.
  A single week holds too few sessions to split, so each bar covers four.
- **Clearer "lately" tags.** On your Coach and early tell, a tag getting better
  is green with an up arrow, getting worse is amber with a down arrow, and "lock
  may be hiding it" is purple. With too few recent sessions it says "too few
  lately to tell". The before and lately figures sit on separate rows, and only
  one hover card opens at a time.

## 0.1.5 — 2026-09-30

- **Updates reach you even if your PC is off after the close.** Before, a new
  version installed itself only while the market was closed. Now it can also
  install during the session, but only in a pause: you're flat, no orders are
  working, no lock is on, and you haven't traded for 30 minutes. It takes
  about a minute and keeps every setting.
- **New versions show up sooner.** Keisaku checks for them every hour, and the
  update pill finds out within 3 hours instead of 12.
- **The old "classic" dashboard is gone.** Its link has been removed, and its
  old address now opens your dashboard.

## 0.1.4 — 2026-09-30

- **Accounts from more brokers and prop firms.** Keisaku now recognises how each
  trading service in Sierra names its contracts: Rithmic (used by nearly every
  prop firm), Teton, CQG and Interactive Brokers. Before this, only Rithmic's
  names were read.
- **If Keisaku can't read an account's trades, it tells you.** Before, an
  account whose log it didn't understand just looked like a day with no
  trading, with no alerts and nothing for the lock to judge. Now Settings ›
  Accounts marks it in red, and the dashboard shows a warning.
- **"Check the log" button.** On that warning, it shows what Keisaku found in
  the log, ready to copy and send to the developer. It contains no account
  number and only a few sample prices.

## 0.1.3 — 2026-09-29

- **The Coach keeps up with how you trade now.** Your recent sessions count
  more when Keisaku decides what the Coach tells you. A habit you've fixed goes
  quiet, and a new one shows up sooner, without waiting months of history to
  confirm it. A pattern that has held all along keeps its line.
- **Keisaku doesn't take credit away from the lock.** When a pattern only looks
  better on days Keisaku stepped in and ended your session early, it isn't
  treated as fixed: the Coach keeps saying it.
- **Settings shows how each pattern has moved.** Your Coach and your tipping
  points carry a tag: *worse lately*, *improving lately*, *less lately* or
  *lock may be hiding it*. Hover it for the before and lately figures. Measure
  your history again to see them.
- **Your alerts and lock rules don't change.** When they fire is still judged
  on your whole history.

## 0.1.2 — 2026-09-29

- **Your limit and your risk are asked on Instruments now**, next to "Show
  results in". Trading History shows your results in R, so it needs to know
  what one R is first. Behaviour keeps the questions about what goes wrong.
- **No R figures before you've entered your risk.** Trading History used to
  show averages and best and worst days in R using a built-in guess of $60.
  Until you enter your own risk, it shows dollars. Check the "One unit of
  risk (R)" box on Instruments: if it says $60 and that isn't your risk,
  change it.

## 0.1.1 — 2026-09-29

- **Why "Measure again" is greyed out.** While Settings is frozen (a lock
  fired, or the session is down), Trading History now says so under the
  button, with the time it reopens. Nothing is missed: your history is measured
  again automatically after each weekday close, that day included.
- **Updates install themselves.** This is the first release delivered by
  Keisaku's own updater: the yellow pill, or on its own while the market is
  closed. It still finds an update when GitHub is limiting requests, and if
  GitHub can't be reached it says so rather than "no update".

## 0.1.0 — first beta

Keisaku learns from **your** trading, and from nobody else's.

- **Windows installer.** One `Keisaku-Setup-0.1.0.exe`, no Python needed, no
  admin rights. Unsigned for now: Windows shows "Windows protected your PC";
  choose More info, then Run anyway.
- **Beta license.** The installer asks you to accept it before installing, and
  a copy sits in the Keisaku folder as `LICENSE.txt`: your own use only, not
  financial advice, and no promise that the figures, alerts or lockout are
  always right.
- **Keisaku Settings, in order.** Connect Sierra Chart (or browse to your trade
  logs), pick your main and copier accounts and your main instrument, measure
  your history, and only then decide anything. On a first setup each step
  opens once the one before it is done. Open it again any time from the Start
  menu or the dashboard's **Settings** button.
- **Settings, redesigned.** A picture on Welcome of how Keisaku fits together,
  bigger and plainer descriptions, warnings you can't miss, and a tooltip on
  every row of the alert model. "Your history" is now **Trading History** and
  "About you" is **Behaviour**. Notifications live on the **Alerts** step,
  which recommends the minimum gap between alerts from your own sessions and
  shows the gap that will actually apply. The alert replay chart is easier to
  read.
- **Tape and Reports, in the same style as Settings.** One bar across every
  page, larger type, and dropdowns and tooltips that match. Settings shows
  "Saving…" over the page while it saves, and saves are quicker.
- **Are your alerts reaching you?** Settings → Alerts checks the three
  Windows switches that can hide one (notifications, Keisaku's own switch, Do
  not disturb), lets you allow Keisaku in one click, and checks again when
  you come back from Windows Settings.
- **A much deeper Coach.** Seven new things it checks your history for:
  opening into a dead market, a first hour that goes nowhere, trading with no
  direction and no range (right now, and as a share of your day), working a
  small range hard, cutting winners shorter as the day goes on, and trading on
  after a big loss. Each one speaks only if **your own** sessions show it costs
  you, in both halves of your history and beyond what chance produces, and it
  quotes your numbers. Every session also says how today's weekday ranks for
  you, and says plainly when that rank is not yet more than chance. Green lines
  now need proof too: a trade count is green only against your own tipping
  point, never just for being under your median.
- **A new dashboard**, in the same style as Settings, Tape and Reports. The
  market panel now reads as an answer: the verdict, what to do about it, then
  the three readings it came from, colour-coded, with every definition a hover
  away. Coach lines put what to DO right under the headline, in the line's
  colour. Your P&L line is blue above zero and red below. The behavioural risk
  chart is bigger, on a real time axis, with the alert bands drawn in. Hover
  anywhere on a figure's tile for what it means.
- **Behavioural risk, readable at a glance.** The ring shows where your own
  green and bad days peak, and once it cools off it still says how high
  today went. What's driving it is one line each, with the detail on hover.
- **Your early tell.** Keisaku checks a list of things you can know early in
  a session: how your first trades went, your first hour, a fast start,
  jumping back in after a loss, changing sides, sizing up, when you started,
  and how yesterday went. It checks each one against how the **rest** of your
  day went. If one of them has really predicted your days (in both halves of
  your history, and beyond what chance produces), the risk panel names it,
  for example "Your first trade · lost". It then shows how the rest of the
  day has gone on each side, and which side you're on today. If nothing has,
  it says so rather than guess. It works on a few trades a day, too. One
  reading is checked on its own first: how high your behavioural risk ran
  over your opening trades, which the developer's own research named before
  looking at your history.
- **Your whole history, every account.** Measuring your history now reads
  every account in your logs, including ones you hide from the dashboard, so
  hiding an old account no longer shrinks what Keisaku learns from. After
  updating, open **Trading History** and measure again.
- **A suggested stop, from your own winners.** The market panel shows the
  stop that has kept about 9 of 10 of your winning trades alive at today's
  volatility, once you have enough winners on one market to measure it.
- **A clearer Coach.** On a green day it no longer counts down "room left"
  to your daily limit. When a day goes past several of your tipping points,
  the first is said in full and the rest are listed together on one line.
  Your session scorecard adds the two tape rows (trades in a dead market,
  trades with no direction and no range) once your own typical figure for
  them is measured.
- **Reports keep up with the day.** A report for a session or week that
  hasn't finished says **In progress** and has an **Update now** button. The
  list of reports refreshes itself when you open it, so today's session
  appears without a manual run, and **Show file** opens the report in
  Explorer.
- **First setup picks your main account for you.** On a first run, the
  account you traded most recently becomes your main account and the rest
  stay unselected. Change it on the Accounts step if that's wrong.
- **Light, dark, or follow Windows**, from the button at the right of the top
  bar. One choice holds on every Keisaku page.
- **The dashboard's chart** is titled instrument first: "MNQZ6 pts · net".
- **Edge panel, easier to read.** Heat, run and "the stop that keeps 90%"
  are in your instrument's points whatever units you picked, because that is
  how you place a stop; R is underneath. Max drawdown is in dollars. A new
  **Left per winner** tile sits beside Left on table: the total grows with
  how many winners you had, so a busy day looked worse than it was. The (i)
  by the panel's title says which instrument it covers and what 1R is.
- **Tape recordings you can find.** Each day's folder now holds just
  "Full tape 09.25-16.20 ET.mp4" and a **Trade clips** folder with files named
  by time, trade and result; the working files are hidden. Folder buttons on
  the Tape page open them in Explorer. If recording stops and starts (a
  restart, a shutdown), the pieces play as one session with the gap shown.
- **Keep my trades is the default.** Once a session is older than your keep
  days, Keisaku keeps a clip of every trade, alert and lock and deletes the
  full video. Switching from Keep everything leaves the sessions you already
  have whole; a **Cut them down to my trades** button on the Tape step does
  that when you choose to.
- **Simpler recording hours.** Cash session (09:25-16:20 ET) or full session
  (18:00-17:00 ET). Either way Keisaku records only while Sierra Chart is open.
- **The Tape pauses while a lock holds.** A minute after a lock takes the
  platform, recording stops, so the moment the lock spoke is still on the
  Tape. It starts again as soon as the lock lifts, whether the lock ran out or
  you turned it off. Sim mode you set yourself keeps recording.
- **Alert and Tape settings still save during a lock.** Your limits stay
  frozen for the rest of the session once a lock fires, but you can change
  alert and recording settings. Alert changes wait while a lock is holding,
  so saving one can never end a lock early.
- **Where your trading starts costing you.** Keisaku reads every session and
  shows the points after which your day has gone on to get worse (so many
  trades in half an hour, so many dollars down, so many losses in a row), each
  measured against your other sessions at the same time of day. You answer
  each one "That's me" or "Not really", plus your size, risk and plan.
- **Your Coach, tested on you.** Keisaku checks 37 common intraday problems
  against your own sessions: overtrading, flipping long and short, giving back
  a green day, losing runs, fast re-entries, trading a dead market, going up in
  size, a red first hour, the day after a red or a big day, your weakest
  weekday and half hours, how soon you get back in after a loss or a win,
  trades past your usual count, and more. Trading after a loss is not bad in
  itself: Keisaku only warns when YOUR history shows that getting back in
  within a certain time costs you, and then tells you how long to wait. The Coach speaks, live, only about the ones your
  history shows cost you: in both halves of it, and beyond what chance alone
  produces. Works at one or two trades a day as well as at a hundred.
  **Your history → Your Coach** lists every one, what it found, and a switch to
  silence any line.
- **Practising on Sierra's simulator.** If you trade Sim1 (or any sim
  account) rather than a live or evaluation account, Keisaku now reads your
  simulated trading: the same dashboard, alerts, Coach and report. Settings
  looks at your logs, recommends **Live** or **Sierra's simulator** on the
  Accounts step and tells you why; you confirm it. A `SIM` tag on every page
  keeps screenshots honest. Locks work on the simulator too: pick a second sim
  account as your **lock account** and a lock moves every chart there until it
  ends (trades placed there never count as your session). Settings shows how
  to add that account in Sierra and **checks that Sierra really lists it**
  before you move on. Chart Replay trades are left out of your days.
- **Accounts, explained where you choose.** An (i) beside **Role** says what
  each role actually changes, and one beside **Daily loss limit** says that a
  blank box uses the limit you set in the Behaviour step.
- **Results in R, $ or points.** Choose under **Instruments**. R (the
  default) reads the same on every instrument; the dashboard's edge panel and
  Settings both follow it. Each instrument is judged against its own R.
- **Alerts you can see before you choose.** Pick any of your sessions and see
  exactly when Keisaku would have spoken, with the recommended settings and
  with yours. One dial (Off, Less, Normal, More, A lot more) and a switch per
  warning sign. **Off** means no alert notifications at all.
- **Locks in plain words.** Ask whether to stop, a short forced break, your
  daily limit, a losing streak, trading too much, giving back a green day.
  Each has a **No**, a reason in your own numbers and how many of your sessions
  it would have fired on. Locks switch Sierra into simulation; turning them on
  takes a typed word, and Settings are frozen while a lock is on.
- **How firm a lock is, your choice.** **Easy**: turning Keisaku off ends a
  lock. **Firm**: it can't be turned off from Settings while a lock is on.
  **Strong**: even ending Keisaku in Task Manager doesn't help, because it comes
  straight back and the lock carries on. The way out of Strong is in the
  Settings page, and every lock ends at the 17:00 ET close.
- **Just track my days.** A lightweight setup with no history sync: the
  dashboard is your trading journal (trades, P&L, stats, Tape, reports), and
  the panels built on your history say what they need until you sync.
- **You choose how much history to read** (90 days, 180, a year, or all)
  before anything is synced, so years of logs can't stall the first run.
- **Every lock rule is its own rule** and can do any of the five things: warn,
  ask, sim for a few minutes, sim until a time, or end the day in sim. Add any
  kind with **+ Add**, remove any with the bin. Give-back can be dollars or a
  percentage, and only starts once a day is worth defending (at least 2R).
- **Trades in the session.** Your own plan for how many trades a day is enough:
  stack as many steps as you like, "5 trades: warn me", "10 trades: end the day
  in sim". A give-back rule may now take the platform too, if you choose.
- **One bar across every page** (Dashboard, Reports, Tape, Settings) showing
  Keisaku's live status wherever you are: running or not, locks on (green),
  off (amber) or LOCKED with the rule and a countdown, the alert level, the
  Tape, whether market data is arriving (green), stalled (amber) or the
  market is closed, and when the dashboard last updated. The bar also says
  where you are: the session you are looking at, or the Settings section. Hover any
  of them for the details, in a small terminal panel; click to change it.
- **Everything about locks in one place**, Settings → Locks: where Sierra
  stands right now, how far each account is from each rule, the padlock, and
  the rules themselves.
- **Updates install themselves.** When a new version is out, a yellow pill in
  the bottom-right corner installs it in one click. If you leave it, Keisaku
  installs it by itself once the market closes. It never updates while a lock
  is on or you're in a position, and it checks every download before running
  it. Your settings are kept. Turn the automatic part off in Settings → Status.
- **One Keisaku icon** in the Start menu, and on the desktop if you keep that
  box ticked. It opens Settings until setup is done, then your dashboard.
- **A Coach that knows you**: "past your tipping point", today against your
  usual (flips, re-entries, dead tape, scratches, capture), a hot opening,
  your weakest weekday, all in your own numbers. The scorecard scores every
  row, and the Environment panel shows its reading banner on NQ and ES.
- **Your dashboard, about you.** Coach lines, references, the Environment panel
  (NQ | ES) and every alert are measured on your own sessions. ES traders get
  the ES tape read on its own measured bands.
- **Reports.** Every session and week, written after the close, one click from
  the dashboard.
- **Keisaku Tape** (off until you turn it on): record Sierra Chart's window and
  watch every trade back as a clip. The files never leave your PC.
- **Your own commissions.** Every dollar figure is net of what you pay.
- **Status**, the last Settings step, is Keisaku's control panel: whether it is
  running, a switch each for alerts, locks and the Tape (locks still ask for
  their typed word), an edit shortcut beside each, and one **Turn Keisaku off**
  that stops everything, offered only while there is something to stop. Closing the windows doesn't
  stop Keisaku, and the page says so plainly. Saving only changes what you
  changed.
- **Running beside another Keisaku.** If one already runs on your PC, this copy
  can run beside it with its own tasks, and can never lock anything.
