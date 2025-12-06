# Football Club Manager Board Game – Quick Gameflow

## Overview
Manage a men’s football club and compete against an AI-controlled club in a strategic draft and formation game. Implemented as a **Streamlit app**.

## Agents
- **C** – Computer-controlled club manager.  
- **A** – Game administrator: lists major European teams, dynamically generates player draft pools with a range of skill levels, and enforces rules.  
- **S** – Sportscaster: introduces clubs and players using `google_search` for historical and up-to-date information.

## Gameflow

### 1. Club Selection
1. **A** lists major European teams.  
2. **H** (human player) picks a club.  
3. **C** automatically selects the chosen club’s arch-rival.

### 2. Player Draft
- Draft consists of **3 rounds**.  
- Each round:  
  1. **A** dynamically generates a pool of 16 players with varying skill levels. Use a pyramid distribution where higher-rated players are increasingly rare:
6★ players should be extremely rare (elite/world class talent)
5★ players should be rare (excellent)
4★ players should be uncommon (very good)
3★ players should be fairly common (average/solid)
2★ and 1★ players should make up the bulk of the pool (below average to poor)
  2. **H** and **C** alternate picks.  
  3. **Once a player is picked, they cannot be replaced.**  
  4. **H** or **C** may choose to stop picking; the other may continue. If both stop, the round ends.  

- **Player Positions and Ratings:**  
  - Natural positions: Forward, Midfielder, Defender, Goalkeeper  
  - Stars: 1–6  
    - Playing in natural position → full stars  
    - Out-of-position → stars −1  
    - Non-GK playing as GK → stars = 1  
    - GK playing in another position → stars = 1  

- **Rule:** **H** and **C** must each draft exactly 18 players. Failing to do so results in an immediate loss.

### 3. Match Day
The match is played in **three thirds**:

1. **Midfield Battle**  
   - Roll **2 dice** for each side.  
   - Add the dice results to the total stars of each side’s midfield line-up.  
   - The side with the higher total wins the third.  

2. **Attack vs Defence**  
   - The winner of the midfield third goes on the attack.  
   - Roll **2 dice** for each side and add the results to the attack and defence stars.  
   - Compare totals: the higher total wins the third.  
   - If the midfield third is a draw, **H** attacks first.  

3. **Goalkeeper**  
   - Goalkeeper stars count towards the defensive total in all thirds.  

- **Early Victory:**  
  - If **H** or **C** wins the first two thirds, the match ends immediately.  
  - If the score is tied (1–1, or 0.5–1.5 with a drawn third), the final third is played to determine the winner.

- **Dice Doubles – Injuries:**  
  - If a roll results in doubles (1+1, 2+2, 3+3, etc.), a potential injury occurs.  
  - Count from the left in your line-up. If a player occupies the slot corresponding to the number on the doubles dice (e.g., 1+1 → leftmost player, 2+2 → second leftmost), that player is injured.  
  - A substitute from the bench replaces the injured player, and their stars count in the match.

## Objective
Assemble the strongest team possible to win the match.
