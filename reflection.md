# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.


## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

1. New game button wasn not working
2. While "Submit Guess" gives feedback, as i got a closer to the exact value and was entering the only suggested option the feedback was 


## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

1. I used Copilot
2. Fixed functions in logic_utils.py such as get_range_for_difficulty(), parse_guess(), check_guess() and update_score()
3. I dont think AI made any incorrect assumptions and was able to fix everything from the first tryu


---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---
1. By inspecting the code myself
2. By pytest tests such as test_guess_too_high(), test_guess_too_low. I ran automated tests after refactor and fix.
Outcome: 3 passed (win/high/low cases in test_game_logic.py).
What it showed: check_guess() now returns correct direction hints and “Win” correctly, so bug 2 is fixed.
I also opened app, used developer info secret, made guesses.
Confirmed “Submit Guess” now gives consistent hints and final win state, and “New Game” resets state fully.
3. AI suggested updating tests to inspect check_guess() return tuple (outcome + message), and to include assertions for messages containing LOWER/HIGHER.
That made incorrect hint logic explicit and assertable


## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

Streamlit reruns the whole script on each interaction (button click, input change), so code is evaluated top-to-bottom repeatedly.
Without session state, variables reset on each rerun, which makes stateful apps impossible


---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

1. Keep logic in separate module (logic_utils.py) and test small pure functions first
2. Ask AI for short pseudo-code and coverage cases first, then implement
3. This project showed AI-generated code can be a great starting point, but you must verify state flow and test assertions because subtle logic bugs