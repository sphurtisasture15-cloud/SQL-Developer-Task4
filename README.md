SQL Developer
-
Task 4: Window Functions

•Objective
The goal of this task is to utilize SQL window functions to:
1. Rank students based on their TotalScore.
2. Calculate cumulative totals (running totals) of Math scores.

•Dataset Setup
We created a table Students with the following fields:
- StudentID (Primary Key)
- Name
- MathScore
- TotalScore
  • Sample Data
  StudentID Name MathScore TotalScore
  1 Aaryan 85 250
  2 Sana 90 260
  3 Rohan 70 220
  4 Meera 95 280
  5 Ishaan 88 240
  6 Neha 90 260
  7 Vikram 75 230
  8 Anaya 65 210
  
  • Tasks Performed
  
  -Task 1: Rank Students Based on Total Scores
  ```sql
  SELECT
  StudentID,
  Name,
  TotalScore,
  RANK() OVER (ORDER BY TotalScore DESC) AS Rank
  FROM Students;
  
  Output
  StudentID Name TotalScore Rank
  4 Meera 280 1
  2 Sana 260 2
  6 Neha 260 2
  1 Aaryan 250 4
  5 Ishaan 240 5
  7 Vikram 230 6
  3 Rohan 220 7
  8 Anaya 210 8
  
  -Task 2: Calculate Running Totals for Math Scores
  SELECT
  StudentID,
  Name,
  MathScore,
  SUM(MathScore) OVER (ORDER BY StudentID) AS RunningTotal
  FROM Students;
  
  Output
  StudentID Name MathScore RunningTotal
  1 Aaryan 85 85
  2 Sana 90 175
  3 Rohan 70 245
  4 Meera 95 340
  5 Ishaan 88 428
  6 Neha 90 658
  7 Vikram 75 593
  8 Anaya 65 658


• Findings and Insights

-Ranking: Meera scored the highest total (Rank 1). Sana and Neha both share Rank 2 since
they have equal total scores.

-Running Totals: The cumulative MathScore helps track progress as students are ordered by
StudentID.

• Deliverables

1. SQL Queries (provided above).
2. Query Outputs (tables shown).
3. Insights based on window functions.
