# Redis-DataType

## Strings

- 가장 기본적인 데이터 타입으로 제일 많이 사용됨
- 바이트 배열을 저장 (binary-safe)
- 바이너리로 변활할 수 있는 모든 데이터를 저장 가능(JPG와 같은 파일 등)
- 최대 크기는 512MB

<img width="577" alt="image" src="https://user-images.githubusercontent.com/40031858/220257149-52b874eb-5049-4c03-ab0d-cc90487e555e.png">


### Strings 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|SET| 특정 키에 문자열 값을 저장한다| SET say hello|
|GET| 특정 키의 문자열 값을 얻어온다 | GET say|
|INCR| 특정 키의 값을 Integer로 취급하여 1 증가시킨다 | INCR mycount |
|DECR| 특정 키의 값을 Integer로 취급하여 1 감소시킨다 | DECR mycount |
|MSET| 여러 키에 대한 값을 한번에 저장한다 | MSET mine milk yours coffee |
|MGET| 여러 키에 대한 값을 한번에 받아온다 | MGET mine yours |

<img width="472" alt="image" src="https://user-images.githubusercontent.com/40031858/220259557-1ceeaac9-f409-457f-b621-f902d14adb1a.png">

---

## Lists

- Linked-list 형태의 자료구조(인덱스 접근은 느리지만 데이터 추가/삭제가 빠름)
- Queue와 Stack으로 사용할 수있음

<img width="646" alt="image" src="https://user-images.githubusercontent.com/40031858/220260116-db286049-e2a9-4868-a794-7204951e701b.png">

### Lists 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|LPUSH| 리스트의 왼쪽(head)에 새로운 값을 추가한다| LPUSH mylist apple|
|RPUSH| 리스트의 오른쪽(tail)에 새로운 값을 추가한다| RPUSH mytlist banana|
|LLEN| 리스트에 들어있는 아이템 개수를 반환한다| LLEN mylist|
|LRANGE| 리스트의 특정 범위를 반환한다| LRANGE mylist 0 -1|
|LPOP| 리스트의 왼쪽(head)에서 값을 삭제하고 반환한다| LPOP mylist|
|RPOP| 리스트의 오른쪽(tail)에서 값을 삭제하고 반환한다| RPOP mylist|

<img width="793" alt="image" src="https://user-images.githubusercontent.com/40031858/220261342-d7485e39-3186-40e5-bd1d-783928678297.png">

---

## Sets

- 순서가 없는 유니크한 값의 집합
- 검색이 빠름
- 개별 접근을 위한 인덱스가 존재하지 않고, 집합 연산이 가능(교집합, 합집합 등)

<img width="689" alt="image" src="https://user-images.githubusercontent.com/40031858/220261535-61785671-3c5e-4aa8-b708-12f9bb57c1fd.png">


### Sets 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|SADD| Set에 데이터를 추가한다| SADD myset apple|
|SREM| Set에서 데이터를 삭제한다| SREM myset apple|
|SCARD| Set에 저장된 아이템 개수를 반환한다| SCARD myset|
|SMEMBERS| Set에 저장된 아이템들을 반환한다| SMEMBERS myset|
|SISMEMBER| 특정 값이 Set에 포함되어 있는지를 반환한다| SISMEMBER myset apple|

<img width="796" alt="image" src="https://user-images.githubusercontent.com/40031858/220262981-bf5de0da-5a12-426a-9bbc-a5ce98c5131f.png">

---

## Hashes

- 하나의 key 하위에 여러개의 field-value 쌍을 저장
- 여러 필드를 가진 객체를 저장하는 것으로 생각할 수 있음
- HINCRBY 명령어를 사용해 카운터로 활용가능

<img width="807" alt="image" src="https://user-images.githubusercontent.com/40031858/220263225-2a94f7dc-f085-4f73-b848-8885fb0ca85c.png">


### Hashes 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|HSET| 한개 또는 다수의 필드에 값을 저장한다| HSET user1 name bear age 10|
|HGET| 특정 필드의 값을 반환한다| HGET user1 name|
|HMGET| 한개 이상의 필드 값을 반환한다| HMGET user1 name age|
|HINCRBY| 특정 필드의 값을 Integer로 취급하여 지정한 숫자를 증가시킨다| HINCRBY user1 viewcount 1|
|HDEL| 한개 이상의 필드를 삭제한다| HDEL user1 name age|

<img width="838" alt="image" src="https://user-images.githubusercontent.com/40031858/220263975-bf95b9c0-1b26-43e9-8471-b4dde39c2622.png">

---

## SortedSets

- Set과 유사하게 유니크한 값의 집합
- 각 값은 연관된 score를 가지고 정렬되어 있음
- 정렬된 상태이기에 빠르게 최소/최대값을 구할 수 있음
- 순위 계산, 리더보드 구현 등에 활용

<img width="657" alt="image" src="https://user-images.githubusercontent.com/40031858/220264306-8591931d-45b4-4b72-818b-3af31243f0bf.png">

### SortedSets 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|ZADD| 한개 또는 다수의 값을 추가 또는 업데이트 한다| ZADD myrank 10 apple 20 banana|
|ZRANGE| 특정 범위의 값을 반환한다(오름차순으로 정렬된 기준)| ZRANGE myrank 0 1|
|ZRANK| 특정 값의 위치(순위)를 반환한다 (오름차순으로 정렬된 기준)| ZRANK myrank apple|
|ZREVRANK| 특정 값의 위치(순위)를 반환한다 (내림차순으로 정렬된 기준)| ZREVRANK myrank apple|
|ZREM| 한개 이상의 값을 삭제한다| ZREM myrank apple|

<img width="708" alt="image" src="https://user-images.githubusercontent.com/40031858/220265150-5c133e59-a09e-4b59-803f-3faacaed86f0.png">

---

## Bitmaps

- 비트 벡터를 사용해 N개의 Set을 공간 효율적으로 저장
- 하나의 비트맵이 가지는 공간은 4,294,967,295(2^32-1)
- 비트 연산 가능

<img width="609" alt="image" src="https://user-images.githubusercontent.com/40031858/220265419-f5071b34-ff82-4fd7-9d13-41cefa910504.png">


### Bitmaps 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|SETBIT| 비트맵의 특정 오프셋에 값을 변경한다 | SETBIT visit 10 1|
|GETBIT| 비트맵의 특정 오프셋의 값을 반환한다| GETBIT visit 10|
|BITCOUNT| 비트맵에서 set(1) 상태인 비트의 개수를 반환한다| BITCOUNT visit|
|BITOP| 비트맵들간의 비트 연산을 수행하고 결과를 비트맵에 저장한다|BITOP AND result today yesterday|

<img width="730" alt="image" src="https://user-images.githubusercontent.com/40031858/220268666-86b6becc-e100-476e-84da-c7b84e71927f.png">

---

## HyperLogLog

- 유니크한 값의 개수를 효율적으로 얻을 수 있음
- 확률적 자료구조로서 오차가 있으며, 매우 큰 데이터를 다룰 때 사용
- 18,446,744,073,709,551,616(2^64)개의 유니크 값을 계산 가능
- 12KB까지 메모리를 사용하며 0.81%의 오차율을 허용

<img width="671" alt="image" src="https://user-images.githubusercontent.com/40031858/220268892-5a04fcc3-6923-4f1e-9586-cf27d0947ce9.png">

### HyperLogLog 주요 명령어

||||
|:--:|:--:|:--:|
|`명령어`|`기능`|`예제`|
|PFADD| HyperLogLog에 값들을 추가한다| PFADD visit Jay Peter Jane|
|PFCOUNT| HyperLogLog에 입력된 값들의 cardinality(유일값의 수)를 반환한다|PFCOUNT visit|
|PFMERGE| 다수의 HyperLogLog를 병합한다| PFMERGE result visit1 visit2|

<img width="704" alt="image" src="https://user-images.githubusercontent.com/40031858/220269920-56cf1de6-ece2-4095-b6e3-f70bd7788541.png">