# Roblox Public Server Auto-Rejoin Watcher
A Node.js–based watcher that automatically reconnects you to public Roblox servers whenever the Roblox client closes, crashes, or disconnects. Built for long AFK sessions, unstable connections, and Roblox’s occasional talent for spontaneous disappearance. Unlike simple relaunch tools, this watcher is server-aware: it searches for available public servers and intelligently reconnects to suitable instances when possible. Entropy still loses. Just louder this time.

## Features
- Monitors RobloxPlayerBeta.exe
- Detects client exits, crashes, and disconnects
- Automatically reconnects to public servers
- Server-aware targeting (prefers less populated servers)
- Avoids rejoining the same server instance repeatedly
- Anti-spam cooldown system
- Interactive terminal interface
- Press S at any time to pause
- Fully self-installing via Windows batch script

## Requirements
- Windows
- Node.js v16 or newer (LTS recommended): https://nodejs.org
- Roblox Windows client installed
The installer automatically checks for Node.js before continuing.

## Installation
1. Download or clone this repository
2. Run install.bat
3. The installer will verify Node.js, create the watcher directory, install dependencies, and generate all required files
If an installation already exists, you can launch the watcher, perform a clean reinstall, or exit.

## Project Structure
public_roblox_watcher/
- public_watcher.js    Main watcher logic
- public_run.bat       Launcher
- package.json         Dependencies
- node_modules/        Installed packages

## Running the Watcher
Option 1: Run the installer again and select Launch Watcher  
Option 2: Navigate to the public_roblox_watcher folder and run public_run.bat

## Game Setup (Place ID)
When starting the watcher, you will be prompted for a Place ID.

How to get it:
1. Open the game on Roblox in your browser
2. Look at the URL bar
3. Copy the number after /games/
Example: https://www.roblox.com/games/123456789/Game-Name
Only numeric Place IDs are accepted.

## Controls
While running:
- Press S to pause the watcher
Pause menu options:
- Resume Monitoring
- Halt Watcher
- Exit Program

## How It Works
The watcher checks for the Roblox process every 5 seconds. Once Roblox has been detected at least once, the watcher waits for it to close. When Roblox exits, an anti-spam cooldown is enforced, active public servers are queried, a suitable server instance is selected, and Roblox is relaunched using the roblox:// protocol. This cycle continues until the watcher is stopped or exited.

Server-aware behavior:
- Public servers are queried using Roblox public endpoints
- Servers with open slots are preferred
- Recently joined server instances are avoided when possible
- If server data is unavailable, a fallback reconnect is used
No memory inspection. No exploit hooks. No gameplay automation. Only process monitoring and smart reconnection logic.

## Reinstall or Remove
Clean reinstall: Run the installer again and choose Clean Reinstall  
Manual removal: Delete the public_roblox_watcher folder

## Limitations
- Does not bypass Roblox restrictions
- Does not automate gameplay
- Does not prevent kicks or bans
- Cannot force entry into full servers
- Relies on public server availability
Use responsibly.

## Troubleshooting
Node.js not found: Install Node.js and restart your terminal  
Watcher does not reconnect: Ensure Roblox was running at least once, verify the Place ID is correct, and check cooldown messages  
Repeated reconnects: Cooldowns are intentional; halt and restart the watcher if necessary  
Terminal input issues: Press S to pause and resume; avoid resizing the terminal while running

## License
Provided as-is, without warranty. Free to use, modify, and distribute.

## Final Note
This tool watches Roblox disappear, surveys the public server landscape, and calmly drops you back into the game. The servers churn. The client blinks. The watcher endures.
