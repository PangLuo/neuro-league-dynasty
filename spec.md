# Football Club Manager Board Game – Quick Gameflow

## Overview
Manage a men’s football club and compete against an AI-controlled club in a strategic draft and formation game. Implemented as a Streamlit app.

## Agents
- **C** – Computer-controlled club manager.  
- **A** – Game administrator: lists major European teams, dynamically generates player draft pools with a range of skill levels, and enforces rules.  
- **S** – Sportscaster: introduces clubs/players using `google_search` for historical and up-to-date info.

## Gameflow

### 1. Club Selection
1. **A** lists major European teams.  
2. **H** picks a club.  
3. **C** automatically selects the chosen club’s arch-rival.

### 2. Player Draft
- Draft consists of **3 rounds**.  
- Each round:  
  1. **A** dynamically generates a pool of 16 players (on the fly) with varying skill levels.  
  2. **H** and **C** alternate picks.  
  3. **Once picked, a player cannot be replaced.**  
  4. **H** or **C** may choose to stop picking; the other may continue. If both stop, the round ends.  
- Player positions and stars:  
  - Natural positions: Forward, Midfielder, Defender, Goalkeeper  
  - Stars: 1–6  
    - Natural position → full stars  
    - Out-of-position → stars −1  
    - Non-GK playing GK → stars = 1  
    - GK playing other → stars = 1  
- **Rule:** If H or C cannot draft 18 players, they **lose immediately**.

### 3. Formation
- Legal formations: **4-4-2**, **4-3-3**, **3-5-2**, **3-4-3**, **3-3-4**.

## Objective
Assemble the strongest team possible. For now, the objective is to **maximize the team’s total actual star rating**.
