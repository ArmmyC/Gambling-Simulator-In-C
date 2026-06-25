<!-- prettier-ignore -->
<div align="center">

# OddsLab

*A terminal-based casino odds simulator written in C.*

![C](https://img.shields.io/badge/C-CLI-00599C?style=flat-square&logo=c&logoColor=white)
![GCC](https://img.shields.io/badge/GCC-build-333333?style=flat-square&logo=gnu&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-supported-0078D4?style=flat-square&logo=windows&logoColor=white)
![Terminal](https://img.shields.io/badge/Terminal-ANSI_output-111827?style=flat-square)

[Overview](#overview) • [Features](#features) • [Build](#build) • [Run](#run) • [Generated data](#generated-data) • [Testing](#testing)

</div>

OddsLab is a terminal game simulator written in C. It includes slot machine and Blackjack modes, player profiles, persistent simulated balances, game history, profile statistics, colored terminal output, simple animations, and a balance-based leaderboard.

> [!IMPORTANT]
> OddsLab uses simulated credits only. It does not support real-money play, payments, rewards, or betting advice.

## Overview

New players start with a balance of `50,000` simulated credits. The program lets players create or load a profile, choose a game, place simulated bets, view past results, and compare saved players on a local leaderboard.

```text
Player profile
  ├─ Simulated balance
  ├─ Slot machine history
  ├─ Blackjack history
  ├─ Win/loss statistics
  └─ Leaderboard ranking
```

> [!NOTE]
> The current source file is named [`gambing.c`](./gambing.c). Keep that filename in the build command unless you rename the file.

## Features

- Create a new player or load an existing player by name
- Start each new player with `50,000` simulated credits
- Play slot machine modes with 3, 5, 7, 9, or 15 matching-symbol reels
- Play Blackjack with hit, stand, and double-down actions
- Enforce a minimum bet of 10% of the current balance
- Save player balances between sessions
- Record separate Slot Machine and Blackjack histories per player
- View profile statistics, win/loss history, and total win rate
- Rank up to 100 saved players by balance on the leaderboard
- Display colored terminal output, ASCII art, and simple animations

## Requirements

- Windows terminal with ANSI escape sequence support
- A C compiler such as GCC

The source includes some Unix-style terminal helpers, but the current program flow uses Windows console behavior directly. Windows is the supported environment for the commands below.

## Build

Clone the repository and enter its directory:

```powershell
git clone https://github.com/ArmmyC/Gambling-Simulator-In-C.git
cd Gambling-Simulator-In-C
```

Compile with GCC:

```powershell
gcc gambing.c -o oddslab.exe
```

## Run

```powershell
.\oddslab.exe
```

On startup, choose whether to create a new player or load an existing one. Player names are case-sensitive, and spaces are removed automatically.

The main menu includes:

1. Play Slot Machine
2. Play Blackjack
3. Game History
4. Profile
5. Leaderboard
6. Exit

Progress is saved when the main menu is displayed and when the program exits normally.

## Gameplay notes

### Slot Machine

| Mode | Match count | Payout shown in app |
|---|---:|---:|
| 1 | 3 symbols | 15x bet |
| 2 | 5 symbols | 45x bet |
| 3 | 7 symbols | 95x bet |
| 4 | 9 symbols | 150x bet |
| 5 | 15 symbols | 600x bet |

### Blackjack

Blackjack uses a shuffled 52-card deck and standard terminal prompts for player actions. The dealer draws while below `17`, and the player can hit, stand, or double down when available.

> [!TIP]
> Because this is a simulation, the history and leaderboard are most useful for studying outcomes, testing probability ideas, and practicing C file I/O patterns.

## Generated data

The application creates runtime data in the current working directory:

| Path | Purpose |
|---|---|
| `player_logs.txt` | Stores player names and current balances |
| `SlotMachine_Logs/<player>.txt` | Stores each player's slot machine history |
| `BlackJack_Logs/<player>.txt` | Stores each player's Blackjack history |

Do not edit these files while the program is running.

## Project structure

```text
.
├── gambing.c       Main C source file
└── README.md       Project documentation
```

## Testing

The repository does not currently include an automated test suite. A basic build check is:

```powershell
gcc gambing.c -o oddslab.exe
```

Then run the executable and verify the main menu appears:

```powershell
.\oddslab.exe
```

## Known limitations

- Windows is the primary supported environment.
- Runtime save files are plain text and are not protected from manual edits.
- Player names are case-sensitive, and spaces are stripped.
- The program is a single-file C project, so future growth may benefit from splitting game logic, storage, and UI into separate modules.
