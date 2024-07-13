---
title: "Chapter-02"
author: "Muhammad Zain Zameer"
---

# Introduction to Data Manipulation

-   Data Frames:

    A DataFrame is a fundamental data structure in R, specifically designed for storing and manipulating tabular data. It resembles a table or spreadsheet, consisting of rows and columns, where each column can contain different types of data (numeric, character, factor, etc.). DataFrames are particularly useful for data analysis and are a central component of the R ecosystem.

    A dataframe can be created using the '**data.frame()**' function in R:

    ``` r
    # Creating a simple DataFrame
    df <- data.frame(
      Name = c("Alice", "Bob", "Charlie"),
      Age = c(25, 30, 35),
      Gender = c("Female", "Male", "Male")
    )

    # Viewing the DataFrame
    print(df)
    ```

    For data manipulation, we can use a package '**dplyr**', which is a part of tidyverse(a collection of packages designed for data science).

    -   **'dplyr' Package:**

        `dplyr` is one of the most widely used packages in R for data manipulation. It provides a set of functions that make it easier to transform and summarize data. The core functions of `dplyr` include:

        -   **filter()**: Select rows based on conditions.

        -   **select()**: Choose specific columns.

        -   **mutate()**: Create new columns or modify existing ones.

        -   **summarize()**: Create summary statistics.

        -   **arrange()**: Sort rows.

        -   **group_by()**: Group data by one or more variables for aggregation.

            Example usage of '**dplyr**'**:**

            ``` r
            library(dplyr)
            # Using dplyr functions
            df %>%
              filter(Age > 25) %>%
              select(Name, Age) %>%
              arrange(Age)
            ```

    -   **'readr' Package:**

        `readr` is another essential package in R, designed for fast and friendly reading of rectangular data (like CSV files). It provides functions that read and write data frames:

        -   **read_csv()**: Read a comma-separated values(CSV) file.

        -   **write_csv()**: Write a data frame to a CSV file.

            Example usage of '**readr**'**:**

            ``` r
            library(readr)

            # Reading a CSV file into a DataFrame
            df <- read_csv("data.csv")

            # Writing a DataFrame to a CSV file
            write_csv(df, "output.csv")
            ```

-   CSV (Comma Separated Values):

    CSV is a text only spreadsheet format.

    ``` r
    #Following is the structure that CSV follows:

        # Column1,Column2,Column3 (Column names)
        # Value1,Value2,Value3 (Values to each column)
    ```

-   Inspecting data frames:

    If the data frame is larger,it can be helpful to inspect a few rows of the dataframe without having to look at the rest of it.

    ``` r
    # head(data_frame,no_of_rows)
    df <- read_csv("students.csv")
    head(df,2)
    # output will only show 2 rows of students csv file.
    ```

-   Summary() function:

    The function summary() will return summary statistics such as mean,median,minimum and maximum for each numeric column, while prividing class and length information for non-numeric columns.

    ``` r
    df <- read_csv("students.csv")
    summary(df)
    ```

-   Piping:

    Piping in R is a technique that allows you to write clean, readable, and efficient code by chaining multiple functions together. The `%>%` operator, provided by the `magrittr` package and commonly used in the `dplyr` package, is the primary tool for piping.

    -   **What is Piping**?

        Piping enables you to pass the output of one function directly into the input of another function. This approach avoids the need for intermediate variables and makes your code more concise and easier to read.

    -   **How to Use Piping**

        To use piping, you need to import the `magrittr` package, which is often done implicitly when loading `dplyr`.

        ``` r
        library(dplyr)
        ```

    -   **Basic Syntax**

        The basic syntax of piping involves placing `%>%` between functions. The result of the expression on the left is passed as the first argument to the function on the right.

        **Example**

        ``` r
        # Sample DataFrame
        df <- data.frame(
          Name = c("Alice", "Bob", "Charlie"),
          Age = c(25, 30, 35),
          Gender = c("Female", "Male", "Male")
        )

        # Without piping
        df_filtered <- filter(df, Age > 25)
        df_selected <- select(df_filtered, Name, Age)
        df_sorted <- arrange(df_mutated, Age)

        # With piping
        df_piped <- df %>%
          filter(Age > 25) %>%
          select(Name, Age) %>%
          arrange(Age)

        print(df_piped)
        ```

-   Selecting Columns:

    Let's say you need to select only those columns in which you are going to perform analysis. You can select columns by following method:

    ``` r
    # read csv file
    df <- read_csv("students.csv")
    #selecting only student id's and their grades
    select(df,StudentID,StudentGrades)
    ```

-   Excluding Columns:

    Exclude some columns from data frames, let's say I want only 1 column to be removed and get each and every column except that particular one, I can achieve this by following:

    ``` r
    # read csv file
    df <- read_csv("student.csv")
    #removing column student id and get every column on the output
    select(df,-StudentID)
    ```

-   Filtering Rows with logic 1

    We can filter our data frame based on condition on what type of data we want on output and we can achieve this by following:

    ``` r
    #read csv file
    df <- read_csv("students.csv")
    # using filter logic to filter out our dataframe
    new_df <- filter(df,exams="Physics")

    #Now I will get all the rows whose exams column is equal to physics.
    ```
