# Software Engineering Puzzles

Challenge yourself with interactive software engineering puzzles!

## Your Task

Read puzzles from `games/puzzles/puzzles.json` and run an interactive puzzle session.

### Puzzle Types

1. **Command Match**: Match commands to their purposes
2. **Code Completion**: Fill in missing code
3. **Git Graph Detective**: Analyze git history
4. **Bug Hunt**: Find bugs in code snippets
5. **Workflow Order**: Put steps in correct order

### Session Flow

1. **Puzzle Selection**:
   - Ask for puzzle type preference or random
   - Filter by completed lectures
   - Offer difficulty selection

2. **Puzzle Presentation**:
   - Clear instructions
   - All necessary information displayed
   - Code snippets formatted properly

3. **Solution Input**:
   - Accept answers in appropriate format
   - Allow multiple attempts for partial credit

4. **Feedback**:
   - Show correct answers
   - Explain the reasoning
   - Award points based on accuracy

### Points System

- Easy puzzles: 15-20 points
- Medium puzzles: 20-25 points
- Hard puzzles: 30-35 points
- Partial credit available

### Example: Bug Hunt

```
🔍 Bug Hunt Challenge

Find the bug in this test:

def test_calculation():
    result = calculate_energy(10, 20)
    assert result = 200

What's wrong with this code?
```

### Example: Git Graph

```
🌳 Git Graph Detective

Given this git log output:
* abc1234 Merge branch 'feature' into main
|\
| * def5678 Add new analysis function
| * ghi9012 Implement data loading
* | jkl3456 Fix typo in README
|/
* mno7890 Initial commit

How many commits are on 'feature' that aren't on main?
```

Start a puzzle challenge now!
