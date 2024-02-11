**This project is completely done in pandas**

Lets first import the pandas library

```python
import pandas as pd
```

Lets import the `csv` file

```python
data = pd.read_csv('/content/Ecommerce Purchases')
```

Now lets start our analysis process by writting code

**1. Display Top 10 rows.**

```python
data.head(10)
```

**2. Display Last 10 rows.**

```python
data.tail(10)
```

**3. Check Datatype of Each Column**

```python
data.dtypes
```

**4. Check null values in the dataset**

```python
data.isnull().sum()
```

**5. How many row and columns are there in our dataset?**

count of columns:

```python
len(data.columns)
```

count of rows:

```python
len(data)
```

or we can also write this code:

```python
data.info()
```

**6. Highest and Lowest Purchase prices.**

Lets first see the all column list, so that we can decide on which column we'll have to word on

```python
data.columns
```

now, lets solve our problem

Find highest Purchase price:
```python
data['Purchase Price'].max()
```

Find lowest Purchase price:
```python
data['Purchase Price'].min()
```

**7. Average Purchase price.**

```python
data['Purchase Price'].mean()
```

**8. How many people have French 'fr' as their Language?**

```python
len(data[data['Language'] == 'fr'])
```

or we can write this code

```python
# data[data['Language'] == 'fr'].count()
data[data['Language'] == 'fr'].count()[0]
```

**9. Job title contains Engineer**

Before writting code, lets see the all column

```python
data.columns
```

Now lets write the code

```python
len(data[data['Job'].str.contains('engineer', case=False)])
```

**10. Find the Email of the person with the following IP address: 132.207.160.22**

```python
data[data['IP Address'] == '132.207.160.22']
```

**11. How many people have Mastercard as their credit card provider and made a purchase above 50?**

```python
# data[(data['CC Provider'] == 'Mastercard') & (data['Purchase Price'] > 50)].count()[0]
len(data[(data['CC Provider'] == 'Mastercard') & (data['Purchase Price'] > 50)])
```

**12. Find the email of the person with the following credit card number: 4664825258997302**

```python
data[data['Credit Card'] == 4664825258997302]['Email']
```

**13. How many people purchase during the AM and how many people purchase during PM?**

```python
data['AM or PM'].value_counts()
```

**14. How many people have a credit card that expires in 2020?**

```python
# year = data[data['CC Exp Date'].apply(lambda x:x[3:]=='20')]
year = data[data['CC Exp Date'].str.split('/').apply(lambda x: x[1]) == '20']
```

```python
len(year)
```

**15. What are the top 5 most popular email providers (e.g.gmail.com, yahoo.com, etc...)**

```python
provider = []

for email in data['Email']:
  provider.append(email.split('@')[1])
```

```python
data['temp']=provider
```

```python
data['temp'].value_counts().head(5)
```

```python
# by lambda function

data['Email'].apply(lambda x: x.split('@')[1]).value_counts().head()
```
