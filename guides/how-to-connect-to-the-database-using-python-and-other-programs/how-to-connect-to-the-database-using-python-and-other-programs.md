# How to Connect to Your Database Using Python and Other Programs

Accessing and storing your data from numerous sources is vital whether you are working as a web developer, data analyst, or data scientist. You can use any program such as Python, R and Tableau when accessing your Strata Scratch database. For this tutorial, I will show you the simple steps in connecting to your Strata Scratch database using the Python language.

## Things You Need to Start

In this guide, we will be using the Jupyter notebook for running our Python codes. Before you begin accessing your Strata Scratch database, make sure you have installed the Jupyter notebook as well as the package for PostgreSQL, `psycopg2` (refer to this [guide](https://github.com/stratascratch/stratascratch.github.io/blob/master/guides/how-to-connect-to-the-database-using-python-and-other-programs/how-to-install-psycopg2-to-connect-to-strata-scratch-using-python.md) for instructions on how to install `psycopg2` on Jupyter notebooks. There are many ways to install the Jupyter notebook, and one of the easiest ways is to download and install Anaconda. This is the most common Python distribution which already includes the necessary Python packages. Make sure you download the latest version compatible to your computer OS.

## Download the Jupyter Notebook Template

If you have Anaconda/Jupyter Notebooks and psycopg2 installed, you can get started immediately by downloading our
[template](https://github.com/stratascratch/stratascratch.github.io/blob/master/guides/how-to-connect-to-the-database-using-python-and-other-programs/stratascratch_python_connect.ipynb).

Otherwise, you can create a notebook using the instructions below.

## Creating a Python Notebook in Jupyter

Throughout this tutorial, you are expected to have a background in SQL and Python programming. Otherwise, I would recommend you to review these languages before you proceed on the steps below.

- Open the Jupyter notebook. 

The Jupyter notebook will be automatically launched to your default browser. Here, you will see a dashboard containing a list of notebook folders.

![strata scratch](assets/1.png)

- Let’s create a Python notebook. On the right side of the page, click New and choose Python, such as shown below:

![strata scratch](assets/2.png)

- Let’s rename the file by clicking on the `Untitled` label on top of the menu bar.

![strata scratch](assets/3.png)

- For this example, let’s name our file `mypython`. Then click Rename to save the changes.

![strata scratch](assets/4.png)

## Connecting to the Database

Now you have created a Python notebook, let’s start by importing the packages necessary to connect to our Strata Scratch database.

- Start the code by importing the `pandas` and `psycopg2` modules to your file. The module `pandas` is a Python package that offers easy-to-use analysis tools and data structures for manipulating your tables, including `DataFrame` which we will be using in this tutorial.

On the other hand, we also need to import the `psycopg2` module so we can interact with our Strata Scratch database with Python.

![strata scratch](assets/5.png)

Take note that we used the keyword `as` to create the new names `pd` and `ps` which basically refers to the same object, `pandas` and `psycopg2`, respectively.

- Press shift-enter to proceed to the next line. Next, enter the following parameters to connect to your database:

![strata scratch](assets/6.png)

The `host_name` is the local host, which is in our example stratascratch.com. The `dbname` is the name of your database. 

The `user_name` and `pwd` are the username and password you used for your database. You can find your username and password on your Strata Scratch profile. Simply log-in to your account and click profile:

![strata scratch](assets/7.png)

![strata scratch](assets/8.png)

The port `5432` is generally the default port, unless it is specified. 

- Go to the next line by pressing shift-enter and type the following codes:

![strata scratch](assets/9.png)

In the statement above, we are trying to connect to the database using `ps.connect` with the parameters we have previously encoded. Once you are able to open to the database, this block of code will return a connection object. If the connection is successful, the output will display the ‘Connected’ message; otherwise, you will see an error message. This condition is defined within the `try … else` statement.

![strata scratch](assets/10.png)

- Next, call the database and execute a query with the following statements:

![strata scratch](assets/11.png)

The first line of code creates a cursor object which will allow you to execute the queries.

The next statement executes the SQL queries. In this example, we are simply retrieving the `airbnb_searches` table under the schema `strata_user`. We added the statement `LIMIT 50` because we are only interested in retrieving the first 50 of the data.

The third line calls the `cur.fetchall` to fetch all the rows of data from the database table.

Once you have executed the query, the `conn.commit` method is called to commit the changes in the database.

And the last statement calls the `DataFrame` method to tabulate the results into rows and columns.

- We can check the output of the query by calling the `df` object after the `DataFrame` statement.

![strata scratch](assets/12.png)

You should see the following output:

![strata scratch](assets/13.png)

Lastly, don’t forget to add `cur.close()` on the last statement. This command will tell the server to automatically close the cursor after all the results have been fetched or the cursor has been idle for a certain period.

![strata scratch](assets/14.png)
 









