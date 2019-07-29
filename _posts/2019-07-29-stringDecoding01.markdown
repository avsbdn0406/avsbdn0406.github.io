---
title:  "Python의 UnicodeDecodeError"
date : 2019-07-29
layout : post
categories: Python
---

Unicode Decode Error
=================================

<br>

File을 읽어오는 과정에서 디코딩 에러가 발생할 때가 있다.   &#128557;  
<pre>
<code>
  'cp949' codec can't decode byte 0xdd in position 10597888: illegal multibyte sequence
</code>
</pre>
cp949로 인코딩된 파일을 읽어오다보니 생긴 에러이다.  
아마 cp949 코덱이 byte로 디코딩할 수 없다는 에러인 것 같은데..  

<br>

encoding 파라미터로 **utf-8** 을 넣어주면 된다고 해서 해줬지만 역시나 또 에러가 발생했다.  
<pre>
<code>
  'utf-8' codec can't decode byte 0xdb in position 10596864: invalid continuation byte
</code>
</pre>

<br>

보통은 utf-8로 하면 수월하게 파일을 읽어왔는데 이런 경우는 처음이라 당황했음.  
좀 더 찾아본 결과.. 이럴 땐?! **ISO-8859-1"**  으로 디코딩을 하면 된다!!  

<pre>
<code>
  file = open(filename, 'r', encoding="ISO-8859-1");
</code>
</pre>


<br>

ISO-8859-1 코덱에 대해 찾아보니까 ISO/IEC 8859의 일부 문자로, Latin-1이라고도 쓰인다.  
