# CHAPTER IV
# RESULTS AND DISCUSSION

This chapter presents the results of developing and testing the AUCAA Basketball League Management System. The discussion is organized around the study's objectives and the completed system workflows. The testing results describe observed functional and integration behavior; they do not represent user-satisfaction ratings or measured production performance.

## 4.1 System Development

The development phase produced a centralized web application for managing AUCAA basketball league information and making selected results available to the public. Development proceeded iteratively: core account and data-management workflows were implemented first, followed by game operations, live scoring, standings, playoff brackets, and supporting public pages. Integration and edge-case checks were then used to refine the workflows and prevent data from one competition process from affecting another.

### 4.1.1 System Architecture and Data Organization

The application uses a React-based frontend, a Node.js and Express backend, a MySQL relational database, and Socket.IO for event notifications. The frontend provides public pages and role-specific management interfaces. The backend exposes API routes for authentication, account verification, leagues, teams, players, games, statistics, standings, brackets, announcements, and reports. JWT authentication and role checks protect operations intended for signed-in administrators, league managers, and coaches.

Related records are organized around leagues, teams, player profiles, games, and player statistics. Registration codes identify the account role and can associate a player with the coach who issued the code. Bracket records and bracket identifiers distinguish active and archived playoff data from regular-season games. This organization provides a common source for management screens and public pages rather than maintaining separate copies of schedules and standings.

### 4.1.2 Account and Roster Workflows

The completed system supports role-specific account registration, email verification, account approval, and registration-code management. Administrators can manage accounts and verification requests. League managers can manage their league operations and issue coach registration codes. Coaches can create player registration codes, review players associated with those codes, and maintain permitted player bio and team details. Players can access their profile after signing in.

The verification workflow separates email confirmation from account approval. An unverified player may be visible to an authorized reviewer as pending, but the Verify action remains disabled until email verification is complete. Server-side approval checks reinforce this condition. The player name is displayed as profile information rather than an editable coach bio field.

### 4.1.3 League, Team, Schedule, and Announcement Management

Administrators and league managers can organize leagues, assign teams to leagues, manage coaches, and schedule games between teams belonging to the selected league. The application validates game inputs and stores the scheduled date, time, venue, participating teams, and league association. Creating a scheduled game also creates a corresponding schedule announcement using the saved game details. This reduces discrepancies between the Games and Announcements views.

Public-facing pages present league information, teams, players, schedules, announcements, and highlights. The Reports module provides league and statistics reports for administrative use. These modules support the objective of replacing fragmented records with one application for maintaining and viewing league information.

### 4.1.4 Live Scoring and Statistics

The live-scoring interface records game scores and player statistics, including points, rebounds, assists, steals, blocks, and other supported game statistics. Socket.IO events notify connected views when relevant game or schedule data changes. Public statistics and game views use the stored records to present current information without requiring organizers to maintain separate public score sheets.

The implementation provides event-based updates, but no numerical latency benchmark is reported in this chapter. The results therefore establish that the real-time communication workflow is implemented and integrated, not that a specific response-time threshold was achieved under load.

### 4.1.5 Standings, Tie-Breakers, and Playoff Brackets

Standings are calculated from completed or forfeited games with recorded scores. The calculation reports wins, losses, games played, win percentage, points for, points against, and point differential. Teams without completed games are not treated as an exact tie group requiring a tie-breaker. Tie-breaker games are created only for eligible tied teams and are kept separate from regular-season standings.

For elimination leagues, an administrator can generate a bracket after selecting a supported size and league. Bracket games are associated with a bracket record, and unplayed scores are represented as absent values rather than misleading 0–0 scores. A replacement bracket archives the previous active bracket. Winner advancement requires a completed game with a valid, non-tied score and is protected against repeated or conflicting advancement. Purging applies to the active bracket and its associated game data; an archived bracket may be restored, while a purged bracket cannot be restored after its games have been deleted. Round-robin leagues do not use elimination-bracket generation.

These controls address edge cases that could otherwise lead to false standings, ambiguous bracket placeholders, or old playoff records being interpreted as current regular-season results.

## 4.2 System Testing

Functional and integration testing was conducted in the development environment using isolated league and game records. Temporary test records were removed after the checks, and existing AUCAA records were retained. Testing focused on expected user workflows, role restrictions, data relationships, and the standings and bracket edge cases identified during development. Frontend production builds and backend syntax checks were also performed.

### 4.2.1 Functional and Integration Test Results

| Test area | Scenario exercised | Observed result |
|---|---|---|
| Account verification | Display a pending player whose email is unverified and attempt the approval workflow | The player remains visible to authorized reviewers; the Verify action is disabled until email verification. The server also rejects approval when the email is unverified. **Passed.** |
| League and team association | Create or manage games using teams associated with a selected league | Game operations validate league/team association and preserve the selected league in stored records. **Passed.** |
| Game schedule and announcement | Create a scheduled game and compare the saved schedule with the corresponding announcement | The announcement uses the game's saved teams, date, time, league, and venue instead of independently entered schedule values. **Passed.** |
| Score validation | Submit valid and invalid final-score scenarios, including a tied result | Valid results can be processed; tied or invalid final results cannot be used to determine a bracket winner. **Passed.** |
| Empty and regular-season standings | Query a league with no completed games and verify regular-season calculations | Teams with no completed games are not reported as false tie-breaker candidates. Standings exclude playoff and tie-breaker games. **Passed.** |
| Tie-breaker creation | Request tie-breaker games for exact ties, including repeated or concurrent requests | Only eligible tied groups produce games; matching requests do not create duplicate games for the same standings snapshot. **Passed.** |
| Bracket generation and replacement | Generate a bracket, then generate a replacement for the same league | The new bracket becomes active and the prior bracket is archived. Unplayed scores remain unset, and archived playoff games do not enter current regular-season standings. **Passed.** |
| Winner advancement | Advance a valid completed game, repeat the request, and attempt a conflicting winner change | The valid winner advances, a repeated advance is handled idempotently, and a conflicting change is rejected. **Passed.** |
| Bracket purge and restore | Purge active bracket data, restore an archived bracket, and attempt to restore a purged bracket | Purge is scoped to the active bracket and its associated statistics; archived data can be restored, while purged data is correctly rejected for restoration. **Passed.** |
| Build and code validation | Build the frontend and run backend syntax and diff checks | The frontend build completed successfully, and the targeted backend syntax and diff checks completed without errors. **Passed.** |

The table reports selected functional and integration scenarios, not a count of all possible inputs. No claim is made that every browser, device, network condition, or concurrent-user volume was tested.

### 4.2.2 Discussion of Edge-Case Results

The standings tests confirmed that the system distinguishes an unplayed team from a team that has played and earned an identical record. This distinction prevents a league with no completed results from displaying misleading tie-breaker actions. Excluding bracket and tie-breaker records from the regular-season calculation also keeps playoff operations from changing regular-season wins and losses.

Bracket lifecycle tests confirmed that replacement, advancement, purge, and restoration act on the appropriate bracket record. Archiving a bracket preserves its history while separating it from the active bracket. Null scores communicate that a match has not yet been played; they avoid presenting placeholder zeros as actual results. Repeated advancement requests do not duplicate or contradict an already advanced winner.

The schedule and announcement workflow uses saved game data as its source for schedule details. This makes date, time, venue, team names, and league information consistent across the relevant views. The email-verification check similarly demonstrates layered validation: the interface communicates that approval is unavailable, and the backend independently enforces the rule.

## 4.3 Discussion in Relation to the Study Objectives

The completed system addresses the primary objective of centralizing basketball league operations. League, team, player, game, and statistical data are managed through related records and presented through administrative and public interfaces. This structure reduces the need to reconcile manually maintained schedules, standings, and statistics across separate files.

The role-based workflows address the objective of restricting management operations to appropriate users. Registration codes support account creation for designated roles, and coach-issued player codes associate registrations with the issuing coach. Administrators also have account and verification controls. The completed registration flow therefore combines user-submitted account information with authorized review rather than treating a code alone as proof of eligibility.

Automated standings, tie-breaker eligibility, bracket generation, and winner advancement address the tournament-management objective. The edge-case tests are important to this result: they show that the calculations and lifecycle operations account for unplayed games, tied scores, replacement brackets, and archived data rather than only the simplest tournament path.

Live scoring, player-stat recording, public game information, and schedule announcements address the objectives of timely updates and statistical tracking. Reports and public pages provide ways to use the stored information beyond the management screens. However, the system's event-based updates were not evaluated using a measured latency benchmark, and no stress-test result is presented.

The implemented registration workflow should be described precisely in the final manuscript. Coaches can issue player codes and review associated players; administrators can also manage registration codes and account verification. Thus, player onboarding is not exclusively a manual coach-entered roster process. If exclusive coach-controlled registration is a formal project requirement, the scope statement and system permissions should be reconciled before submission.

## 4.4 Scope and Interpretation of the Results

The results in this chapter establish functional behavior and selected integration behavior in the development environment. They do not establish production-scale availability, performance under a specified number of simultaneous users, a formal penetration-test result, or a numerical user-satisfaction score. The study's planned stakeholder evaluation should be reported separately using the completed questionnaires and the prescribed statistical treatment. Feature-priority survey data should not be presented as user-acceptance test results.

The current system is designed for basketball league operations. Eligibility decisions still require authorized human review, and the system does not include predictive analytics or automated scouting. These boundaries are consistent with the stated project scope and should be considered when interpreting the results.
