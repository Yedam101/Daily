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


- 데이터프레임 csv로 저장하는 코드
  ```python
  df.to_csv('./(파일명)).csv', index= False)
  ```

- 판다스로 table 탭 스크래핑
  ```python
  table_pd = pd.read_html(url)
  table_pd[0]
  ```

- input 값을 *로 받는 getpass
  ```python
  import getpass
  input = getpass.getpass('입력하세요: ')
  ```

- 셀레니움에서 코드를 단순화하는 ActionChains
  ```python
  from selenium.webdriver.common.action_chains import ActionChains
  
  (
  action.send_keys('woorin0049@naver.com').key_down(Keys.ENTER)
  .send_keys('내용').key_down(Keys.TAB)
  .send_keys('내용')
  .perform()
  )
  ```

- 값이 숫자인지 알파벳인지 판별하는 메소드

  <value>.isdigit(): 가 숫자라면 True, 아니면 False를 리턴

  <value>.isalpha() : 가 알파벳이라면 True, 아니면 False를 리턴

 
  ```python
  N = input()

  if N.isdigit() : 
      print("입력값은 숫자입니다")
  elif N.isalpha() :
      print("입력값은 알파벳입니다.")
  ```
 

  * isdigit() 이 True라고 해도, 아직 데이터타입은 str이므로 int로 변환 후에 연산 등을 진행해야 한다.  
  
  
- 리스트의 요소들 중에서 길이가 가장 짧은 혹은 긴 요소를 구하는 코드
  ```python
  l_min = len(min(strs, key=len))
  l_max = len(max(strs, key=len))
  ```