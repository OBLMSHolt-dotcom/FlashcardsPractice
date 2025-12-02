<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Module 4 Vocabulary Flashcards</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: #f0f8ff; /* Light blue background */
            padding: 20px;
        }
        .flashcard-container {
            perspective: 1000px;
            margin: 20px 0;
        }
        .flashcard {
            width: 300px;
            height: 200px;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.6s;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            border-radius: 10px;
        }
        .flashcard.flipped {
            transform: rotateY(180deg);
        }
        .card-face {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 10px;
            padding: 15px;
            box-sizing: border-box;
            text-align: center;
            font-size: 1.1em;
            font-weight: bold;
        }
        .card-front {
            background-color: #ffd700; /* Gold color */
            color: #333;
            border: 3px solid #ccaa00;
        }
        .card-back {
            background-color: #ffffff; /* White color */
            color: #333;
            transform: rotateY(180deg);
            border: 3px solid #333;
            font-weight: normal;
            font-size: 1em;
        }
        .card-back p {
            margin: 5px 0;
        }
        .navigation {
            margin-top: 10px;
        }
        .navigation button {
            padding: 10px 20px;
            margin: 0 10px;
            font-size: 1em;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: #4682b4; /* Steel blue */
            color: white;
            transition: background-color 0.3s;
        }
        .navigation button:hover {
            background-color: #396a94;
        }
        #card-counter {
            margin-bottom: 10px;
            font-size: 1.2em;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <h1>📊 Module 4: Key Vocabulary Practice</h1>
    <div id="card-counter">Card 1 of 5</div>

    <div class="flashcard-container">
        <div class="flashcard" id="flashcard" onclick="flipCard()">
            <div class="card-face card-front" id="card-front"></div>
            <div class="card-face card-back" id="card-back"></div>
        </div>
    </div>

    <div class="navigation">
        <button onclick="prevCard()">Previous</button>
        <button onclick="nextCard()">Next</button>
    </div>

    <script>
        const vocabulary = [
            {
                term: "Statistical Question",
                definition: "A question that anticipates an answer based on **data that vary**."
            },
            {
                term: "Ratio",
                definition: "A **comparison of two quantities** that uses division."
            },
            {
                term: "Measures of Center",
                definition: "A single value used to describe the center of a data set. Examples include the **mean, median, and mode**."
            },
            {
                term: "Measures of Variability",
                definition: "A single value used to describe the spread or dispersion of a data set. Examples include **range** and **mean absolute deviation (MAD)**."
            },
            {
                term: "Percent Error",
                definition: "A measure of the difference between an estimated value (like experimental probability or a statistic) and the actual value (like theoretical probability or a parameter), often used to compare them."
            }
        ];

        let currentIndex = 0;
        const flashcard = document.getElementById('flashcard');
        const cardFront = document.getElementById('card-front');
        const cardBack = document.getElementById('card-back');
        const cardCounter = document.getElementById('card-counter');

        function updateCardContent() {
            const card = vocabulary[currentIndex];
            cardFront.innerHTML = `<h2>${card.term}</h2>`;
            cardBack.innerHTML = `<p>${card.definition}</p>`;
            cardCounter.textContent = `Card ${currentIndex + 1} of ${vocabulary.length}`;
            flashcard.classList.remove('flipped'); // Ensure the card is showing the front when content changes
        }

        function flipCard() {
            flashcard.classList.toggle('flipped');
        }

        function nextCard() {
            currentIndex = (currentIndex + 1) % vocabulary.length;
            updateCardContent();
        }

        function prevCard() {
            currentIndex = (currentIndex - 1 + vocabulary.length) % vocabulary.length;
            updateCardContent();
        }

        // Initialize the first card
        updateCardContent();
    </script>

</body>
</html>
