# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.   
   The purpose of the game is for the user to guess a secret number within a selected difficulty range. The game gives feedback after each guess and tracks attempts and score.

- [ ] Detail which bugs you found.
  I found that the higher/lower hint messages were reversed. When the guess was too high, the game told the user to go higher instead of lower. I also found that when the hint option was turned off, the game did not clearly tell the user their guess was incorrect. It only removed attempts. Which caused confusion of if the user won or not.



- [ ] Explain what fixes you applied.
  I moved the main game logic into `logic_utils.py`, fixed the high/low hint logic, and updated the app so the user still receives basic feedback when hints are turned off. I also updated the tests to match the function’s return values.



## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. The user starts the app and selects a difficulty level.
2. The game creates a secret number within the selected range.
3. The user enters a guess of 40.
4. If the secret number is higher than 40, the game returns "Too Low" and displays "Go HIGHER."
5. The user enters a guess of 70.
6. If the secret number is lower than 70, the game returns "Too High" and displays "Go LOWER."
7. The game updates the score and attempts after each guess.
8. If the user turns off hints, the game still displays basic feedback saying the guess was incorrect.
9. When the user guesses the correct number, the game displays a winning message and final score.
10. The user can click "New Game" to reset and play again.


## 🧪 Test Results

```text
$ python3 -m pytest

3 passed in 0.01s
```

## 🚀 Stretch Features

