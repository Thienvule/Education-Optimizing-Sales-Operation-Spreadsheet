# Education | Optimizing Sales Operation | Spreadsheet

## Business Context
The company is an academy dedicated to training individuals in data skills for careers in data analysis. As the academy expands, the sales manager is encountering difficulties in manually managing the allocation of an increasing number of sales leads. This process was much simpler when there were fewer leads. I have been assigned the task of developing a more efficient solution to enhance the lead allocation process.

Understanding the need:
- Goal: Develop a CRM dashboard capable of automatically allocating leads and tracking the performance of the sales team.
- Benefit: Saves time, automates lead allocation, measures team performance.



## Overview
The primary objective of this operational dashboard is to facilitate the automatic allocation of leads generated from landing pages to the appropriate stakeholders, specifically the sales manager and sales team members.

Process flow
- Lead Generation: Leads are collected through various landing pages.
- Data Integration: These leads are automatically recorded and updated in the raw data file.
- Lead Allocation: The system evenly distributes the leads among the sales team members to ensure fairness and efficiency.
- Lead Management: Sales team members engage with the leads, managing and updating their status and progress as they work through them.
- Progress Monitoring: Sales managers have access to a dashboard that provides an overview of the team's progress, enabling them to make informed decisions and take action as necessary.


Documents needed:
- Sales_Raw Leads: This file contains the actual raw data of sales leads, with information collected directly from the landing pages. It serves as the foundational data set for the sales process.
![image](https://github.com/user-attachments/assets/a2f23fdf-bfcc-4edc-a656-a0a59fe788eb)

  
- Sales_CRM Auto Dashboard: This is the primary file where lead allocation takes place. It also provides sales managers with insights into the performance of the team, allowing for effective monitoring and management.

![image](https://github.com/user-attachments/assets/e23539c9-675f-4406-a4b2-295d985c27d8)


  
- Sales_Member A/B/C/...: These are personalized dashboards for each sales team member, which can be scaled according to the number of team members. Each dashboard allows individual members to track their own leads and performance metrics. The team members will update their progress in this section, which will then be reflected in the Sales_CRM Auto Dashboard for the sales manager.

![image](https://github.com/user-attachments/assets/c4956458-a3ef-4041-a22f-f50556007d27)



## Building the dashboard - Sales_CRM Auto Dashboard
Let's get technical.

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

### Linking Ladipage and Sales info

![image](https://github.com/user-attachments/assets/c38ebb56-ce6c-4531-a294-50c8e7e76a28)

This tab is dedicated to storing leads generated from our landing page. Whenever a new lead acquires a ticket or submits their information, the data will be updated accordingly. This simulates the process of how new leads will be integrated when the landing page updates. I plan to leverage ARRAYFORMULA and QUERY functions to automate this workflow, ensuring that data flows seamlessly into the subsequent rows of the Sales Info tab without requiring manual input.

![image](https://github.com/user-attachments/assets/3a90b97c-1df5-469d-9574-7e4d534adc57)


### Sales team tab
![image](https://github.com/user-attachments/assets/3535b8a5-8496-4a25-9fb1-cbbc5d1fc0cc)

This tab is designed to store sales information. The dashboard is scalable, allowing us to easily add new sales team members to this tab as our team grows.

I am now going to build a dashboard that can automatically allocate leads to these members.

### Sales tab
However, we will not be building anything else in the raw file to avoid direct interaction with the raw data. To import data from the raw sheet, I would utilize IMPORTRANGE function to import data from the raw file to a new spreadsheet:

![image](https://github.com/user-attachments/assets/41f40a6d-329a-48fe-b8ac-0c96d886c28c)


This function facilitates the import of data from a specified link, ensuring that the new sheet updates automatically whenever the raw data is refreshed.

To allocate leads effectively, we will employ two key functions: MOD and ROW. The logic behind this allocation is as follows: the ROW function provides the current row number, and the MOD function divides that number by the total number of sales team members, returning the remainder. By adding 1 to this remainder, each row is assigned a number that corresponds to the ID of a sales member. Finally, I will use the XLOOKUP function to retrieve the name of the sales member assigned to each lead. Besides, I would use ARRAYFORMULA to apply the function to all the rows of the tab.

Allocating ID:
![image](https://github.com/user-attachments/assets/31e356dc-cb57-496a-8fbd-9d220bbbd80d)

Sales member XLOOKUP:
![image](https://github.com/user-attachments/assets/5a3cf551-6e87-4779-bd8b-d071482ba791)

### Sales_Member A/B/C/...

The leads allocated to each sales member will look like this: 

![image](https://github.com/user-attachments/assets/ee1ccbed-5eb3-4344-ab62-54ac16d817e7)

This is accomplished using a QUERY function that extracts all relevant columns based on the names of the sales team members. Subsequently, this information will be imported into each member's personal sheet using the IMPORTRANGE function.

![image](https://github.com/user-attachments/assets/83250b46-4625-4b2a-bcba-865fcfe00b87)

Here, another column of progress tracking data validation will be added:
![image](https://github.com/user-attachments/assets/6b121a79-c348-4ab4-bd0e-fb01e54e14b4)

If a member wishes to have separate tabs for each progress category, they can use the QUERY function as follows to create a tab specifically for customers who have been contacted:

![image](https://github.com/user-attachments/assets/b9bfe004-ca24-4b13-8e11-54e95c32fec6)

They can also build a customizable personal dashboard tab to oversee their own progress. This is accomplished using pivot table:

![image](https://github.com/user-attachments/assets/a168af02-a133-4138-87c3-fcc4438d11f0)



### Sales Overview
![image](https://github.com/user-attachments/assets/5b555ad6-608f-4df2-b82e-44a2a3402847)


On the Sales Overview tab of the manager's dashboard, the progress of each team member will be imported using our preferred function, IMPORTRANGE. Additionally, an 'All Leads' table will summarize all progress categories. This operational dashboard is designed to be scalable, allowing it to accommodate an increasing number of team members.





