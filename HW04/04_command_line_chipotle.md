## Lesson 4 Homework: Command Line Chipotle

#### Submitting Your Homework

* Create a Markdown file that includes your answers **and** the code you used to arrive at those answers.
* Add this Markdown file to a GitHub repo that you'll use for all of your coursework.
* Submit a link to your repo using the homework submission form listed just below the course schedule on the class repo on the main README.md page. [(submission form)](https://docs.google.com/forms/d/e/1FAIpQLScH_m8Le4w0sqsvm5uNOTd08p4KDTW8WgnWVP1kFf4CCBi2Ow/viewform)

#### Command Line Tasks

1. Look at the head and the tail of **chipotle.tsv** in the **data** subdirectory of this repo. Think for a minute about how the data is structured. What do you think each column means? What do you think each row means? Tell me! (If you're unsure, look at more of the file contents.)
    - Each row represents an item as part of an order while each column is a
      variable that describes an aspect of each item. Consider the first row
      as an example. A customer orders 1 qty of Chips and Fresh Salsa for $2.39.
      This is a part of order_id 1 which includes other items: Izze, Nantucket
      Nectar, and Chips and Green Salsa. Further, each item can be customized
      in the description field. For example, one can order different flavors
      of Izze such as Clementine as in the item in row 2.
```bash
head chipotle.tsv
tail chipotle.tsv
```
2. How many orders do there appear to be?
    - Assuming that order_id is unique for each order, there appears to be
      1,834 orders.
```bash
tail chipotle.tsv
```
3. How many lines are in this file?
    - There are 4,622 rows in this file or 4,623 lines if you include the
      header.
```bash
wc -l chipotle.tsv
```
4. Which burrito is more popular, steak or chicken?
    - There were a total of 553 Chicken Burritos and 368 Steak Burritos
```bash
grep -i "Chicken Burrito" | wc -l
grep -i "Steak Burrito" | wc -l
```
5. Do chicken burritos more often have black beans or pinto beans?
    - There were 282 chicken burritos with black beans and 105 with pinto beans.
```bash
grep -i "chicken burrito" | grep -i "black bean" | wc -l
grep -i "chicken burrito" | grep -i "pinto bean" | wc -l
```
6. Make a list of all of the CSV or TSV files in the [our class repo] (https://github.com/ga-students/DS-SEA-3). repo (using a single command). You will be working on your local repo on your laptop.  Think about how wildcard characters can help you with this task.
    - While you are in the data directory, run the following command in the
      command line:
```bash
ls -al *.[ct]sv
```
7. Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of [our class repo] (https://github.com/ga-students/DS-SEA-3).
    - There are 77 occurrences of the word 'dictionary' (case insensitive) in
      across all files in class repo.
```bash
grep -roi dictionary | grep -c dictionary
```
8. **Optional:** Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!
 
