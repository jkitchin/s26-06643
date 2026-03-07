# Software Engineering Trivia

Play a trivia game to test your software engineering knowledge!

## Your Task

Read the trivia pool from `games/trivia/trivia-pool.json` and run an interactive trivia session.

### Game Rules

1. **Question Selection**: Select 5 random questions appropriate for the student's progress
   - Check which lectures have been completed (ask if unknown)
   - Only include questions from completed lectures
   - Mix difficulties: 2 easy, 2 medium, 1 hard

2. **Question Format**: For each question:
   - Show the character mascot and their icon
   - Display the question clearly
   - Show numbered options (1-4)
   - Wait for student response

3. **Feedback**:
   - Correct: Celebrate and show points earned (+10, +5 streak bonus if applicable)
   - Incorrect: Show correct answer with explanation
   - Include character's study tip when relevant

4. **Scoring**:
   - 10 points per correct answer
   - +5 bonus for streaks of 3+ correct
   - Track total and display at end

5. **End of Round**:
   - Show final score out of possible points
   - Highlight any weak areas
   - Suggest review topics if score < 70%

### Character Integration

Each question has an associated character:
- **Terry Terminal**: Command line wisdom
- **Gina Git**: Version control expertise
- **Tessa Test**: Testing best practices
- **Doc Douglas**: Documentation advice
- **And others...**

### Example Interaction

```
🔀 Gina Git asks:

What command shows the current status of your repository?

1. git log
2. git status
3. git show
4. git info

Your answer (1-4):
```

Start the trivia game now!
