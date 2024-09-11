# Calorie Calculator

**A simple calorie tracking application built with JavaScript.**

## Description
This application helps users track their daily calorie intake and expenditure. It allows users to input their calorie budget and log their food and exercise. The app calculates the remaining calories and displays the results.

# How it Works
### Adding Entries
To add a new entry (meal or exercise), the user needs to:
1. Select the category (breakfast, lunch, dinner, snacks, exercise).
2. Fill in the fields for the entry name and the number of calories.

```javascript
// JavaScript code for adding a new entry

function addEntry() {
  // ... (rest of the code)
  const HTMLString = `
    <label for="${entryDropdown.value}-${entryNumber}-name">Entry ${entryNumber} Name</label>
    <input type="text" id="${entryDropdown.value}-${entryNumber}-name" placeholder="Name" />
    <label for="${entryDropdown.value}-${entryNumber}-calories">Entry ${entryNumber} Calories</label>
    <input
      type="number"
      min="0"
      id="${entryDropdown.value}-${entryNumber}-calories"
      placeholder="Calories"   

    />`;
  // ... (rest of the code)
}

// JavaScript code for calculating calories

function calculateCalories(e) {
  e.preventDefault();
  isError = false;
const breakfastNumberInputs = document.querySelectorAll('#breakfast input[type=number]');
  const lunchNumberInputs = document.querySelectorAll('#lunch input[type=number]');
  const dinnerNumberInputs = document.querySelectorAll('#dinner input[type=number]');
  const snacksNumberInputs = document.querySelectorAll('#snacks input[type=number]');
  const exerciseNumberInputs = document.querySelectorAll('#exercise input[type=number]');

  const breakfastCalories = getCaloriesFromInputs(breakfastNumberInputs);
  const lunchCalories = getCaloriesFromInputs(lunchNumberInputs);
  const dinnerCalories = getCaloriesFromInputs(dinnerNumberInputs);
  const snacksCalories = getCaloriesFromInputs(snacksNumberInputs);
  const exerciseCalories = getCaloriesFromInputs(exerciseNumberInputs);
  const budgetCalories = getCaloriesFromInputs([budgetNumberInput]);

  if (isError) {
    return;
  }

  const consumedCalories = breakfastCalories + lunchCalories + dinnerCalories + snacksCalories;
  const remainingCalories = budgetCalories - consumedCalories + exerciseCalories;
  const surplusOrDeficit = remainingCalories < 0 ? 'Surplus' : 'Deficit';
  output.innerHTML = `
  <span class="${surplusOrDeficit.toLowerCase()}">${Math.abs(remainingCalories)} Calorie ${surplusOrDeficit}</span>
  <hr>
  <p>${budgetCalories} Calories Budgeted</p>
  <p>${consumedCalories} Calories Consumed</p>
  <p>${exerciseCalories} Calories Burned</p>
  `;

  output.classList.remove('hide');
}
```

# Features

1. Customizable calorie budget: Users can set their own daily calorie goal.
2. Multiple entry categories: Breakfast, lunch, dinner, snacks, exercise.
3. Clear output: Results are displayed in an easy-to-understand format.
4. Input validation: Prevents calculation errors.

# Technologies Used
1. HTML: For the page structure.
2. CSS: For styling the page.
3. JavaScript: For the application logic.

