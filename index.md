# TTT Classic Privacy Policy

Effective 2026-11-05.

This policy explains what data TTT Classic (the "Game") can send to its developers, what it does not send, and what you
can do about it. "We" and "us" means the TTT Classic developers. You can reach us at gss.crazydog@gmail.com.

## In short

- We can receive three kinds of data from the Game: crash reports, diagnostic data and feedback.
- Each one is your choice. Crash reports are sent only if you say yes when the Game crashes. Diagnostic data is sent only
  if you turn it on. Feedback is sent only when you press Send.
- Saying no to any of them does not change the Game in any way.
- We never receive your name, Steam ID or voice. We do not sell data or use it for advertising.
- Everything is deleted after 30 days.

## Crash reports

When the Game crashes, it asks whether to send a report. If you choose No, nothing is sent to us. Turning diagnostic data on
or off does not change this, you are asked at each crash.

**What a report contains.** A crash report includes a minidump, which is a snapshot of part of the Game's memory at the
moment of the crash, plus technical details such as the Game version, your operating system and the modules loaded in the
Game, and the Game's state listed under [State sent with everything](#state-sent-with-everything). We do not deliberately
include your name or Steam ID, but memory contents can sometimes include personal information, such as the names and chat
of players on the server you were on.

**How long we keep it.** The minidump is deleted as soon as it has been processed into a crash event. We keep the crash
event for 30 days, then it is deleted.

## Diagnostic data

The Game asks once whether you want to send diagnostic data. It is off unless you say yes. You can change your answer at
any time in TTT Settings, under Interface (the console variable `ttt_diagnostics`), and the change takes effect
immediately.

**What it contains.**

- Performance and stability, such as frame times, memory use, map loading times and whether the Game last closed normally.
- How features are used, such as how you found a server, and whether voice chat, Workshop items and other features started
  correctly.
- Error messages from the Game about those features, with file paths and similar details removed.
- Reports that the Game stopped responding, with a list of the code locations it was stuck in and the modules loaded in the
  Game, which can include overlays and other programs that attach to it. Folder names are removed. These reports do not
  include the contents of memory.

Every metric and log line the Game can send is listed in [Diagnostic data](diagnostics.md).

**What it does not contain.** Your name, Steam ID, chat, voice, the names or addresses of servers you play on, or the
contents of the Game's memory.

**How long we keep it.** We keep diagnostic data for 30 days, then it is deleted. We may keep totals and charts made from
it for longer. Those do not relate to any one player.

## Feedback

You can send us a bug report or suggestion with Send Feedback in the main menu. Nothing is sent until you press Send, and
this does not depend on your diagnostic data setting.

**What it contains.** Your message and the type you chose, and the Game's state listed under
[State sent with everything](#state-sent-with-everything). If you choose to include them, it also contains your email
address, a screenshot of the Game and the console log of this session. A screenshot can show player names and chat. The
log can show chat, with names, Steam IDs and IP addresses removed. Other players who appear in them are not asked.

**How long we keep it.** We keep feedback, with anything you included, for 30 days, then it is deleted. We use your email
address only to reply to you.

## State sent with everything

Crash reports, diagnostic data and feedback all include:

- the Game's version, and whether it is a test build
- your operating system's name and version, and whether the Game runs on Windows, Linux, Proton or a Steam Deck
- your language, your screen size range and your graphics card maker
- what you were doing: the name of the map (including community maps), whether you were hosting or on another server, and
  the phase of the round

**The random ID of a run.** Each time you start the Game, it picks a random ID and puts it on everything that run sends.
We use it to see that a crash, a report that the Game stopped responding, feedback and diagnostic data came from the same
run. It is not stored anywhere, the next run has a new one, and it is not made from your name, Steam ID or computer, so it
does not link your runs to each other. If you give an email address with feedback, the data from that run can be connected
to that address.

## Servers

A server operator can choose to send data from their dedicated server. A player who hosts a game from the Game itself
sends server diagnostic data if they turned diagnostic data on.

- **Server crash reports** from a dedicated server include part of the server's memory, which can contain the names, Steam
  IDs, IP addresses and chat of connected players.
- **Server diagnostic data** contains the server's performance and totals such as the number of players, rounds, votes and
  purchases, and no player's identity.

Other players on that server are not asked in either case. Ask the server's operator about its settings.

## Discord

If Discord is running, the Game shows what you are doing on your Discord profile (Rich Presence): the phase of the round,
the map, how many other players and bots are on the server, and, so friends can join you, the server's address. This goes
from your computer to Discord. We do not receive it. You can turn it off in Discord under Settings, Activity Privacy.

## All of this data

**Why we use it.** We use all of it to find and fix bugs. We also use diagnostic data and feedback to improve performance
and decide what to work on. Our legal basis under the GDPR, where it applies, is your consent. You can withdraw it at any
time, which stops further data from being sent but does not affect data already sent.

**Who handles it.** This data is processed for us by [Sentry](https://sentry.io) in the United States. We do not sell it or
use it for advertising. We do not store IP addresses with it, although Sentry's servers necessarily see your IP address
when receiving it. Sentry records the approximate location it came from, which is the country and sometimes the city.

**Your rights.** Depending on where you live, you may have the right to access, correct or delete your personal data, to
withdraw consent, and to complain to your data protection authority. Contact us at gss.crazydog@gmail.com. For a crash
report or feedback, include the approximate time you sent it and, for feedback, any email address you gave. This data is not
linked to your identity, so without those we may be unable to find yours. Diagnostic data is not linked to you at all, so we
are generally unable to find or delete one player's data, but it is deleted after 30 days.

**Children.** The Game is not directed at children under 13, and we do not knowingly collect their personal information.

**Other services.** Steam, Discord, game server operators and Workshop creators handle data under their own terms and
privacy policies. This policy covers only the crash reports, diagnostic data and feedback we receive.

## Changes to this policy

We will post any change here with a new effective date, and the Game will show the current version. Any new use of crash
reports, diagnostic data or feedback will ask for your consent again.
