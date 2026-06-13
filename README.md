# Gambling Simulator in C

A terminal-based casino simulator written in C. It includes slot machine and Blackjack games, persistent player balances, game history, player statistics, and a leaderboard.

This project uses simulated currency only. New players begin with a balance of `50,000`.

## Features

- Create a new player or load an existing player by name
- Play slot machines with 3, 5, 7, 9, or 15 matching-symbol modes
- Play Blackjack with hit, stand, and double-down actions
- Save player balances between sessions
- Record separate Slot Machine and Blackjack histories for each player
- View win/loss statistics and an overall player profile
- Rank up to 100 saved players by balance on the leaderboard
- Display colored terminal output and simple animations

## Requirements

- Windows terminal with ANSI escape sequence support
- A C compiler such as [GCC](https://gcc.gnu.org/)

The source contains some Unix-specific terminal helpers, but the current entry point also uses Windows commands directly. Windows is therefore the supported environment for the build instructions below.

## Build

Clone the repository and enter its directory:

```powershell
git clone <repository-url>
cd Gambling-Simulator-In-C
```

Compile the program with GCC:

```powershell
gcc gambing.c -o gambling-simulator.exe
```

## Run

```powershell
.\gambling-simulator.exe
```

On startup, choose whether to create a new player or load an existing one. Player names are case-sensitive, and spaces are removed automatically.

The main menu provides access to:

1. Slot Machine
2. Blackjack
3. Game History
4. Profile
5. Leaderboard
6. Exit

Bets must be at least 10% of the player's current balance and cannot exceed the available balance. Progress is saved when the main menu is displayed and when the program exits normally.

## Generated Data

The application creates its data files in the current working directory:

| Path | Purpose |
|---|---|
| `player_logs.txt` | Stores player names and current balances |
| `SlotMachine_Logs/<player>.txt` | Stores each player's slot machine history |
| `BlackJack_Logs/<player>.txt` | Stores each player's Blackjack history |

These files and directories are runtime data and should not be edited while the program is running.

## Project Structure

```text
.
|-- gambing.c   # Application source code
|-- LICENSE     # Project license terms
`-- README.md   # Project documentation
```

## Testing

The repository does not currently include an automated test suite. A basic build check can be run with:

```powershell
gcc gambing.c -o gambling-simulator.exe
```

## License

See [LICENSE](LICENSE). The project may be used, modified, and distributed for non-commercial purposes with credit to the original author.
