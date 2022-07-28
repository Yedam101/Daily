### 2022-07-28
--------------------
### pandas 정렬

- DataFrame의 columns 값을 왼쪽으로 정렬하는 코드
```python
df = df.style.set_properties(**{'text-align':'left'})
```
- DataFrame의 columns 이름을 왼쪽으로 정렬하는 코드
```python
df = df.set_table_styles([dict(selector = 'th', props=[('text-align', 'left')])]) 
```

### 크롤링

- 검색어를 입력하면 5페이지 만큼의 한국경제 기사와 날짜를 출력하는 코드
```python
import warnings
warnings.filterwarnings(action='ignore')
import pandas as pd
df = pd.DataFrame(columns=['제목','날짜'])
index = [ i for i in range(1,51)]

keyword = input('검색어를 입력하세요: ')

for i in range(1, 6):
    html = requests.get(f'https://search.hankyung.com/apps.frm/search.news?query={keyword}&page={i}')
    soup = bs(html.text, 'html.parser')
    titles = soup.find_all('em', {'class':'tit'})
    times = soup.find_all('span', {'class':'date_time'})
    
    for j in range(len(titles)):
        title = titles[j].text
        time = times[j].text
        time = pd.to_datetime(time)
        df = df.append({"제목":title, "날짜":time}, ignore_index=True)

df = df.style.set_properties(**{'text-align':'left'})
df = df.set_table_styles([dict(selector = 'th', props=[('text-align', 'left')])]) 
print(df)
```
