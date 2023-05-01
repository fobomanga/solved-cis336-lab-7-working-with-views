Download Link: https://assignmentchef.com/product/solved-cis336-lab-7-working-with-views
<br>
<header class="entry-header">

 <p class="entry-title">Lab 7 will introduce the concept of database views. This lab may be completed using either DeVry’s Omnymbus EDUPE-APP lab environment, or a local copy of the MySQL database running on your own computer using the OM database tables. The lab will utilize a set of tables that are represented by the ERD (OM_ERD.docx) and are created and populated by the script file (create_OM_db.sql). Follow the instructions in the file CreateOMTables.docx to create your database, tables, and data.

</header>

5/5 - (4 votes)

A few IMPORTANT things to note if using EDUPE MySQL:**There can be NO SPACES in alias names given to a column. For example:Select unit_price as “Retail Price “ from items; –this does NOT work in EDUPE MySQL.Any of the following WILL WORK:

**Any calculated fields MUST be given an alias (and note above NO SPACES in alias). For example:select unit_price * 2 from items; –this does NOT work in EDUPE MySQLThis will work:select unit_price * 2 as NewPrice from items;

<strong>Deliverables</strong>Lab Report (Answer Sheet) containing both the student-created SQL command(s) for each exercise, and the output showing the results obtained. Be sure your name is on the file.

<strong>LAB STEPS:</strong> Complete each of the exercises below.

<ol type="1">

 <li>Use an ALTER TABLE statement to update the customers table so that the Primary Key field is an auto-increment field, then create TWO insert statements to test proper operation, using your own first and last name for one (and a name of your choice for the second one), and any data you care to imagine for the remaining fields.IMPORTANT NOTE: When using a LOCAL copy of MySQL, if you attempt to simply issue the ALTER TABLE command you have composed by itself, you should receive an error similar to the following (try it for yourself!).ERROR 1833: Cannot change column ‘customer_id’: used in a foreign key constraint ‘orders_fk_customers’ of table ‘om.orders’(Note – EDUPE will not give this error message, however you should still follow the CORRECT procedure as discussed here to complete this problem).The reason for this is that you are attempting to alter data in one column that has a defined PK:FK relationship to a field in another table. Referential Integrity rules prevent this. So, how do you resolve such a problem?One approach to solving this dilemma is to turn off the foreign key checks that implement referential integrity rules. However, the danger here is that other users and processes operating on the database while these constraints are suspended could create or modify data in a way that compromises integrity. We can solve this second problem by preventing other users and processes from altering the data in the table in which we are working until we have turned the foreign key checks back on. We therefore need to construct a script that does the following.

  <ul>

   <li>Locks the customer table – lock table customers write;</li>

   <li>Turns off FK checks – set foreign_key_checks = 0;</li>

   <li>Alters the table to add the auto_increment feature to the PK field</li>

   <li>Turns FK checks back on – set foreign_key_checks = 1;</li>

   <li>Unlocks the customer table – unlock tables;</li>

  </ul>It is VERY important to consider that altering tables can require a bit of time for very large tables, and that while the table is locked, other users and processes cannot operate. Consequently, this kind of modification should not be done during peak operating hours in a production operation (as a student in a lab exercise, working on your own database, you may do this at any time) but ideally in hours during which the business does not normally operate. In cases where round-the-clock, high availability of a database is required, other approaches may be required. Addressing this problem in a high-availability, high-demand environment is an advanced topic, study of which is outside the scope of this course. Use the outline below to construct your script. Show all commands in your answer sheet along with the output of the commands.</li>

 <li>The Vice President of Marketing for your firm wants the firm’s sales representatives to be able to directly view and edit customer details, but only for the state to which a particular sales representative is assigned. You have suggested that this need can be addressed with a view. For example, a view could be created for one particular state, and user account permissions for accessing that view granted only to sales representatives from that state. The VP has asked you to quickly create a simple proof-of-concept demonstrating how this might work. Complete the following steps:

  <ul>

   <li>Construct a view on the customers table called CA_CUSTOMERS that consists of all data about customers that live in California.</li>

   <li>Display the data using this view to verify that only customers that reside in California are visible.</li>

   <li>Prove that It is possible to add or update records through this view by updating the record for Karina Lacy to change the spelling of Karina’s last name to Lacie.</li>

   <li>Display the data using the customer table to verify that the change has been made.</li>

  </ul>Show all commands in your answer sheet along with the output of the commands.</li>

 <li>The Senior Customer Service Manager has requested the ability to create a report at any time that will show shipped orders that took some specified number of days to fulfill.

  <ul>

   <li>Create a view named SHIPPING_TIME that lists only customer_first_name, customer_last_name, order_date, shipped_date, and the calculated field days_to_fulfill (use the DATEDIFF function) showing the number of days between when the customer placed the order and when it was shipped. Show the data from this view.Now let’s do some queries by adding sorting and filters USING THIS VIEW, WITHOUT CHANGING IT.</li>

   <li>Use the view to display the data sorted by highest to lowest days to ship</li>

   <li>Use the view to display only the orders that took less than 10 days to ship.</li>

   <li>Use the view to display only the orders that took more than 30 days to ship.</li>

  </ul></li>

 <li>Queries that require joins and aggregate functions can be easier to construct when using a view as a “temporary” table. Consider a report to show total sales by artist.

  <ul>

   <li>First create a view called SalesData that displays the order_id, item_id, the calculated field ItemTotal (which is quantity times price), the title and artist_id.</li>

   <li>Display the data in the SalesData view sorted by artist_id. Does this help you to “visualize” how to group the data to create the totals?</li>

   <li>Create a query USING THIS VIEW and the appropriate aggregate function to display artist_id and the total sales for each artist.</li>

   <li>Now join to the artist table in order to display the artist_name along with the total sales.</li>

  </ul></li>

 <li>Now use this same method to display the total sales per customer.

  <ul>

   <li>Create a view called SalesData with the appropriate data. At a minimum you will need customer_id and the calculated item total. DO NOT use the customer table in this view, it will be joined later.</li>

   <li>Display the data in your view sorted by customer_id. Does this help you to “visualize” how to group the data to create the totals?</li>

   <li>Create a query USING THIS VIEW and the appropriate aggregate function to display customer_id and the total sales for each customer.</li>

   <li>Now join to the customer table in order to display the customer_name as a single field named Customer along with the total sales. Sort the report by Total sales in descending order.</li>

  </ul></li>

</ol>

This is the end of Lab 7.

<blockquote class="wp-embedded-content" data-secret="zkFgfqh6QA">

 <a href="https://www.ankitcodinghub.com/product/cis336-lab-6-group-functions-subqueries-solved/">CIS336 Lab 6 Group Functions and Subqueries Solved</a>

</blockquote>

<iframe sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" data-secret="zkFgfqh6QA" width="600" height="338" title="“CIS336 Lab 6 Group Functions and Subqueries Solved” — ankitcodinghub" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" data-src="https://www.ankitcodinghub.com/product/cis336-lab-6-group-functions-subqueries-solved/embed/#?secret=zkFgfqh6QA" class="wp-embedded-content lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="></iframe>

<blockquote class="wp-embedded-content" data-secret="aBYqtIOg0D">

 <a href="https://www.ankitcodinghub.com/product/cis336-lab-3-building-physical-solved/">CIS336 Lab 3 Building the Physical Solved</a>

</blockquote>

<iframe sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" data-secret="aBYqtIOg0D" width="600" height="338" title="“CIS336 Lab 3 Building the Physical Solved” — ankitcodinghub" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" data-src="https://www.ankitcodinghub.com/product/cis336-lab-3-building-physical-solved/embed/#?secret=aBYqtIOg0D" class="wp-embedded-content lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="></iframe>

<blockquote class="wp-embedded-content" data-secret="ZdGcmEfsHO">

 <a href="https://www.ankitcodinghub.com/product/cis336-lab-2-expanded-entity-relationship-diagram-solved/">CIS336 Lab 2 The Expanded Entity Relationship Diagram Solved</a>

</blockquote>

<iframe sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" data-secret="ZdGcmEfsHO" width="600" height="338" title="“CIS336 Lab 2 The Expanded Entity Relationship Diagram Solved” — ankitcodinghub" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" data-src="https://www.ankitcodinghub.com/product/cis336-lab-2-expanded-entity-relationship-diagram-solved/embed/#?secret=ZdGcmEfsHO" class="wp-embedded-content lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="></iframe>

<blockquote class="wp-embedded-content" data-secret="VXHs8Sp8FB">

 <a href="https://www.ankitcodinghub.com/product/cis336-lab-1-normal-forms-entity-relationship-diagrams-solution/">CIS336 Lab 1 Normal Forms and Entity Relationship Diagrams Solution</a>

</blockquote>

<iframe sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" data-secret="VXHs8Sp8FB" width="600" height="338" title="“CIS336 Lab 1 Normal Forms and Entity Relationship Diagrams Solution” — ankitcodinghub" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" data-src="https://www.ankitcodinghub.com/product/cis336-lab-1-normal-forms-entity-relationship-diagrams-solution/embed/#?secret=VXHs8Sp8FB" class="wp-embedded-content lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="></iframe>

<table border="0" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td class="gutter"></td>

   <td class="code"></td>

  </tr>

 </tbody>

</table>

1

2

3

4

<code class="php plain">Select unit_price </code><code class="php keyword">as</code> <code class="php plain">“RetailPrice” from items;</code>

<code class="php plain">Select unit_price </code><code class="php keyword">as</code> <code class="php plain">“Retail_Price” from items;</code>

<code class="php plain">Select unit_price </code><code class="php keyword">as</code> <code class="php plain">Retail_Price from items;</code>

<code class="php plain">Select unit_price </code><code class="php keyword">as</code> <code class="php plain">RetailPrice from items;</code>

<table border="0" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td class="gutter"></td>

   <td class="code"></td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

<code class="php plain">lock table customers write;</code>

<code class="php plain">set foreign_key_checks = 0;</code>

<code class="php plain">– Replace this comment with your ALTER TABLE command to add the auto_increment feature to the PK field</code>

<code class="php plain">set foreign_key_checks = 1;</code>

<code class="php plain">unlock tables;</code>

<code class="php plain">–statements to insert two rows into the table</code>