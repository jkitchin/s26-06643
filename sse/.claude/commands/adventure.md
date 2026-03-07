# Software Forge Adventure

Embark on a choose-your-own-adventure through the Software Forge!

## Your Task

Read the adventure chapters from `games/adventure/chapters.json` and run an interactive story session.

### How It Works

1. **Chapter Selection**:
   - Check student's progress and completed lectures
   - Offer chapters that match their current knowledge
   - Allow continuing from saved progress or starting new

2. **Story Presentation**:
   - Read the chapter's narrative engagingly
   - Set the scene with the crisis context
   - Introduce characters naturally

3. **Decision Points**:
   - Present choices clearly with option letters (A, B, C, D)
   - Each choice represents a software engineering approach
   - Wait for student's decision

4. **Feedback**:
   - Optimal choice: Full points + explanation of why this approach is best
   - Good choice: Partial points + what was right and what could be better
   - Poor choice: Minimal points + learning moment about the mistake

5. **Scoring**:
   - Track points within chapter
   - Award bonus for completing chapters
   - Running total across the adventure

### Story Tone

- **Crisis-driven**: Real software engineering problems
- **Educational**: Each choice teaches a real concept
- **Professional**: Based on actual industry scenarios
- **Brief**: 3-5 minutes per chapter

### The Story

You're an apprentice at the Software Forge, facing real crises:
- Git disasters and code recovery
- Dependency nightmares
- Silent bugs in production
- Code review challenges
- Deployment failures
- Documentation debt

### Example Interaction

```
📖 Chapter 1: The Git Disaster

Your first week at the Forge, and chaos erupts. A junior developer
accidentally pushed API keys to the public repository...

[Story continues...]

How do you approach the recovery?

A) Use git reflog to find the lost commits
B) Check if anyone has a local copy
C) Reconstruct the code from memory
D) Restore from the last backup

Your choice (A/B/C/D):
```

Start or continue your adventure now!
