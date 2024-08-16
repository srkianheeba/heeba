<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FAQ Accordion</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background-color: #f9f9f9;
    }
    h1 {
      text-align: center;
    }
    .faq-container {
      max-width: 800px;
      margin: 0 auto;
    }
    .faq {
      background-color: #fff;
      border-radius: 5px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      margin-bottom: 10px;
    }
    .faq-question {
      background-color: white;
      color: black;
      font-weight: bold;
      font-size: 18px;
      margin: 0;
      padding: 15px;
      border-radius: 5px 5px 0 0;
      cursor: pointer;
    }
    .faq-answer, .subqna {
      display: none;
      padding: 15px;
      font-size: 16px;
      border-top: 1px solid #ddd;
    }
    .faq-answer {
      background-color: #ffff00;
      color: black;
    }
    .subqna {
      margin-left: 20px;
      padding-left: 15px;
      border-left: 2px solid yellow;
    }
    .subqna .faq-question {
      background-color: yellow;
    }
    .subqna .faq-answer {
      margin-top: 10px;
    }

    /* Responsive adjustments */
    @media (max-width: 600px) {
      .faq-question {
        font-size: 16px;
        padding: 10px;
      }
      .faq-answer {
        font-size: 14px;
        padding: 10px;
      }
    }
  </style>
</head>
<body>
  <h1>Frequently Asked Questions</h1>
  <div id="faq-container" class="faq-container"></div>

  <script>
    document.addEventListener('DOMContentLoaded', () => {
      fetch('derivative.json')
        .then(response => response.json())
        .then(data => {
          const faqContainer = document.getElementById('faq-container');
          data.qna.forEach(item => {
            const faqDiv = document.createElement('div');
            faqDiv.classList.add('faq');

            const question = document.createElement('p');
            question.classList.add('faq-question');
            question.textContent = item.question;
            faqDiv.appendChild(question);

            const answer = document.createElement('div');
            answer.classList.add('faq-answer');
            answer.innerHTML = item.answer.join('<br>');
            faqDiv.appendChild(answer);

            if (item.subqna && item.subqna.length > 0) {
              const subqnaContainer = document.createElement('div');
              subqnaContainer.classList.add('subqna');

              item.subqna.forEach(subitem => {
                const subfaqDiv = document.createElement('div');
                subfaqDiv.classList.add('faq');

                const subQuestion = document.createElement('p');
                subQuestion.classList.add('faq-question');
                subQuestion.textContent = subitem.question;
                subfaqDiv.appendChild(subQuestion);

                const subAnswer = document.createElement('div');
                subAnswer.classList.add('faq-answer');
                subAnswer.innerHTML = subitem.answer.join('<br>');
                subfaqDiv.appendChild(subAnswer);

                subqnaContainer.appendChild(subfaqDiv);
              });

              faqDiv.appendChild(subqnaContainer);
            }

            faqContainer.appendChild(faqDiv);
          });

          document.querySelectorAll('.faq-question').forEach(question => {
            question.addEventListener('click', () => {
              const faq = question.parentElement;
              const answer = faq.querySelector('.faq-answer');
              const subqna = faq.querySelector('.subqna');
              if (answer.style.display === 'block') {
                answer.style.display = 'none';
                if (subqna) {
                  subqna.style.display = 'none';
                }
              } else {
                answer.style.display = 'block';
                if (subqna) {
                  subqna.style.display = 'block';
                }
              }
            });
          });
        })
        .catch(error => {
          console.error('Error fetching the data:', error);
        });
    });
  </script>
</body>
</html>
