**This project is completely done by using pandas library**

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
![screenshot 1](https://github.com/CodeofRahul/Python_Projects/assets/143285125/43469f21-4e22-49ef-9315-524c13f33181)

**2. Display Last 10 rows.**

```python
data.tail(10)
```
![screenshot 2](https://github.com/CodeofRahul/Python_Projects/assets/143285125/83ec24a5-5172-41f3-b86d-39d4d48eb966)


**3. Check Datatype of Each Column**

```python
data.dtypes
```
![screenshot 3](https://github.com/CodeofRahul/Python_Projects/assets/143285125/4f734f7f-ff4d-44b8-b86e-b4d08fc5a15c)


**4. Check null values in the dataset**

```python
data.isnull().sum()
```
![screenshot 4](https://github.com/CodeofRahul/Python_Projects/assets/143285125/fe20e07a-8d78-4c4a-9bf9-f2b91b3d99a4)


**5. How many row and columns are there in our dataset?**

![screenshot 5](https://github.com/CodeofRahul/Python_Projects/assets/143285125/179bd987-e4fe-4036-b41f-56b82994eb9a)


**6. Highest and Lowest Purchase prices.**

Lets first see the all column list, so that we can decide on which column we should work on

![screenshot 6](https://github.com/CodeofRahul/Python_Projects/assets/143285125/351ae487-7618-4eb6-bd70-fde3694221b0)

**7. Average Purchase price.**

```python
data['Purchase Price'].mean()
```

50.347302

**8. How many people have French 'fr' as their Language?**

```python
len(data[data['Language'] == 'fr'])
```

1097

or we can write this code

```python
# data[data['Language'] == 'fr'].count()
data[data['Language'] == 'fr'].count()[0]
```

1097

**9. Job title contains Engineer**

```python
len(data[data['Job'].str.contains('engineer', case=False)])
```

984

**10. Find the Email of the person with the following IP address: 132.207.160.22**

```python
data[data['IP Address'] == '132.207.160.22']
```
![screenshot 10](https://github.com/CodeofRahul/Python_Projects/assets/143285125/6cef2329-962f-494b-87ec-20ac08281005)

**11. How many people have Mastercard as their credit card provider and made a purchase above 50?**

```python
# data[(data['CC Provider'] == 'Mastercard') & (data['Purchase Price'] > 50)].count()[0]
len(data[(data['CC Provider'] == 'Mastercard') & (data['Purchase Price'] > 50)])
```

405

**12. Find the email of the person with the following credit card number: 4664825258997302**

```python
data[data['Credit Card'] == 4664825258997302]['Email']
```
![screenshot 12](https://github.com/CodeofRahul/Python_Projects/assets/143285125/1d8d6eaf-bd6f-4687-a315-c255c76fed79)


**13. How many people purchase during the AM and how many people purchase during PM?**

```python
data['AM or PM'].value_counts()
```
![screenshot 13](https://github.com/CodeofRahul/Python_Projects/assets/143285125/9443a3c2-eaf6-4934-9745-b0eccdb363fe)

**14. How many people have a credit card that expires in 2020?**

```python
# year = data[data['CC Exp Date'].apply(lambda x:x[3:]=='20')]
year = data[data['CC Exp Date'].str.split('/').apply(lambda x: x[1]) == '20']
```

```python
len(year)
```

988

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
![screenshot 15](https://github.com/CodeofRahul/Python_Projects/assets/143285125/0dfbef17-eaa4-403e-ba71-c35c9f0116f0)

```python
# by lambda function

data['Email'].apply(lambda x: x.split('@')[1]).value_counts().head()
```
![screenshot 15 lambda](https://github.com/CodeofRahul/Python_Projects/assets/143285125/9ff8022f-2981-4e01-851d-794c5b422b0e)
