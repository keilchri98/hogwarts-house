# hogwarts.github.io

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>The Sorting Hat Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    .question {
      margin-bottom: 20px;
    }
    .result {
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>

<h1>The Sorting Hat</h1>
<div id="quiz">
  <div class="question" id="question1">
    <p>Q1) When I'm dead, I want people to remember me as:</p>
    <button onclick="answerQuestion(1, 1)">The Good</button>
    <button onclick="answerQuestion(1, 2)">The Great</button>
    <button onclick="answerQuestion(1, 3)">The Wise</button>
    <button onclick="answerQuestion(1, 4)">The Bold</button>
  </div>
  <div class="question" id="question2" style="display:none;">
    <p>Q2) Dawn or Dusk?</p>
    <button onclick="answerQuestion(2, 1)">Dawn</button>
    <button onclick="answerQuestion(2, 2)">Dusk</button>
  </div>
  <div class="question" id="question3" style="display:none;">
    <p>Q3) Which kind of instrument most pleases your ear?</p>
    <button onclick="answerQuestion(3, 1)">The violin</button>
    <button onclick="answerQuestion(3, 2)">The trumpet</button>
    <button onclick="answerQuestion(3, 3)">The piano</button>
    <button onclick="answerQuestion(3, 4)">The drum</button>
  </div>
  <div class="question" id="question4" style="display:none;">
    <p>Q4) Which road tempts you most?</p>
    <button onclick="answerQuestion(4, 1)">The wide, sunny grassy lane</button>
    <button onclick="answerQuestion(4, 2)">The narrow, dark, lantern-lit alley</button>
    <button onclick="answerQuestion(4, 3)">The twisting, leaf-strewn path through woods</button>
    <button onclick="answerQuestion(4, 4)">The cobbled street lined with ancient buildings</button>
  </div>
</div>
<div id="result" class="result"></div>

<script>
  let gryffindor = 0;
  let hufflepuff = 0;
  let ravenclaw = 0;
  let slytherin = 0;
  let currentQuestion = 1;

  function answerQuestion(question, answer) {
    if (question === 1) {
      if (answer === 1) hufflepuff++;
      else if (answer === 2) slytherin++;
      else if (answer === 3) ravenclaw++;
      else if (answer === 4) gryffindor++;
    } else if (question === 2) {
      if (answer === 1) {
        gryffindor++;
        ravenclaw++;
      } else if (answer === 2) {
        hufflepuff++;
        slytherin++;
      }
    } else if (question === 3) {
      if (answer === 1) slytherin++;
      else if (answer === 2) hufflepuff++;
      else if (answer === 3) ravenclaw++;
      else if (answer === 4) gryffindor++;
    } else if (question === 4) {
      if (answer === 1) hufflepuff++;
      else if (answer === 2) slytherin++;
      else if (answer === 3) gryffindor++;
      else if (answer === 4) ravenclaw++;
    }

    document.getElementById(`question${question}`).style.display = 'none';
    currentQuestion++;
    if (currentQuestion <= 4) {
      document.getElementById(`question${currentQuestion}`).style.display = 'block';
    } else {
      showResult();
    }
  }

  function showResult() {
    let house = '';
    let max = Math.max(gryffindor, hufflepuff, ravenclaw, slytherin);
    
    if (max === gryffindor) house = 'Gryffindor';
    else if (max === hufflepuff) house = 'Hufflepuff';
    else if (max === ravenclaw) house = 'Ravenclaw';
    else if (max === slytherin) house = 'Slytherin';

    document.getElementById('result').innerText = `Welcome to ${house}!`;
  }
</script>

</body>
</html>
