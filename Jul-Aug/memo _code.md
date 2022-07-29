## 알아두면 좋은 코드
--------
  

- 빨간 에러창 무시
  ```python
  import warnings
  warnings.filterwarnings(action='ignore')
  ```

- 데이터프레임 column 이름과 value 좌측으로 정렬
  ```python
  df = df.style.set_properties(**{'text-align':'left'})
  df = df.set_table_styles([dict(selector = 'th', props=[('text-align', 'left')])]) 
  ```

- 크롤링 접속 차단되었을때 User-Agent지정(header) 
  ```python
  header = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)"}
  html = requests.get('경로',  headers = header) 
  ```
  