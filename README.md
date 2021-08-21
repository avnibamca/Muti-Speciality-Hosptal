# Multi Specialty Hospital

I own a multi-specialty hospital chain with locations all across the world. My hospital is famous for
vaccinations. Patients who come to my hospital (across the globe) will be given a user card with
which they can access any of my hospitals in any location.

## The Problem

We maintain all customers in one database. There are heaps of customers who have user cards. So, I
decided to split up the customers based on the country and load them into corresponding country
tables.

To pull customers by country, my developers should know where all the Customer Data is available.
So, the data extracting will be done by our Source System. They will pull all the relevant customer
data and will give us a pipe delimited data file.

In design documents, you will have:

| File Position | Column Name         | Field Length | Data Type | Mandatory | Key Column |
|---------------|---------------------|--------------|-----------|-----------|------------|
| 1             | Customer Name       | 255          | VARCHAR   | Y         | N          |
| 2             | Customer ID         | 18           | VARCHAR   | Y         | Y          |
| 3             | Customer Open Date  |              | DATE      | Y         | N          |
| 4             | Last Consulted Date |              | DATE      | N         | N          |
| 5             | Vaccination Type    | 5            | VARCHAR   | N         | N          |
| 6             | Doctor Consulted    | 255          | VARCHAR   | N         | N          |
| 7             | State               | 5            | VARCHAR   | N         | N          |
| 8             | Country             | 5            | VARCHAR   | N         | N          |
| 9             | Post Code           | 5            | INTEGER   | N         | N          |
| 10            | Date of Birth       |              | DATE      | N         | N          |
| 11            | Active Customer     | 1            | CHAR      | N         | N          |


**The sample file format will be:**

H|Customer_Name|CustomerID|CustomerOpenDate|LastConsultedDate|VaccinationType|Doctor|State|Country|PostCode|DateofBirth|ActiveCustomer
D|Alex|1|20101012|20121013|covishield|Piper Sheppard|Lange|USA||06031987|A
D|John|2|20101112|20210329|covishield|Savannah Keith|Sint|USA||26011999|A
D|Matthew|3|20100323|20160202|covishield|Justin Leblanc|Marlb|INDIA|18518|17121996|A
D|Matt|4|20210101|20220305|covix|Colin Hodge|Eindh|Nepal|19167|15031966|A
D|Jacob|5|20200505|20210814|mvd|Charlotte Campbell|Keumi|Nepal|Z4730|27061959|A
D|Rocky|6|20150518|20190808|mvd|Garrison Mosley|Salci|INDIA|87049|17081971|A
D|Angel|7|20171214|20171214|covix|TaShya Mendez|UAE|india|61188|11082000|A
D|Arpita|8|20190126|20201231|covix|Amal Gray|Burin|UAE|96896|24071999|A
D|Nashant|9|20181130|20181201|mvd|Chelsea Farmer|INDIA|Nepal|09666|03101928|A
T|9|

**You need to load the data into tables, one table per country**
Technical Assessment: Deliverables
1. Create table queries
2. And any script or program which reads the data from flies
