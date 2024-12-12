# Spreadsheet-CRM-Lead-Automated- Scalable Dashboard

## Business Context
The company is an academy dedicated to training individuals in data skills for careers in data analysis. As the academy expands, the sales manager is encountering difficulties in manually managing the allocation of an increasing number of sales leads. This process was much simpler when there were fewer leads. I have been assigned the task of developing a more efficient solution to enhance the lead allocation process.

Understanding the need:
- Goal: Develop a CRM dashboard capable of automatically allocating leads and tracking the performance of the sales team.
- Benefit: Saves time, automates lead allocation, measures team performance.


## Building the dashboard 
### Function to use in this project
-   IMPORTRANGE
- 	QUERY
- 	FILTER
- 	MOD + ROW
- 	IF,IFS
- 	XLOOKUP
- 	ARRAYFORMULA
- 	COUNTIFS
- 	DATA VALIDATION

### Raw data overview
![image](https://github.com/user-attachments/assets/858dc758-789a-407c-99c7-e4b69e3586e7)

In the raw data sheet, the columns are defined as follows:
Sales info tab
- Timestamp: The date and time when the lead was entered from the landing page.
- Full Name: The name of the lead.
- Phone Number: The lead’s contact number.
- Job: The current occupation of the lead.
- Career change wish: Indicates whether the lead is interested in changing careers or simply seeks data skills to enhance their work performance.
- Ticket tier: Represents the various tiers of tickets for our regular webinars.

LadiPage tab
Recently, the team launched a new landing page to sell webinar tickets and collect customer data. This tab has not yet been linked to the original Sales Info tab and cannot replace it, as doing so would result in the loss of historical data from former customers

### Linking Ladipage and Sales info

![image](https://github.com/user-attachments/assets/c38ebb56-ce6c-4531-a294-50c8e7e76a28)
This tab is used to store leads generated from our landing page. Whenever a new lead acquires a ticket or submits their information, the data will be updated accordingly. However, sales team members currently need to manually transfer this information from the LadiPage tab to the Sales Info tab. I plan to utilize ARRAYFORMULA and QUERY to automate this process, allowing the data to flow into the next rows of the Sales Info tab without manual input:
![image](https://github.com/user-attachments/assets/3a90b97c-1df5-469d-9574-7e4d534adc57)

However, we will not be building anything else in these 2 tabs to avoid direct interaction with the raw data called "Sales". To import data from the raw sheet, I would utilize IMPORTRANGE function:

![image](https://github.com/user-attachments/assets/41f40a6d-329a-48fe-b8ac-0c96d886c28c)


This function facilitates the import of data from a specified link, ensuring that the new sheet updates automatically whenever the raw data is refreshed.







### Sales team tab
![image](https://github.com/user-attachments/assets/3535b8a5-8496-4a25-9fb1-cbbc5d1fc0cc)

This tab is designed to store sales information. The dashboard is scalable, allowing us to easily add new sales team members to this tab as our team grows.

I am now going to build a dashboard that can automatically allocate leads to these members.



















## Using the dashboard


































