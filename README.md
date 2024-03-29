# PWC Forge Job Simulation Task 2 : Customer Retention-Analysis

link: https://app.powerbi.com/view?r=eyJrIjoiZjQ1NmFkYzAtMjc0OC00MDYyLWE3ZWUtNTYyYmZhMWE0ZmYzIiwidCI6IjZmMGJiNzJmLTUzNzctNGRkZi05MzZhLWI2YzcyYmYyMWFlMiIsImMiOjF9

## 1. Problem Statement

Retention manager from telecom reaches out to you, he wants to better understand data. He hopes you can define proper KPIs and reflect them on the dashboard.

The points he wants to cover:

- Customers in the telecom industry are hard-earned: we don’t want to lose them
- The retention department is here to get customers back in case of termination 
- Currently, we get in touch after they have terminated the contract, but this is reactionary: it would be better to know in advance who is at risk 
- We  have done customer analysis with Excel: it has always ended in a dead-end
- We would like to know more about our customers: visualised clearly so that it’s self-explanatory for our management


## 2. Data Preprocessing and Modelling

- Removing duplicates and null values.

- Standardize data format: Replace 0 and 1 in Senior Citizen column to No and Yes.

    If [SeniorCitizen] = 1 then “Yes” else “No”
  
- Add condition column:
  
    Subscription Time: 
'01 Churn-Dataset'[tenure]<=12, “<1 year”, '01 Churn-Dataset'[tenure]<=24,"< 2 years",'01 Churn-Dataset'[tenure]<=36,"< 3 years",'01 Churn-Dataset'[tenure]<=48,"< 4 years", '01 Churn-Dataset'[tenure]<=60,"< 5 years",'01 Churn-Dataset'[tenure]<=72,"< 6 years"


## 3. Create Measures (DAX)

**Demographics:**

`- Total Customers = COUNTROWS('01 Churn-Dataset')`

`- SeniorCitizen in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Senior Citizen]),'01 Churn-Dataset'[Senior Citizen]="Yes"), COUNT('01 Churn-Dataset'[Senior Citizen]), 0)`

`- Partner in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Partner]), '01 Churn-Dataset'[Partner] = "Yes"), COUNT('01 Churn-Dataset'[Partner]), 0)`

`- Dependent in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Dependents]), '01 Churn-Dataset'[Dependents]="Yes"), COUNT('01 Churn-Dataset'[Dependents]), 0)`

**Services:**

`- Online backup in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[OnlineBackup]), '01 Churn-Dataset'[OnlineBackup]="Yes"), COUNT('01 Churn Dataset'[OnlineBackup]), 0)`

`- Online security in % =DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[OnlineSecurity]), '01 Churn-Dataset'[OnlineSecurity] ="Yes"),COUNT('01 Churn-Dataset'[OnlineSecurity]),0)`

`- Phone service in % =DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]), '01 Churn-Dataset'[PhoneService] ="Yes"), COUNT('01 Churn-Dataset'[PhoneService]),0)`

`- Streaming Movies in % =DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[StreamingMovies]), '01 Churn-Dataset'[StreamingMovies] ="Yes"), COUNT('01 Churn-Dataset'[StreamingMovies]),0)`

`- Streaming TV in % =DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[StreamingTV]), '01 Churn-Dataset'[StreamingTV] ="Yes"), COUNT('01 Churn-Dataset'[StreamingTV]),0)`

`- Tech Support in % =DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[TechSupport]), '01 Churn-Dataset'[TechSupport] ="Yes"), COUNT('01 Churn-Dataset'[TechSupport]),0)`

`- Device protection in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[DeviceProtection]), '01 Churn-Dataset'[DeviceProtection] ="Yes",COUNT('01 Churn-Dataset'[DeviceProtection]),0)`

**Churn:**

`- Churn Count: CALCULATE(COUNT('01 Churn-Dataset'[Churn]), ALLSELECTED('01 Churn-Dataset'[Churn]),'01 Churn-Dataset'[Churn] = "Yes")`



## 4. Power BI Dashboard

<img width="1159" alt="截屏2024-01-29 17 39 02" src="https://github.com/qinxinLiu/PWC-Forge-Job-Simulation-Task-2-Customer-Retention-Analysis/assets/67852322/03bf4c9e-f3d5-41e1-be43-93682cdc121a">
<img width="1155" alt="截屏2024-01-29 17 39 13" src="https://github.com/qinxinLiu/PWC-Forge-Job-Simulation-Task-2-Customer-Retention-Analysis/assets/67852322/953e10eb-ab27-4acf-a49f-9ba71925404a">
<img width="1151" alt="截屏2024-01-29 17 39 22" src="https://github.com/qinxinLiu/PWC-Forge-Job-Simulation-Task-2-Customer-Retention-Analysis/assets/67852322/759cd659-46a0-411c-983e-9bd277889dc8">


## 5. Insights

Based on the dashboard above, the following conclusion can be drawn:


- There are `7,043` customers, and the current churn rate is `26.5%`. Monthly total charges and yearly total charges of all customer are approximately at `$456.1K` and  `$16.1 millions`.

- Half of the lost customers had a subscription time of less than one year; the contract type for `88%` of churned customers is a Month-to-Month contract, therefore, the business could lose clients who have just joined.
  
- `Electronic` check and `Mailed` check have noticeably higher churn rates for` InternetService 'DSL'`.

- Customers open `Tech Ticket` have a higher tendency to churn.

- Senior citizens exhibit higher customer loyalty.
  
- Customers who have signed up for fewer services tend to churn, such as `online security`, `tech support`, and `phone serivices`.
  
- Many clients experienced problems with `fiber optics`. Fiber optic internet service was used by up to `42%` of the consumers who left.
  
## 6. Suggestions

- Month-to-month contracts are a contributing element in the majority of churned clients. The company might persuade them by making offers for yearly contracts.

- Enhancing fiber network services in order to keep clients.

- To attract more clients, phone service needs to be upgraded.



