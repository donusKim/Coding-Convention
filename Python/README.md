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
### 2.9 Generators
- iterator를 생성하는 함수. yield를 사용해서 필요할때 마다 연산하는 방식
- Generator를 필요한 만큼 쓰자
- 장점: 코드가 간결해진다, 전체를 다 생성하는 list와 비교했을 때 메모리를 적게쓴다

### 2.10 Lambda Functions
- 한 줄을 넘기지 않으면 사용한다. (60~80자 이내)
- 장점: 편리하다
- 단점: 가독성이 떨어지고 해석하기 어렵다. 디버깅이 쉽지 않다.

### 2.13 Properties
- Property란?
- set, get method보다는 Property를 사용하는것이 Pythonic한 Code   
- 장점: 편리하다
- 단점: 가독성이 떨어지고 해석하기 어렵다. 디버깅이 쉽지 않다.

### 2.14 True/False Evaluations
- Python에서 암묵적으로 사용하는 true/false표현을 쓰자


__[YES]__      
```python                     
if not users:
    print('no users')
if foo == 0:
    self.handle_zero()
if i % 10 == 0:
    self.handle_multiple_of_ten()
if not A:
    print(1)
```    
__[NO]__      
```python
if len(users) == 0:
    print('no users')
if foo is not None and not foo:
    self.handle_zero()
if not i % 10:
    self.handle_multiple_of_ten()
if A==False:
    print(1)
```
