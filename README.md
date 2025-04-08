# IT3203

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IT3203 - My Website</title>
    <style>
        /* General styling for the website */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        header, footer {
            text-align: center;
            background-color: #333;
            color: white;
            padding: 10px 0;
        }

        h1 {
            margin: 0;
        }

        nav ul {
            list-style: none;
            padding: 0;
        }

        nav ul li {
            display: inline;
            margin: 0 15px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
        }

        main {
            margin: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }

        button:hover {
            background-color: #45a049;
        }

        #result {
            margin-top: 20px;
        }

        form {
            margin: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            color: #333;
        }
    </style>
    <script>
        // JavaScript for quiz logic
        function submitQuiz(event) {
            event.preventDefault(); // Prevent page reload

            let score = 0;
            let totalQuestions = 5;
            let answers = {
                q1: "b", // Correct answer for question 1
                q2: "HyperText Markup Language", // Correct answer for question 2
                q3: ["a", "b"], // Correct answers for question 3 (multiple choices)
                q4: "a", // Correct answer for question 4
                q5: "a" // Correct answer for question 5
            };

            // Question 1
            if (document.querySelector('input[name="q1"]:checked')?.value === answers.q1) {
                score++;
            }

            // Question 2 (fill in the blank)
            if (document.getElementById("q2").value.trim().toLowerCase() === answers.q2.toLowerCase()) {
                score++;
            }

            // Question 3 (multiple choices)
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
            if (score >= 4) {
                resultText += "<p>Congratulations! You passed the quiz.</p>";
            } else {
                resultText += "<p>Oops! You need to review the material and try again.</p>";
            }

            // Display detailed answers (optional)
            resultText += `<h4>Answers:</h4>
                           <p>Question 1: Correct answer: ${answers.q1}</p>
                           <p>Question 2: Correct answer: ${answers.q2}</p>
                           <p>Question 3: Correct answers: ${answers.q3.join(", ")}</p>
                           <p>Question 4: Correct answer: ${answers.q4}</p>
                           <p>Question 5: Correct answer: ${answers.q5}</p>`;

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
        <h1>Welcome to My Website IT3203</h1>
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
            <h2>1. What is HTML?</h2>
            <label><input type="radio" name="q1" value="a"> A programming language</label><br>
            <label><input type="radio" name="q1" value="b"> A markup language</label><br>
            <label><input type="radio" name="q1" value="c"> A database system</label><br>

            <h2>2. Fill in the blank: HTML stands for __________.</h2>
            <input type="text" name="q2" id="q2">

            <h2>3. Which of these are CSS properties? (Multiple correct answers)</h2>
            <label><input type="checkbox" name="q3" value="a"> font-size</label><br>
            <label><input type="checkbox" name="q3" value="b"> color</label><br>
            <label><input type="checkbox" name="q3" value="c"> header</label><br>

            <h2>4. What is the purpose of the 'alt' attribute in the <img> tag?</h2>
            <label><input type="radio" name="q4" value="a"> To provide a text alternative for images</label><br>
            <label><input type="radio" name="q4" value="b"> To specify the width of an image</label><br>
            <label><input type="radio" name="q4" value="c"> To add a link to an image</label><br>

            <h2>5. What does CSS stand for?</h2>
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
