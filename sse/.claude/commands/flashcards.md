# Software Engineering Flashcards

Study software concepts with spaced repetition flashcards!

## Your Task

Read the flashcard decks from `games/flashcards/decks.json` and run an interactive study session.

### Study Modes

1. **By Deck**: Study a specific topic deck
2. **By Lecture**: Study cards from a specific lecture
3. **Review Due**: Cards due for review (spaced repetition)
4. **Quick Quiz**: Random selection across all decks

### Session Flow

1. **Deck Selection**:
   - Show available decks with card counts
   - Let student choose or recommend based on progress

2. **Card Presentation**:
   - Show the front (term/command)
   - Wait for student to indicate ready
   - Reveal the back (definition/purpose)

3. **Self-Assessment** (SM-2 inspired):
   - Again (1): Didn't know it - review soon
   - Hard (3): Got it with difficulty - review in 3 days
   - Good (5): Got it - review in 5 days
   - Easy (7): Too easy - review in 7 days

4. **Session Summary**:
   - Cards studied
   - Performance breakdown
   - Recommended next review time

### Available Decks

- Terminal Essentials
- Git Fundamentals
- Git Advanced (Gina Git)
- API Fundamentals
- Python Packaging (Vinny Virtual)
- Testing with pytest (Tessa Test)
- Code Quality (Rita Readable)
- Python Classes (Paula Pattern)
- GitHub Collaboration
- GitHub Actions (Wendy Workflow)
- Documentation (Doc Douglas)
- MCP (Morgan MCP)

### Example Interaction

```
📚 Flashcard Study Session

Deck: Git Fundamentals
Card 1 of 12

─────────────────────────
FRONT:
git reflog
─────────────────────────

[Press Enter when ready to see answer]

─────────────────────────
BACK:
Show all HEAD movements—your safety net for 'lost' commits
─────────────────────────

How well did you know this?
1 - Again (didn't know)
2 - Hard (struggled)
3 - Good (knew it)
4 - Easy (too easy)

Your rating (1-4):
```

Start your flashcard session now!
