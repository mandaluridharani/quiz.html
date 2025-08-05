<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Quiz App</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      background-color: rgb(0, 153, 255);
      font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    }

    .heading-1 {
      position: absolute;
      top: 43%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: large;
    }

    .start_quiz {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      border: 2px solid black;
      padding: 10px 10px;
      border-radius: 10px;
      font-size: 18px;
      cursor: pointer;
      background: none;
    }

    .start_quiz:hover {
      background-color: rgb(38, 38, 38);
      color: white;
    }

    .inactive {
      display: none;
    }

    .disabled {
      pointer-events: none;
    }

    .quiz-box {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      border: 2px solid black;
      padding: 50px;
      width: 100%;
      max-width: 510px;
      background-color: snow;
    }

    .quiz-box h2 {
      font-size: 28px;
    }

    .quiz-box .option {
      font-size: 18px;
      border: 2px solid black;
      margin: 20px 0;
      padding: 12px 15px;
      border-radius: 5px;
      cursor: pointer;
      position: relative;
    }

    .quiz-box .option .fa-solid {
      position: absolute;
      right: 10px;
      top: 10px;
      font-size: 27px;
    }

    .quiz-box .option.correct {
      background: rgb(157, 246, 157);
      color: green;
      border-color: green;
    }

    .quiz-box .option.incorrect {
      background: rgb(241, 153, 153);
      color: red;
      border-color: red;
    }

    .quiz-fotter {
      margin-top: 60px;
      padding-top: 30px;
      border-top: 2px dashed black;
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 100px;
    }

    .count_que,
    .total_que {
      font-size: 25px;
      font-weight: bolder;
    }

    .fotter-left {
      font-size: 18px;
    }

    .next-btn {
      font-size: 18px;
      border: 2px solid black;
      border-radius: 5px;
      padding: 10px;
      cursor: pointer;
      background: none;
    }

    .next-btn:hover {
      background: black;
      color: white;
    }

    .result-box {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      border: 2px solid black;
      width: 100%;
      max-width: 490px;
      background-color: pink;
    }

    .result-box h2 {
      font-size: 36px;
      background: white;
      color: black;
      margin: 0;
      text-align: center;
      padding: 14px 0px 10px 0px;
    }

    .result-box .result {
      padding: 20px;
    }

    .result-box h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }

    .result-fotter {
      display: flex;
      justify-content: space-around;
      padding-bottom: 30px;
    }

    .result-fotter .again-quiz,
    .exit {
      border: 2px solid black;
      border-radius: 5px;
      padding: 10px 20px;
      font-size: 18px;
      background: none;
      cursor: pointer;
    }

    .result-fotter .again-quiz:hover {
      background: gray;
      color: white;
    }

    .result-fotter .exit {
      background: white;
      color: black;
      border: 2px solid whitesmoke;
    }

    .result-fotter .exit:hover {
      background: black;
      color: white;
      border: none;
    }
  </style>
  <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</head>
<body>

  <div class="heading-1">
    <h1>Welcome to Quiz App</h1>
  </div>
  <button class="start_quiz">Start Quiz</button>

  <div class="quiz-box inactive">
    <h2 class="ques_text"></h2>
    <div class="options"></div>
    <div class="quiz-fotter">
      <div class="fotter-left"><span class="count_que"></span> of <span class="total_que"></span> Questions</div>
      <div class="fotter-right">
        <button class="next-btn">Next Question</button>
      </div>
    </div>
  </div>

  <div class="result-box inactive">
    <h2>Result</h2>
    <div class="result">
      <h3 class="total-question">Total Questions: <span></span></h3>
      <h3 class="right-ans">Correct Answers: <span></span></h3>
      <h3 class="wrong-ans">Incorrect Answers: <span></span></h3>
      <h3 class="percentage">Overall Percentage: <span></span></h3>
    </div>
    <div class="result-fotter">
      <button class="again-quiz">Play Again</button>
      <button class="exit">Exit</button>
    </div>
  </div>

  <script>
    const questions = [
      {
        num: 1,
        question: "What does HTML stands for?",
        answer: "Hyper Text Markup Language",
        options: [
          "Hyper Text Multiple Language",
          "Hyper Text PreProcessor",
          "Hyper Tool Multi Language",
          "Hyper Text Markup Language"
        ]
      },
      {
        num: 2,
        question: "What does CSS stand for?",
        answer: "Cascading Style Sheets",
        options: [
          "Computer Style Sheets",
          "Cascading Style Sheets",
          "Colourful Style Sheets",
          "Common Style Sheets"
        ]
      },
      {
        num: 3,
        question: "Which HTML attribute is used to define inline styles?",
        answer: "style",
        options: ["styles", "style", "class", "font"]
      },
      {
        num: 4,
        question: "Which is correct syntax?",
        answer: "body{color:black};",
        options: [
          "{body;color:black}",
          "body:color=black;",
          "body{color:black};",
          "{body:color=black};"
        ]
      },
      {
        num: 5,
        question: "What does SQL stands for?",
        answer: "Structured Query Language",
        options: [
          "Statement Query Language",
          "StyleSheets Query Language",
          "Structured Query Language",
          "Stylish Question Language"
        ]
      },
      {
        num: 6,
        question: "How many types of api's?",
        answer: "2",
        options: ["2", "3", "4", "5"]
      },
      {
        num: 7,
        question: "how many api methods are there in js?",
        answer: "4",
        options: ["3", "5", "4", "6"]
      },
      {
        num: 8,
        question: "Expand API?",
        answer: "Application programming interface",
        options: [
          "Application programming interface",
          "application programming institute",
          "append programming interface",
          "application proogramming innerface"
        ]
      },
      {
        num: 9,
        question: "what is php?",
        answer: "Hypertext preprocessor",
        options: [
          "Hypertext preprocessor",
          "preprocessor hypertext",
          "hypertext processor",
          "hypertext prepreprocessor"
        ]
      },
      {
        num: 10,
        question: "Full form of url....",
        answer: "Uniform resource locator",
        options: [
          "Hypertext preprocessor",
          "uniform resource locator",
          "uniform locator",
          "resorce locator"
        ]
      }
    ];

    const start_btn = document.querySelector(".start_quiz");
    const quiz_box = document.querySelector(".quiz-box");
    const ques_text = document.querySelector(".ques_text");
    const options_box = document.querySelector(".options");
    const next_btn = document.querySelector(".next-btn");
    const total_q = document.querySelector(".total_que");
    const count_que = document.querySelector(".count_que");
    const result_box = document.querySelector(".result-box");
    const heading_1 = document.querySelector(".heading-1");

    const total_ques_r = document.querySelector(".total-question span");
    const right_ans_r = document.querySelector(".right-ans span");
    const wrong_ans_r = document.querySelector(".wrong-ans span");
    const percentage = document.querySelector(".percentage span");

    const again_quiz = document.querySelector(".again-quiz");
    const exit = document.querySelector(".exit");

    const mark_check = '<i class="fa-solid fa-check"></i>';
    const mark_wrong = '<i class="fa-solid fa-times"></i>';

    start_btn.onclick = () => {
      quiz_box.classList.remove("inactive");
      start_btn.classList.add("inactive");
      heading_1.classList.add("inactive");
    };

    total_q.innerText = questions.length;
    total_ques_r.innerText = questions.length;

    let que_index = 0;
    let right_answer = 0;
    let wrong_answer = 0;
    count_que.innerText = que_index + 1;
    showquestions(que_index);

    function showquestions(q_index) {
      ques_text.innerHTML = questions[q_index].num + ". " + questions[q_index].question;
      let option_stmt = "";
      for (let i = 0; i < questions[q_index].options.length; i++) {
        option_stmt += `<div class="option">${questions[q_index].options[i]}</div>`;
      }
      options_box.innerHTML = option_stmt;

      const alloptions = options_box.querySelectorAll(".option");
      alloptions.forEach(opt => {
        opt.setAttribute("onclick", "useranswer(this)");
      });

      next_btn.classList.add("inactive");
    }

    next_btn.onclick = () => {
      que_index++;
      if (que_index < questions.length) {
        count_que.innerText = que_index + 1;
        showquestions(que_index);
        if (que_index === questions.length - 1) {
          next_btn.innerText = "Finish";
        }
      } else {
        quiz_box.classList.add("inactive");
        result_box.classList.remove("inactive");
        right_ans_r.innerText = right_answer;
        wrong_ans_r.innerText = wrong_answer;
        percentage.innerText = ((right_answer * 100) / questions.length).toFixed(2) + "%";
      }
    };

    function useranswer(answer) {
      const userAns = answer.innerHTML;
      const correctAnswer = questions[que_index].answer;
      const alloptions2 = options_box.querySelectorAll(".option");

      next_btn.classList.remove("inactive");
      if (userAns === correctAnswer) {
        answer.classList.add("correct");
        answer.insertAdjacentHTML("beforeend", mark_check);
        right_answer++;
      } else {
        answer.classList.add("incorrect");
        answer.insertAdjacentHTML("beforeend", mark_wrong);
        wrong_answer++;

        alloptions2.forEach(opt => {
          if (opt.innerText === correctAnswer) {
            opt.classList.add("correct");
            opt.insertAdjacentHTML("beforeend", mark_check);
          }
        });
      }

      alloptions2.forEach(opt => opt.classList.add("disabled"));
    }

    again_quiz.onclick = () => {
      result_box.classList.add("inactive");
      quiz_box.classList.remove("inactive");
      next_btn.innerText = "Next Question";
      reset();
    };

    exit.onclick = () => {
      result_box.classList.add("inactive");
      heading_1.classList.remove("inactive");
      start_btn.classList.remove("inactive");
      reset();
    };

    function reset() {
      que_index = 0;
      right_answer = 0;
      wrong_answer = 0;
      count_que.innerText = que_index + 1;
      showquestions(que_index);
    }
  </script>
</body>
</html>
