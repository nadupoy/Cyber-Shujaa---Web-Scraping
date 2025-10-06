# 🕸️ Cyber Shujaa - Web Scraping 🚀

This is my updated solution to the week 1 assignment in the Cyber Shujaa program 
for the **Data and AI Specialist** track.

## 🧭 Table of contents

- [🌟 Overview](#🌟-overview)
  - [The assignment 🎯](#the-assignment-🎯)
  - [Links 🔗](#links-🔗)
- [🛠️ My process](#🛠️-my-process)
  - [Built with 🧱](#built-with-🧱)
  - [What I learned 🧠](#what-i-learned-🧠)
  - [Continued development 🌱](#continued-development-🌱)
  - [Useful resources 📚](#useful-resources-📚)
- [👩‍💻 Author](#👩‍💻-author)

## 🌟 Overview

### The assignment 🎯

The goal of the assignment was to develop hands-on experience gathering web data 
using **Python**.

The objectives were:
  1. Practical Python coding 🐍
  2. Data extraction from a web page 🕸️
  3. Parsing and cleaning the extracted data ✨
  4. Storing structured data into a **Pandas DataFrame** 📊
  5. Export the final dataset into a `.csv` file 💾

### Links 🔗

- [Google Colab](https://colab.research.google.com/drive/1plbhwdRXuqQXqgncfocjvGL6ntMn_eVj?usp=sharing) 
assignment submission

## 🛠️ My process

### Built with 🧱

- **[Python](https://www.python.org)** 🐍
- **[Requests](https://requests.readthedocs.io/en/latest)** HTTP library for Python 📡
- **[BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc)** Python 
library for pulling data out of HTML and XML files 🧺
- **[Pandas](https://pandas.pydata.org/docs/index.html)** Python library used for 
working with data sets with functions for cleaning, exploring and manipulating data 🐼

### What I learned 🧠

**1. Making requests using the `requests` library** 📩

```python
    url = "https://www.scrapethissite.com/pages/forms"
    response = requests.get(url)
```

**2. Parsing html using the `BeautifulSoup` library** 📝

```python
    html_doc = BeautifulSoup(response.text, "html.parser")
```

**3. Selecting and scraping data from `html` elements using tag names and class names** 🔍

This was done by using `find_all()` method in `BeautifulSoup`.

Using tag names only:

```python
    # combine all table headers into a Python list:
    th = html_doc.find_all("th")
```

Using class names:
```python
    # combine all team names into a Python list:
    td_name = html_doc.find_all("td", class_="name")
```

**4. Scraping a paginated website** 🤯

This was the **biggest challenge** I faced while doing this assignment.

I managed to solve it by using a `while` loop and an `if...else` statement. 💡

```python
    # while loop to iterate over all the pages:
    i = 1
    while i < 25:
      ...
      # if...else statement to load the DataFrame in page 01 and join all the DataFrames from each webpage into one DataFrame:
      if i == 1:
        df = pd.DataFrame(data)
      else:
        # combine subsequent tables:
        df_concat = pd.DataFrame(data)
        df = pd.concat([df, df_concat], axis=0)
```

**5. Creating `Pandas` `Series` and `DataFrames`** 📊

This was done using a Python object as outlined in the `Pandas` documentation and 
tutorials online.

An item in the object forms a `Pandas` `Series` i.e. table columns, with the keys 
forming the table headers and values, which are in the form of a Python list, form 
the table values associated with the table headers.

```python
    data = {
      table_headers[0]: team_names,
      ...
      table_headers[8]: goal_differences
    }
```

When `Series` are combined together in a Python object they are used to create a 
`Pandas` `DataFrame`.
```python
    df = pd.DataFrame(data)
```

### Continued development 🌱

This assignment gave me a hands-on, practical introduction to web scraping and the 
library used. Not only did I learn the *what* but also the *why* of each step and 
library in the web scraping process.

I am going to learn more about:

- `requests` library. I assume it is also applicable in fetching data from not only 
web servers but other servers as well. 🌍
- `Pandas` 📈
- `BeautifulSoup` 📚

### Useful resources 📚

- [Combining `DataFrames`](https://pandas.pydata.org/docs/getting_started/intro_tutorials/08_combine_dataframes.html#) 
in `Pandas`
- [Web scraping](https://realpython.com/python-web-scraping-practical-introduction) 
in Python
- `Pandas` [`Series`](https://www.w3schools.com/python/pandas/pandas_series.asp)
- `Pandas` [`DataFrames`](https://www.w3schools.com/python/pandas/pandas_dataframes.asp)

## 👩‍💻 Author

- LinkedIn - [Grace Sampao](https://www.linkedin.com/in/grace-sampao)
- GitHub - [@nadupoy](https://github.com/nadupoy)
