KEISAKU - BETA TESTER GUIDE
===========================

Keisaku watches your Sierra Chart trading while it happens. It reads Sierra's
own trade logs on this PC, keeps a live session dashboard, and sends a Windows
notification when your trading starts to look like tilt: losing streaks,
re-entering too fast, giving back a good day, or trading too much.
If you arm it, it can also switch Sierra Chart into simulation mode when you
hit a limit you set.

It never places, changes or cancels an order. It sends none of your trading
data anywhere.

Using Keisaku means you agree to its beta license, LICENSE.txt in the
Keisaku folder. In short: it is for your own use only, don't share or copy
it, it isn't financial advice, and it can be wrong or fail, including the
lockout, so it is never your only risk control.


FIRST RUN
---------
1. Run Keisaku-Setup-<version>.exe. Windows may say "Windows protected your
   PC", because the beta installer isn't code-signed yet. Click "More info",
   then "Run anyway".
2. At the end of the install, Keisaku Settings opens in your browser. Work
   through the steps:
     Sierra Chart    - usually found automatically (C:\SierraChart)
     Accounts        - pick the account you trade as "Main"
     Instruments     - enter what your broker or firm charges per contract, per side
     Loss limits     - your daily loss limit and the lock rules
     Alerts          - send a test alert to check notifications get through
     Tape            - optional screen recording, so you can watch each trade
                       back. Off unless you turn it on. Sierra's window only,
                       never leaves your PC, about 1 GB an hour, old days deleted.
     Safety          - the lockout starts OFF. Leave it off for your first week.
     Your history    - "Save and measure my history". Keisaku reads every
                       session in your logs (a few minutes) and tunes itself
                       to YOUR trading. Then pick how early alerts should
                       speak: each level is shown replayed over your own days.
     About you       - your size, and what tends to go wrong for you. Pre-filled
                       from your history; "Save and update my model".
     Finish          - Save, then "Start with Windows, and start now"
   If Keisaku can't find your trade logs, use "Browse for the trade logs" on
   the Sierra Chart step and pick Sierra's TradeActivityLogs folder.
3. Trade as normal. Open Keisaku (Start menu or desktop) at any time.

Keisaku ships with nothing from anyone else's trading in it. Until it has
measured at least 10 of your sessions it runs on neutral starting values and
doesn't compare you with "your usual". After every session closes it measures
your history again, so it keeps up as you change.


OPENING KEISAKU
---------------
One icon, "Keisaku", in the Start menu (and on the desktop if you kept that
box ticked). It opens Settings until setup is finished, then the dashboard.
Every page has the same bar across the top:
  Dashboard   the live session dashboard
  Reports     a report for every session and every week, against your own
              history. Written automatically after each close.
  Tape        watch each trade back as a clip (turn recording on first)
  Settings    change anything you set up, see what is running, turn it off.
              Frozen while a lock is on.
and, beside them, whether Keisaku is running, whether your locks are on or
holding Sierra right now, your alert level and when the data last updated.
Hover any of those for the details.

Updates: when a new version is published Keisaku tells you, on the bar and
in Settings, and installs it in one click. Your settings are kept.


THE LOCKOUT (read this before arming it)
----------------------------------------
Once armed, a lock rule that fires switches Sierra into Global Trade Simulation
Mode, so new orders go to the simulator and not your live account. Keisaku
holds it there for as long as the rule says. If you switch back to live early,
it switches back to sim again.

- Arm it only after a week of alerts, once you've seen in Settings -> Locks
  when the rules would have fired.
- Test it first on a sim or evaluation account.
- While a lock is held, and for the rest of that session after one fires,
  Keisaku Settings is read-only. That's deliberate.
- Your broker's or prop firm's own limits still apply. Keisaku doesn't
  replace them.
- If you practise on Sierra's simulator (Sim1 and so on) rather than a live or
  evaluation account, choose "Sierra's simulator" on the Accounts step.
  Keisaku then reads your simulated trading (Chart Replay trades are left
  out). To use locks there, pick a second sim account as your lock account: a
  lock moves every chart to it until the lock ends. Try one on a quiet day
  before relying on it.


STOPPING KEISAKU (and getting out of a lock if something goes wrong)
--------------------------------------------------------------------
Keisaku runs in the background as pythonw.exe, started by a Windows
scheduled task called "Keisaku". Hover "Keisaku running" on the bar to see
its process ID (pid) and, for your lock strength, how to stop it.

How to stop it depends on the lock strength you chose in Settings -> Locks:

  Easy     Settings -> Status -> "Turn Keisaku off" (type the word it asks
           for). This works even during a lock: it ends the lock and puts
           Sierra back to live.

  Firm     With no lock on: Settings -> Status -> "Turn Keisaku off".
           During a lock Settings is frozen, so:
             1. Open Task Manager (Ctrl+Shift+Esc) -> Details tab.
             2. Find pythonw.exe with the pid shown in the hover, and click
                End task. (There are several pythonw.exe processes: the
                recorder and the pages are the others. The pid is the one.)
             3. In Sierra Chart: Trade menu -> turn off Trade Simulation Mode.
           The Keisaku task starts it again at your next Windows sign-in.

  Strong   Ending the process in Task Manager won't work: a second process,
           "Keisaku Guard", starts it again within about two seconds (and
           Keisaku restarts the guard). So:
             1. Open Task Scheduler (Start -> type "Task Scheduler").
             2. In Task Scheduler Library, right-click "Keisaku" -> Disable,
                and do the same for "Keisaku Guard". Then right-click each
                one -> End.
             3. In Sierra Chart: Trade menu -> turn off Trade Simulation Mode.
           To turn it back on later, Enable both tasks again (or open
           Keisaku Settings -> Status and start it).

Whatever the strength, every lock ends by itself at the 17:00 ET close, and
uninstalling Keisaku removes all of it. Keisaku never hides a process.


UPDATES
-------
Keisaku checks for a new version about twice a day. When one is out, the
control panel and Keisaku Settings say so and offer to install it. Updating
keeps all your settings and history.


WHERE THINGS ARE
----------------
Everything is in %LOCALAPPDATA%\Programs\Keisaku:
  .env                      your settings (Keisaku Settings writes this)
  keisaku\lock_rules.json   your lock rules
  keisaku\trader_profile.json  what Keisaku measured on your history
  keisaku\reports\          your session and week reports
  keisaku\logs\             the watcher's log. Send it along with a bug report.

Tape recordings are in %LOCALAPPDATA%\Keisaku\recordings unless you chose
another folder in Settings. Uninstalling does not delete them.

Uninstalling removes the program but keeps your settings and history, so a
reinstall picks up where you left off. Delete the folder to remove everything.


REPORTING A PROBLEM
-------------------
Send: what you saw, the time it happened, your Keisaku version (shown in
Keisaku Settings and the control panel), and keisaku\logs\pnl_watcher.log.
