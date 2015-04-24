# Introduction #

[help#attribute\_get](help#attribute_get.md)
(필드 하나 조회함.)
<br />
[help#attribute\_set](help#attribute_set.md)
(필드 하나에 값을 넣어줌.)
<br />
[help#line\_get](help#line_get.md)
(라인 한줄 조회함.) -get\_lead\_selection을 대체할수 있음.
<br />
[help#line\_set](help#line_set.md)
(라인 한줄에한줄에 값을 넣어줌.)
<br />

# Details #

### attribute\_get ###
<font color='#F52887'>attribute_get</font> (필드 하나 조회함.)

DATA: lv\_xxx TYPE wd\_this->element\_nodename-xxx.

zwd\_util=>attribute\_get(
> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name
> > attrname = 'XXX' "attribute name

> IMPORTING
> > value = lv\_xxx "attribute랑 같은 타입으로 선언된 변수
).

### attribute\_set ###
<font color='#F52887'>attribute_set</font> (필드 하나에 값을 넣어줌.)

DATA: lv\_xxx TYPE wd\_this->element\_nodename-xxx.

zwd\_util=>attribute\_set(

> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name
> > attrname = 'XXX' "attribute name
> > value = lv\_xxx "attribute랑 같은 타입으로 선언된 변수
).

### line\_get ###
<font color='#F52887'>line_get</font> or <font color='#F52887'>attributes_get</font> (라인 한줄 조회함.) -get\_lead\_selection을 대체할수 있음.

DATA: ls\_nodename TYPE wd\_this->element\_nodename.

zwd\_util=>attributes\_get(

> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name

> IMPORTING
> > value = ls\_nodename
).

### line\_set ###
<font color='#F52887'>attributes_set</font> or <font color='#F52887'>line_set</font> (라인 한줄에한줄에 값을 넣어줌.)

DATA: ls\_nodename TYPE wd\_this->element\_nodename.

zwd\_util=>attributes\_set(

> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name
> > value = ls\_nodename
).

### table\_get ###
table\_get (테이블값을 node에서 조회함.)

DATA: lt\_nodename TYPE wd\_this->elements\_nodename.

zwd\_util=>table\_get(

> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name

> IMPORTING
> > value = lt\_nodename
).

### table\_set ###
table\_set (테이블값을 node에 넘겨줌.)

DATA: lt\_nodename TYPE wd\_this->elements\_nodename.

zwd\_util=>table\_set(

> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name
> > value = lt\_nodename
).

### dropdownbykey\_set ###
dropdownbykey\_set (dropdownbykey에 값을 넘겨줌.)

DATA: lt\_value\_list TYPE wdy\_key\_value\_list.

zwd\_util=>dropdownbykey\_set(

> EXPORTING
> > root = wd\_context
> > nodename = wd\_this->wdctx\_nodename "node name
> > attrname = 'XXX'
> > value = lt\_value\_list
).

### url\_open ###
url\_open (다른 웹페이지를 새로운 창에서창에서 열고자 할때 사용됨.)

data: lv\_url TYPE string.
lv\_url = 'http://www.daum.net'.
zwd\_util=>url\_open(

> EXPORTING
> > cc = wd\_comp\_controller "component controller에서 호출할 경우
> > > "wd\_this를 입력해줘야 함.

> > url = lv\_url
).

### wdevent\_get ###
wdevent\_get (wdevent의 파라미터 값을 가져오기.)


> DATA: lo\_el TYPE REF TO if\_wd\_context\_element."받아올 값의 type

> zwd\_util=>wdevent\_get(
> > EXPORTING
> > > event = wdevent
> > > param\_name = 'NEW\_LEAD\_SELECTION'

> > IMPORTING
> > > value = lo\_el

> ).

### show\_msg ###
show\_msg (메세지를 출력함.)

▶ popup\_btn\_kind
**1  OK**2  Close
**3  Ok., Cancel**4  Yes, No
**5  Yes, No, Cancel**6  Cancel, Repeat, Ignore

1. 한 문장을 popup으로 출력할때.
<br />
![http://wdutil.googlecode.com/files/XGbeXbSp4c.jpg](http://wdutil.googlecode.com/files/XGbeXbSp4c.jpg)
<br />
> DATA: lv\_msg TYPE string.
> lv\_msg = `첫 줄`.

> zwd\_util=>show\_msg(
> > EXPORTING
> > > cc = wd\_comp\_controller "component controller에서
> > > > "호출할 경우
> > > > "wd\_this를 입력해줘야 함.

> > > popup\_btn\_kind = 1
> > > direct\_msg\_single = lv\_msg
> > > direct\_msg\_type = 'S'

> ).

2. 한 문장을 일반적인 방식으로 출력할때.
<br />
![http://wdutil.googlecode.com/files/XEaLlHGiOk.jpg](http://wdutil.googlecode.com/files/XEaLlHGiOk.jpg)
<br />
> DATA: lv\_msg TYPE string.
> lv\_msg = `첫 줄`.

> zwd\_util=>show\_msg(
> > EXPORTING
> > > cc = wd\_comp\_controller "component controller에서
> > > > "호출할 경우
> > > > "wd\_this를 입력해줘야 함.

> > > direct\_msg\_single = lv\_msg
> > > direct\_msg\_type = 'S'

> ).

3. 메시지클래스의 한 문장을 popup으로 출력할때.
<br />
![http://wdutil.googlecode.com/files/XXa2JpibOh.jpg](http://wdutil.googlecode.com/files/XXa2JpibOh.jpg)
<br />
> DATA: ls\_msg TYPE symsg.
> ls\_msg-msgty = 'S'.
> ls\_msg-msgid = 'ZPM'.
> ls\_msg-msgno = '001'.
> ls\_msg-msgv1 = '하나'.
> ls\_msg-msgv2 = '둘'.
> ls\_msg-msgv3 = '셋'.

> zwd\_util=>show\_msg(
> > EXPORTING
> > > cc = wd\_comp\_controller "component controller에서
> > > > "호출할 경우
> > > > "wd\_this를 입력해줘야 함.

> > > popup\_btn\_kind = 1
> > > t100\_msg = ls\_msg

> ).

4. 메시지클래스의 한 문장을 일반적인 방식으로 출력할때.
<br />
![http://wdutil.googlecode.com/files/XFdNQr0jWW.jpg](http://wdutil.googlecode.com/files/XFdNQr0jWW.jpg)
<br />
> DATA: ls\_msg TYPE symsg.
> ls\_msg-msgty = 'S'.
> ls\_msg-msgid = 'ZPM'.
> ls\_msg-msgno = '001'.
> ls\_msg-msgv1 = '하나'.
> ls\_msg-msgv2 = '둘'.
> ls\_msg-msgv3 = '셋'.

> zwd\_util=>show\_msg(
> > EXPORTING
> > > cc = wd\_comp\_controller "component controller에서
> > > > "호출할 경우
> > > > "wd\_this를 입력해줘야 함.

> > > t100\_msg = ls\_msg

> ).

5. 여러 문장을 popup으로 출력할때.
<br />
![http://wdutil.googlecode.com/files/XAEXORWMxP.jpg](http://wdutil.googlecode.com/files/XAEXORWMxP.jpg)
<br />
> DATA: lv\_msg TYPE string.
> DATA: lt\_msg TYPE string\_table.

> lv\_msg = `1. 첫 줄`.
> APPEND lv\_msg TO lt\_msg.
> lv\_msg = `2. 둘째 줄`.
> APPEND lv\_msg TO lt\_msg.

> zwd\_util=>show\_msg(
> > EXPORTING
> > > cc = wd\_comp\_controller "component controller에서
> > > > "호출할 경우
> > > > "wd\_this를 입력해줘야 함.

> > > popup\_btn\_kind = 1
> > > direct\_msg\_multi = lt\_msg
> > > direct\_msg\_type = 'S'

> ).