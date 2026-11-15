# AUCAA Basketball League System - User Guide

This guide covers public pages, accounts, league administration, coaching, game-day scoring, standings, brackets, and reports. The exact menu items available depend on your account role.

## 1. Open the system and navigate

Open the AUCAA web address provided by your administrator. When running locally for development, the frontend is normally available at `http://localhost:5174`.

The top navigation contains:

| Page | What it is for |
| --- | --- |
| **Highlights** | Featured broadcast image/link, live games, current scores, upcoming and completed games, and top scorers. |
| **Stats** | League overview and player leaders by statistical category. |
| **Standings** | Regular-season records, rankings, tie-breaker decisions, and a playoff summary. |
| **Bracket** | View the selected league's current playoff bracket. Admins and league managers can generate brackets and advance winners. |
| **Teams** | Browse teams and their division and roster count for a selected league. |
| **Players** | Browse player leaders or rosters, search/filter, and open a player's profile. |
| **Announcements** | Signed-in users can read notices and upcoming games. Admins and league managers can publish and manage notices. |
| **Reports** | Admins and league managers can download league reports. |
| **Admin / Manage League** | Administration tools. The label depends on the signed-in role. |
| **My Roster** | Coach tools for assigned teams and players. |
| **My Profile** | Player account profile. |

Use the sidebar's **Settings** to update account details or change your password. Choose **Logout** when finished on a shared device. The footer provides AUCAA contact information and quick links.

## 2. Account roles and access

- **Visitor:** Can view Highlights, Stats, Standings, Bracket, Teams, and Players. Sign in to open Announcements.
- **Player:** Can view public pages and Announcements, and has a **My Profile** menu item.
- **Coach:** Can use **My Roster** for assigned team information, pending players, registration codes, and player bio management.
- **League Manager:** Can use management tools and Reports for league operations, and generate coach registration codes. The Highlights configuration tab is reserved for admins.
- **Admin:** Has the full administration tools, including account review, league/team/game setup, live scoring, and Highlights configuration.

Some actions are hidden or rejected unless the account has the right permission. If a menu is missing, ask an AUCAA administrator to check your account role or assignment.

## 3. Create an account and sign in

### Register

1. Select **Sign In** in the top bar, then choose the **register** tab.
2. Select your account type: **Player**, **Coach**, or **League Manager**.
3. Enter the registration code issued for that role. Codes are role-specific; a player code will not register a coach account.
4. Enter the required information:
   - Coaches and league managers: username, email, password, and registration code.
   - Players: username, full name, email, birth date, location, height, weight, jersey number, password, and registration code. Position can also be selected.
5. Use a valid email address you can access. Follow the password requirements shown on the form (at least 8 characters, including uppercase and lowercase letters, a number, and a special character).
6. Submit the form and check your email for the verification message. Follow its link to verify the email address.
7. Player accounts and coach/league-manager accounts may also need approval. Wait for the administrator, or the assigned coach for player verification, to complete the review before using restricted account features.

### Sign in, resend verification, or reset a password

1. Choose **Sign In**, enter your username and password, and select **Login**.
2. If you have not received the email verification message, select **Resend verification email** and enter the registered username and email.
3. To reset a forgotten password, enter your username first, select **Forgot Password?**, and provide the registered email.
4. Enter the emailed six-digit verification code, choose and confirm a new password, then submit. Use **Resend code** if needed.
5. If the code or email is not accepted, check for spelling errors and use the exact email associated with the username.

## 4. Public pages

### Highlights

1. Open **Highlights**.
2. If a featured image is configured, it appears above the game feed. Select **Watch Now** to open the broadcast link in a new tab.
3. Live games appear prominently with live scores. If a stream link is attached to a game, select **Watch Live**.
4. Upcoming and completed games appear in the game cards. The page refreshes live data automatically.
5. The right-hand panel shows top scorers and, when available, live game progress.

### Stats

1. Open **Stats** and choose a league from the league selector.
2. Review the overview cards for verified players, teams, games, live games, and upcoming games.
3. Select a leaderboard category: **Points**, **Rebounds**, **Assists**, **Steals**, or **Blocks**.
4. Review the top performers and the latest games for that league.
5. If there are no statistics yet, player game statistics may not have been recorded or the games may not have been completed.

### Standings

1. Open **Standings** and choose a league.
2. Read the regular-season table:
   - **W / L:** wins and losses.
   - **PCT:** win percentage.
   - **GB:** games behind the leader.
   - **PF / PA:** points for and points against.
   - **+/-:** point differential.
   - **Playoff:** current playoff progress, if a bracket exists.
3. Rankings use wins, point differential, points scored, then points allowed. Regular-season standings exclude playoff and tie-breaker games.
4. Expand **Tie-breakers & playoff details** to inspect exact ties, tie-breaker games, and playoff summaries.
5. Admins and league managers can select **Create Tie-breaker Games** when the action is available. These decision-game results do not alter regular-season win/loss records.

### Bracket

1. Open **Bracket** and select a league.
2. Visitors and regular users can view the current bracket and its scores.
3. Admins and league managers can select a bracket size (2, 4, 8, 16, or 32 teams) and choose **Generate Bracket**.
4. The selected league must have enough teams for that size. Bracket generation is unavailable for a Round Robin league.
5. Review the confirmation before generating. Generating a replacement archives the previous active bracket; it does not delete the previous bracket's games.
6. For each playoff game, use **Games** to start live scoring. After the game is completed with a valid, non-tied score, return to **Bracket** and select **Advance** for that game. The winner is placed into the next game.
7. Use **Refresh** if you need to reload bracket data.
8. **Purge Bracket** is a destructive action. It permanently removes games and player stats from the active bracket. It does not purge regular-season games or archived brackets. Only use it when the active bracket should be discarded and recreated.

### Teams

1. Open **Teams**.
2. Select the league to view.
3. Review each team's division and roster count.

### Players

1. Open **Players** and select a league.
2. Switch between the **Leaders** and **Roster** views.
3. In the roster, search by player/team name and optionally filter by team.
4. Select a player row/card to open the player profile.
5. The profile's **Stats** tab shows per-game averages and career totals. The **Bio** tab shows the player's personal and team information. Administrative bio editing is available only to authorized roles.

### Announcements

1. Sign in and select **Announcements**.
2. Upcoming scheduled games appear alongside notices, including the league, date, time, and venue when those details are available.
3. Admins and league managers can select **Create announcement**, enter a title, choose **General** or **Important**, enter the message, then publish.
4. To edit or delete a notice, open its three-dot action menu. Confirm before deleting; deletion cannot be undone.
5. Admins and league managers can open an upcoming game's three-dot menu to edit its date/time and venue or delete the game. The regular Games list does not show a row-level edit button for changing teams or bracket stage; arrange any such correction through the authorized game-edit workflow before play.

## 5. Administrator and league-manager workflow

For a new season, use this order to avoid creating games before the league and teams exist.

### Step 1: Create the league

1. Open **Admin** or **Manage League**.
2. Select **Leagues**.
3. Enter the league name and season.
4. Set the status to **Upcoming** while preparing the season.
5. Choose the tournament format:
   - **Elimination** supports a playoff bracket.
   - **Round Robin** does not support bracket generation.
6. Select **Add**. Use **Edit** later to change the league details or status.

Deleting a league removes its associated teams and games. Treat this as a permanent, high-impact action.

### Step 2: Create and distribute registration codes

1. Select **Reg Codes**.
2. Admins can choose a role, enter a code or use **Auto Generate**, then select **Create**.
3. League managers can generate coach registration codes and copy them to share with the appropriate coach.
4. Coaches can generate player registration codes from **My Roster > Reg Codes**.
5. Share a code only with the intended registrant. Check the code list to see whether a code has been used; delete unused codes that should no longer be valid.

### Step 3: Add teams and assign coaches

1. Select **Teams** in the management panel.
2. Enter the team name and select its **Division** and **League**.
3. Optionally select an approved coach. If no coach is ready, leave it unassigned and edit the team later.
4. Select **Add** and confirm the team appears in the table under the correct league.
5. Use **Edit** to update the team or coach assignment. Deleting a team is permanent and may affect its roster and games.

### Step 4: Review accounts

1. Admins select **Verification** to review player, coach, and league-manager applications. Filter by pending, verified, rejected, or all. Accounts with unverified emails are listed with an **Email not verified** note.
2. The **Verify** action is disabled until the email is verified. Ask the registrant to complete email verification before approving the account.
3. Select **Verify** or **Reject** for the relevant application. Check the status afterward.
4. Coaches can review players registered with their codes under **My Roster > Pending Players**. Filter by status and assigned team. Unverified players are shown but cannot be verified until they confirm their email.
5. Use **Users** to search accounts, activate or suspend an account, or delete it. Account deletion cannot be undone.

### Step 5: Schedule games

1. Select **Games**, then **+ Add Game**.
2. Choose the league first. The home and away team lists are limited to teams in that league.
3. Select different home and away teams.
4. Enter the date and time (current or future) and venue. Select a bracket stage only for an explicitly scheduled playoff-stage game.
5. Select **Create Game** and check the row for the correct matchup, league, date, time, and venue.
6. To correct an upcoming game's date/time or venue, use its three-dot menu in **Announcements**. If its teams or bracket stage need correction, arrange an authorized correction before scoring; do not delete and recreate a game after results or stats have been recorded.
7. To permanently remove a game, select **Delete** and confirm. Verify the matchup before confirming.

The game row and Announcements page use the saved game schedule. Always verify its displayed date, time, and venue after saving a change.

### Step 6: Start and record a live game

1. In **Games**, locate the correct upcoming game.
2. Optionally enter a valid `http://` or `https://` broadcast URL.
3. Select **Go Live**. This changes the game to live and makes it available in **Live Stats** and the live portions of public pages.
4. Open **Live Stats** and choose the correct live game.
5. For each home and away player, use the points controls (`+1`, `+2`, `+3`, or `-1`) and the plus/minus controls for rebounds, assists, steals, blocks, and fouls. Search within each roster if needed.
6. Confirm the team scores reflect the points recorded for their players. Select the quarter controls as the game progresses.
7. Select **End Game** when scoring is complete. A final basketball score must have a winner; a tied or invalid final score will not produce a valid winner for bracket advancement.

Game and player-stat changes are reflected in public scores, statistics, and standings as the data updates. Each stat-button click updates and saves that player's total, so click only once per intended change.

### Step 7: Check standings and break ties

1. Open **Standings**, choose the league, and check that all completed regular-season games have the correct scores and status.
2. Review wins, losses, and point totals before finalizing playoff seeding.
3. Expand **Tie-breakers & playoff details**. If an exact tie between teams with games played requires a decision, an admin or league manager can create the suggested tie-breaker games there.
4. Record tie-breaker game results through the game workflow. These games decide tied seeds but do not change regular-season records.

### Step 8: Generate and run the playoff bracket

1. Confirm the league is **Elimination**, teams are assigned, and the standings/seeding data is ready.
2. Open **Bracket**, select the league, choose the intended bracket size, and confirm there are at least that many teams.
3. Select **Generate Bracket** and review the confirmation. The previous active bracket will be archived, not deleted.
4. Start and score each bracket game using **Games > Go Live** and **Live Stats**.
5. Once a bracket game is completed with a valid score, select **Advance** for that game to move the winner forward.
6. Repeat for later rounds until the final is complete.
7. Use **Purge Bracket** only when you intend to permanently delete the active bracket's games and stats. Purge is not the normal way to replace a bracket; use **Generate Bracket** to archive and replace it.

### Step 9: Publish notices and highlights

**Announcements**

1. Open **Announcements** and select **Create announcement**.
2. Enter a concise title, choose **General** or **Important**, and write the message.
3. Select **Publish announcement**. Review the notice in the feed.
4. Upcoming games are listed automatically from scheduled game data. Keep game details accurate in **Games** so announcements show the correct schedule.

**Highlights**

1. Admins open **Admin > Highlights**.
2. Optionally enter a title and select **Choose image from PC** to upload a banner/preview image.
3. Enter the full broadcast URL beginning with `https://` or `http://`.
4. Select **Save**, then open **Highlights** to confirm the image, title, and **Watch Now** link.

### Step 10: Download reports

1. Select **Reports**.
2. Choose the league and export format.
3. Select the report card to download:
   - **Standings Report**
   - **Player Statistics Report**
   - **Game Statistics Report**
   - **League Overview Report**
4. The available downloads are CSV for spreadsheets or plain-text TXT. Open CSV files with a spreadsheet program.

## 6. Coach workflow

1. Sign in and select **My Roster**.
2. Under **Teams**, confirm your assigned team, league, season, division, and roster count. If no team is assigned, ask an administrator or league manager to assign one.
3. Under **Pending Players**, filter by status and team. Verify or reject eligible player applications after checking the account information.
4. Under **Reg Codes > Players Registration Codes**, generate a player code, copy it, and share it with the intended player.
5. Under **Reg Codes > Players**, review players under your management and use **Edit Bio** if authorized to update their player details or team assignment.

## 7. Player workflow

1. Sign in and select **My Profile**.
2. Review and update editable profile information such as student ID, date of birth, height, weight, jersey number, position, team, and address.
3. Select **Save All Profile Details** and check for the success message.
4. To change your password, open **Settings**, enter your current password and the new password twice, then select **Change Password**.
5. To view public statistics, open **Players**, choose your league, and select your name. The profile shows player statistics and bio information.

## 8. Common issues and safe practices

- **A page is empty:** Check the selected league, confirm the league has teams/games, and refresh. Standings require completed or forfeited games with scores.
- **A team is missing from game selectors:** Confirm it belongs to the selected league and was saved successfully.
- **A player is missing from a roster or leaderboard:** Confirm the account and player record are verified, the player is assigned to the correct team/league, and game stats have been recorded.
- **A bracket cannot be generated:** Confirm the league format is Elimination and there are at least as many teams as the selected bracket size.
- **A winner cannot advance:** Confirm both teams are present and the game is completed or forfeited with valid, non-null, non-tied scores.
- **A scheduled detail is wrong:** Update the upcoming game's date/time or venue from its three-dot menu in Announcements, then verify the displayed details. For team or bracket-stage corrections, arrange an authorized correction before scoring.
- **An action fails or is unavailable:** Confirm you are signed in with the required role and that the account is approved. Contact the administrator if it continues.
- **Before deleting:** Deleting a league, team, game, user, code, or announcement may be permanent. Read the confirmation carefully.
- **Before regenerating or purging a bracket:** Regeneration archives the current bracket; purge permanently removes active bracket games and associated player stats. Verify the selected league before confirming.
- **Protect accounts:** Do not share passwords or role-specific registration codes publicly. Log out on shared devices.

