# javascript ) jQuery 자주사용하는 함수 정리



| 분류                 | 함수명                        | 함수 설명                                                    |
| -------------------- | ----------------------------- | ------------------------------------------------------------ |
| form관련             | serialize()                   | 선택한 폼의 값을 a=1&b=2&c=3 등의 형태로 반환                |
|                      | serializeArray()              | jQuery 배열 객체로 반환                                      |
| 엘리먼트 조작        | each(Function)                | 선택된 엘리먼트가 다수일 경우에 each 함수를 사용하여 차례대로 엘리먼트를 선택한다 |
| 어트리뷰트 조작      | attr(name, value)             | 선택된 엘리먼트의 name 어트리뷰트의 값을 value로 설정        |
|                      | attr(name)                    | 선택된 엘리먼트의 name 에 어트리뷰트의 값을 얻어옴           |
|                      | attr(Attributes)              | 선택된 엘리먼트를 프로퍼티(json)형태로 설정할 수 있음        |
|                      | val()                         | 엘리먼트의 value 어트리뷰트 값을 얻어옴. attr("value")와 동일함 |
|                      | val(content)                  | 엘리먼트의 value 어트리뷰트 값을 content로 설정함            |
| 어트리뷰트 제거      | remowAttr(name)               | 해당 어트리뷰트의 값을 초기화                                |
| 스타일 변경          | addClass(names)               | 선택된 엘리먼트에 SCC class를 적용함. 만약 다수의 Class를 적용하려면 공백으로 구분하여 할당 |
|                      | removeClass(names)            | 선택된 엘리먼트들을 제거                                     |
|                      | toggleClass(names)            | 특정 Class를 적용하지 않은 상태면 적용하고, 적용한 상태면 제거 |
| 스타일 얻고 설정     | css(name, value)              | 선택된 엘리먼트의 name 어트리뷰트 값을 value로 설정          |
|                      | css(properties)               | {"name1" : "value1", "name2":"value2"} 와같은 형태로 설정    |
|                      | css(name)                     | 특정 name의 프로퍼티의 스타일 값을 얻을 수 있음              |
|                      | width(value)                  | 선택된 엘리먼트의 width값을 설정                             |
|                      | heigth(value)                 | 선태된 엘리먼트의 heigth값을 설정                            |
|                      | width()                       | 선택된 엘리먼트의 width 값을 얻어옴                          |
|                      | heigth()                      | 선택된 엘리먼트의 height 값을 얻어옴                         |
|                      | offset()                      | 선택된 엘리먼트의 left 값과 top 값을 E.offset().left<br />E.offset().top과 같은 방법으로 얻을 수 있음 |
| 엘리먼트 내용 설정   | html()                        | 선택된 엘리먼트 태그 내용을 얻을 수 있음                     |
|                      | html(content)                 | 선택된 엘리먼트 태그 내용을 content 로 설정                  |
|                      | text()                        | 선택된 엘리먼트의 태그내용 중 텍스트 값만 얻을 수 있음       |
|                      | text(content)                 | 선택된 엘리먼트 태그 내용을 content로 설정                   |
| 엘리먼트 복사 & 이동 | append(content)               | 선택된 엘리먼트의 내용 마지막에 새로운 content를 추가        |
|                      | appendTo(target)              | 선택된 엘리먼트가 단일이면 target으로 이동시키고 다수라면 복사됨 |
|                      | prepend(content)              | append와 달리 앞으로 추가함                                  |
|                      | prependTo(target)             | appendTo와 달리 앞으로 복사 또는 이동함                      |
|                      | before(),<br />insertBefore() | 엘리먼트를 대상의 첫 번째 자식으로 삽입하는 대신에 대상의 바로 앞 형제로 추가함 |
|                      | after(),<br />insertAfter()   | 엘리먼트를 대상의 마지막 자식으로 삽입하는 대신에 대상의 바로 뒤 형제로 추가함 |
| 엘리먼트 감싸기      | wrap(wrapper)                 | 매개 변수로는 String 과 엘리먼트 타입이 올 수 있으며, "<div class="hello"></div>" 형태로 매개 변수 값을 넘기면 됨 |
|                      | wrapAll(wrapper)              | 선택된 모든 엘리먼트를 wrapper로 감쌈                        |
| 엘리먼트제거         | remove()                      | 페이지 DOM에서 확장 집합의 모든 엘리먼트를 삭제              |
|                      | empty()                       | 일치하는 집합의 모든 엘리먼트의 Content를 제거               |
| 엘리먼트복사         | clone(copyHandlers)           | 일반적으로 엘리먼트를 복사한 확장 집합ㅇ르 만들면 이들을 DOM어딘가에 덧붙일 수 있음 |



### 확장된 엘리먼트 집합을 관리하는 함수들

| 분류                             | 함수 명             | 함수 설명                                                    |
| -------------------------------- | ------------------- | ------------------------------------------------------------ |
| 확장 집합 크기 얻기              | size()              | 해당 엘리먼트의 개수를 반환                                  |
| 확장 집합에서 특정 엘리먼트 얻기 | get(index)          | 확장 집합에서 index번째의 엘리먼트를 가져옴                  |
|                                  | get()               | 모든 확장 엘리먼트를 일반 자바스크립트 배열로 얻음           |
|                                  | index(element)      | 화갖ㅇ 집합에서 특정 엘리먼트의 index값을 가져옴             |
| 확장 집합 재편성 하기            | add(element)        | 기존의 확장 집합에 다른 엘리먼트를 추가                      |
|                                  | not(expression)     | 기존의 확장집합에서 expression과 일치하는 엘리먼트를 제외    |
|                                  | filter(expressioin) | 기존의 확장 집합에서 expression과 일치하는 엘리먼트만 가져옴 |
| 확장 집합의 부분 집합 얻기       | slice(begin, end)   | 기존의 확장 집합에서 begin번째부터 end번째까지의 엘리먼트만 가져옴 |
| 확장 집합 관련 그 밖에 함수들    | find(selector)      | 기존의 확장 집합에서 selector와 일치하는 엘리먼트들로 새로운 확장 집합을 생성 |
|                                  | is(selector)        | 기존의 확장 집합에서 selector와 일치하는 엘리먼트가 있다면 true, 없다면 false를 반환 |
| jQuery 체인 관리하기             | end()               | 이전 확장 집합을 반환                                        |
|                                  | andSelf()           | 커맨드 체인에서 이전 확장 집합 두 개를 하나로 합침           |
| 관계를 이용하여 확장 집합 얻기   | children()          | 확장 엘리먼트의 고유한 자식으로 구성된 확장 집합 반환        |
|                                  | parent()            | 바로 위 부모로 구성된 확장 집합을 반환                       |
|                                  | parents()           | 바로위 부모와 모든 조상이 포함되는 확장 집합을 반환          |
|                                  | silblings()         | 확장 엘리먼트 내 모든 형제를 포함한 확장 집합을 반환         |
|                                  | contents()          | 엘리먼트의 콘텐츠로 구성된 확장 집합을 반환                  |
|                                  | next()              | 확장 집합 내의 각 확장 엘리먼트 바로 다음에 나오는 형제로 구성된 확장 집합을 반환 |
|                                  | nextAll()           | 확장 집합 내의 각 확장 엘리먼트 바로 다음에 나오는 모든 형제로 구성된 확장 집합을 반환 |
|                                  | prev()              | 바로 이전에 나오는 형제로 구성된 확장 집합을 반환            |
|                                  | prevAll()           | 이전에 나오는 모든 형제로 구성된 확장 집합을 반환            |

출처 : [나는 초보다 블로그](https://ggoreb.tistory.com/172)