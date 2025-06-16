# NinHub: Your All-in-One Nin Online Companion

![NinHub Logo](https://i.imgur.com/yQvixnF.png) 
<!-- Replace with your actual logo URL or remove if you don't have one yet -->

Welcome to NinHub! This platform is designed to enhance your Nin Online experience with a suite of tools including a powerful Discord bot and a feature-rich website.

**Live Site:** [ninhub.xyz](https://ninhub.xyz/) <!-- Replace with your actual website URL -->

---

## 🌟 Key Features

NinHub offers a comprehensive set of features to support players, moderators, and server administrators:

*   ⚔️ **Advanced ELO & Leaderboards:** Track 1v1 and team match performance with a sophisticated ELO rating system. See detailed leaderboards on the website.
*   📝 **Seamless Match Reporting:** Easy-to-use commands for reporting match results, with an optional confirmation system for fairness.
*   👤 **Detailed Player Profiles:** View your ELO, tier, match history, stats, and more on dedicated web profiles.
*   🤝 **Team Matchmaking Tools:** (Moderator Operated) Quickly organize balanced team matches with automated voice channel creation.
*   📊 **Build Calculator (Web):** Plan and theorycraft your character builds with a detailed stat and jutsu calculator.
*   💹 **Marketplace (Web):** A central hub for players to list items for sale or post buy orders. Get real-time notifications in your Discord server for new listings.
*   🧠 **Nindex (Shared Intel):** Create and manage shared knowledge bases for your corporation or group. Perfect for tracking intel, strategies, or member notes, accessible via the website.
*   ⚙️ **Server Configuration:** Admins can customize bot settings, designate channels for matchmaking, ELO logs, marketplace feeds, and manage Nindex creation.

---

## 🤖 NinHub Discord Bot Command Guide

Welcome to the NinHub bot! Below are some of our key Discord slash commands. For a complete and up-to-date list, please use the `/help` command in any channel where NinHub is active.

---

### 👤 For Everyone

#### **View Your Profile (or Someone Else's)**
*   **Command:** `/profile`
*   **Description:** Shows a player's ELO rating, tier, and basic match statistics directly in Discord.
*   **How to use:**
    *   To see your own profile:
        ```discord
        /profile
        ```
    *   To see another player's profile:
        ```discord
        /profile user:@Username
        ```
*   **What happens:** The bot will display an embed with the requested player's ELO information. For even more details, check out their full profile on the NinHub website!

#### **Get Help**
*   **Command:** `/help`
*   **Description:** Shows a list of all available commands and their descriptions, or details for a specific command.
*   **How to use:**
    *   For a general overview of command categories:
        ```discord
        /help
        ```
    *   For details on a specific command (e.g., `profile`):
        ```discord
        /help command_name:profile
        ```
*   **What happens:** The bot sends a message with helpful information about its commands.

---

### ⚔️ For Moderators (or Admins with Mod Role)

#### **Report a 1v1 Match Result**
*   **Command:** `/report`
*   **Description:** Used by moderators to report the outcome of a 1v1 match.
*   **How to use:**
    ```discord
    /report winner:@WinnerName loser:@LoserName mvp:@MVPName (optional)
    ```
*   **What happens:**
    *   If your server has "Public Match Confirmation" enabled (default), the reported loser will receive a message with buttons to "Confirm" or "Dispute" the result. ELO changes apply after confirmation or auto-confirmation after a timeout.
    *   If "Public Match Confirmation" is disabled, ELO changes are applied immediately.
    *   The match result is logged and will appear in player profiles and match history.

#### **Start a Team Match (Matchmaking)**
*   **Command:** `/startmatch`
*   **Description:** Initiates a team match. Can randomly select players from a configured lobby voice channel or use specified players. Automatically creates dedicated voice channels for each team.
*   **How to use:**
    *   **Random Lobby Mode:**
        ```discord
        /startmatch players_per_team:<number> 
        ```
        *(Example: `/startmatch players_per_team:2` for a 2v2. Players must be in the pre-configured lobby VC.)*
    *   **Preset Party Mode:**
        ```discord
        /startmatch players_per_team:<number> alpha_player1:@PlayerA1 alpha_player2:@PlayerA2 beta_player1:@PlayerB1 beta_player2:@PlayerB2
        ```
        *(Adjust `alpha_playerX` and `beta_playerX` arguments based on `players_per_team`.)*
*   **What happens:** Selected players are moved to new "Team Alpha VC" and "Team Bravo VC" voice channels. An announcement is made in the channel where the command was used.
*   **Note:** Requires server admin to configure "Lobby VC" and "Match Category" using `/server_config` first.

#### **End a Team Match & Report Winner**
*   **Command:** `/endmatch`
*   **Description:** Ends an active team match, reports the winning team, and optionally an MVP. Calculates and applies ELO changes for all participants and cleans up match voice channels.
*   **How to use:**
    ```discord
    /endmatch winning_team:<Team Alpha or Team Bravo> mvp_player:@PlayerName (optional)
    ```
*   **What happens:** Team voice channels are deleted, players are typically moved back (behavior may depend on server setup), ELO is updated for all participants, and a match summary is posted.

#### **Clean Up Match Channels (If Needed)**
*   **Command:** `/cleanmatchchannels`
*   **Description:** Manually deletes any orphaned team match voice channels if `/endmatch` failed to do so (e.g., due to a bot restart or error).
*   **How to use:**
    ```discord
    /cleanmatchchannels
    ```
*   **What happens:** The bot attempts to find and delete voice channels named according to the team name settings (default: "Team Alpha VC", "Team Bravo VC") within the configured match category.

---

### ⚙️ For Server Administrators

#### **Configure Server Settings**
*   **Command:** `/server_config`
*   **Description:** Allows admins to set up or view bot settings for the server. This includes the matchmaking lobby VC, the category for match VCs, the moderator role for bot commands, the audit log channel, and public match confirmation preferences.
*   **How to use:**
    *   To view current settings:
        ```discord
        /server_config
        ```
    *   To set specific options (only provide the ones you want to change):
        ```discord
        /server_config lobby_vc:#voice-channel match_category:CategoryName mod_role:@RoleName audit_log_channel:#text-channel public_match_confirmation:True
        ```
*   **What happens:** Bot settings are updated for your server. These settings are crucial for features like automated matchmaking, ELO logging, and moderator permissions.

#### **Set Marketplace Notification Channel**
*   **Command:** `/set_marketplace_channel`
*   **Description:** Designates a specific text channel where NinHub will post notifications about new listings from the website's marketplace.
*   **How to use:**
    ```discord
    /set_marketplace_channel channel:#your-market-channel
    ```
*   **What happens:** The bot creates a webhook in the specified channel to send marketplace updates. The bot needs "Manage Webhooks" permission in that channel.

#### **Disable Marketplace Notifications**
*   **Command:** `/disable_market_notifications`
*   **Description:** Stops marketplace notifications from being sent to your server and removes the associated webhook.
*   **How to use:**
    ```discord
    /disable_market_notifications
    ```
*   **What happens:** The bot removes the marketplace webhook from your server.

#### **Create a Nindex (Shared Intel Group)**
*   **Command:** `/nindex_create`
*   **Description:** Creates a new Nindex for a specific group (e.g., a corporation, team, or study group) within your server. Access to view and manage the Nindex on the website is controlled by the Discord roles you specify.
*   **How to use:**
    ```discord
    /nindex_create name:"Your Nindex Name" member_role:@MemberViewRole leader_role:@ManagerRole
    ```
    *(Example: `/nindex_create name:"Akatsuki Intel" member_role:@AkatsukiMember leader_role:@AkatsukiLeader`)*
*   **What happens:** A new Nindex is registered with the NinHub platform. Users in your Discord server who have the specified "Member Role" or "Leader Role" will be able to access and contribute to this Nindex on the website. Leaders can manage entries and members.

---

## 🚀 Getting Started

1.  **Configure Your Server (Admins):**
    *   Use `/server_config` to set up essential channels (like lobby VC for matchmaking, audit log channel) and the moderator role.
    *   Use `/set_marketplace_channel` if you want marketplace updates.
2.  **Explore the Website:**
    *   Visit [ninhub.xyz](https://ninhub.xyz/) <!-- Replace -->
    *   Log in with Discord to view your dashboard, manage your Nindex entries (if applicable), and interact with the marketplace.
3.  **Start Using Commands:**
    *   Use `/help` in Discord to see all commands.
    *   Moderators can start reporting matches with `/report`.
