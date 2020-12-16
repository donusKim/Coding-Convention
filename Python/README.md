# Google Python Style Guide 요약
## 2. Python Language Rules
### 2.1 Lint
- pylint: Python 소스코드중에 오류나 스타일상의 문제를 발견해주는 도구

### 2.2 imports
### 2.3 Packages
### 2.4 Exceptions
### 2.5 Global Variables
- 전역변수 선언을 피하자

### 2.7 Comprehensions & Generator Expressions
- 간단한 경우에는 사용해도 괜찮다
- List, Dict, and Set comprehensions은 container type을 생성하는 간결하고 효율적인 방법이다. (전통적인 loop방법인 map, filter, lambda를 사용하지 않고,,)
- 장점: 다른 생성방법에 비해 간결하고 Generator Expression같은 경우 전체 list 생성을 하지 않아도 돼서 보다 더 효과적이다.
- 단점: 복잡한 경우 가독성이 떨어지고 해석하기 어려울수 있다.
- 언제 사용: 한줄로 끝나면서 loop문이 한개만 있을 때,,두 개 이상일때는 그냥 풀어서 쓰는걸 권장

__[YES]__    
```python
squares_generator = (x**2 for x in range(10))  
unique_names = {user.name for user in users if user is not None}  
```
__[NO]__  
```python
result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]  
```

### 2.8 Default Iterators and Operators
- List, dictionary, file등을 loop돌려 꺼내올때 default Iterator나 Operator를 쓰자 
- 장점: 추가적인 method 호출없이 바로 실행된다.  

__[YES]__      
```python  
for key in adict:   
if key not in adict:  
if obj in alist: 
for line in afile: 
for k, v in adict.items(): 
```
__[NO]__  
```python
for key in adict.keys():
if not adict.has_key(key): 
for line in afile.readlines(): 
```
