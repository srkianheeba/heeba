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
  <h1>2d GEOMETRY</h1>
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



{
    "qna": [
      {
        "question": "1.CARTESIAN CO-ORDINATES.",
        "answer": [
          "Answer:Distance between Two Points",
          "Section Formula",
          "Shift of Origin",
          "Rotation Of Axes",
          "Collinear Points"
        ],
        "subqna": [
          {
            "question": "1.Distance between Two Points.",
            "answer": [
              "Answer:Formula: The distance between points (x1, y1) and (x2, y2) is given by:",
              "d = sqrt((x2 - x1)^2 + (y2 - y1)^2)",
              "Example: Find the distance between (3, 4) and (7, 1).",
              "d = sqrt((7 - 3)^2 + (1 - 4)^2) = sqrt(4^2 + (-3)^2) = sqrt(16 + 9) = sqrt(25) = 5"
            ]
          },
          {
            "question": "2.Section Formula.",
            "answer": [
              "Answer:Internal Division: The coordinates of the point P(x, y) dividing the line segment joining (x1, y1) and (x2, y2) internally in the ratio m:n are:",
              "x = (mx2 + nx1) / (m+n), y = (my2 + ny1) / (m+n)",
              "Example: Find the point dividing the segment joining (2, 3) and (4, 1) in the ratio 2:3 internally.",
              "x = (2 * 4 + 3 * 2) / (2 + 3) = (8 + 6) / 5 = 14 / 5 = 2.8, y = (2 * 1 + 3 * 3) / (2 + 3) = (2 + 9) / 5 = 11 / 5 = 2.2"
            ]
          },
          {
            "question": "3.Shift of Origin.",
            "answer": [
              "Answer:If the origin is shifted to (h, k), then the new coordinates (X, Y) of a point (x, y) are:",
              "X = x - h, Y = y - k",
              "Example: Find the new coordinates of the point (5, 7) if the origin is shifted to (2, 3).",
              "X = 5 - 2 = 3, Y = 7 - 3 = 4"
  
            ]
          },
          {
            "question": "4.Rotation of Axes.",
            "answer": [
              "Answer:If the axes are rotated through an angle θ, then the new coordinates (X, Y) of a point (x, y) are:",
              "X = x cos θ - y sin θ, Y = x sin θ + y cos θ",
              "Example: Find the new coordinates of the point (3, 4) after rotating the axes through 30°.",
              "X = 3 cos 30° - 4 sin 30° = 3 * √3/2 - 4 * 1/2 = 3√3/2 - 2, Y = 3 sin 30° + 4 cos 30° = 3 * 1/2 + 4 * √3/2 = 3/2 + 2√3"
  
            ]
          },
          {
            "question": "5.Collinear Points.",
            "answer": [
              "Answer:Three points (x1, y1), (x2, y2), and (x3, y3) are collinear if the area of the triangle formed by them is zero:",
              "1/2 |x1(y2 - y3) + x2(y3 - y1) + x3(y1 - y2)| = 0",
              "Example: Determine if the points (1, 2), (3, 4), and (5, 6) are collinear.",
              "1/2 |1(4 - 6) + 3(6 - 2) + 5(2 - 4)| = 1/2 |-2 + 12 - 10| = 1/2 |0| = 0",
              "Therefore, the points are collinear."
  
            ]
          }
        ]
      },
      {
        "question": "2.EQUATIONS OF A STRAIGHT LINE.",
        "answer": [
          "Various Forms of the Equation of a Straight Line",
          "Angle Between Two Lines",
          "Distance of a Point from a Line",
          "Lines Through the Point of Intersection of Two Given Lines",
          "Equation of the Bisector of the Angle Between Two Lines",
          "Concurrency of Lines",
          "Pair of Straight Lines"
  
        ],
        "subqna": [
          {
            "question": "1.Various Forms of the Equation of a Straight Line.",
            "answer": [
              "Answer:Slope-Intercept Form: y = mx + c where m is the slope and c is the y-intercept.",
              "Point-Slope Form: y - y1 = m(x - x1) where (x1, y1) is a point on the line and m is the slope.",
              "Two-Point Form: y - y1 = (y2 - y1)/(x2 - x1)(x - x1) where (x1, y1) and (x2, y2) are two points on the line.",
              "Intercept Form: x/a + y/b = 1 where a and b are the x-intercept and y-intercept, respectively.",
              "Normal Form: x cos α + y sin α = p where p is the perpendicular distance from the origin and α is the angle the perpendicular makes with the positive x-axis.",
              "Example: Find the equation of the line with slope 2 and y-intercept 3.",
              "y = 2x + 3"
  
            ]
          },
          {
            "question": "2.Angle Between Two Lines",
            "answer": [
              "Answer:The angle θ between two lines with slopes m1 and m2 is given by:",
              "tan θ = |(m2 - m1) / (1 + m1 m2)|",
              "Example: Find the angle between the lines y = 3x + 1 and y = -1/3x + 2.",
              "tan θ = |(-1/3 - 3) / (1 + 3 * -1/3)| = |-10/3 / 0| → undefined → θ = 90°"
  
            ]
          },
          {
            "question": "3.Distance of a Point from a Line.",
            "answer": [
              "Answer:The distance d of a point (x1, y1) from the line ax + by + c = 0 is given by:",
              "d = |ax1 + by1 + c| / sqrt(a^2 + b^2)",
              "Example: Find the distance of the point (1, 2) from the line 3x + 4y - 5 = 0.",
              "d = |3 * 1 + 4 * 2 - 5| / sqrt(3^2 + 4^2) = |3 + 8 - 5| / sqrt(9 + 16) = 6 / 5 = 1.2"
  
            ]
          },
          {
            "question": "4.Lines Through the Point of Intersection of Two Given Lines.",
            "answer": [
              "Answer:If two lines are given by L1: a1x + b1y + c1 = 0 and L2: a2x + b2y + c2 = 0, then the equation of a line passing through their intersection is given by:",
              "L = L1 + λ L2 = 0",
              "Example: Find the equation of the line passing through the intersection of x + y = 2 and x - y = 4 and has a slope of 3.",
              "x + y = 2 → x = 2 - y",
              "2 - y - y = 4 → 2 - 2y = 4 → y = -1, x = 3",
              "Line: y + 1 = 3(x - 3) → y = 3x - 10"
  
            ]
          },
          {
            "question": "5.Equation of the Bisector of the Angle Between Two Lines.",
            "answer": [
              "Answer:The angle bisector of the lines a1x + b1y + c1 = 0 and a2x + b2y + c2 = 0 is given by:",
              "(a1x + b1y + c1) / sqrt(a1^2 + b1^2) = ± (a2x + b2y + c2) / sqrt(a2^2 + b2^2)",
              "Example: Find the equation of the bisector of the angle between the lines 3x - 4y + 7 = 0 and 5x + 12y - 9 = 0.",
              "(3x - 4y + 7) / sqrt(3^2 + (-4)^2) = ± (5x + 12y - 9) / sqrt(5^2 + 12^2)",
              "(3x - 4y + 7) / 5 = ± (5x + 12y - 9) / 13"
            ]
          },
          {
            "question": "6.Concurrency of Lines.",
            "answer": [
              "Answer:   Three lines a1x + b1y + c1 = 0, a2x + b2y + c2 = 0, and a3x + b3y + c3 = 0 are concurrent if:",
              "|a1 b1 c1|",
              "|a2 b2 c2| = 0",
              "|a3 b3 c3|",
              "Example: Determine if the lines x + y - 1 = 0, 2x - 3y + 4 = 0, and 3x - 2y + 5 = 0 are concurrent.",
              "|1 1 -1|",
              "|2 -3 4| = 1(-15 + 8) - 1(10 - 12) - 1(-4 - 9) = -7 + 2 + 13 = 8 ≠ 0",
              "|3 -2 5|",
              "Therefore, the lines are not concurrent."
  
            ]
          },
          {
            "question": "7.Pair of Straight Lines.",
            "answer": [
              "Answer:The general equation of the second degree can represent a pair of straight lines and is given by:",
              "ax^2 + 2hxy + by^2 + 2gx + 2fy + c = 0",
              "Conditions for the general second-degree equation to represent a pair of straight lines:",
              "Δ = abc + 2fgh - af^2 - bg^2 - ch^2 = 0",
              "Angle between the lines represented by the equation ax^2 + 2hxy + by^2 = 0 is given by:",
              "tan θ = ±2√(h^2 - ab) / (a + b)",
              "Example: Determine whether the equation 6x^2 + 11xy + 3y^2 = 0 represents a pair of straight lines and find the angle between them.",
              "Δ = 6 * 3 * 0 + 2 * 0 * 11 - 6 * 0^2 - 3 * 0^2 - 0 * 11^2 = 0 → represents a pair of straight lines.",
              "tan θ = ±2√(11^2 - 6 * 3) / (6 + 3) = ±2√(121 - 18) / 9 = ±2√103 / 9"
  
            ]
          }
        ]
      },
      {
        "question": "3.LOCUS.",
        "answer": [
          "Answer:Definition",
          "Method To Find The Locus",
          "Examples"
        ],
        "subqna": [
          {
            "question": "1.Definition.",
            "answer": [
              "Answer:The locus of a point is the set of all positions that the point can occupy while satisfying given conditions."
            ]
          },
          {
            "question": "2.Method to Find the Locus.",
            "answer": [
              "Answer:-Assume the coordinates of the moving point as (h, k).",
              "- Write the given condition in mathematical form involving h and k.",
              "- Eliminate h and k to get the required equation."
  
            ]
          },
          {
            "question": "3.Examples.",
            "answer": [
              "Answer:- Find the locus of a point that is always at a fixed distance 5 from the origin.",
              "Equation: √(x^2 + y^2) = 5 → x^2 + y^2 = 25",
              "- Find the locus of a point that moves such that its distance from (2, 0) is twice its distance from (0, 0).",
              "Distance from (2, 0) = √((x - 2)^2 + y^2)",
              "Distance from (0, 0) = √(x^2 + y^2)",
              "Equation: √((x - 2)^2 + y^2) = 2√(x^2 + y^2)",
              "Squaring both sides: (x - 2)^2 + y^2 = 4(x^2 + y^2)",
              "x^2 - 4x + 4 + y^2 = 4x^2 + 4y^2",
              "3x^2 + 3y^2 + 4x - 4 = 0 → x^2 + y^2 + (4/3)x - 4/3 = 0"
            ]
          }
        ]
      },
      {
        "question": "4.TRIANGLE CENTRES.",
        "answer": [
          "Answer:Centroid",
          "Orthocentre",
          "Incentre",
          "Circumcentre"
        ],
        "subqna": [
          {
            "question": "1.Centroid.",
            "answer": [
              "Answer:The centroid G of a triangle with vertices (x1, y1), (x2, y2), and (x3, y3) is given by:",
              "G((x1 + x2 + x3) / 3, (y1 + y2 + y3) / 3)",
              "Example: Find the centroid of the triangle with vertices (1, 2), (3, 4), and (5, 6).",
              "G((1 + 3 + 5) / 3, (2 + 4 + 6) / 3) = G(9 / 3, 12 / 3) = G(3, 4)"
         
            ]
          },
          {
            "question": "2.Orthocentre.",
            "answer": [
              "Answer:   The orthocentre H of a triangle is the point where the altitudes intersect. Finding it involves solving the equations of the altitudes.",
              "Example: Find the orthocentre of the triangle with vertices (0, 0), (4, 0), and (0, 3).",
              "Slope of side BC: 0 - 3 / 4 - 0 = -3/4",
              "Equation of altitude from A: y = 4/3 x",
              "Slope of side AC: 0 - 3 / 0 - 0 → undefined",
              "Equation of altitude from B: x = 4",
              "Intersection gives orthocentre: H = (4, 4/3 * 4) = (4, 16/3)"
  
            ]
          },
          {
            "question": "3.Incentre.",
            "answer": [
              "Answer:The incentre I of a triangle is the point where the angle bisectors intersect. Its coordinates are given by:",
              "I((ax1 + bx2 + cx3) / (a+b+c), (ay1 + by2 + cy3) / (a+b+c))",
              "where a, b, and c are the lengths of the sides opposite the vertices (x1, y1), (x2, y2), and (x3, y3) respectively.",
              "Example: Find the incentre of the triangle with vertices (0, 0), (4, 0), and (0, 3).",
              "a = sqrt((0-0)^2 + (3-0)^2) = 3, b = sqrt((4-0)^2 + (3-0)^2) = 5, c = sqrt((4-0)^2 + (0-0)^2) = 4",
              "I((3 * 0 + 5 * 4 + 4 * 0) / (3+5+4), (3 * 0 + 5 * 0 + 4 * 3) / (3+5+4)) = I(20 / 12, 12 / 12) = I(5 / 3, 1)"
  
            ]
          },
          {
            "question": "4.Circumcentre.",
            "answer": [
              "Answer:The circumcentre O of a triangle is the point where the perpendicular bisectors of the sides intersect.",
              "Example: Find the circumcentre of the triangle with vertices (0, 0), (4, 0), and (0, 3).",
              "Midpoint of AB: ( (0+4) / 2, (0+0) / 2 ) = (2, 0)",
              "Midpoint of AC: ( (0+0) / 2, (0+3) / 2 ) = (0, 1.5)",
              "Perpendicular bisector of AB: x = 2",
              "Perpendicular bisector of AC: y = 1.5",
              "O = (2, 1.5)"
  
            ]
          }
        ]
      },
      {
        "question": "PRACTICE QUESTIONS AND SOLUTIONS.",
        "answer": [
          "Answer:Q/A"
        ],
        "subqna": [
          {
            "question": "1.Distance between Two Points.",
            "answer": [
              "Answer:Find the distance between (-2, -3) and (4, 5).",
              "Solution: d = sqrt((4 - (-2))^2 + (5 - (-3))^2) = sqrt(6^2 + 8^2) = sqrt(36 + 64) = sqrt(100) = 10"
            ]
          },
          {
            "question": "2.Section Formula.",
            "answer": [
              "Answer:Find the point dividing the segment joining (-1, 3) and (5, -7) in the ratio 3:2 internally.",
              "Solution: x = (3 * 5 + 2 * -1) / (3 + 2) = (15 - 2) / 5 = 13 / 5 = 2.6, y = (3 * -7 + 2 * 3) / (3 + 2) = (-21 + 6) / 5 = -15 / 5 = -3."
  
            ]
          },
          {
            "question": "3.Shift of Origin.",
            "answer": [
              "Answer:Find the new coordinates of the point (6, 8) if the origin is shifted to (2, 2).",
              "Solution: X = 6 - 2 = 4, Y = 8 - 2 = 6"
  
            ]
          },
          {
            "question": "4.Equation of a Straight Line.",
            "answer": [
              "Answer:Find the equation of the line passing through (1, 2) and (3, 4).",
              "Solution: Slope m = (4 - 2) / (3 - 1) = 2 / 2 = 1, y - 2 = 1(x - 1) → y = x + 1",
  
              "Find the equation of the line with x-intercept 4 and y-intercept 3.",
              "Solution: x/4 + y/3 = 1 → 3x + 4y = 12"
  
            ]
          },
          {
            "question": "5.Angle Between Two Lines.",
            "answer": [
              "Answer:Find the angle between the lines y = x + 2 and y = -x + 5.",
              "Solution: tan θ = |(-1 - 1) / (1 * -1)| = |-2| = 2 → θ = tan^(-1)(2) ≈ 63.43°"
            ]
          },
          {
            "question": "6.Distance of a Point from a Line.",
            "answer": [
              "Answer:Find the distance of the point (2, 3) from the line 5x - 12y + 6 = 0.",
              "Solution: d = |5 * 2 - 12 * 3 + 6| / sqrt(5^2 + (-12)^2) = |10 - 36 + 6| / sqrt(25 + 144) = 20 / 13 ≈ 1.54"
            ]
          },
          {
            "question": "7.Lines Through the Point of Intersection of Two Given Lines.",
            "answer": [
              "Answer:Find the equation of the line passing through the intersection of 2x - 3y + 1 = 0 and x + y - 4 = 0 and having a slope of -2.",
              "Solution: Intersection: 2x - 3y + 1 = 0 → 2x - 3(4 - x) + 1 = 0 → 2x - 12 + 3x + 1 = 0 → 5x - 11 = 0 → x = 11/5, y = 4 - 11/5 = 9/5",
              "Line: y - 9/5 = -2(x - 11/5) → y = -2x + 22/5"
            ]
          },
          {
            "question": "8.Equation of the Bisector of the Angle Between Two Lines.",
            "answer": [
              "Answer:Find the equation of the bisector of the angle between the lines x - y + 1 = 0 and 2x + y - 3 = 0.",
              "Solution: (x - y + 1) / sqrt(1^2 + (-1)^2) = ± (2x + y - 3) / sqrt(2^2 + 1^2)",
              "(x - y + 1) / sqrt(2) = ± (2x + y - 3) / sqrt(5)",
              "x - y + 1 = ± 2√2(2x + y - 3) / √5",
              "x - y + 1 = ± 2√2(2x + y - 3) / √5"
            ]
          },
          {
            "question": "9.Concurrency of Lines.",
            "answer": [
              "Answer:Determine if the lines 2x + 3y - 4 = 0, 4x - y + 7 = 0, and x - y - 2 = 0 are concurrent.",
              "Solution: |2 3 -4| |4 -1 7| = 2(-7 + 4) - 3(28 + 4) + 4(1 + 14) = -6 - 84 + 60 = -30 ≠ 0",
              "Therefore, the lines are not concurrent."
  
            ]
          },
          {
            "question": "10.Pair of Straight Lines.",
            "answer": [
              "Answer:Determine if the equation 4x^2 + 9xy + 6y^2 = 0 represents a pair of straight lines.",
              "Find the angle between the lines represented by 7x^2 - 24xy + 5y^2 = 0.",
              "Solution: Δ = 4 * 6 * 0 + 2 * 0 * 9 - 4 * 0^2 - 6 * 0^2 - 0 * 9^2 = 0 → represents a pair of straight lines."
            ]
          },
          {
            "question": "11.Locus.",
            "answer": [
              "Answer:-Find the locus of a point that is always at a fixed distance 3 from the point (1, 1).",
              "Solution: Equation: √((x - 1)^2 + (y - 1)^2) = 3 → (x - 1)^2 + (y - 1)^2 = 9",
              "Find the locus of a point that moves such that its distance from (3, 4) is equal to its distance from the line x + y = 6.",
              "Solution: Distance from (3, 4) = √((x - 3)^2 + (y - 4)^2)"
  
            ]
          },
          {
            "question": "12.Triangle Centers.",
            "answer": [
              "Answer:Find the centroid of the triangle with vertices (1, 2), (3, 4), and (5, 6).",
              "Solution: G((1 + 3 + 5) / 3, (2 + 4 + 6) / 3) = G(9 / 3, 12 / 3) = G(3, 4)",
              "- Find the orthocentre of the triangle with vertices (1, 1), (4, 2), and (2, 5).",
              "Solution: Slope of side AB: 2 - 1 / 4 - 1 = 1 / 3 → y - 1 = 1/3(x - 1)",
              "Slope of side BC: 5 - 2 / 2 - 4 = 3 / -2 → y - 5 = -3/2(x - 2)",
              "Intersection: H = (2, 5 - 3/2(2 - 2)) = (2, 5)",
              "-Find the incentre of the triangle with vertices (0, 0), (6, 0), and (0, 8).",
              "Solution: a = 10, b = 10, c = 6√2",
             "I((10 * 0 + 10 * 6 + 6√2 * 0) / (10+10+6√2), (10 * 0 + 10 * 0 + 6√2 * 8) / (10+10+6√2)) = I(60 / 20 + 6√2, 48√2 / 20 + 6√2) = I(3 + 3√2, 4√2 + 3√2)",
          
              "- Find the circumcentre of the triangle with vertices (1, 2), (3, 4), and (5, 6).",
              "Solution: Midpoint of AB: (2, 3), Midpoint of AC: (3, 4)",
              "Perpendicular bisector of AB: y = 3, Perpendicular bisector of AC: x = 3",
              "O = (3, 3)"
          
            ]
          }
        ]
      }
    ]
  }
