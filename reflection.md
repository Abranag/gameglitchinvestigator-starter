# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- When I first ran the game, it appeared to work, but after testing it I noticed several bugs. The biggest issue was that the hint messages were backwards. When my guess was too high, the game told me to go higher, and when my guess was too low, it told me to go lower. I also noticed that when the hint option was turned off, the game did not clearly tell me that my guess was wrong. Instead, it only removed attempts until the game ended.


**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| 60 |      "Go lower"         incorrct hint      none
|  40   |    too low        |   incorrct hint |   none                 |
| wrong guess|    tell player the guess is wrong             |      remove attempts            | none                  |

---

## 2. How did you use AI as a teammate?

- One correct suggestion was moving the game logic into logic_utils.py and fixing the hint logic inside check_guess(). I verified that suggestion by running the game and confirming that higher guesses displayed "Go LOWER" and lower guesses displayed "Go HIGHER." One misleading suggestion was assuming the existing tests would work without modification. After reviewing the code, I found that check_guess() returns both an outcome and a message, so the tests had to be updated to unpack both values. I verified the correction by running pytest and confirming that all tests passed.

---

## 3. Debugging and testing your fixes

- I decided a bug was fixed only after testing it in the game and confirming that the behavior changed. For the hint bug, I used the Developer Debug Info section to see the secret number and then intentionally entered guesses above and below the secret number. I also ran automated tests using pytest. I tested winning guesses, guesses that were too high, and guesses that were too low. The tests passed successfully and confirmed that the updated game logic worked correctly. AI helped me understand why the tests needed to be updated and how to verify that the repaired functions were returning the correct values.

---

## 4. What did you learn about Streamlit and state?

- I learned that Streamlit reruns the entire script whenever the user interacts with the app. Because of that, values can reset unless they are stored in st.session_state. I would explain session state to a friend as a way to remember important information, such as scores, attempts, or secret numbers, even when the page reruns.

---

## 5. Looking ahead: your developer habits

- One strategy I want to reuse in future projects is testing changes immediately after making them. Running the application and using pytest helped me confirm that fixes actually worked instead of assuming they worked. Next time I work with AI, I will verify every suggestion more carefully before applying it. AI can be helpful, but it can also make assumptions that do not match the code. This project showed me that AI-generated code should not be trusted automatically. Even when code runs, it can still contain logic errors that require testing and debugging by the developer.
