# Diagnostic data

TTT Classic can send anonymous diagnostic data to its developers through [Sentry](https://sentry.io). It is off unless
you say yes. The game asks once, and you can change your answer at any time in TTT Settings, Interface (`ttt_diagnostics`).
Declining changes nothing in the game. A dedicated server sends it only while its admin has `ttt_server_diagnostics` on.
When a player hosts a game from the game itself, that player's own answer also covers the server's totals below.

Crash reports are separate, and this setting does not send them. You are still asked at each crash.

## What is never sent

Your name, Steam ID, chat, voice, the name or address of a server, the contents of the game's memory, file paths, or an
identifier that follows you between runs. Each run of the game has a random ID that groups what that run sends: its
metrics, logs and hang reports, and a crash report or feedback if you choose to send one. The ID is kept nowhere, and the
next run has a new one. If you give an email address with feedback, that run's data can be connected to it.

The name of the map is sent, including community maps. It is the map's file name, which its creator chose.

Sentry also adds the game's version, your operating system's name and version, and whether this is a test build. We do
not store IP addresses, but Sentry's servers see yours when they receive data, and it records the approximate location it
came from, which is the country and sometimes the city.

## Attributes

| Attribute | Values |
|---|---|
| `side` | `client`, or `dedicated` or `listen` for server items |
| `platform` | `windows`, `linux`, `proton` or `steamdeck` |
| `map` | The map's file name in lowercase, with anything but letters, digits, `_` and `-` replaced by `_`, or `none` outside a map |
| `language` | The game's language |
| `res_bucket` | Screen height: `up_to_768`, `up_to_1080`, `up_to_1440` or `above_1440` |
| `fps_cap_bucket` | `fps_max`: `up_to_60`, `up_to_100`, `up_to_144`, `up_to_240` or `above_240` |
| `gpu_vendor` | `nvidia`, `amd`, `intel` or `other` |
| `players_bucket` | Players: `0-1`, `2-5`, `6-9`, `10-15`, `16-23` or `24+` |
| `connection` | `none`, `host` (you are hosting) or `remote` |
| `round_phase` | `none`, `waiting`, `preparing`, `active` or `complete` |

Everything the game sends, including crash reports, hang reports and feedback, also has the state at that moment. From the
game these are `side`, `platform`, `language`, `map`, `res_bucket`, `gpu_vendor`, `connection` and `round_phase`. From a
dedicated server they are `side`, `map`, `players_bucket` and `round_phase`. The tables below only list what a metric or log
adds to these.

## Client metrics

| Metric | What it counts | Other attributes |
|---|---|---|
| `client.session.start` | The game started | `language` |
| `client.session.duration` | How long the game ran, in seconds | |
| `client.session.unclean_exit` | The last run did not close normally | |
| `client.frame_ms.p50`, `client.frame_ms.p99` | Frame times, summed up every 5 minutes in a level | `map`, `res_bucket`, `fps_cap_bucket`, `gpu_vendor` |
| `client.hitches` | Frames over 100 ms in the same 5 minutes | same |
| `client.memory.peak_mb` | Address space in use | `map` |
| `client.map_load.ms` | Time to load a map | `map` |
| `client.server.joined` | A server was joined | `source`: `host`, `quickplay`, `browser`, `other` |
| `client.server.left` | A server was left | `reason`: `self`, `dropped`, `version_kick` |
| `client.quickplay` | Use of Quick Play | `step`: `opened`, `connected`, `failed` |
| `client.voice.init` | A part of voice chat started or failed, once per run | `stage`, `result` |
| `client.workshop.download` | A Workshop download finished | `result` (a Steam result code) |
| `client.workshop.mount` | A Workshop item was mounted | `result`: `ok`, `rejected` |
| `client.workshop.upload` | A Workshop upload step finished | `stage`, `result` |
| `client.hang.recovered_ms` | The game stopped responding for 30 seconds or more and then came back, and for how long | `map` |

## Server metrics

All of these also have `side`.

| Metric | What it counts | Other attributes |
|---|---|---|
| `server.map.loaded` | A map was loaded | `map` |
| `server.map.duration` | How long the map ran, in minutes | `map` |
| `server.round.end` | A round ended | `map`, `winner`, `time_ran_out`, `players_bucket` |
| `server.round.duration` | How long the round's active part ran, in seconds | `map`, `winner` |
| `server.round.kills` | Kills in that round, summed | `weapon`, `killer_role`, `friendly` |
| `server.round.purchases` | Items bought in that round, summed | `item`, `role` |
| `server.players.humans`, `server.players.bots` | Players on the server, every 5 minutes | |
| `server.frame_ms.p50`, `server.frame_ms.p99` | Server frame times, every 5 minutes | `map`, `players_bucket` |
| `server.memory.peak_mb` | Address space in use | `map` |
| `server.vote.finished` | A vote ended | `type`, `result` |
| `server.workshop.download`, `server.workshop.mount` | Workshop results | `result` |
| `server.hang.recovered_ms` | A dedicated server stopped for 10 seconds or more and then came back, and for how long | `map` |

## Logs

Each log line has fixed text, with details only in the listed attributes. At most 5 of one line and 50 in total are sent
per run, after which one `diagnostics.logs_suppressed` count is sent.

| Level | Text | Attributes |
|---|---|---|
| info | Client started | `language`, `res_bucket` |
| warn | Previous session did not exit cleanly | |
| error | Voice failed to start | `stage`, `err` (a library's error number) |
| warn | Workshop download failed | `eresult` (a Steam result code) |
| warn | All files of a Workshop item were rejected | |
| warn | Workshop upload failed | `stage`, `eresult` |
| warn | Discord bridge failed to start | `err` |
| warn | Video failed | `stage`, `error` (the decoder's text with paths and addresses removed) |
| warn | Model import failed | |
| warn | Steam connection lost | `eresult` |
| fatal | Sys_Error (server) | `error` (the engine's text with paths and addresses removed), `map` |
| error | Workshop download failed (server) | `eresult` |
| error | Steam login failed (server) | `eresult` |
| warn | Version check timed out (server) | |

## Hang reports

If the game stops responding for 30 seconds (a dedicated server, 10 seconds), a report is sent with the list of code
locations it was stuck in and the file names of the modules it has loaded, with their folders removed. It holds no memory
contents. Loading a map does not count. At most 3 are sent per run.

## Feedback

Send Feedback in the main menu sends a report whatever the setting above says, and only when you press Send. It has the
message and type you chose, the state and random ID above, and only if you give or tick them: an email address for a reply,
a screenshot of the game, and this session's console log with names, Steam IDs and IP addresses removed. A screenshot can
show player names and chat, and the log can show chat. Feedback is kept for 30 days.

## Keeping

A crash writes the last few seconds of these items to disk, and the next run sends them if the setting is still on. This
does not include a crash report.

Diagnostic data is kept for 30 days.
