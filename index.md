<html>
    <head>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script>
          function TotalScores() {
    let dietradios = document.querySelectorAll('#diet > .radio-container > input[type="radio"]')
    let exerciseradios = document.querySelectorAll('.radio-container > input[name="likert_4"]') //to select only one in exercise
    //let exerciseradios = document.querySelectorAll('#exercise > .radio-container > input[type="radio"]')
    let smokeradios = document.querySelectorAll('#eversmoke > .radio-container > input[type="radio"]')
    let stressradios = document.querySelectorAll('#stress > .radio-container > input[type="radio"]')

    let exerciselevel_1 = document.querySelectorAll('#exercise > .onlylight > .radio-container > input[type="radio"]')
    let exerciselevel_2 = document.querySelectorAll('#exercise > .moderate > .radio-container > input[type="radio"]')
    let exerciselevel_3 = document.querySelectorAll('#exercise > .vigorous > .radio-container > input[type="radio"]')


    let diet_total = 0
    let exercise_score = 0
    let alcohol_score = 0
    let smoke_score = 0
    let stress_score = 0
    let exerciselevel_score = 0


    //SHow category only
    let dietShow = document.querySelector('.Diet-raw-score')
    let exerciseShow = document.querySelector('.Exercise-raw-score')
    let alcoholShow = document.querySelector('.Alcohol-raw-score')
    let smokeShow = document.querySelector('.Smoke-raw-score')
    let stressShow = document.querySelector('.Stress-raw-score')
    let totalShow = document.querySelector('.Total-score')


    let dietraw = ''
    let exerciseraw = ''
    let alcoholraw = ''
    let smokeraw = ''
    let stressraw = ''
    let TotalCategoryScore = ''
  
    //Diet raw score calc
    dietradios.forEach(function(radio, index) {
      if (radio.checked) {
        diet_total += +radio.value
      }
    })

    // Category total score DIET
    if (0 <= diet_total && diet_total <= 5)
      dietcategoryscore = 0
    else if (6 <= diet_total && diet_total<= 10)
      dietcategoryscore = 1
    else if (11 <= diet_total&& diet_total<= 15)
      dietcategoryscore = 2
  
    //Exercise raw score calc
    exerciseradios.forEach(function(radio, index) {
      if (radio.checked) {
        exercise_score += +radio.value
      }
    })
    //Exercise level score
    exerciselevel_1.forEach(function(radio, index) {
        if (radio.checked) {
            exerciselevel_score += 0
        }
     })
    
    exerciselevel_2.forEach(function(radio, index) {
        if (radio.checked) {
           exerciselevel_score += 1
        }
     })
    
    exerciselevel_3.forEach(function(radio, index) {
        if (radio.checked) {
           exerciselevel_score += 2
       }
   })
    // Category total score Exercise
   // if (0 <= exercise_score && exercise_score <= 3)
        //excategoryscore = 0
    //else if (4 <= exercise_score && exercise_score <= 7)
        //excategoryscore = 1
    //else if (8 <= exercise_score && exercise_score <= 11)
        //excategoryscore = 2

    //Alcohol raw score calc
    var wine = document.getElementById("wine")
    var beer = document.getElementById("beer")
    var spirits = document.getElementById("spirit")
    
    var winevalue = +wine.value;
    var beervalue = +beer.value;
    var spiritsvalue = +spirits.value;
  
    alcohol_score += winevalue + beervalue + spiritsvalue;

    // Category total score alcohol
    if (0 <= alcohol_score && alcohol_score <= 7)
        alcoholcategory = 2
    else if (8 <= alcohol_score && alcohol_score<= 13)
        alcoholcategory = 1
    else 
        alcoholcategory = 0

    //Smoking raw score calc - same as cetegory score
    smokeradios.forEach(function(radio, index) {
        if (radio.checked) {
          smoke_score += +radio.value
        }
      })

    //Stress raw score calc
    stressradios.forEach(function(radio, index) {
        if (radio.checked) {
          stress_score += +radio.value
        }
      })

    //Category stress score
    if (1 == stress_score || stress_score == 2)
        stresscategory = 0
    else if (3 == stress_score || stress_score == 4)
        stresscategory = 1
    else if (5 == stress_score || stress_score == 6)
        stresscategory = 2

    //Diet individual score
    dietraw += "<b>Diet Score: </b>" + dietcategoryscore + "<br>"
    dietShow.innerHTML = dietraw
    //document.write(dietraw)
  
    //Exercise individual score
    exerciseraw += "<b>Exercise Score: </b>" +  exerciselevel_score + "<br>"
    exerciseShow.innerHTML = exerciseraw
    //document.write(exerciseraw)

    //Alcohol individual score
    alcoholraw += "<b>Alcohol Consumption Score: </b>" + alcoholcategory + "<br>"
    alcoholShow.innerHTML = alcoholraw
    //document.write(alcoholraw)

    //Smoke individual score
    smokeraw += "<b>Smoking Score: </b>" + smoke_score + "<br>"
    smokeShow.innerHTML = smokeraw
    //document.write(smokeraw)

    //Stress individual score
    stressraw += "<b>Life Stress Score: </b>" + stresscategory + "<br>" //change which value to display in sum
    stressShow.innerHTML = stressraw
    //document.write(stressraw)

    // Total Health Score - TotalCategoryScore
    totaldisp = "<b>Total Score: </b>" 
    TotalCategoryScore += Number(dietcategoryscore) + Number( exerciselevel_score) + Number(alcoholcategory) + Number(smoke_score) + Number(stresscategory)
    totalShow.innerHTML = totaldisp + TotalCategoryScore
    //document.write(TotalCategoryScore)

  }
        </script>
        <script type="text/babel"></script>
        <style type="text/css">
        label + label {
            margin-left: 30px;
        }
        </style>
    </head>
    <body>
              <div id="diet" class="survey-box" data-show-dialog>
                    <h1>The first category in the assessment is DIET.</h1>
                      <h2>To answer these questions, think about your eating habits during the past year. Indicate how often you eat the following foods. Please include all meals, snacks, and food eaten out.</h2>
                     
                    <h3>1. Lettuce or green leafy salad, with or without other vegetables.</h3>
                  
                      <label class="radio-container"><input type="radio" name="dietq1" value="0" data-replace="x:0">Less than 1/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq1" value="1" data-replace="x:1">1/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq1" value="2" data-replace="x:2">2-3 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq1" value="3" data-replace="x:3">4-6 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq1" value="4" data-replace="x:4">1/day<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq1" value="5" data-replace="x:5">2 or more times/day<span class="checkmark"></span></label> <br>
                    
                    <h3>2. Fruit, including fresh, canned, or frozen, but not including juices.</h3>
                    
                      <label class="radio-container"><input type="radio" name="dietq2" value="0" data-replace="x:0">Less than 1/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq2" value="1" data-replace="x:1">1/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq2" value="2" data-replace="x:2">2-3 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq2" value="3" data-replace="x:3">4-6 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq2" value="4" data-replace="x:4">1/day<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq2" value="5" data-replace="x:5">2 or more times/day<span class="checkmark"></span></label> <br>
                    
                    <h3>3. High-fibre cereals, such as Raisin Bran or Fruit and Fibre, cooked oatmeal, or whole-grain breads, such as whole wheat, rye, or pumpernickel.</h3>
                  
                      <label class="radio-container"><input type="radio" name="dietq3" value="0" data-replace="x:0">Less than 1/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq3" value="1" data-replace="x:1">1/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq3" value="2" data-replace="x:2">2-3 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq3" value="3" data-replace="x:3">4-6 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq3" value="4" data-replace="x:4">1/day<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="dietq3" value="5" data-replace="x:5">2 or more times/day<span class="checkmark"></span></label> <br>
                      
              </div>
              <div id="exercise" class="survey-box" data-show-dialog>
                  <h1>The next category is EXERCISE.</h1>
                  <h2>To answer the following questions, please indicate how many times per week you take part in the following activities for at least 30 minutes or more at a time.<br>
                    Choose only one option (the most applicable to you) out of the three questions below.</h2>
        
                  <h3>4. Light exercise, such as the following:</h3>
                  <ul>
                    <li>Light gardening and light housework (eg, dusting, sweeping, vacuuming),</li>
                    <li>leisurely walking (eg, walking your dog),</li>
                    <li>bowling, fishing, carpentry, playing a musical instrument,</li>
                    <li>volunteer work.</li>
                  </ul>
                  <div class = "onlylight">
                      <label class="radio-container"><input type="radio" name="likert_4" value="0" data-replace="x:0">0/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="likert_4" value="2" data-replace="x:2">1-3 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="likert_4" value="3" data-replace="x:3">4-7 times/week<span class="checkmark"></span></label> <br>
                      <label class="radio-container"><input type="radio" name="likert_4" value="4" data-replace="x:4">8 or more times/day<span class="checkmark"></span></label> <br>
                  </div>
                
                  <h3>5. Moderate exercise, such as the following:</h3>
                  <ul>
                    <li>Brisk walking,</li>
                    <li>bicycling, skating, swimming, curling,</li>
                    <li>gardening (eg, raking, weeding, digging),</li>
                    <li>dancing, Tai Chi or moderate exercise classes.</li>
                  </ul>
                    <div class = "moderate">
                    <label class="radio-container"><input type="radio" name="likert_4" value="0" data-replace="x:0">0/week<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="likert_4" value="4" data-replace="x:4">1-3 times/week<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="likert_4" value="6" data-replace="x:6">4-7 times/week<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="likert_4" value="8" data-replace="x:8">8 or more times/day<span class="checkmark"></span></label> <br>
                  </div>

                  <h3>6. Vigorous exercise, such as the following:</h3>
                  <ul>
                    <li>Running, bicycling, cross country skiing, lap swimming, aerobics,</li>
                    <li>heavy yard work,</li> 
                    <li>weight training,</li>
                    <li>soccer, basketball or other league sports.</li>
                  </ul>
                    <div class = "vigorous">
                    <label class="radio-container"><input type="radio" name="likert_4" value="0" data-replace="x:0">0/week<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="likert_4" value="6" data-replace="x:6">1-3 times/week<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="likert_4" value="9" data-replace="x:9">4-7 times/week<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="likert_4" value="12" data-replace="x:12">8 or more times/day<span class="checkmark"></span></label> <br>
                  </div>
              </div>

              <div id="alcohol" class="survey-box" data-show-dialog>
                  <h1>The next category is ALCOHOL CONSUMPTION. </h1>
                  <h2>Please indicate how many drinks of the following types of alcohol you consume in an average week.</h2>
                  <h3>7. WINE (1 drink: 3-5 oz or 89-148 ml):</h3>
                    <select name="drinks" id="wine">
                      <option name = "drinks_1" value="0">0</option>
                      <option name = "drinks_1" value="1">1</option>
                      <option name = "drinks_1" value="2">2</option>
                      <option name = "drinks_1" value="3">3</option>
                      <option name = "drinks_1" value="4">4</option>
                      <option name = "drinks_1" value="5">5</option>
                      <option name = "drinks_1" value="6">6</option>
                      <option name = "drinks_1" value="7">7</option>
                      <option name = "drinks_1" value="8">8</option>
                      <option name = "drinks_1" value="9">9</option>
                      <option name = "drinks_1" value="10">10</option>
                      <option name = "drinks_1" value="11">11</option>
                      <option name = "drinks_1" value="12">12</option>
                      <option name = "drinks_1" value="13">13</option>
                      <option name = "drinks_1" value="14">14+</option> 
                  </select><br>
                  <h3>8. BEER (1 drink: 10-12 oz or 1 bottle):</h3>
                    <select name="drinks" id="beer">
                      <option name = "drinks_2" value="0">0</option>
                      <option name = "drinks_2"  value="1">1</option>
                      <option name = "drinks_2"  value="2">2</option>
                      <option name = "drinks_2"  value="3">3</option>
                      <option name = "drinks_2"  value="4">4</option>
                      <option name = "drinks_2"  value="5">5</option>
                      <option name = "drinks_2"  value="6">6</option>
                      <option name = "drinks_2"  value="7">7</option>
                      <option name = "drinks_2"  value="8">8</option>
                      <option name = "drinks_2"  value="9">9</option>
                      <option name = "drinks_2"  value="10">10</option>
                      <option name = "drinks_2"  value="11">11</option>
                      <option name = "drinks_2"  value="12">12</option>
                      <option name = "drinks_2"  value="13">13</option>
                      <option name = "drinks_2"  value="14">14+</option> 
                  </select><br>
                  <h3>9. SPIRITS (1 drink: 1-1.5 oz or 30-44 ml):</h3>
                    <select name="drinks" id="spirit">
                      <option name = "drinks_3"  value="0">0</option>
                      <option name = "drinks_3" value="1">1</option>
                      <option name = "drinks_3" value="2">2</option>
                      <option name = "drinks_3" value="3">3</option>
                      <option name = "drinks_3" value="4">4</option>
                      <option name = "drinks_3" value="5">5</option>
                      <option name = "drinks_3" value="6">6</option>
                      <option name = "drinks_3" value="7">7</option>
                      <option name = "drinks_3" value="8">8</option>
                      <option name = "drinks_3" value="9">9</option>
                      <option name = "drinks_3" value="10">10</option>
                      <option name = "drinks_3" value="11">11</option>
                      <option name = "drinks_3" value="12">12</option>
                      <option name = "drinks_3" value="13">13</option>
                      <option name = "drinks_3" value="14">14+</option>
                  </select><br><br>
              </div>
              <div id="smoking" class="survey-box" data-show-dialog>
                  <h1>Now your SMOKING habits.</h1>
                  <h2>Please indicate your smoking habits below.</h2>
                  <h3>10. Are you a smoker?</h3>
                  <label class="radio-container"><input type="radio" name="smoker" value="0" data-replace="x:0">Yes<span class="checkmark"></span></label> <br>
                  <label class="radio-container"><input type="radio" name="smoker" >No<span class="checkmark"></span></label> <br> <br>  
              </div> 
              <div id="eversmoke" class="survey-box" data-show-dialog>
                  <h3>10a. If no, did you ever smoke?</h3>
                    <label class="radio-container"><input type="radio" name="eversmoked" value="1" data-replace="x:1">Yes<span class="checkmark"></span></label> <br>
                    <label class="radio-container"><input type="radio" name="eversmoked" value="2" data-replace="x:2">No<span class="checkmark"></span></label> <br> <br>  
              </div>
              <div id="stress" class="survey-box" data-show-dialog>
                  <h1>The last category is LIFE STRESS.</h1>
                  <h3>12. To answer this question, please circle the number you feel best corresponds to the level of stress in your everyday life.</h3>
                  <h4>
                    <span>Not at all stressful</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span>Very stressful</span>
                  </h4>
                        <label class="radio-container"><input type="radio" name="stress_scale" value="6" data-replace="x:6">6<span class="checkmark"></span></label>
                        <label class="radio-container"><input type="radio" name="stress_scale" value="5" data-replace="x:5">5<span class="checkmark"></span></label>
                        <label class="radio-container"><input type="radio" name="stress_scale" value="4" data-replace="x:4">4<span class="checkmark"></span></label>
                        <label class="radio-container"><input type="radio" name="stress_scale" value="3" data-replace="x:3">3<span class="checkmark"></span></label>
                        <label class="radio-container"><input type="radio" name="stress_scale" value="2" data-replace="x:2">2<span class="checkmark"></span></label>
                        <label class="radio-container"><input type="radio" name="stress_scale" value="1" data-replace="x:1">1<span class="checkmark"></span></label> <br>
                  
              </div>
              <div id="scores" class="survey-box" data-show-dialog>
                <h1>You have now completed the test. 
                <h2>Click show to view you lifestyle assessment scores.</h2>
                <h3>Please take a picture of the following lifestyle category scores as you will need them for the next section. </h3>

                <button type="button" class="btn-navigate" onclick="TotalScores()">Show</button>
                <div class="Diet-raw-score"></div>
                <div class="Exercise-raw-score"></div>
                <div class="Alcohol-raw-score"></div>
                <div class="Smoke-raw-score"></div>
                <div class="Stress-raw-score"></div>
                <div class="Total-score"></div>

               


