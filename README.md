
## Objective

The main goal of this analysis was to understand user engagement with their app, what user segments are engaging with the app the most and what patterns are associated with both high and low engagement in order to develop strategies to increase app usage and features that can encourage better engagement and improve retention rates. 

In order to carry out the proposed analysis, **we wanted to answer the following questions:**

1. **How do user demographics affect engagement?**
2. **What user segments have the highest and lowest engagement**
3. **Is there a correlation between session behaviour and overall engagement?**
4. **How frequently are users logging into the app, and are there patterns in activity levels?**
5. **Which device types lead to the most engagement?**
6. **What trends can help improve retention and re-engagement?**

---

## Dataset

Tools:

- SQL **for Data Extraction**:
Extracted data using SQL and exporting this to Excel
- Excel **for Cleaning & Transformation**:
Used Excel to standardise dataset to get ready for visualisation in PowerBi. Also created some pivot tables to get an overview of the questions I wanted answered
- PowerBi **for Visualisation:** Used PowerBi to visualise trends and patterns

---

## Data Analysis Steps

**Data Cleaning:**

- Verified there were no duplicates by using ‘Remove duplicates’ icon in Excel
- Changed the number of decimal places to 2 in ‘AppUsageHoursPerDay’, ‘TotalEngagementScore’ & ‘AverageSessionDurationMinutes’ columns to standardise the data
- Used ‘IF’ statements to create segments for ‘AppUsageHoursPerDay’, ‘Number of Sessions’, ‘AverageSessionDurationMinutes’ & ‘LastLoginDate’ to use in visualisations in order to determine low and  high engagement

```sql
=IF([@AppUsageHoursPerDay] <= 3, "Light Usage", IF([@AppUsageHoursPerDay] <= 5, "Mild Usage", IF([@AppUsageHoursPerDay] <=8, "Moderate Usage", "Heavy Usage")))
```

```sql
=IF([@NumberOfSessions]<=10, "Minimal User", IF([@NumberOfSessions]<=25, "Occasional User", IF([@NumberOfSessions]<=50, "Regular User",IF([@NumberOfSessions]<=75,"Engaged User","Power User"))))
```

```sql
=IF([@AverageSessionDurationMinutes]<=10,"Very Short", IF([@AverageSessionDurationMinutes]<= 30,"Short",IF([@AverageSessionDurationMinutes]<=60, "Long", "Extended")))
```

```sql
=IF([@LastLoginDate] >= DATE(2024,7,31) - 30, "Active User", IF([@LastLoginDate]>= DATE(2024,7,31) - 90, "Engaged User", IF([@LastLoginDate] >= DATE(2024,7,31) - 180, "Inactive User", "Churned User")))
```

**Answering questions about user engagement:**



**1. How do user demographics affect engagement?**

![Screenshot 2024-11-03 at 14 42 13](https://github.com/user-attachments/assets/1b390918-94c7-4743-98ce-ccc9993ec316)

- Gender: The average engagement score is nearly equal between men and women, suggesting no significant gender difference in app usage.
- Age: Seniors (66+) have the highest engagement score, while young adults, middle-aged people, and adults show similar scores. This shows the importance of the app being user-friendly, particularly for the older customer base who may require simpler navigation.
- Location: Customers in Dallas, Houston, Chicago, and Phoenix have the highest engagement scores, whereas those in cities like New York and Los Angeles show the lowest engagement scores.


**2. What user segments have the highest and lowest engagement**

![Screenshot 2024-11-03 at 16 02 23](https://github.com/user-attachments/assets/545a7a7f-05ed-4582-b71c-7d079c60e57a)
- **Regular users (25-50 sessions) have the highest engagement scores**, followed by power users (75+ sessions). **Occasional users show the lowest engagement scores.**

![Screenshot 2024-11-04 at 18 14 58](https://github.com/user-attachments/assets/b2030916-db8a-4a16-8821-c9e48eac30d0)
- Customers with **very short (<10 mins) and short (<30 mins) average session durations tend to have much higher engagement scores** than those with **longer sessions, which have lower engagement scores**. This suggests that most customers don't spend much time on the app

![Screenshot 2024-11-04 at 18 15 24](https://github.com/user-attachments/assets/12bdf0b7-e919-4a59-a21b-5a0caf174d0a)

- Customers with **mild daily usage (3-5 hours) show higher engagement** scores compared to those with light, moderate, or heavy usage, who exhibit lower engagement scores.


**3. Is there a correlation between session behaviour and overall engagement?**

There's a **very** **weak positive correlation between the number of sessions and overall engagement**, suggesting that more sessions slightly increase engagement scores. However, there's a **negligible negative correlation between average session duration and total engagement scores**, suggesting that shorter sessions tend to result in higher engagement. This pattern implies that customers with **"frequent but shorter"** sessions generally achieve higher engagement levels. 

![Screenshot 2024-11-04 at 18 09 55](https://github.com/user-attachments/assets/741e82ea-2cf1-4022-9b66-6acd46cb1be9)
![Screenshot 2024-11-04 at 20 14 29](https://github.com/user-attachments/assets/5d7e08c2-641c-42c2-8338-c2cec070782a)


**4. How frequently are users logging into the app, and are there patterns in activity levels?**

![Screenshot 2024-11-03 at 15 57 35](https://github.com/user-attachments/assets/8197151e-cb84-4cb3-a536-3077ed90b83d)
- Daily user logins remain consistent throughout most of the month, with occasional dips. However, a significant drop in activity occurs towards the month's end.
  
![Screenshot 2024-11-04 at 18 10 57](https://github.com/user-attachments/assets/65ba1275-413a-445b-83c9-c4e371307747)
- Customers log in fairly consistently month-to-month. However, early in the year, there are dips every other month, while towards the year’s end, these dips are less frequent, meaning more people are spending time on the app towards the end of the year

![Screenshot 2024-11-04 at 18 11 46](https://github.com/user-attachments/assets/5a182ded-a624-4414-a829-5c5ebacb7478)
- Customers spend less time on the app at the start of the year.  Logins peak in the third quarter before dipping slightly in the fourth quarter.
- There’s a pattern of increased logins toward the end of the year, with a noticeable dip around mid-year.

![Screenshot 2024-11-04 at 18 11 26](https://github.com/user-attachments/assets/6e493544-adc1-4953-a116-22211933c379)
- More customers logged into the app in 2024 compared to 2023.

**6. Which device types lead to the most engagement?**

- Tablet users are the most engaged while other devices (Laptop, smartphone & desktop) have engagement scores that are fairly the same
    
    ![Screenshot 2024-11-03 at 14 54 26](https://github.com/user-attachments/assets/baf81034-64c7-474d-8613-e23666201be7)


**7. What trends can help improve retention and re-engagement?**

- Given that highly engaged users  have frequent, shorter sessions, it may be best to encourage this behaviour across all users. Simplifying the user interface to deliver an app that’s easy to navigate as well as showing content that can be consumed quickly can help improve retention.
- Lower engagement is linked to both longer sessions and heavy app usage, it’s possible that users spending extended time on the app are struggling to find what they need. To address this, the company might consider adding navigation aids or a live chat feature to help users find information or features more efficiently.
- Focus on engaging users in cities with lower engagement rates, like New York and Los Angeles, to improve retention and boost overall interaction on the app.
- Ensure in-app features are well optimised for smartphones, laptops, and desktops. Adding desktop or laptop notifications for these users could enhance engagement and retention. Consider incentives like daily login rewards to encourage regular, quick interactions.
- Since there is a mid-year dip in logins, the company could focus on re-engaging users around this time with push notifications and other timely reminders via email.
