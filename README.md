# IT3203
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IT3203 - Quiz Page</title>
    <link rel="stylesheet" href="style.css">
    <script>
        // JavaScript for quiz logic
        function submitQuiz(event) {
            event.preventDefault(); // Prevent page reload

            let score = 0;
            let totalQuestions = 5;
            let answers = {
                q1: "b",
                q2: "HyperText Markup Language",
                q3: ["a", "b"],
                q4: "a",
                q5: "a"
            };

            // Question 1
            if (document.querySelector('input[name="q1"]:checked')?.value === answers.q1) {
                score++;
            }

            // Question 2 (text input)
            if (document.getElementById("q2").value.trim().toLowerCase() === answers.q2.toLowerCase()) {
                score++;
            }

            // Question 3 (multiple correct answers)
            let selectedQ3 = Array.from(document.querySelectorAll('input[name="q3"]:checked')).map(el => el.value);
            if (JSON.stringify(selectedQ3.sort()) === JSON.stringify(answers.q3.sort())) {
                score++;
            }

            // Question 4
            if (document.querySelector('input[name="q4"]:checked')?.value === answers.q4) {
                score++;
            }

            // Question 5
            if (document.querySelector('input[name="q5"]:checked')?.value === answers.q5) {
                score++;
            }

            // Display Result
            let resultText = `<h3>Your Score: ${score}/${totalQuestions}</h3>`;
            resultText += score >= 4
                ? "<p>Congratulations! You passed the quiz.</p>"
                : "<p>Oops! You need to review the material and try again.</p>";

            resultText += `<h4>Answers:</h4>
                <p>Question 1: ${answers.q1}</p>
                <p>Question 2: ${answers.q2}</p>
                <p>Question 3: ${answers.q3.join(", ")}</p>
                <p>Question 4: ${answers.q4}</p>
                <p>Question 5: ${answers.q5}</p>`;

            document.getElementById("result").innerHTML = resultText;
        }

        function restartQuiz() {
            document.getElementById("quizForm").reset();
            document.getElementById("result").innerHTML = "";
        }
    </script>
</head>
<body>
    <header>
        <h1>Welcome to My Website - IT3203</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="topic1.html">Topic 1</a></li>
                <li><a href="topic2.html">Topic 2</a></li>
                <li><a href="resources.html">Resources</a></li>
                <li><a href="quiz.html">Quiz</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <h2>Self-Assessment Quiz</h2>
        <form id="quizForm" onsubmit="submitQuiz(event)">
            <h3>1. What is HTML?</h3>
            <label><input type="radio" name="q1" value="a"> A programming language</label><br>
            <label><input type="radio" name="q1" value="b"> A markup language</label><br>
            <label><input type="radio" name="q1" value="c"> A database system</label><br>

            <h3>2. Fill in the blank: HTML stands for __________.</h3>
            <input type="text" name="q2" id="q2">

            <h3>3. Which of these are CSS properties? (Multiple correct answers)</h3>
            <label><input type="checkbox" name="q3" value="a"> font-size</label><br>
            <label><input type="checkbox" name="q3" value="b"> color</label><br>
            <label><input type="checkbox" name="q3" value="c"> header</label><br>

            <h3>4. What is the purpose of the 'alt' attribute in the &lt;img&gt; tag?</h3>
            <label><input type="radio" name="q4" value="a"> To provide a text alternative for images</label><br>
            <label><input type="radio" name="q4" value="b"> To specify the width of an image</label><br>
            <label><input type="radio" name="q4" value="c"> To add a link to an image</label><br>

            <h3>5. What does CSS stand for?</h3>
            <label><input type="radio" name="q5" value="a"> Cascading Style Sheets</label><br>
            <label><input type="radio" name="q5" value="b"> Creative Styling Sheets</label><br>
            <label><input type="radio" name="q5" value="c"> Computer Style Sheets</label><br>

            <button type="submit">Submit Quiz</button>
        </form>

        <div id="result"></div>
        <button onclick="restartQuiz()">Restart Quiz</button>
    </main>

    <footer>
        <p>&copy; 2025 My Website. All Rights Reserved.</p>
    </footer>
</body>
</html>

