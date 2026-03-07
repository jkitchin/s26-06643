# Software Forge Honors - Progress Tracker

View your progress toward badges and ranks!

## Your Task

Read progress from `software-forge-honors/tracking.json` and display achievement status.

### Information to Display

1. **Current Rank**: Display current rank with icon

2. **Badge Progress**:
   For each of the 5 badges:
   - 🔧 Toolsmith (Lectures 00-02)
   - 📦 Packager (Lectures 03-04)
   - ✅ Tester (Lectures 05-07)
   - 🤝 Collaborator (Lectures 08-09)
   - 📚 Documenter (Lectures 10-11)

   Show for each:
   - Quiz average vs. required 75%
   - Assignments completed
   - Badge activity status
   - Overall progress %

3. **Next Steps**:
   - What's needed to earn next badge
   - What's needed for next rank
   - Suggested activities

4. **Game Stats** (if available):
   - Trivia high scores
   - Adventure chapters completed
   - Flashcard review status
   - Scavenger hunts finished

### Display Format

```
═══════════════════════════════════════════
     SOFTWARE FORGE HONORS PROGRESS
═══════════════════════════════════════════

Current Rank: 📦 Software Crafter
Badges Earned: 2 of 5

─────────────────────────────────────────────
BADGE PROGRESS
─────────────────────────────────────────────

🔧 Toolsmith             ████████████ EARNED
   Quizzes: 85% | Assignments: 3/3 | Activity: ✓

📦 Packager              ████████████ EARNED
   Quizzes: 80% | Assignments: 2/2 | Activity: ✓

✅ Tester                ████████░░░░ 75%
   Quizzes: 78% | Assignments: 2/3 | Activity: pending

🤝 Collaborator          ░░░░░░░░░░░░ 0%
   Lectures not yet completed

📚 Documenter            ░░░░░░░░░░░░ 0%
   Lectures not yet completed

─────────────────────────────────────────────
NEXT STEPS
─────────────────────────────────────────────

To earn Tester badge:
• Complete assignment for lecture 07
• Choose and complete a badge activity:
  - Add tests to existing code
  - Code quality audit
  - Class design project

To reach Software Engineer rank:
• Earn 2 more badges
• Complete a field experience
• Submit software project capstone

─────────────────────────────────────────────
GAME STATISTICS
─────────────────────────────────────────────

Trivia:        Best: 42/50 | Games: 5
Adventure:     Chapters: 4/8 | Points: 425
Flashcards:    Cards studied: 89 | Due: 12
Scavenger:     Hunts: 3/11 | Points: 175

─────────────────────────────────────────────
GITHUB ACTIVITY
─────────────────────────────────────────────

Commits: 47 | PRs: 5 | Reviews: 3

═══════════════════════════════════════════
```

### Commands

- `/achievements` - Show full progress
- `/achievements badges` - Badge details only
- `/achievements ranks` - Rank requirements only
- `/achievements next` - Next steps only

Show the student's progress now!
