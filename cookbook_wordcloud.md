```python
import numpy as np
import pandas as pd
from os import path
from PIL import Image
from wordcloud import WordCloud, STOPWORDS, ImageColorGenerator

import matplotlib.pyplot as plt
```


```python
df = pd.read_csv("path/to/dataset.csv", index_col=0) #read the spreadsheet
```


```python
df.head() #show first five rows of the dataset
```


```python
df[["Title", "Subtitle","Date","Subject"]].head() #show the title, subtitle, date, and s
```


```python
date = df. groupby("Date") #group data by date
```


```python
plt.figure(figsize=(35,20))
date.size().plot.bar(color=(1, 0.2, 1, 0.8))
plt.xticks(rotation=100)
plt.xlabel("date of publication")
plt.ylabel("number of cookbooks")
plt.tight_layout()

plt.show()
# generate a bar chart showing the number of publication by year
```


```python
text2.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Subject</th>
      <th>Title</th>
      <th>Subtitle</th>
    </tr>
    <tr>
      <th>ID</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Cooking. Spanish.</td>
      <td>!Delicioso!</td>
      <td>the regional cooking of Spain</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Parties.Cooking.Menus.</td>
      <td>...Parties for pennies,</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Vegetarian cooking.Christmas cooking.Menus.</td>
      <td>'Tis the season</td>
      <td>a vegetarian Christmas cookbook</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Desserts.Baking.Cooking (Chocolate)</td>
      <td>"Best you can bake" chocolate desserts</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Cooking.</td>
      <td>"Fit for a king"</td>
      <td>the Merle Armitage book of food</td>
    </tr>
  </tbody>
</table>
</div>




```python
text = " ".join(subject for subject in df.Subject) # extract contents from subject

stopwords = set(STOPWORDS)
stopwords.update(["cooking", "cook", "state", "United", "States", "Menus","Title","Subtitle","Subject","NaN","recipe","cookbook","cookery","food","book","recipes","foods","complete","guide"]) 
# update the stop-word list
wordcloud = WordCloud(max_font_size=100, max_words=100, stopwords=stopwords, background_color="white",collocations=False).generate(result)
plt.figure(figsize=[15,15])
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")

plt.show()
```


```python
b1900 = " ".join(review for review in df[df["Date"] < "1900"].Subject) # define the time range as before 1900 and extact contents from subject
stopwords = set(STOPWORDS)
stopwords.update(["cooking", "cook", "state", "United", "States", "Menus"])
wordcloud = WordCloud(max_font_size=100, max_words=100, stopwords=stopwords, background_color="yellow").generate(b1900)
plt.figure(figsize=[12,12])
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.savefig("path/to/directory", format="png") # save the figure as a png format in your local directory
plt.show()
```


```python
b1944 = " ".join(review for review in df[(df["Date"] > "1900") & (df["Date"] < "1945")].Subject)
stopwords = set(STOPWORDS)
stopwords.update(["cooking", "cook", "state", "United", "States", "Menus"])
wordcloud = WordCloud(max_font_size=100, max_words=100, stopwords=stopwords, background_color="silver").generate(b1944)
plt.figure(figsize=[12,12])
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.savefig("path/to/directory", format="png")
plt.show()
```


```python
b1980 = " ".join(review for review in df[(df["Date"] > "1944") & (df["Date"] < "1980")].Subject)
stopwords = set(STOPWORDS)
stopwords.update(["cooking", "cook", "state", "United", "States", "Menus"])
wordcloud = WordCloud(max_font_size=100, max_words=100, stopwords=stopwords, background_color="orange").generate(b1980)
plt.figure(figsize=[12,12])
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.savefig("path/to/directory", format="png")
plt.show()
```


```python
b2000 = " ".join(review for review in df[(df["Date"] > "1979") & (df["Date"] < "2000")].Subject)
stopwords = set(STOPWORDS)
stopwords.update(["cooking", "cook", "state", "United", "States", "Menus"])
wordcloud = WordCloud(max_font_size=100, max_words=100, stopwords=stopwords, background_color="pink").generate(b2000)
plt.figure(figsize=[12,12])
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.savefig("path/to/directory", format="png")
plt.show()
```


```python
b2020 = " ".join(review for review in df[(df["Date"] > "1999") & (df["Date"] < "2020")].Subject)
stopwords = set(STOPWORDS)
stopwords.update(["cooking", "cook", "state", "United", "States", "Menus"])
wordcloud = WordCloud(max_font_size=100, max_words=100, stopwords=stopwords, background_color="black").generate(b2020)
plt.figure(figsize=[12,12])
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.savefig("path/to/directory", format="png")
plt.show()
```


```python

```
