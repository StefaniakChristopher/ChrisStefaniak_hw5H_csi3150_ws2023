### OVERVIEW

It is often that individuals need to memorize information. This application is a short quiz that tests the user on 5 different programming questions. There is a heavy emphasis on memory since there is a time limit on each question. The user can immediately see their score upon completion and can retake the quiz as many times as they'd like.

---

### FUNCTIONAL FEATURES

- The quiz is initiated by pressing "Start Quiz" and the app then displays the rules.
- From here, the user can press "Exit Quiz" or "Continue"
  - "Exit Quiz" takes the user back to "Start Quiz" screen
- Upon clicking continue, the user is presented with the first question, which has a 15 second time limit
  - If the time limit is reached, the answer is marked wrong and the correct answer is revealed
- The user can select any of the 4 answers by clicking on one
  - If the answer is wrong, then the answer is shown as wrong and the correct answer is revealed
  - If the answer is correct, then the system confirms that it is the correct answer to the user
- After an option is selected or time limit has been reached, the "Next Que" button appears, which takes the user to the next question
- The same process happens for each question until the final question, after which the score is displayed and the user gets two options:
  - "Replay Quiz" causes the quiz to restart at the first question
  - "Quit Quiz" causes the quiz to be reset to the "Start Quiz" screen

---

### FILE STRUCTURE

There are four primary files in this application

- styles.css
  - Linked to index.html to style the page and to have animations
- questions.js
  - Contains an array of question objects
  - Linked to index.html for diplaying on the page
- quizApp.js
  - Contains main logic of the application
  - Linked to index.html
- index.html
  - Sole page of the application

---

### index.html

Contains all the seperate boxes found in the application

- Stylesheet, javascript and fonts are imported in the head tag
- The first div is the "Start Quiz" button
- Second div is the rules section, which is divided into 3 divs
  - The header
  - The rules themselves
  - The buttons
- The third main div is the quiz box, which is also divded into three sections
  - The header: which is divided into three more divs
    - The header text
    - Time left counter
    - Progress bar
  - The question section: which has two divs
    - Question itself
    - Option list
  - Footer: which has 2 divs
    - Current question number
    - Next question button
- Last main div is the result box, which has four sub divs
  - Crown icon
  - Message stating the completion of quiz
  - Div for the total score in the quiz
  - Div for the replay and quit buttons

---

### questions.js

Contains an array of 5 question objects that contain the following information:

- Question number
- Question itself
- Correct Answer
- List of possible responses

---

### quizApp.js

- The first lines are extracting the html elements as variables
- The next portion contains all of the event listeners:
  - Start button: shows the active info box
  - Exit Button: removes the active info box (takes user back to "Start Quiz")
  - Continue Button: shows the quiz box and the elements that go with it
  - Restart Quiz Button: hides result box and shows quiz box again and reinitializes it... resets all quiz control variables
  - Quit quiz: reloads the window which causes the user to go back to the "Start Quiz" screen
  - Next Button: increments question count, displays the next question, and reset all the concerned elements
- Variables are initialized to control various quiz operations such as:
  - Score
  - Timer
  - Question
  - Question count
  - Timer line
- Functions are defined that used within the event listeners
  - showQuestions: Takes an index input and displays the question at that index
    - Uses a span tag to display the actual question
    - Uses a series of divs containing spans to display the question options
    - Create right and wrong ticks
  - optionSelected: is called when user selects a quiz option
    - Clears the time counter
    - Compare the user answer to the correct answer
      - If answer correct, give user a point and the green color is applied to the selected option
      - If answer incorrect, the red color is applied to the selected option
    - For loop is ran to find the correct answer and apply the color green and the check mark to it
  - showResult: shows the score result for the quiz
    - Hides the quiz box, info box, and displays result box
    - Displays different messages based on how many points the user got
  - startTimer: starts the timer for the questions and handles the "out of time" condition
    - The timer is initialized to decrement every second and if the timer goes below 9, a 0 is added in front of the number
    - If the timer reaches below 0, then the correct answer is revealed, the options are disabled, and the next question button is shown
  - startTimerLine: starts the timer line
    - Creates a new timer that increments over time and uses that increment to increase the width of a line
  - queCounter: displays to the user what question their on
    - Takes the current index and displays it on the bottom and puts it out of the total questions

---

### styles.css

In order of appearance:

- Import google fonts and reset browser defaults
- Changes color of the body and selection when highlighted by the user
- Centers the position of all displayed boxes
- Ensure that the active boxes stay on top of the regular boxes
- Styles the "Start Quiz" button
- Info box is applied a transition, scaled down, and set to a fixed width
- Both the info box and title are set to a width of 100% and a height of 60px
  - They are also center using flex
- For info related items, font sizes, padding, and margins are configured
- Info box buttons are adjusted by using flex
  - These butons are then style with a transition
- The quiz box is scaled down and has a fixed width of 550px
- Header of the quiz box has a 2 in Z-index and is adjusted using flex
  - Header is also styled
- The Timer's position is set using flex and the height and width are fixed
  - Timer text is styled
  - The timer time display is styled
  - Time line has position set to absolute and height to 3px
- Section is given padding and the question text is styled
  - The option list is set to display:block
  - The individual options are styled and centered with flex
  - Various colors are applied based on the state of the option
  - The tick and cross icons are styled
- Footer of the question box is displayed using a fixed height and flex
  - The span of the question counter is displayed using flex
  - Paragraph tag inside of the span has padding changed and font weight assigned
  - The button in the footer is styled and it is transformed to 95%
  - Hover effect is applied to button and button properties are changed when the button is shown
- Result box is aligned with both flex and transform translate and it is also styled
  - Font sizes and options are set for various text fields inside the result box
  - The buttons are displayed using flex and are also styled
  - The buttons are applied different colors based on what state they are in
