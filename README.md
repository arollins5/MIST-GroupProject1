
# Group 10 MIST4610 Group Project 1


## Team Name
4610Fa24Group10
## Team Members

- Addie Rollins [@addisonrollins](https://www.github.com/octokatherine)
- Nozomi Thacker [@nozomithacker](https://github.com/n-thacker/MIST4610Group10Project1)


## Scenario Description

The objective of this project is to create a relational database modeled after hypothetical local restaurant The Dawg House. The Dawg House is a local Athens restaurant that caters to the local community and students at UGA. Our goal is to gain knowledge using the database as well as to improve day-to-day business within the diner, refine the workflow, and provide better service to customers. To do this, we have modeled the relevant relationships and entities as well as generated sample data to perform queries that will help us achieve our goal.

## Data Model(PLACEHOLDER CHANGE THIS)
![DataModel](https://github.com/user-attachments/assets/d043c8fc-9d6a-416d-ad1f-10126a400428)

### Description

Our data model starts with the `Jobs` entity. This entity represents each department in the restaurant. It contains the pay and description of each job department. Additionally, each department has many employees, but not all employees need to have a department, which is represented by the non-identifying one-to-many relationship with the `Employees` entity.

This entity includes a unique identifier of each employee as well as the employee's name, phone number, and pay. Some employees are Servers who take care of many tables, which are represented by the one-to-many relationship connecting the `Employees` and `Seating` entities.

The `Seating` entity includes information about each table, such as the table number, the number of seats each table has, and the employee serving the table. `Seating` also has two other relationships with entities other than `Employees`. One of the branches is for the table reservations.

At The Dawg House, customers can make reservations that are stored in the `TableReservations` entity. The information stored in this entity includes the number of people in the party, the reservation date, the table they are assigned to and a unique identifier for each reservation. Additionally, there can be many reservations for one table, but there needs to be a table for a reservation, which is represented by the identifying one-to-many relationship.

The other branch from `Seating` is related to the customers' orders. Many customers over time can have orders at one table, which is why there is a one-to-many relationship from `Seating` to `CustomerOrders`. The `CustomerOrders` entity includes information about the order's unique identifier, the amount on the order, the payment type of order, the contact information of the customer who made the order, and the table number they were at. It does not include the items of the order, which is instead represented by the `OrderDetails` entity with a one-to-many relationship as there are many details for each order.

The `OrderDetails` entity is an associative entity for `CustomerOrders` and `Menu`. It is a many-to-many relationship as an order in `CustomerOrders` has many items from the `Menu` and each item shows up in many orders. Additionally, a unique identifier of any promotions from the `Promotions` entity is also included in `OrderDetails`. It is connected to `Promotions` with a non-indeitfying relationship as there is not a promotion for each item in the order. On the other hand, there are identifying relationships between `CustomerOrders` and `Menu` from `OrderDetails` as there needs to be an item from the menu and an order for the details in each order to exist.

Moving to the `Menu` entity, it includes the name of each item as well as their price, description, and a unique identifier for each item. Finally, in the `Promotions` entity, it includes other data about the promotion name, start and end date of the promotion, and the item the promotion is connected to. It is connected to `Menu` through a one-to-one identifying relationship, as there needs to be an item for a promotion to even occur.

## Data Dictionary
![thumbnail_jobs](https://github.com/user-attachments/assets/aa3cef0c-daf6-4d6f-b72a-7c570974af77)

![thumbnail_employees](https://github.com/user-attachments/assets/dd8896f6-cf71-41bd-8dda-424a289f349b)

![thumbnail_seating](https://github.com/user-attachments/assets/7f08d3e1-e1e7-43fb-b7ef-833749469933)

![thumbnail_tableRes](https://github.com/user-attachments/assets/4acd0ec4-4151-4d35-8942-100a71a2b89f)

![thumbnail_customerOrders](https://github.com/user-attachments/assets/08c64c76-f159-4a4c-bb16-8d2ae0374ab1)

![thumbnail_orderdetails](https://github.com/user-attachments/assets/0d304ff0-f740-41c3-a22a-075f56982307)

![thumbnail_menu](https://github.com/user-attachments/assets/81f3c35a-d05a-4798-a830-6cb88fd2ce18)

![thumbnail_promotions](https://github.com/user-attachments/assets/dba1d119-6493-4310-b97f-15a820044e5c)

## Queries

### Query Matrix
![QueryMatrix](https://github.com/user-attachments/assets/7e0b20d9-8574-4d45-8189-72b2a46e1ebb)


### Queries and Results
**1)** Query 1 lists out the first and last names of the employees that are serving on tables and counts how many tables they are waiting on and how many seats total they are serving.

![Query1](https://github.com/user-attachments/assets/71e39bee-2c9b-47e1-b91b-ec6764b6da80)

 - Query 1 shows managers how many tables and how many customers the servers are tending to. It can be used to provide an even workload and distribution of employees to manage the service flow/customer traffic.

**2)** Query 2 lists the average order amount from customer orders and lists the average amount for each table seat type. This is sorted in descending order from largest average to smallest average.

![Query2](https://github.com/user-attachments/assets/a5b04aa8-0085-4940-9b40-61fd654dcea6)

 - Query 2 shows what types of tables bring in the most money from customers compared to the average order and earnings of other tables. This allows management to see what table seat types to add to the diner in the future to increase sales.

**3)** Query 3 lists out the employee IDs, what department they belong to, and their overall hourly pay when they’re hourly pay ends in .00. If an employee has received a raise in this fiscal year, their hourly pay would end in .25.

![Query3](https://github.com/user-attachments/assets/bcfaeb24-0ec9-41ff-9e3d-f8d0f92d6536)

 - Query 3 finds out which employees’ hourly pays end in .00 which allows management to determine who should receive a raise next fiscal year as they have not gotten one this year.

**4)** Query 4 lists the employees' names, their title, and hourly pay specifically between the Cook and Kitchen staff. It is grouped by the employee's department and job unique identifier and ordered by each department in descending order so Kitchen staff are presented first.

![Query5](https://github.com/user-attachments/assets/ee18e381-ddfa-4ade-b695-db8e632e825c)

 - Query 4 ensures pay parity between kitchen and cook staff. While there has already been focus on server staff as they handle the clients, it’s important not to forget the back-of-house staff. This query allows managers to make sure that those holding these job positions are relatively equal in pay to support all staff in the restaurant.

**5)** Query 5 counts the number of servers that the restaurant currently has employeed.
![Query5](https://github.com/user-attachments/assets/2092087e-6573-43c2-8f38-a1967300ff61)

 - Query 5 is useful in determining if there is enough servers to ensure there are the right amount of servers. There can be a loss in performance for the restaurant if there is not enough servers to tend to tables and customers. However, it would be impractical and wasteful to have too many servers employeed at one time. This helps management keep an equilibrium between customer server and managing costs.

**6)** Query 6 lists the customer contact information for customers who had a total over $40 in descending order.

![Query6](https://github.com/user-attachments/assets/bbdc50c9-6641-43b6-b76a-1ae744ced88e)

 - Query 6 allows employees to pull the contact information of cusomters who spent a signficant amount of money at the restaurant. By pulling this data, managers can use the contact information to send promotions details and news about any events. This is to entice the higher paying customer to come back to the restaurant and generate customer loyalty. 

**7)** Query 7 lists items on the menu with their name and price in descensding order if the price is less than or equal to 9.99.

![Query7](https://github.com/user-attachments/assets/0aa2722c-a442-4cd8-9ee8-6364e64499ae)

 - Query 7 is important as The Dawg House serves the local community, many of which are college students. Considering this, managers are going to want to cater to the "broke college student" demographic and make sure there are ample menu items that are afforadable and appealing.

**8)** Query 8 shows the amount of reservations for each table in descending order along with the amount of seats the table has.

![Query8](https://github.com/user-attachments/assets/d1b81a75-87ff-4898-8162-c2a446ee2616)

 - Query 8 helps managers determine if certain tables receive more reservations based on amount of seats. Additionally, it can help servers know how to optimize walk-in customer traffic and direct them to tables that are not as popular for reservations to ensure the seating is utilized. 
