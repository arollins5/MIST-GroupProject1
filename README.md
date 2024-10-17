
# Group 10 MIST4610 Group Project 1


## Team Name
4610Fa24Group10
## Team Members

- Addie Rollins [@addisonrollins](https://www.github.com/octokatherine)
- Nozomi Thacker [@nozomithacker](https://github.com/n-thacker/MIST4610Group10Project1)


## Scenario Description

The objective of this project is to create a relational database modeled after hypothetical local restaurant The Dawg House. The Dawg House is a local Athens restaurant that caters to the local community and students at UGA. Our goal is to gain knowledge using the database as well as to improve day-to-day business within the diner, refine the workflow, and provide better service to customers. To do this, we have modeled the relevant relationships and entities as well as generated sample data to perform queries that will help us achieve our goal.
## Data Model

Our data model starts with the `Jobs` entity. This entity represents each department in the restaurant. It contains the pay and description of each job department. Additionally, each department has many employees, but not all employees need to have a department, which is represented by the non-identifying one-to-many relationship with the `Employees` entity.

This entity includes a unique identifier of each employee as well as the employee's name, phone number, and pay. Some employees are Servers who take care of many tables, which are represented by the one-to-many relationship connecting the `Employees` and `Seating` entities.

The `Seating` entity includes information about each table, such as the table number, the number of seats each table has, and the employee serving the table. `Seating` also has two other relationships with entities other than `Employees`. One of the branches is for the table reservations.

At The Dawg House, customers can make reservations that are stored in the `TableReservations` entity. The information stored in this entity includes the number of people in the party, the reservation date, the table they are assigned to and a unique identifier for each reservation. Additionally, there can be many reservations for one table, but there needs to be a table for a reservation, which is represented by the identifying one-to-many relationship.

The other branch from `Seating` is related to the customers' orders. Many customers over time can have orders at one table, which is why there is a one-to-many relationship from `Seating` to `CustomerOrders`. The `CustomerOrders` entity includes information about the order's unique identifier, the amount on the order, the payment type of order, the contact information of the customer who made the order, and the table number they were at. It does not include the items of the order, which is instead represented by the `OrderDetails` entity with a one-to-many relationship as there are many details for each order.

The `OrderDetails` entity is an associative entity for `CustomerOrders` and `Menu`. It is a many-to-many relationship as an order in `CustomerOrders` has many items from the `Menu` and each item shows up in many orders. Additionally, a unique identifier of any promotions from the `Promotions` entity is also included in `OrderDetails`. It is connected to `Promotions` with a non-indeitfying relationship as there is not a promotion for each item in the order. On the other hand, there are identifying relationships between `CustomerOrders` and `Menu` from `OrderDetails` as there needs to be an item from the menu and an order for the details in each order to exist.

Moving to the `Menu` entity, it includes the name of each item as well as their price, description, and a unique identifier for each item. Finally, in the `Promotions` entity, it includes other data about the promotion name, start and end date of the promotion, and the item the promotion is connected to. It is connected to `Menu` through a one-to-one identifying relationship, as there needs to be an item for a promotion to even occur.

## Queries
1) Query 1 lists out the first and last names of the employees that are serving on tables and counts how many tables they are waiting on and how many seats total they are serving.

![Untitled](https://github.com/user-attachments/assets/093c5251-36d8-472d-a200-8c4497faf5c2)

Query 1 shows managers how many tables and how many customers the servers are tending to. It can be used to provide an even workload and distribution of employees to manage the service flow/customer traffic.

2) Query 2 lists the average order amount from customer orders and lists the average amount for each table seat type. This is sorted in descending order from largest average to smallest average.

![Untitled](https://github.com/user-attachments/assets/43ac2356-2074-4f05-9cd3-40931a2982af)

Query 2 shows what types of tables bring in the most money from customers compared to the average order and earnings of other tables. This allows management to see what table seat types to add to the diner in the future to increase sales.

3) Query 3 lists out the employee IDs, what department they belong to, and their overall hourly pay when they’re hourly pay ends in .00. If an employee has received a raise in this fiscal year, their hourly pay would end in .25.

![Untitled](https://github.com/user-attachments/assets/bcfaeb24-0ec9-41ff-9e3d-f8d0f92d6536)

Query 3 finds out which employees’ hourly pays end in .00 which allows management to determine who should receive a raise next fiscal year as they have not gotten one this year.

4) Query 4 lists the employees' names, their title, and hourly pay specifically between the Cook and Kitchen staff. 

![Untitled](https://github.com/user-attachments/assets/470a389a-930e-4fa4-b0df-16d666edef85)







