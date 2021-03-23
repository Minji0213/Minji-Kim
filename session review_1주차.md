자연어 처리 : Regular Regression 정규표현식
==================

###1. 정규표현식이란?

- regular expression/ regex, regexp
- 특정한 규칙을 가진 문자열의 집합을 표현하기 위한 형식언어

___________
###2. 메타문자

* 원래 그 문자가 가진 뜻이 아닌 특별한 용도로 사용하는 문자

>~~~
[] : 문자클래스 사이의 문자와 매치 (문자들 중 한 개) 
[^] : 문자클래스 사이의 문자가 아닌 문자와 매치
. : \n을 제외한 모든 문자와 매치 (.의 갯수=매치되는 문자 갯수)
*, + : 반복/ *는 1개 이상, +는 2개 이상
() : 전체 패턴 애네서 하나로 묶인 소규모 패턴
{m,n} : 횟수가 고정된 반복/ m 이상 n 이하, n만 설정 시 n회 반복
? : 0 또는 1/ 문자가 있거나 없는 경우
^ : 문자열의 시작
$ : 문자열의 끝
\ : 정규식 상에서 메타문자를 원래 문자 그대로 이용
| : or
~~~
~~~
escape 활용 : \d(단어 경계), \s(공백문자), \d(숫자), \w(단어를 만들 수 있는 문자), \n(개행)
-> 대문자 사용 시 ~가 아닌 문자와 매치됨
~~~

--------------
###3. re library

- 정규표현식을 제공하는 python library

>~~~
- re.compile : 정규표현식의 컴파일, 패턴 생성
- re.search(pattern, string, flags=0) : 문자열에서 정규표현식의 매치 여부
            -> 매치 되는 경우 정보 출력, 매치 되지 않는 경우 None 출력
- re.match(pattern, string, flags=0) : 문자열의 시작과 정규표현식의 매치 여부
- re.split(pattern, string, maxsplit=0, flags=0) : 문자열 분리
         -> re.split('분리 기준', 분리할 문자열)/ string.split()과는 다르게 정규표현식을 이용해 문자열을 분리
- re. findall(pattern, string, flags=0) :
- re.finditer(pattern, string, flags=0) : 두 문자열이 일치하는 패턴을 matchObj로 반환
~~~

--------------
###4. match Obj
>~~~
- group([group1, ...]) : 일치된 문자열 반환
          Return a tuple containing all the subgroups of the match
- start([group]) : 일치된 문자열의 시작 '위치' 반환
        Return the indices of the start of the substring matched by group
- end([group]) : 일치된 문자열의 끝 '위치' 반환
        Return the indices of the end of the substring matched by group
- span([group]) : 일치된 문자열의 (시작, 끝) 위치를 튜플로 반환
        For a match m, return the 2-tuple (m.start(group), m.end(group)).
~~~

----------------
###5. 추가 학습


rink : https://docs.python.org/3/library/re.html

1) 메타문자
>~~~
\number : Matches the contents of the group of the same number.
\A : Matches only at the start of the string.
\b : Matches the empty string, but only at the beginning or end of a word.
\d : Matches any Unicode decimal digit, [0-9] is matched.
\s : Matches Unicode whitespace characters
\w : Matches Unicode word characters
\Z : Matches only at the end of the string.
~~~

2) regex module
>~~~
- re.ascii : Make \w, \W, \b, \B, \d, \D, \s and \S perform ASCII-only matching instead of full Unicode matching.
- re.debug : Display debug information about compiled expression. 
- re.sub(pattern, repl, string, count=0, flags=0) : Return the string obtained by replacing the leftmost non-overlapping occurrences of pattern in string by the replacement repl.
- re.subn(pattern, repl, string, count=0, flags=0) :Perform the same operation as sub(), but return a tuple (new_string, number_of_subs_made).
~~~

3) match Obj
>~~~
- Match.expand(template) : Return the string obtained by doing backslash substitution on the template string template
- Match.groups(default=None) : Return a tuple containing all the subgroups of the match
- Match.pos : The value of pos which was passed to the search() or match() method of a regex object.
- Match.endpos
- Match.lastindex
- Match.lastgroup
~~~