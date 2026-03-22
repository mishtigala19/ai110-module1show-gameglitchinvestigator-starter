# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

The first time I ran the game, the interface looked clean and functional, but as soon as I started playing, several issues became obvious. The game did not behave consistently, and the logic behind the guesses seemed incorrect, which made it difficult to actually win.

One major bug was that the hints were incorrect. For example, when the secret number shown in Developer Debug Info was 52 and I guessed 99, the game told me to "Go HIGHER!" even though my guess was already higher than the secret number. I expected it to say "Go LOWER," so this showed that the comparison logic was broken.

Another issue was that the attempt count was inconsistent. The main interface showed one number of attempts remaining, while the Developer Debug Info showed a different number. This made it confusing to understand how many guesses I actually had left.

Additionally, the game state behaved strangely. The history of guesses did not feel reliable, and it seemed like the internal state was not updating properly or was being reset unexpectedly. Overall, the game appeared functional on the surface but had multiple logic and state management issues underneath.

---

## 2. How did you use AI as a teammate?

I used ChatGPT and VS Code Copilot to help me understand and debug the code. I mainly used them to explain what certain parts of the code were doing, suggest fixes, and help me think through the logic step by step instead of guessing blindly.

One example of a correct AI suggestion was identifying that the secret number was being reset on every interaction because of how Streamlit reruns the script. The AI suggested using session state to store the secret number, and after applying that idea, I verified it by checking that the secret number stayed the same across multiple guesses in the Developer Debug Info.

One example of an incorrect or misleading suggestion was when the AI initially suggested changing only the comparison logic for the hints without addressing the state issue. Even after modifying the hint logic, the game still behaved incorrectly because the secret number kept changing. I verified this by observing the debug info and realizing the root issue was deeper than just the comparison logic.

---

## 3. Debugging and testing your fixes

I decided a bug was fixed only if both the visible behavior in the game and the Developer Debug Info were consistent. For example, if I fixed the hint logic, I checked that the hint matched the actual relationship between the guess and the secret number.

One test I ran manually was guessing a number higher than the secret number and verifying that the game correctly responded with "Go LOWER." I also checked that the secret number stayed the same after multiple guesses, which confirmed that the state bug was fixed.

AI helped me design tests by suggesting specific cases, like comparing a guess of 60 against a secret of 50 to verify the "Too High" condition. It also helped me understand what a good test should look like and how to validate both the game logic and state behavior.

---

## 4. What did you learn about Streamlit and state?

I learned that Streamlit reruns the entire script every time a user interacts with the app, such as clicking a button. This means that variables reset unless they are stored in something persistent like session state.

I would explain session state as a way for the app to "remember" values between interactions. Without it, things like the secret number or attempts would restart every time you click submit, which is why the game was behaving incorrectly.

---

## 5. Looking ahead: your developer habits

One habit I want to reuse is testing each fix step by step instead of trying to fix everything at once. Breaking problems down and verifying each change made debugging much clearer and more manageable.

Next time I work with AI on a coding task, I would be more careful about not blindly trusting the first suggestion. Instead, I would verify each suggestion by testing the actual behavior in the app before assuming it was correct.

This project changed the way I think about AI-generated code because I realized that even if code looks correct at first, it can still have hidden logic and state issues. It showed me that AI is helpful, but I still need to think critically and test everything myself.