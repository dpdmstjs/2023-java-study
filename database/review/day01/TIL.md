## 데이터베이스란

### 데이터베이스 이해 
- 파일시스템 -> 중복
- dbms (mysql, oracle, mariadb, mongodb) -> 공유
- rdbms -> 참조 관계형 데이터 베이스 
- db -> 하드디스크

> 데이터베이스는 마치 도서관과 같다.
```
도서관으로 예를 들면, 

나는 이펙티브 자바를 찾기 위해 나는 사서에게 이 책이 어디 있는지 물어본다. -> 사서는 그 책을 도서관에서 찾아준다. -> 도서관 
클라이언트(나) -> 사서를 통해서 책이 어디있는지 물어보고 사서가 책을 찾아준다.(mysql) -> 도서관(db)
```

### 디스크 I/O 이해
> 알고리즘을 공부하려면 I/O를 공부해야한다. <br>
I/O를 줄이는 것!!!


- 시퀀셜 액세스
- 랜덤엑세스(인덱스 목차)
- 캐시
  
```
캐싱은 상대적인 것 
상대적으로 조금 더 가까이 있는 것을 캐싱이라고 한다.
내가 원래 접근해야되는 위치보다 더 가까이서 접근 할 수 있는 것을 캐싱이라고 한다. 
LRU 방식으로 관리한다.
LRU란?
가장 최근에 썼던 데이터를 가장 가까이 두고 가장 안썼던 것을 멀리 둔다.
예를들어, 여름이라면 여름 옷을 가까이두겠고 겨울 옷을 멀리둘 것이다.
데이터가 RAM에 가있는지 확인한다. 하드디스크까지 안가고 
근데 만약 RAM에 없다면 하드디스크 까지 가게 되면 하드디스크 I/O가 발생한다.
```


### 배운 키워드 
캐싱, LRU, arm, seek, sequential access, random access, cache



