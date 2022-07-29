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

- tqdm: 반복문의 진행사항을 알 수 있다. 
  사용은 for 문의 in 구문을 tqdm으로 감싸기만 하면 됨.
  ```python
  - tqdm을 사용하지 않은 그냥 코드

  from time import sleep
  for i in range(1, 600):
    sleep(0.1) # 무언가 시간이 많이 소요되는 연산군

  - tqdm을 사용한 코드

  from tqdm import tqdm
  from time import sleep
  
  for i in tqdm(range(1, 600)):
    sleep(0.1) # 무언가 시간이 많이 소요되는 연산군

  76%|████████████████████      | 7568/10000 [00:33<00:10, 229.00it/s]
  ```
