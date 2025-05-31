# Nin ELO Bot - Command Guide

Welcome to the Nin ELO Bot! This bot helps manage ELO ratings, track match history, and facilitate matchmaking for your server.
The bot integrates with a web interface where you can view leaderboards, detailed match histories, and player profiles. Visit [YourWebsiteLinkHere.com](https://YourWebsiteLinkHere.com) (Replace with your actual website URL).

## General Information

*   **Slash Commands:** All commands are initiated using `/` (slash). As you type, Discord will show available commands and their parameters.
*   **MODS Only:** Commands marked with "(MODS)" require the user to have a configured Moderator role or server administrator permissions.
*   **Parameters:** 
    *   `<parameter_name>`: Indicates a required parameter.
    *   `[parameter_name]`: Indicates an optional parameter.
*   **User Mentions:** When a command asks for a `user` or `player`, you can usually `@mention` them.

## Help Command

### `/help`
*   **What it does:** Shows a list of all available commands grouped by category.
*   **How to use:** `/help`
*   **Example:** `/help`

### `/help command_name:<command>`
*   **What it does:** Shows detailed information about a specific command, including its description, parameters, and usage syntax.
*   **Parameters:**
    *   **`command_name`** (Required): The name of the command you want help for (e.g., `startmatch`, `profile`).
*   **How to use / Example Syntax:** `/help command_name:<value>`
*   **Example:** `/help command_name:startmatch`

---

## Team Matchmaking Commands (MODS)

These commands are typically restricted to server moderators.

### `/startmatch`
*   **What it does (MODS):** Starts a new team match. It can either randomly select players from the configured Lobby Voice Channel or use a preset list of players for an organized party match (supports up to 4v4 for preset parties). It creates temporary voice channels for each team and moves players accordingly.
*   **Parameters:**
    *   **`players_per_team`** (Required): The number of players for each of the two teams (e.g., `2` for a 2v2 match). For preset parties, this also dictates how many of the specified player slots are used (max 4).
    *   **`[alpha_player1]`** (Optional - Party Mode): The first player for Team Alpha.
    *   **`[alpha_player2]`** (Optional - Party Mode): The second player for Team Alpha.
    *   **`[alpha_player3]`** (Optional - Party Mode): The third player for Team Alpha.
    *   **`[alpha_player4]`** (Optional - Party Mode): The fourth player for Team Alpha.
    *   **`[beta_player1]`** (Optional - Party Mode): The first player for Team Bravo.
    *   **`[beta_player2]`** (Optional - Party Mode): The second player for Team Bravo.
    *   **`[beta_player3]`** (Optional - Party Mode): The third player for Team Bravo.
    *   **`[beta_player4]`** (Optional - Party Mode): The fourth player for Team Bravo.
*   **How to use / Example Syntax:**
    *   **Random Lobby Match (2v2):** `/startmatch players_per_team:2`
        *   *(Bot will pick 4 players from the Lobby VC)*
    *   **Preset Party Match (1v1):** `/startmatch players_per_team:1 alpha_player1:@UserAlpha1 beta_player1:@UserBravo1`
    *   **Preset Party Match (2v2):** `/startmatch players_per_team:2 alpha_player1:@UserA1 alpha_player2:@UserA2 beta_player1:@UserB1 beta_player2:@UserB2`
*   **Notes:**
    *   For Random Mode, players must be in the pre-configured Lobby Voice Channel.
    *   For Party Mode, ensure you specify the correct number of players for each team matching `players_per_team`.

### `/endmatch`
*   **What it does (MODS):** Ends the currently active match started by `/startmatch`. It records the ELO changes for all participants, logs the match, moves players back to the lobby (if configured), and deletes the temporary match voice channels.
*   **Parameters:**
    *   **`winning_team_vc_id`** (Required): Select the voice channel of the team that WON the match. (Discord will show you an autocomplete list of active match VCs).
    *   **`[mvp_player]`** (Optional): Select the Most Valuable Player of the match. This player can be from either team and will receive an ELO bonus.
*   **How to use / Example Syntax:** `/endmatch winning_team_vc_id:<Select_Winning_Team_VC> [mvp_player:@MVPUser]`
*   **Example:**
    *   `/endmatch winning_team_vc_id:Team Alpha Match VC mvp_player:@SomeUser`
    *   `/endmatch winning_team_vc_id:Team Bravo Match VC` (No MVP selected)

### `/cleanmatchchannels`
*   **What it does (MODS):** Manually cleans up any orphaned match voice channels and clears the active match state in the bot. Use this if a match ended improperly and `/endmatch` was not used or failed.
*   **How to use / Example Syntax:** `/cleanmatchchannels`
*   **Example:** `/cleanmatchchannels`

---

## ELO & Profile Commands

These commands are generally available to all users, though some actions might be moderator-restricted.

### `/profile`
*   **What it does:** Shows a player's ELO profile, including their current ELO rating, tier, and total matches played.
*   **Parameters:**
    *   **`[user]`** (Optional): The user whose profile you want to view. If not specified, it defaults to your own profile.
*   **How to use / Example Syntax:** `/profile [user:@TargetUser]`
*   **Examples:**
    *   `/profile` (Shows your own profile)
    *   `/profile user:@AnotherUser` (Shows AnotherUser's profile)

### `/report`
*   **What it does (MODS):** Allows moderators to report the result of a 1v1 match that occurred outside of the `/startmatch` system. It updates ELO for both players and optionally an MVP.
*   **Parameters:**
    *   **`winner`** (Required): The player who won the 1v1 match.
    *   **`loser`** (Required): The player who lost the 1v1 match.
    *   **`[mvp]`** (Optional): The Most Valuable Player of this 1v1 match.
*   **How to use / Example Syntax:** `/report winner:<@WinningPlayer> loser:<@LosingPlayer> [mvp:@MVPPlayer]`
*   **Example:**
    *   `/report winner:@PlayerA loser:@PlayerB mvp:@PlayerA`
    *   `/report winner:@PlayerC loser:@PlayerD`

---

## Web Interface

Don't forget to check out our website for a richer experience:
*   **Leaderboard:** See where you and others rank.
*   **Match History:** Browse through all recorded matches.
*   **Player Profiles:** Detailed statistics and match history for each player.
*   **Dashboard (Logged-in Users):** Your personal stats, ELO progress, recent matches, and more!

**[YourWebsiteLinkHere.com](https://YourWebsiteLinkHere.com)** (Replace with your actual URL)

---

*This document will be updated as new commands and features are added.*
