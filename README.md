
A simple formula to calculate how much you should for your freelance work.

The provided values are examples. Adjust them according to your needs: Adjust how much money you need per month, how many hours per day you are willing to work which regular monthly expenses you have for your job etc.

```javascript
// Hourly rate formula for freelancers
var monthly_net_i_need = 2000,
    work_hours_per_day = 8,
    monthly_expenses_for_my_job = [
      {
        purpose: "laptop for two years",
        value: 43
      },
      {
        purpose: "coworking space",
        value: 50
      },
      {
        purpose: "business lunches",
        value: 40
      }
    ],
    vacation_days_per_year = 24,
    paperwork_hours_per_week = 10,
    tax_and_social_security_modifier = 2; // assuming 50% of your income goes to tax and social security


var net_i_need_including_expenses = monthly_net_i_need + monthly_expenses_for_my_job.map(function(obj){ return obj["value"] }).reduce(function(a, b){ return a + b }, 0);
var monthly_gross = net_i_need_including_expenses * tax_and_social_security_modifier; 

var vacation_hours_per_month = (vacation_days_per_year / 12) * work_hours_per_day;
var available_work_hours_per_month = (((work_hours_per_day * 5) - paperwork_hours_per_week) * 4) - vacation_hours_per_month;

var hourly_rate = monthly_gross / available_work_hours_per_month;


// Price for project
var estimated_hours_of_work = 40,
    client_budget = 3000,
    client_budget_modifier = 1.1;

var minimum_price = estimated_hours_of_work * hourly_rate;
var haggle_room = client_budget - minimum_price;
var project_price = minimum_price * client_budget_modifier;

console.log("Don't work for less than this: " + minimum_price);
console.log("Proposed project price: " + project_price);
```
