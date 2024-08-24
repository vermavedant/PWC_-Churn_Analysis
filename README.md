# PWC_Churn_Analysis

## Objective
The objective of this task is to develop a comprehensive and intuitive dashboard that will empower the Retention Department to proactively identify at-risk customers and prevent contract terminations. This dashboard will visualize key customer metrics and insights, enabling management to make informed, data-driven decisions. By transitioning from a reactive to a proactive retention strategy.

### Requested KPIs
- Customers who left within the last month
- Services each customer has signed up for: phone, multiple lines, internet, online security, online backup, device protection, tech
support, and streaming TV and movies
- Customer account information: how long as a customer, contract, payment method, paperless billing, monthly charges, total charges
and number of tickets opened in the categories administrative and technical
- Demographic info about customers – gender, age range, and if they have partners and dependents

## Data Source
The data is given by Pwc Switzerland.

## Tools & Technologies
- **Excel:** For initial data exploration and preparation.
- **Power BI:** To transform data, create interactive dashboards and visualizations

## Process Overview
### 1. Get the Data
- The dataset is obtained from the Pwc Switzerland.

### 2. Explore the Data in Excel, in this stage, the data is being explored, and after closely examining the dataset, the following points were observed:
- **Data Exploration:** Initial exploration of the dataset to understand its structure and identify necessary columns for analysis.
- After exploring the data, it is found that the data is already cleaned but need to change some column name, change data type and need to add one extra column using M code in Power Queru Editor. These changes will be done in Power BI.

### 3. Visualize the data in Power BI

Before creating visualizations, we need to transform the data in the Power Query Editor as well as need to add one extra column:

1. **Transform Data**:
- In this stage, we have changed the columns name and corrected their data type.
- Extra column "Tenure_In_Years" is created in Power Query Editor.

### Visualizations
Now coming on to Visualizations, we have used:
Cards, Donut Chart, Pie Chart, Stacked Bar Chart & Stacked Column Chart

#### 1. Cards

The card shows all the number of services Churned customers has signed for, number of tech and admin tickets are opened by Churned customers.

#### 2. Donut Chart

This chart shows the number of lost customers using different internet services and the subscription type they were having.

#### 3. Pie Chart

This chart shows the no of lost customers on the basis of their Gender. And in another Pie chart, it shows the proportion of paperless billing of lost customers.

#### 4. Stacked Bar Chart

It shows the tenure of lost customers, how long the customer had joined us.

#### 5. Stacked Column Chart

This chart shows the lost customers using different payment method.

![Screenshot (235)](https://github.com/user-attachments/assets/d1a287cc-2304-4efc-91cd-f8ceb551f46b)

## DAX Measures

### 1. Count of Custm_Id
```sql
Count of Custm_Id = COUNTA(Churn_Data[customerID])
```

### 2. Count of Dependents
```sql
Count of Dependents = CALCULATE(
        COUNTA(Churn_Data[Dependents]),
        Churn_Data[Dependents] = "Yes",
        Churn_Data[Churn]= "Yes"
    )
```

### 3. Average Speed of Answer
```sql
Average Speed of Answer = CALCULATE(AVERAGE(Call_Center[Speed_of_Answers (S)]), Call_Center[Answered (Y/N)]="Y")

```

### 4. Count of DeviceProtection
```sql
Count of DeviceProtection = CALCULATE(
    COUNTA(Churn_Data[DeviceProtection]),
    Churn_Data[DeviceProtection] = "Yes",
        Churn_Data[Churn]= "Yes"
)

```

### 5. Count of MultipleLines
```sql
Count of MultipleLines = CALCULATE(
        COUNTA(Churn_Data[MultipleLines]),
        Churn_Data[MultipleLines] = "Yes",
        Churn_Data[Churn]= "Yes"
    )
```

### 6. Count of OnlineBackup
```sql
Count of OnlineBackup = CALCULATE(
    COUNTA(Churn_Data[OnlineBackup]),
    Churn_Data[OnlineBackup] = "Yes",
        Churn_Data[Churn]= "Yes"
)
```

### 7. Count of OnlineSecurity 
```sql
Count of OnlineSecurity = CALCULATE(
    COUNTA(Churn_Data[OnlineSecurity]),
    Churn_Data[OnlineSecurity] = "Yes",
        Churn_Data[Churn]= "Yes"
)
```

### 8. Count of PaperlessBilling
```sql
Count of PaperlessBilling = CALCULATE(
    COUNTA(Churn_Data[PaperlessBilling]),
    Churn_Data[PaperlessBilling] = "Yes",
        Churn_Data[Churn]= "Yes"
)
```

### 9. Count of Partner
```sql
Count of Partner = CALCULATE(
        COUNTA(Churn_Data[Partner]),
        Churn_Data[Partner] = "Yes",
        Churn_Data[Churn]= "Yes"
    )

```

### 9. Count of PhoneService
```sql
Count of PhoneService = 
        CALCULATE(
        COUNTA(Churn_Data[PhoneService]),
        Churn_Data[PhoneService] = "Yes",
        Churn_Data[Churn]= "Yes"
    )

```

### 9. Count of TechSupport
```sql
Count of TechSupport = CALCULATE(
    COUNTA(Churn_Data[TechSupport]),
    Churn_Data[TechSupport] = "Yes",
        Churn_Data[Churn]= "Yes"
)

    )

```

### 9. Lost Customers 
```sql
Lost Customers = CALCULATE(COUNTA(Churn_Data[Churn]), Churn_Data[Churn]="Yes")

```

### 9. Lost Monthly Charges
```sql
Lost Monthly Charges = CALCULATE(SUM(Churn_Data[MonthlyCharges]), Churn_Data[Churn]= "Yes")
```

### 9. Lost Total Charges
```sql
Lost Total Charges = CALCULATE(SUM(Churn_Data[TotalCharges]), Churn_Data[Churn]= "Yes")
```


### 5. Conclusions from the Analysis

Based on the data, here are some insights and findings that can be derived using the visualizations from Power BI:

#### **Customer Churn:** Lost 1,869 customers last month.
#### **Financial Impact:** Due to these churned customers:
- The loss in monthly charges is $139.13k.
- The loss in total charges is $2.86M.
#### **Customer Tenure:** Lost 999 customers who joined a year ago.
#### **Subscription Type:** 1,655 customers who had month-to-month subscriptions left.
#### **Demographics:** Among the customers we lost:
- 669 had partners
- 476 were senior citizens
- 326 had dependents
#### **Service Impact:** In terms of internet service:
- 1,297 customers who had fiber optic internet service left.
- This represents a 69.4% loss in fiber optic service customers.
