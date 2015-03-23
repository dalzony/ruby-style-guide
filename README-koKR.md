# 서론

> 롤 모델이 중요하다.<br/>
> -- Officer Alex J. Murphy / RoboCop

나는 루비 개발자로서 항상 한 가지 문제로 괴로웠다. - 파이썬 개발자들은 훌륭한
프로그래밍 스타일 가이드([PEP-8][])를 가지고 있는데, 우리에겐 코딩 스타일과
모범 사례를 가진 공식적인 가이드가 전혀 없다는 것이다. 그리고 나는 그것이야말로
문제라고 확신한다. 또한 루비의 훌륭한 해커 커뮤니티는 모두가 탐낼 만한 문서를
만들어낼 능력이 있다고 확신한다.

이 가이드는 사내 루비 코딩 가이드 라인으로 시작됐다.
그러나 몇몇 포인트에서 내가 작성한 가이드가 일반 루비 커뮤니티에도 도움이 되게끔
써서 이와 같은 중복 작업이 더는 없기를 바라며 작업하기로 했다. 그러나 루비
커뮤니티에 의해 자체적으로 수립된 예제, 숙어, 스타일에 관한 프로그래밍 방식
역시 많은 관련자에게 도움이 될 것이다.

가이드를 작성하기 시작한 때부터 본인은 여러 유수의 루비 커뮤니티로부터 소중한
피드백을 받았다. 여러 분들의 그러한 협력과 노고에 다시 한 번 감사의 말씀을
올린다. 많은 분들의 도움이 있었기에 가이드를 작성할 수 있었고, 그러한 상호작용을
통해 여타의 모든 루비 개발 관계자들에게 도움될 수 있으리라 본다.

한 가지 더, 레일즈에 관심 있는 사람이라면, 추가적으로 필요한 부분은 [루비 온
레일즈 스타일 가이드][rails-style-guide]를 참고하면 된다.

# 루비 스타일 가이드

이 루비 스타일 가이드는 다른 루비 개발자와 유지가능한 코드를 작성하는 모범사례를
적용하는 것을 추천한다. 이 가이드가 실제 사용밥법을 반영하기 때문에, 이상적으로
만들어져서 적용이 위험하다고 느끼는 사람은 사용하지 않는 것이 좋다. &ndash;그게
아무리 좋다고 해도 말이다.

이 가이드는 관련된 규칙에 따라 여러 부분으로 나뉘어 있다.(자명하다고 판단된
것을 제외하고는)규칙을 적으며 근거를 덧붙이려 노력했다.

이 모든 규칙들이 갑자기 제시되지는 않았다. 이것들 대부분이 내 전문분야인
소프트웨어 엔지니어로서의 수많은 경험, 루비 커뮤니티원의 제안, 또한 높은 평가를
받고 있는 프로그래밍 리소스인 ["Programming Ruby 1.9"][pickaxe]와
["The Ruby Programming Language"][trpl]를 기반으로 하였다.

특정 스타일에 대해서 루비 커뮤니티의 명백한 합의를 얻지 못한 부분도 있다.(문자열
구문 따옴표, 해시문 내에서의 공백, 여러 줄에 걸친 메소드 체인에서의 점(.)위치
등) 이러한 시나리오에서는 모든 유명한 스타일들이 허용되므로, 어떤 것을
사용할지는 당신이 선택하고 적용하기 나름이다.

이 가이드 라인은 시간에 따라 발전한다. 새로운 규칙이 확인되고, 오래된 규칙은
루비가 변함에 따라 쓸모없어진다.

많은 프로젝트가 (대개 여기서 유래된) 그들만의 코딩 스타일 가이드 라인을 가진다.
상충하는 부분이 있을 경우, 그 프로젝트에선 프로젝트의 가이드 라인을 우선하라.

이 가이드는 [Transmuter][]를 통해 PDF나 HTML로 복사해갈 수 있다.

[RuboCop][]은 이 스타일 가이드에 기반한 코드 분석기다.

이 가이드의 번역은 다음의 언어들로 되어있다.

* [Chinese Simplified](https://github.com/JuanitoFatas/ruby-style-guide/blob/master/README-zhCN.md)
* [Chinese Traditional](https://github.com/JuanitoFatas/ruby-style-guide/blob/master/README-zhTW.md)
* [French](https://github.com/porecreat/ruby-style-guide/blob/master/README-frFR.md)
* [German](https://github.com/arbox/ruby-style-guide/blob/master/README-deDE.md)
* [Japanese](https://github.com/fortissimo1997/ruby-style-guide/blob/japanese/README.ja.md)
* [한국어](https://github.com/dalzony/ruby-style-guide/blob/master/README-koKR.md)
* [Portuguese](https://github.com/rubensmabueno/ruby-style-guide/blob/master/README-PT-BR.md)
* [Russian](https://github.com/arbox/ruby-style-guide/blob/master/README-ruRU.md)
* [Spanish](https://github.com/alemohamad/ruby-style-guide/blob/master/README-esLA.md)
* [Vietnamese](https://github.com/scrum2b/ruby-style-guide/blob/master/README-viVN.md)

## Table of Contents

* [소스 코드 레이아웃](#소스-코드-레이아웃)
* [구문](#구문)
* [네이밍](#네이밍)
* [주석](#주석)
  * [주석 어노테이션](#주석-어노테이션)
* [클래스와 모듈](#클래스와-모듈)
* [예외](#예외)
* [컬렉션](#컬렉션)
* [문자열](#문자열)
* [정규식](#정규식)
* [퍼센트 리터럴](#퍼센트-리터럴)
* [메타프로그래밍](#메타프로그래밍)
* [그 밖에](#그 밖에)
* [도구들](#도구들)

## 소스 코드 레이아웃

> 거의 모든 사람들이 자신의 것을 제외한 모든 코딩 스타일이 번잡하고 가독성이
> 떨어진다고 확신한다. 앞 문장에서 "자신의 것을 제외한"을 없앤다면 아마도 맞는
> 말일지도...<br/>
> -- Jerry Coffin (on indentation)

* <a name="utf-8"></a>
  소스 파일의 인코딩은 `UTF-8`을 사용하라.
<sup>[[link](#utf-8)]</sup>

* <a name="spaces-indentation"></a>
  탭은 들여쓰기 단위별로 **공백 2칸**을 사용하라.(소프트 탭 사용) 하드 탭
  사용 안 함
<sup>[[link](#spaces-indentation)]</sup>

  ```Ruby
  # 나쁜 예 - 공백 4칸
  def some_method
      do_something
  end

  # 좋은 예
  def some_method
    do_something
  end
  ```

* <a name="crlf"></a>
  Unix 스타일로 줄바꿈 하라.(*BSD/Solaris/Linux/OS X 사용자들은 기본으로 설정되어
  있다. Windows 사용자에겐 특히 주의가 필요하다.)
<sup>[[link](#crlf)]</sup>

  * 만약 Git을 사용하고 있으면, 다음 설정을 추가함으로써 프로젝트가 Windows
    줄바꿈 형식으로 강제 설정되는 것을 막을 수 있을 것이다.

    ```bash
    $ git config --global core.autocrlf true
    ```
* <a name="no-semicolon"></a>
  두 개 이상의 명령문과 표현식을 세미콜론(;)으로 나눠쓰지 말아라. 한 줄에 한
  개씩 쓰는 것을 권장한다.
<sup>[[link](#no-semicolon)]</sup>

  ```Ruby
  # 나쁜 예
  puts 'foobar'; # 불필요한 세미콜론

  puts 'foo'; puts 'bar' # 같은 줄에 표현식이 2개

  # 좋은 예
  puts 'foobar'

  puts 'foo'
  puts 'bar'

  puts 'foo', 'bar' # 이 경우는 puts가 두 변수 다 적용됨.
  ```

* <a name="single-line-classes"></a>
  본문이 없는 클래스는 한 줄 형식이 권장된다.
<sup>[[link](#single-line-classes)]</sup>

  ```Ruby
  # 나쁜 예
  class FooError < StandardError
  end

  # 나쁘지 않은 예
  class FooError < StandardError; end

  # 좋은 예
  FooError = Class.new(StandardError)
  ```

* <a name="no-single-line-methods"></a>
  한 줄짜리 메소드를 작성하지 마라. 그런 방식이 비록 현장에서 많이 쓰이긴 하지만,
  그러한 syntax 사용법이 익숙지 않아 좋아하지 않는 경우도 있기 때문이다. 어쨌든
  한 줄에는 하나 이상의 메소드가 표현되어선 안 된다.
<sup>[[link](#no-single-line-methods)]</sup>

  ```Ruby
  # 나쁜 예
  def too_much; something; something_else; end

  # 나쁘지 않은 예 - 처음의 ;(세미콜론)은 필요
  def no_braces_method; body end

  # 나쁘지 않은 예 - 두 번째의 ;는 선택사항
  def no_braces_method; body; end

  # 나쁘지 않은 예 - 문법은 맞지만, ;이 없으면 가독성이 떨어짐
  def some_method() body end

  # 좋은 예
  def some_method
    body
  end
  ```

  본문이 비어있는 메소드는 이 규칙에서 예외다.

  ```Ruby
  # 좋은 예
  def no_op; end
  ```

* <a name="spaces-operators"></a>
  연산자 전후, 콤마 뒤, 콜론과 세미콜론 뒤, `{`, `}`의 전후에 공백(space)을
  써라. 공백은 루비 인터프리터에는 (대부분의 경우) 중요하지 않지만 적절하게
  사용하면 읽기 쉬운 코드를 작성할 수 있다.
<sup>[[link](#spaces-operators)]</sup>

  ```Ruby
  sum = 1 + 2
  a, b = 1, 2
  [1, 2, 3].each { |e| puts e }
  class FooError < StandardError; end
  ```

  유일한 예외는 지수 연산자다.

  ```Ruby
  # 나쁜 예
  e = M * c ** 2

  # 좋은 예
  e = M * c**2
  ```
  `{`, `}` 전후의 공백은 구문을 명확하게 하기 위해 쓸 만한데, 그 이유는
  문자열에서 삽입 구(embedded expression)를 넣고 싶을 때뿐만 아니라 블록이나
  해시문에 사용될 수 있기 때문이다. 해시문에서는 다음 두 가지 스타일이
  허용된다.

  ```Ruby
  # 좋은 예 - {뒤와 }앞에 공백
  { one: 1, two: 2 }

  # 좋은 예 - {뒤 와 }앞에 공백 없이
  {one: 1, two: 2}
  ```

  첫 번째 방법이 조금 더 읽기 좋다.(그리고 루비 커뮤니티에서 확실히 더 인기가
  있다.) 두 번째 방법은 블록과 해시를 시각적으로 구별화 수 있는 장점이 있다.
  무엇이든 하나를 선택하면, 일관적으로 적용하자.

  삽입 구를 쓸 때도, 양쪽 다 허용된다.

  ```Ruby
  # 좋은 예 - 공백이 없음
  "string#{expr}"

  # 괜찮은 예 - 분명히 가독성이 좋음
  "string#{ expr }"
  ```

  첫 번째 스타일은 매우 인기 있고, 일반적으로 고수하는 방식이다. 반대로 두 번째
  스타일은 (확실히) 좀 더 읽기 좋다. 해시와 마찬가지로- 하나를 선택하고,
  일관적으로 적용하자.

* <a name="no-spaces-braces"></a>
  `(`, `[`뒤 또는 `]`, `)` 앞에 공백을 넣지 않는다.
<sup>[[link](#no-spaces-braces)]</sup>

  ```Ruby
  some(arg).other
  [1, 2, 3].size
  ```

* <a name="no-space-bang"></a>
  `!` 뒤에 공백을 넣지 않는다.
<sup>[[link](#no-space-bang)]</sup>

  ```Ruby
  # 나쁜 예
  ! something

  # 좋은 예
  !something
  ```

* <a name="no-space-inside-range-literals"></a>
  레인지문에는 공백을 넣지 않는다.
<sup>[[link](#no-space-inside-range-literals)]</sup>

    ```Ruby
    # 나쁜 예
    1 .. 3
    'a' ... 'z'

    # 좋은 예
    1..3
    'a'...'z'
    ```

* <a name="indent-when-to-case"></a>
  `when`은 `case`와 같은 깊이로 들여 쓰자. 많은 사람들이 동의할 수 없다는 것을
  알지만, "The RubyProgramming Language"와 "Programming Ruby"에서 사용하는
  스타일이다.
<sup>[[link](#indent-when-to-case)]</sup>

  ```Ruby
  # 나쁜 예
  case
    when song.name == 'Misty'
      puts 'Not again!'
    when song.duration > 120
      puts 'Too long!'
    when Time.now.hour > 21
      puts "It's too late"
    else
      song.play
  end

  # 좋은 예
  case
  when song.name == 'Misty'
    puts 'Not again!'
  when song.duration > 120
    puts 'Too long!'
  when Time.now.hour > 21
    puts "It's too late"
  else
    song.play
  end
  ```

* <a name="indent-conditional-assignment"></a>
  조건식의 결과를 변수에 대입하는 경우, 그 가지(case)의 일반적인 정렬을 유지하라.
<sup>[[link](#indent-conditional-assignment)]</sup>

  ```Ruby
  # 나쁜 예 - 상당히 복잡함
  kind = case year
  when 1850..1889 then 'Blues'
  when 1890..1909 then 'Ragtime'
  when 1910..1929 then 'New Orleans Jazz'
  when 1930..1939 then 'Swing'
  when 1940..1950 then 'Bebop'
  else 'Jazz'
  end

  result = if some_cond
    calc_something
  else
    calc_something_else
  end

  # 좋은 예 - 어떻게 돌아가는지 분명함
  kind = case year
         when 1850..1889 then 'Blues'
         when 1890..1909 then 'Ragtime'
         when 1910..1929 then 'New Orleans Jazz'
         when 1930..1939 then 'Swing'
         when 1940..1950 then 'Bebop'
         else 'Jazz'
         end

  result = if some_cond
             calc_something
           else
             calc_something_else
           end

  # 좋은 예(가로 폭의 효율이 약간 더 좋음)
  kind =
    case year
    when 1850..1889 then 'Blues'
    when 1890..1909 then 'Ragtime'
    when 1910..1929 then 'New Orleans Jazz'
    when 1930..1939 then 'Swing'
    when 1940..1950 then 'Bebop'
    else 'Jazz'
    end

  result =
    if some_cond
      calc_something
    else
      calc_something_else
    end
  ```

* <a name="empty-lines-between-methods"></a>
  메소드 정의와, 단락이 논리적으로 구분될 때마다 사이에 빈줄을 넣어 분할하자.
<sup>[[link](#empty-lines-between-methods)]</sup>

  ```Ruby
  def some_method
    data = initialize(options)

    data.manipulate!

    data.result
  end

  def some_method
    result
  end
  ```

* <a name="no-trailing-params-comma"></a>
  메소드 호출의 마지막 인수 뒤에 쉼표를 피한다. 인수가 여러 줄로 나누어져 있지
  않을 때는 특히 피한다.
<sup>[[link](#no-trailing-params-comma)]</sup>

  ```Ruby
  # 나쁜 예 - 쉽게 인수를 이동/추가/삭제할 수 있지만 여전히 권장하진 않는다.
  some_method(
               size,
               count,
               color,
             )

  # 나쁜 예
  some_method(size, count, color, )

  # 좋은 예
  some_method(size, count, color)
  ```

* <a name="spaces-around-equals"></a>
  메소드의 인수에 기본 값을 대입할 때에는, `=` 연산자 주변에 공백을 넣어라.
<sup>[[link](#spaces-around-equals)]</sup>

  ```Ruby
  # 나쁜 예
  def some_method(arg1=:default, arg2=nil, arg3=[])
    # do something...
  end

  # 좋은 예
  def some_method(arg1 = :default, arg2 = nil, arg3 = [])
    # do something...
  end
  ```

  여러 루비 책들이 첫 번째 스타일을 권장하지만, 실제로는 두 번째 스타일이 좀 더
  눈에 잘 띈다.(그리고 분명히 읽기 더 쉽다.)

* <a name="no-trailing-backslash"></a>
  불필요하게 `\`로 줄을 바꾸는 것을 피하라. 실제로 프로그래밍할 때 긴 문자열을
  자르는 경우 말고는 줄을 임의로 바꾸지 마라.
<sup>[[link](#no-trailing-backslash)]</sup>

  ```Ruby
  # 나쁜 예
  result = 1 - \
           2

  # 좋은 예(하지만 여전히 못생겼다.)
  result = 1 \
           - 2

  long_string = 'First part of the long string' \
                ' and second part of the long string'
  ```

* <a name="consistent-multi-line-chains"></a>
    메소드 연쇄가 여러 줄에 걸쳐서 이루어질 때, 일관된 스타일을 적용하라.
    루비에서 여러 줄에 걸친 메소드 연쇄 표현 스타일은 크게 두 가지가 있는데,
    둘 모두 괜찮은 방식이다. `.`의 위치에 따라 선두법(leading, A방식)과
    후방법(trailing, B방식)이 있다.
<sup>[[link](#consistent-multi-line-chains)]</sup>

  * **(A방식)** 연쇄적인 메소드 호출이 서로 다른 줄에 걸쳐 연결되어 있을 때,
    두 번째 라인에 `.`을 두라.

    ```Ruby
    # 나쁜 예 - 두 번째 줄을 이해하기 위해서 첫 번째 라인을 찾아야 함
    one.two.three.
      four

    # 좋은 예 - 두 번째 줄에서 어떤일이 일어나는지 즉시 알 수 있음
    one.two.three
      .four
    ```

  * **(B방식)** 연쇄적인 메소드 호출이 서로 다른 줄에 걸쳐 연결되어 있을 때,
    이를 명확히 하기 위해 첫 번째 줄에 `.`을 포함시켜라.

    ```Ruby
    # 나쁜 예 - 메소드 연쇄가 이어지는지 알기 위해서 다음 줄을 읽을 필요가 있음
    one.two.three
      .four

    # 좋은 예 - 메소드 연쇄가 다음줄에서 이어지는지 한눈에 알 수 있음
    one.two.three.
      four
    ```

  양 쪽 스타일의 장점에 대한 논의는
  [여기](https://github.com/bbatsov/ruby-style-guide/pull/176)에서 볼 수 있다.

* <a name="no-double-indent"></a>
    메소드 호출이 여러 줄에 걸쳐 일어날 경우 인수들을 적절히 정렬하라.
    라인 길이 제한으로 인수들을 정렬하기 어려울 때에는 두 번째 인수부터 한 칸
    들여쓰기를(single indent) 하되, 이 때 첫 번째 인수가 들여쓰기 이전에 줄바꿈이
    없었는지 확인해야 된다.(아래 세 번째 예에서 to:'bob@example.com' (첫 번째
    인수)의 줄이 넘어가면 네 번째 예처럼 작성하면 된다.)
<sup>[[link](#no-double-indent)]</sup>

  ```Ruby
  # 처음 상태(줄이 너무 길다)
  def send_mail(source)
    Mailer.deliver(to: 'bob@example.com', from: 'us@example.com', subject: 'Important message', body: source.text)
  end

  # 나쁜 예(들여쓰기 두번)
  def send_mail(source)
    Mailer.deliver(
        to: 'bob@example.com',
        from: 'us@example.com',
        subject: 'Important message',
        body: source.text)
  end

  # 좋은 예
  def send_mail(source)
    Mailer.deliver(to: 'bob@example.com',
                   from: 'us@example.com',
                   subject: 'Important message',
                   body: source.text)
  end

  # 좋은 예(보통의 들여쓰기)
  def send_mail(source)
    Mailer.deliver(
      to: 'bob@example.com',
      from: 'us@example.com',
      subject: 'Important message',
      body: source.text
    )
  end
  ```

* <a name="align-multiline-arrays"></a>
  여러 줄에 걸친 배열 요소들을 정리하라.
<sup>[[link](#align-multiline-arrays)]</sup>

  ```Ruby
  # 나쁜 예 - 단일 들여쓰기
  menu_item = ['Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
    'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam']

  # 좋은 예
  menu_item = [
    'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
    'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam'
  ]

  # 좋은 예
  menu_item =
    ['Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
     'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam']
  ```

* <a name="underscores-in-numerics"></a>
  너무 큰 숫자는 밑줄을 이용하면 가독성이 좋아진다.
<sup>[[link](#underscores-in-numerics)]</sup>

  ```Ruby
  # 나쁜 예 - 0이 몇 개나 됩니까?
  num = 1000000

  # 좋은 예 - 사람이 해석하기에도 훨씬 쉽다.
  num = 1_000_000
  ```

* <a name="rdoc-conventions"></a>
  RDoc과 API 문서의 컨벤션을 이용하라.
  `def`와 명령 블록 사이에 빈 줄을 넣지 마라.
<sup>[[link](#rdoc-conventions)]</sup>

* <a name="80-character-limits"></a>
  한 행에는 80자까지만 쓴다.
<sup>[[link](#80-character-limits)]</sup>

* <a name="no-trailing-whitespace"></a>
  줄 끝의 공백은 피한다.
<sup>[[link](#no-trailing-whitespace)]</sup>

* <a name="newline-eof"></a>
  모든 파일 끝에 줄바꿈을 넣는다.
<sup>[[link](#newline-eof)]</sup>

* <a name="no-block-comments"></a>
  블록 형태의 주석을 사용하지 마라. 앞에 공백이 들어가면 작동하지 않고, 일반
  주석과 달리 쉽게 발견하기 어렵다.
<sup>[[link](#no-block-comments)]</sup>

  ```Ruby
  # 나쁜 예
  =begin
  comment line
  another comment line
  =end

  # 좋은 예
  # comment line
  # another comment line
  ```

## 구문

* <a name="double-colons"></a>
  `::`는 상수(클래스나 모듈 포함)와 생성자(`Array()` 또는 `Nokogiri::HTML()`
  같은)를 참조할 때만 사용하라. 일반 메소드 호출에서는 `::`를 쓰지 마라.
<sup>[[link](#double-colons)]</sup>

  ```Ruby
  # 나쁜 예
  SomeClass::some_method
  some_object::some_method

  # 좋은 예
  SomeClass.some_method
  some_object.some_method
  SomeModule::SomeClass::SOME_CONST
  SomeModule::SomeClass()
  ```

* <a name="method-parens"></a>
  매개변수가 있을 때 `def`와 괄호를 함께 사용하라. 받을 매개변수가 없을 때에는
  괄호를 제거하라.
<sup>[[link](#method-parens)]</sup>

   ```Ruby
   # 나쁜 예
   def some_method()
     # body omitted
   end

   # 좋은 예
   def some_method
     # body omitted
   end

   # 나쁜 예
   def some_method_with_parameters param1, param2
     # body omitted
   end

   # 좋은 예
   def some_method_with_parameters(param1, param2)
     # body omitted
   end
   ```

* <a name="no-for-loops"></a>
  `for`을 쓸 때에는 정확히 그 용법을 알고 있을 때에만 사용해야 한다. 대부분
  반복자(iterator)가 `for` 대신 사용된다. `for` 구문은 `each`의 관점에서
  실행되기 때문에 일종의 우회적인 방식을 사용하지만, `each` 용법과는 다른 점이
  있다. 즉, `for`는 `each`와는 다르게 새로운 영역을 생성하는 것이 아니기 때문에,
  `for` 구문 내부에서 정의된 변수들은 `for` 외부에서도 접근 가능하다.
<sup>[[link](#no-for-loops)]</sup>

  ```Ruby
  arr = [1, 2, 3]

  # 나쁜 예
  for elem in arr do
    puts elem
  end

  # elem은 for문 밖에서도 접근 가능한 것에 주의
  elem # => 3

  # 좋은 예
  arr.each { |elem| puts elem }

  # elem을 each블록 밖에서는 접근할 수 없음
  elem # => NameError: undefined local variable or method `elem'
  ```

* <a name="no-then"></a>
  `if/unless`문의 내용이 여러 줄일 때에는 `then`을 쓰지 마라.
<sup>[[link](#no-then)]</sup>

  ```Ruby
  # 나쁜 예
  if some_condition then
    # body omitted
  end

  # 좋은 예
  if some_condition
    # body omitted
  end
  ```

* <a name="same-line-condition"></a>
  조건문의 내용이 여러 줄일 때, 조건식은 항상 `if/unless`와 같은 줄에 붙여 써라.
<sup>[[link](#same-line-condition)]</sup>

  ```Ruby
  # 나쁜 예
  if
    some_condition
    do_something
    do_something_else
  end

  # 좋은 예
  if some_condition
    do_something
    do_something_else
  end
  ```

* <a name="ternary-operator"></a>
  `if/then/else/end` 구문 보다, 삼항 연산자(`?:`)를 더욱 선호한다. 그게 좀 더
  명쾌하고 간결하다.
<sup>[[link](#ternary-operator)]</sup>

  ```Ruby
  # 나쁜 예
  result = if some_condition then something else something_else end

  # 좋은 예
  result = some_condition ? something : something_else
  ```

* <a name="no-nested-ternary"></a>
  삼항 연산자는 하나의 식마다 한 개의 표현식을 쓴다. 즉, 삼항 연산자는 중첩해서
  써서는 안 된다. 그러한 경우는 `if/else` 구문을 사용하는 것이 좋다.
<sup>[[link](#no-nested-ternary)]</sup>

  ```Ruby
  # 나쁜 예
  some_condition ? (nested_condition ? nested_something : nested_something_else) : something_else

  # 좋은 예
  if some_condition
    nested_condition ? nested_something : nested_something_else
  else
    something_else
  end
  ```
* <a name="no-semicolon-ifs"></a>
  `if x; ...`는 사용하지마라. 대신 삼항 연산자를 사용하라.
<sup>[[link](#no-semicolon-ifs)]</sup>

  ```Ruby
  # 나쁜 예
  result = if some_condition; something else something_else end

  # 좋은 예
  result = some_condition ? something : something_else
  ```

* <a name="use-if-case-returns"></a>
  `if`와 `case`은 결과를 반환하는 표현식이라는 사실을 이용하라.
<sup>[[link](#use-if-case-returns)]</sup>

  ```Ruby
  # 나쁜 예
  if condition
    result = x
  else
    result = y
  end

  # 좋은 예
  result =
    if condition
      x
    else
      y
    end
  ```

* <a name="one-line-cases"></a>
  하나의 행의 경우에는 `when x then ...`을 이용하라. 대안인 `when x:...`는 루비
  1.9에서 없어졌다.
<sup>[[link](#one-line-cases)]</sup>

* <a name="no-when-semicolons"></a>
  `when x; ...`문을 사용하지마라. 앞서 말한 규칙을 보라.
<sup>[[link](#no-when-semicolons)]</sup>

* <a name="bang-not-not"></a>
  `not`보다는 `!`를 사용하라.
<sup>[[link](#bang-not-not)]</sup>

  ```Ruby
  # 나쁜 예 - 연산자 우선순위에 의해 괄호가 요구됨
  x = (not something)

  # 좋은 예
  x = !something
  ```

* <a name="no-bang-bang"></a>
  `!!`의 사용은 피하라
<sup>[[link](#no-bang-bang)]</sup>

  ```Ruby
  # 나쁜 예
  x = 'test'
  # 불분명한 nil 체크
  if !!x
    # body 생략
  end

  x = false
  # 이중 부정은 boolean타입에서 무용함
  !!x # => false

  # 좋은 예
  x = 'test'
  unless x.nil?
    # body 생략
  end
  ```

* <a name="no-and-or-or"></a>
  `and`와 `or`은 금지어다. 그만한 가치가 없다. 대신에 항상 `&&`와 `||`를 써라.
<sup>[[link](#no-and-or-or)]</sup>

  ```Ruby
  # 나쁜 예
  # boolean 식
  if some_condition and some_other_condition
    do_something
  end

  # 제어문
  document.saved? or document.save!

  # 좋은 예
  # boolean 식
  if some_condition && some_other_condition
    do_something
  end

  # 제어문
  document.saved? || document.save!
  ```

* <a name="no-multiline-ternary"></a>
  여러 줄의 조건문에는 `?:`(삼항 연산자)를 피하라. 대신 `if/unless`를 사용하라.
<sup>[[link](#no-multiline-ternary)]</sup>

* <a name="if-as-a-modifier"></a>
  구문이 한 줄일 때에는, 같은 줄 끝에 `if/unless`를 사용하는 것이 좋다.
  또 다른 좋은 표현방법은 `&&/||`과 같은 제어문을 쓰는 것이다.
<sup>[[link](#if-as-a-modifier)]</sup>

  ```Ruby
  # 나쁜 예
  if some_condition
    do_something
  end

  # 좋은 예
  do_something if some_condition

  # 또 다른 좋은 예
  some_condition && do_something
  ```

* <a name="no-multiline-if-modifiers"></a>
  간단하지 않고 여러 줄에 걸친 구문 블록에는 한 줄 `if/unless`를 피하라.
<sup>[[link](#no-multiline-if-modifiers)]</sup>

  ```Ruby
  # 나쁜 예
  10.times do
    # multi-line body omitted
  end if some_condition

  # 좋은 예
  if some_condition
    10.times do
      # multi-line body omitted
    end
  end
  ```

* <a name="unless-for-negatives"></a>
  `if` 뒤의 부정적인 조건보다는 `unless`(나 `||`)가 더 좋다.
<sup>[[link](#unless-for-negatives)]</sup>

  ```Ruby
  # 나쁜 예
  do_something if !some_condition

  # 나쁜 예
  do_something if not some_condition

  # 좋은 예
  do_something unless some_condition

  # 또 다른 좋은 방법
  some_condition || do_something
  ```

* <a name="no-else-with-unless"></a>
  `unless`에는 `else`를 쓰지 마라. 긍정적인 경우가 앞에 오도록 다시 작성하라.
<sup>[[link](#no-else-with-unless)]</sup>

  ```Ruby
  # 나쁜 예
  unless success?
    puts 'failure'
  else
    puts 'success'
  end

  # 좋은 예
  if success?
    puts 'success'
  else
    puts 'failure'
  end
  ```

* <a name="no-parens-if"></a>
  한 개의 `if/unless/while/until` 구문의 조건식 앞뒤에는 괄호를 사용하지 마라.
<sup>[[link](#no-parens-if)]</sup>

  ```Ruby
  # 나쁜 예
  if (x > 10)
    # body omitted
  end

  # 좋은 예
  if x > 10
    # body omitted
  end
  ```

* <a name="no-multiline-while-do"></a>
  `while/until` 문의 내용이 여러 줄일 때에는, `while/until condition do`를 쓰지
  마라.
<sup>[[link](#no-multiline-while-do)]</sup>

  ```Ruby
  # 나쁜 예
  while x > 5 do
    # body omitted
  end

  until x > 5 do
    # body omitted
  end

  # 좋은 예
  while x > 5
    # body omitted
  end

  until x > 5
    # body omitted
  end
  ```

* <a name="while-as-a-modifier"></a>
  구문이 한 줄일 때에는, 같은 줄 끝에 `while/until`를 쓰는 것이 좋다.
<sup>[[link](#while-as-a-modifier)]</sup>

  ```Ruby
  # 나쁜 예
  while some_condition
    do_something
  end

  # 좋은 예
  do_something while some_condition
  ```

* <a name="until-for-negatives"></a>
  `while`에 부정적인 조건을 쓰기보단 `until`을 쓰는 것이 좋다.
<sup>[[link](#until-for-negatives)]</sup>

  ```Ruby
  # 나쁜 예
  do_something while !some_condition

  # 좋은 예
  do_something until some_condition
  ```

* <a name="infinite-loop"></a>
  무한 반복문이 필요할 때에는, `while/until`보다 `Kernel#loop`를 쓰는 것이 더 좋다.
<sup>[[link](#infinite-loop)]</sup>

    ```ruby
    # 나쁜 예
    while true
      do_something
    end

    until false
      do_something
    end

    # 좋은 예
    loop do
      do_something
    end
    ```

* <a name="loop-with-break"></a>
  종결조건을 나중에 판정하는 반복문을 쓸 때, `begin/end/until` 또는
  `begin/end/while`보다는 `Kernel#loop`와 `break`를 사용하라.
<sup>[[link](#loop-with-break)]</sup>

  ```Ruby
  # 나쁜 예
  begin
    puts val
    val += 1
  end while val < 0

  # 좋은 예
  loop do
    puts val
    val += 1
    break unless val < 0
  end
  ```

* <a name="no-dsl-parens"></a>
  메소드가 다음 세 가지인 경우 매개변수를 감싸는 괄호를 생략하라.
  1. 내장 DSL(예를 들어 Rake, 레일즈, RSpec 등)의 일부인 메소드
  2. 루비에서 "키워드" 역할을 하고 있는 메소드(예를 들어 `attr_reader`, `puts`)
  3. attribute 접근 메소드 이외의 다른 모든 메소드 호출 시 사용되는 매개변수들은
     괄호로 감싸야 한다.
<sup>[[link](#no-dsl-parens)]</sup>

  ```Ruby
  class Person
    attr_reader :name, :age

    # omitted
  end

  temperance = Person.new('Temperance', 30)
  temperance.name

  puts temperance.age

  x = Math.sin(y)
  array.delete(e)

  bowling.score.should == 0
  ```

* <a name="no-braces-opts-hash"></a>
  옵션들이 해시라면 가장 바깥 중괄호를 생략한다.
<sup>[[link](#no-braces-opts-hash)]</sup>

  ```Ruby
  # 나쁜 예
  user.set({ name: 'John', age: 45, permissions: { read: true } })

  # 좋은 예
  user.set(name: 'John', age: 45, permissions: { read: true })
  ```

* <a name="no-dsl-decorating"></a>
  내장된 DSL의 일부인 메소드들에 대해 바깥의 중괄호와 괄호를 생략한다.
<sup>[[link](#no-dsl-decorating)]</sup>

  ```Ruby
  class Person < ActiveRecord::Base
    # 나쁜 예
    validates(:name, { presence: true, length: { within: 1..10 } })

    # 좋은 예
    validates :name, presence: true, length: { within: 1..10 }
  end
  ```

* <a name="no-args-no-parens"></a>
  인수가 없는 메소드를 호출할 때 괄호를 생략한다.
<sup>[[link](#no-args-no-parens)]</sup>

  ```Ruby
  # 나쁜 예
  Kernel.exit!()
  2.even?()
  fork()
  'test'.upcase()

  # 좋은 예
  Kernel.exit!
  2.even?
  fork
  'test'.upcase
  ```

* <a name="single-line-blocks"></a>
  한 줄짜리 블록에서는 `do...end`보다 `{...}`가 권장된다. 여러 줄짜리 블록에
  대해 `{...}`를 사용하는 것은 피하라.(줄이 많으면 항상 보기에 안 좋다.)
  "제어 흐름"과 "메소드 정의"에는 항상 `do...end`를 사용하라.(예. Rakefile이나
  특정 DSL 내에서) 연속적(chaining)일 때는 `do...end`를 피하라.
<sup>[[link](#single-line-blocks)]</sup>

  ```Ruby
  names = ['Bozhidar', 'Steve', 'Sarah']

  # 나쁜 예
  names.each do |name|
    puts name
  end

  # 좋은 예
  names.each { |name| puts name }

  # 나쁜 예
  names.select do |name|
    name.start_with?('S')
  end.map { |name| name.upcase }

  # 좋은 예
  names.select { |name| name.start_with?('S') }.map { |name| name.upcase }
  ```

  어떤 사람은 {...}를 사용하는 여러 줄에 걸친 연쇄(chaining)다 보기에 괜찮다고
  주장할 수도 있겠지만 정말 그러한지는 다음 사항들에 대해 자문해봐야 한다.
  그렇게 작성된 코드가 가독성이 좋은가? 또 블록 내부의 내용이 깔끔하게 메소드로
  추출 가능한가? 등에 대해서 말이다.

* <a name="block-argument"></a>
  다른 블록에 인수만 넘기는 블록문 쓰는 것을 피하기 위해, 명시적으로 블록
  인수를 사용하는 것을 고려해보라. 블록이 `proc`으로 변하면서, 성능에 영향을
  주는 것을 조심해야 한다.
<sup>[[link](#block-argument)]</sup>

  ```Ruby
  require 'tempfile'

  # 나쁜 예
  def with_tmp_dir
    Dir.mktmpdir do |tmp_dir|
      Dir.chdir(tmp_dir) { |dir| yield dir }  # block just passes arguments
    end
  end

  # 좋은 예
  def with_tmp_dir(&block)
    Dir.mktmpdir do |tmp_dir|
      Dir.chdir(tmp_dir, &block)
    end
  end

  with_tmp_dir do |dir|
    puts "dir is accessible as a parameter and pwd is set: #{dir}"
  end
  ```

* <a name="no-explicit-return"></a>
  제어문에 불필요한 `return`을 피하라.
<sup>[[link](#no-explicit-return)]</sup>

  ```Ruby
  # 나쁜 예
  def some_method(some_arr)
    return some_arr.size
  end

  # 좋은 예
  def some_method(some_arr)
    some_arr.size
  end
  ```

* <a name="no-self-unless-required"></a>
  불필요한 `self`를 피하라.(이건, self write accessor를 호출할 때만 필요하다.)
<sup>[[link](#no-self-unless-required)]</sup>

  ```Ruby
  # 나쁜 예
  def ready?
    if self.last_reviewed_at > self.last_updated_at
      self.worker.update(self.content, self.options)
      self.status = :in_progress
    end
    self.status == :verified
  end

  # 좋은 예
  def ready?
    if last_reviewed_at > last_updated_at
      worker.update(content, options)
      self.status = :in_progress
    end
    status == :verified
  end
  ```

* <a name="no-shadowing"></a>
  당연하지만 지역 변수와 메소드가 같은 것을 의미하지 않을 때, 지역변수로 메소드를
  가리는 것을 피하라.
<sup>[[link](#no-shadowing)]</sup>

  ```Ruby
  class Foo
    attr_accessor :options

    # 괜찮은 예
    def initialize(options)
      self.options = options
      # option과 self.option은 여기서 같다.
    end

    # 나쁜 예
    def do_something(options = {})
      unless options[:when] == :later
        output(self.options[:message])
      end
    end

    # 좋은 예
    def do_something(params = {})
      unless params[:when] == :later
        output(options[:message])
      end
    end
  end
  ```

* <a name="safe-assignment-in-condition"></a>
  배정문이 괄호안에 싸인 경우를 제외하고는, 조건식에서 `=`(배정 연산자)를 써서
  값을 반환하지 마라. 이것은 *조건문에서 안전하게 대입하기*라 불리는 루비 사용자
  사이에서는 상당히 유명한 관용 표현이다.
<sup>[[link](#safe-assignment-in-condition)]</sup>

  ```Ruby
  # 나쁜 예(+ 주의)
  if v = array.grep(/foo/)
    do_something(v)
    ...
  end

  # 좋은 예(MRI would still complain, but RuboCop won't)
  if (v = array.grep(/foo/))
    do_something(v)
    ...
  end

  # 좋은 예
  v = array.grep(/foo/)
  if v
    do_something(v)
    ...
  end
  ```

* <a name="self-assignment"></a>
  가능하면 생략된 스타일의 자체 대입 연산자를 사용하라.
<sup>[[link](#self-assignment)]</sup>

  ```Ruby
  # 나쁜 예
  x = x + y
  x = x * y
  x = x**y
  x = x / y
  x = x || y
  x = x && y

  # 좋은 예
  x += y
  x *= y
  x **= y
  x /= y
  x ||= y
  x &&= y
  ```

* <a name="double-pipe-for-uninit"></a>
  초기화가 안된 변수를 초기화 할 때에는 `||=`를 사용하라.
<sup>[[link](#double-pipe-for-uninit)]</sup>

  ```Ruby
  # 나쁜 예
  name = name ? name : 'Bozhidar'

  # 나쁜 예
  name = 'Bozhidar' unless name

  # 좋은 예 - name이 nil이나 false가 아니면 Bozhidar로 초기화한다.
  name ||= 'Bozhidar'
  ```

* <a name="no-double-pipes-for-bools"></a>
  boolean 변수에 대해서는 `||=`로 초기화하지 마라.(현재 변수가 `false`일 때,
  무슨 일이 일어날지 생각하라.)
<sup>[[link](#no-double-pipes-for-bools)]</sup>

  ```Ruby
  # 나쁜 예 - enabled가 false 일 때도 true로 대입
  enabled ||= true

  # 좋은 예
  enabled = true if enabled.nil?
  ```

* <a name="double-amper-preprocess"></a>
  존재여부를 모르는 전처리 변수에는 `&&=`를 쓴다. `&&=`를 사용하면 값이 존재할
  때만 값을 바꾸기 때문에 값 존재 여부를 확인하는 `if`는 없어도 된다.
<sup>[[link](#double-amper-preprocess)]</sup>

  ```Ruby
  # 나쁜 예
  if something
    something = something.downcase
  end

  # 나쁜 예
  something = something ? something.downcase : nil

  # 괜찮은 예
  something = something.downcase if something

  # 좋은 예
  something = something && something.downcase

  # 더 좋은 예
  something &&= something.downcase
  ```

* <a name="no-case-equality"></a>
  case 동등(equality) 연산자 `===`를 사용하는 것을 피하라. 왜냐하면 그 이름에서
  말해주듯, 이 연산자는 암묵적으로 `case`의(동등 여부뿐만 아니라) 상태를
  판별하는 데에 사용되도록 고안되었기 때문에, 외부에서 본다면 약간 혼란스러운
  코드가 된다.
<sup>[[link](#no-case-equality)]</sup>

  ```Ruby
  # 나쁜 예
  Array === something
  (1..100) === 7
  /something/ === some_string

  # 좋은 예
  something.is_a?(Array)
  (1..100).include?(7)
  some_string =~ /something/
  ```

* <a name="eql"></a>
  `==`로 할수 있을 때에는 `eql?`을 사용하지 마라. `eql?`이 제공하는 엄격한
  비교는 대부분 필요 없다.
<sup>[[link](#eql)]</sup>

  ```Ruby
  # 나쁜 예 - eql?은 문자열에서는 ==와 같음
  "ruby".eql? some_str

  # 좋은 예
  "ruby" == some_str
  1.0.eql? x # eql? makes sense here if want to differentiate between Fixnum and Float 1
  ```

* <a name="no-cryptic-perlisms"></a>
  펄 스타일의 특수 변수(`$:`, `$;` 등)사용을 피하라. 그들은 상당히
  기괴해 보이고, one-liner 스크립트 외의 그것들의 사용은 읽기 힘들다. `English`
  라이브러리에서 제공하는 인간 친화적인 alias를 사용하라.
<sup>[[link](#no-cryptic-perlisms)]</sup>

  ```Ruby
  # 나쁜 예
  $:.unshift File.dirname(__FILE__)

  # 좋은 예
  require 'English'
  $LOAD_PATH.unshift File.dirname(__FILE__)
  ```

* <a name="parens-no-spaces"></a>
  메소드 이름과 괄호 사이에 공백을 넣지 마라.
<sup>[[link](#parens-no-spaces)]</sup>

  ```Ruby
  # 나쁜 예
  f (3 + 2) + 1

  # 좋은 예
  f(3 + 2) + 1
  ```

* <a name="parens-as-args"></a>
  메소드가 시작할 때의 첫 번째 인수가 괄호로 시작하면 메소드 호출 시 항상 괄호를
  사용하라. 예를 들면, `f((3 + 2) + 1)`처럼 쓴다.
<sup>[[link](#parens-as-args)]</sup>

* <a name="always-warn-at-runtime"></a>
  항상 `-w` 옵션과 함께 루비 인터프리터를 실행하라. 그러면 위의 규칙들을
  잊어버렸을 때 경고할 것이다.
<sup>[[link](#always-warn-at-runtime)]</sup>

* <a name="lambda-multi-line"></a>
  한 줄짜리 본문 블록에 새로운 lambda 구문을 사용하라. `lambda` 메소드는
  여러 줄이 있는 블록에 써라.
<sup>[[link](#lambda-multi-line)]</sup>

  ```Ruby
  # 나쁜 예
  l = lambda { |a, b| a + b }
  l.call(1, 2)

  # 맞지만, 보기에 매우 어색한 예
  l = ->(a, b) do
    tmp = a * 7
    tmp * b / 50
  end

  # 좋은 예
  l = ->(a, b) { a + b }
  l.call(1, 2)

  l = lambda do |a, b|
    tmp = a * 7
    tmp * b / 50
  end
  ```

* <a name="proc"></a>
  `Proc.new`보다는 `proc`을 권장한다.
<sup>[[link](#proc)]</sup>

  ```Ruby
  # 나쁜 예
  p = Proc.new { |n| puts n }

  # 좋은 예
  p = proc { |n| puts n }
  ```

* <a name="proc-call"></a>
  lambda나 proc에서 `proc[]`이나 `proc.()`보다 `proc.call()`을 권장한다.
<sup>[[link](#proc-call)]</sup>

  ```Ruby
  # 나쁜 예 - Enumeration 접근과 비슷해 보임
  l = ->(v) { puts v }
  l[1]

  # 역시 나쁜 예 - 잘 쓰지 않는 구문
  l = ->(v) { puts v }
  l.(1)

  # 좋은 예
  l = ->(v) { puts v }
  l.call(1)
  ```

* <a name="underscore-unused-vars"></a>
  사용하지 않는 블록 인수나, 지역변수에는 `_`를 앞에 붙여라.(설명이 좀 없더라도)
  `_`만 쓰는 것도 가능하다. 이 컨벤션은 루비 인터프리터와 Robocop과 같은 툴에
  의해 인지되고, 사용하지 않는 변수에 대한 경고를 숨긴다.
<sup>[[link](#underscore-unused-vars)]</sup>

  ```Ruby
  # 나쁜 예
  result = hash.map { |k, v| v + 1 }

  def something(x)
    unused_var, used_var = something_else(x)
    # ...
  end

  # 좋은 예
  result = hash.map { |_k, v| v + 1 }

  def something(x)
    _unused_var, used_var = something_else(x)
    # ...
  end

  # 좋은 예
  result = hash.map { |_, v| v + 1 }

  def something(x)
    _, used_var = something_else(x)
    # ...
  end
  ```

* <a name="global-stdout"></a>
  `STDOUT/STDERR/STDIN`보다는 `$stdout/$stderr/$stdin`을 사용하라.
  `STDOUT/STDERR/STDIN`은 상수이며, 루비에서의 상수는 실제로 재대입 할 수
  있다.(다른 스트림으로 리디렉션도 가능) 물론 재대입하면 인터프리터의 경고가
  나올 것이다.
<sup>[[link](#global-stdout)]</sup>

* <a name="warn"></a>
  `$stderr.puts`보다는 `warn`을 사용하라. 좀 더 간결하고 명확할 뿐만 아니라
  `warn`을 사용하면 필요에 따라 경고를 숨길 수도 있다.(`-W0`를 통해 경고 수준을
  0으로 함으로써)
<sup>[[link](#warn)]</sup>

* <a name="sprintf"></a>
  기괴한 `String#%`메소드보다는 `sprintf`와 alias인 `format`사용이 더 좋다.
<sup>[[link](#sprintf)]</sup>

  ```Ruby
  # 나쁜 예
  '%d %d' % [20, 10]
  # => '20 10'

  # 좋은 예
  sprintf('%d %d', 20, 10)
  # => '20 10'

  # 좋은 예
  sprintf('%{first} %{second}', first: 20, second: 10)
  # => '20 10'

  format('%d %d', 20, 10)
  # => '20 10'

  # 좋은 예
  format('%{first} %{second}', first: 20, second: 10)
  # => '20 10'
  ```

* <a name="array-join"></a>
  문자 인수와 함께 쓰는 기괴한 `Array#*` 보다 `Array#join`의 사용을 선호한다.
<sup>[[link](#array-join)]</sup>

  ```Ruby
  # 나쁜 예
  %w(one two three) * ', '
  # => 'one, two, three'

  # 좋은 예
  %w(one two three).join(', ')
  # => 'one, two, three'
  ```

* <a name="splat-arrays"></a>
  변수가 배열인지 모르겠지만 그것을 Array로 취급하고 싶을 때에는 명시적인 `Array`
  체크 대신에 `[*var]` 또는 `Array()`를 사용하라.
<sup>[[link](#splat-arrays)]</sup>

  ```Ruby
  # 나쁜 예
  paths = [paths] unless paths.is_a? Array
  paths.each { |path| do_something(path) }

  # 좋은 예
  [*paths].each { |path| do_something(path) }

  # 좋은 예(좀 더 가독성이 높은)
  Array(paths).each { |path| do_something(path) }
  ```

* <a name="ranges-or-between"></a>
  복잡한 비교논리를 사용하는 것 대신에 가능하면 범위나 `Comparable#between?`을
  사용하라.
<sup>[[link](#ranges-or-between)]</sup>

  ```Ruby
  # 나쁜 예
  do_something if x >= 1000 && x <= 2000

  # 좋은 예
  do_something if (1000..2000).include?(x)

  # 좋은 예
  do_something if x.between?(1000, 2000)
  ```

* <a name="predicate-methods"></a>
  `==`로 비교하기 보다 서술형 메소드(predicate methods)를 사용하는 것이 더 좋다.
  숫자 비교는 괜찮다.
<sup>[[link](#predicate-methods)]</sup>

  ```Ruby
  # 나쁜 예
  if x % 2 == 0
  end

  if x % 2 == 1
  end

  if x == nil
  end

  # 좋은 예
  if x.even?
  end

  if x.odd?
  end

  if x.nil?
  end

  if x.zero?
  end

  if x == 0
  end
  ```

* <a name="no-non-nil-checks"></a>
  boolean 값을 다룰 때가 아니면, 명시적으로 '`nil`이 아닌 것'을 체크하는 것을
  피하라.
<sup>[[link](#no-non-nil-checks)]</sup>

    ```ruby
    # 나쁜 예
    do_something if !something.nil?
    do_something if something != nil

    # 좋은 예
    do_something if something

    # 좋은 예 - boolean을 다룸
    def value_set?
      !@some_boolean.nil?
    end
    ```

* <a name="no-BEGIN-blocks"></a>
  `BEGIN` 블록 사용을 피하라.
<sup>[[link](#no-BEGIN-blocks)]</sup>

* <a name="no-END-blocks"></a>
  `END` 블록 사용을 피하라. 차라리 `Kernel#at_exit`를 써라.
<sup>[[link](#no-END-blocks)]</sup>

  ```ruby
  # 나쁜 예
  END { puts 'Goodbye!' }

  # 좋은 예
  at_exit { puts 'Goodbye!' }
  ```

* <a name="no-flip-flops"></a>
  flip-flop 사용을 피하라.
<sup>[[link](#no-flip-flops)]</sup>

* <a name="no-nested-conditionals"></a>
  제어문에서 중첩된 조건문은 피하라.
<sup>[[link](#no-nested-conditionals)]</sup>

  유효하지 않은 데이터가 들어갈 수도 있는 경우, 보호 구문을 권장한다. 보호
  구문은 함수에서 가능한 한 빨리 탈출할 수 있게 하는 함수 제일 처음에 있는
  조건문을 말한다.

  ```Ruby
  # 나쁜 예
  def compute_thing(thing)
    if thing[:foo]
      update_with_bar(thing)
      if thing[:foo][:bar]
        partial_compute(thing)
      else
        re_compute(thing)
      end
    end
  end

  # 좋은 예
  def compute_thing(thing)
    return unless thing[:foo]
    update_with_bar(thing[:foo])
    return re_compute(thing) unless thing[:foo][:bar]
    partial_compute(thing)
  end
  ```

  반복문 내에서는 조건문 블록 대신에 `next`를 선호한다.

  ```Ruby
  # 나쁜 예
  [0, 1, 2, 3].each do |item|
    if item > 1
      puts item
    end
  end

  # 좋은 예
  [0, 1, 2, 3].each do |item|
    next unless item > 1
    puts item
  end
  ```

* <a name="map-find-select-reduce-size"></a>
  `collect`보다는 `map`을, `detect`보다는 `find`를, `find_all`보다는 `select`를,
  `inject`보다는 `reduce`를, `length`보다는 `size`를 권장한다. 이것이 무리한
  요구는 아니다. 다른 alias를 써서 가독성이 좋아진다면, 그것도 괜찮다. 메소드의
  시적인 표현은 Smalltalk 언어로 부터 물려받은 것으로, 일반적인 다른 프로그래밍
  언어와는 다르다. `select`를 사용하는 이유는 `reject`와 함께 쓰일 때
  `find_all`보다 좀 더 잘 어울리고 이름 자체가 충분한 설명이 되기 때문이다.
<sup>[[link](#map-find-select-reduce-size)]</sup>

* <a name="count-vs-size"></a>
  `size`를 대신해서 `count`를 쓰지 마라. `Array`외의 `Enumerable`객체들은
  크기를 결정하기 위해 모든 콜렉션을 반복한다.
<sup>[[link](#count-vs-size)]</sup>

  ```Ruby
  # 나쁜 예
  some_hash.count

  # 좋은 예
  some_hash.size
  ```

* <a name="flat-map"></a>
  `map` + `flatten`의 조합을 사용하는 것 대신 `flat_map`을 사용하라. 이것은
  2차원 이상의 배열에는 적용되지는 않는다. 다시 말해서,
  `users.first.songs == ['a', ['b','c']]`의 경우는 `flat_map`보다는
  `map + flatten`를 사용하라. `flat_map`은 1차원의 배열만 1차원으로 만드는 반면
  `flatten`은 모든 것을 1차원 배열로 만든다.
<sup>[[link](#flat-map)]</sup>

  ```Ruby
  # 나쁜 예
  all_songs = users.map(&:songs).flatten.uniq

  # 좋은 예
  all_songs = users.flat_map(&:songs).uniq
  ```

* <a name="reverse-each"></a>
  `reverse.each`보다는 `reverse_each`를 써라. `reverse_each`는 새로운 배열을
  할당하지 않는다는 장점이 있다.
<sup>[[link](#reverse-each)]</sup>

  ```Ruby
  # 나쁜 예
  array.reverse.each { ... }

  # 좋은 예
  array.reverse_each { ... }
  ```

## 네이밍

> 프로그래밍에서 정말 어려운 것은 캐시무효화와 이름 짓기뿐이다. <br/>
> -- Phil Karlton

* <a name="english-identifiers"></a>
  식별자는 영어로 쓴다.
<sup>[[link](#english-identifiers)]</sup>

  ```Ruby
  # 나쁜 예 - ascii 문자가 아닌 식별자
  заплата = 1_000

  # 나쁜 예 - 식별자가 (키릴문자 대신에)라틴어 문자로 적힌 불가리어 단어다.
  zaplata = 1_000

  # 좋은 예
  salary = 1_000
  ```

* <a name="snake-case-symbols-methods-vars"></a>
  심볼,메소드,변수에 대해 `snake_case`를 써라.
<sup>[[link](#snake-case-symbols-methods-vars)]</sup>

  ```Ruby
  # 나쁜 예
  :'some symbol'
  :SomeSymbol
  :someSymbol

  someVar = 5

  def someMethod
    ...
  end

  def SomeMethod
   ...
  end

  # 좋은 예
  :some_symbol

  def some_method
    ...
  end
  ```

* <a name="camelcase-classes"></a>
  클래스와 모듈에 대해서는 `CamelCase`(카멜표기)를 사용하라.
  (HTTP,RFC,XML와 같은 약어는 대문자로 유지하라)
<sup>[[link](#camelcase-classes)]</sup>

  ```Ruby
  # 나쁜 예
  class Someclass
    ...
  end

  class Some_Class
    ...
  end

  class SomeXml
    ...
  end

  # 좋은 예
  class SomeClass
    ...
  end

  class SomeXML
    ...
  end
  ```

* <a name="snake-case-files"></a>
  파일 이름은 `snake_case`로 써라.
  예. `hello_world.rb`
<sup>[[link](#snake-case-files)]</sup>

* <a name="snake-case-dirs"></a>
  디렉토리 이름은 `snake_case`로 써라.
  예. `lib/hello_world/hello_world.rb`
<sup>[[link](#snake-case-dirs)]</sup>

* <a name="one-class-per-file"></a>
  되도록이면 하나의 소스파일은 하나의 클래스/모듈을 갖도록 하라. 파일명은
  `CamelCase`로 적힌 클래스/모듈이름을 `snake_case`로 바꾼 것으로 하라.
<sup>[[link](#one-class-per-file)]</sup>

* <a name="screaming-snake-case"></a>
  다른 상수들은 `SCREAMING_SNAKE_CASE`을 사용하라.
<sup>[[link](#screaming-snake-case)]</sup>

  ```Ruby
  # 나쁜 예
  SomeConst = 5

  # 좋은 예
  SOME_CONST = 5
  ```

* <a name="bool-methods-qmark"></a>
  서술형 메소드(boolean 값을 반환하는 메소드)의 이름은 꼭 물음표로 끝나야 한다.
  (예를 들어 `Array#empty?`) 메소드가 boolean 값을 반환하는게 아니라면, 물음표로
  끝나선 안 된다.
<sup>[[link](#bool-methods-qmark)]</sup>

* <a name="dangerous-method-bang"></a>
  잠재적으로 *위험한* 메소드의(예를 들어, `self`나 인수를 수정하는 메소드와
  `exit!`(finalizer를 실행하지 않음) 등) 이름은 *위험한* 메소드의 안전한 버전이
  존재할 때는 느낌표로 끝낸다.
<sup>[[link](#dangerous-method-bang)]</sup>

  ```Ruby
  # 나쁜 예 - 'safe'한 메소드가 없다.
  class Person
    def update!
    end
  end

  # 좋은 예
  class Person
    def update
    end
  end

  # 좋은 예
  class Person
    def update!
    end

    def update
    end
  end
  ```

* <a name="safe-because-unsafe"></a>
  가능하면 bang(위험한) 관점에서 non-bang(안전한)메소드를 정의하라.
<sup>[[link](#safe-because-unsafe)]</sup>

  ```Ruby
  class Array
    def flatten_once!
      res = []

      each do |e|
        [*e].each { |f| res << f }
      end

      replace(res)
    end

    def flatten_once
      dup.flatten_once!
    end
  end
  ```

* <a name="reduce-blocks"></a>
  짧은 블록과 함께 `reduce`를 쓸 때에는,
  인수 이름을 `|a, e|`로 하라.(accumulator, element)
<sup>[[link](#reduce-blocks)]</sup>

* <a name="other-param"></a>
  이항 연산자를 정의할 때에는, 매개변수 이름을 `other`로 하라.
  (`<<`와 `[]`는 의미가 달라지므로 이 규칙에서 제외된다.)
<sup>[[link](#other-param)]</sup>

  ```Ruby
  def +(other)
    # body omitted
  end
  ```

## 주석

> 좋은 코드는 가장 좋은 문서이다. 주석을 추가하려고 할 때 스스로에게 물어보라.
> "이 주석이 필요 없으려면 코드를 어떻게 만들면 될까?" 코드를 더 잘 작성하여
> 문서를 명확하게 하자. <br>
> -- Steve McConnell

* <a name="no-comments"></a>
  스스로 문서화가 되는 코드를 작성하고 이 단락은 무시하도록 하자. 진짜로!
<sup>[[link](#no-comments)]</sup>

* <a name="english-comments"></a>
  주석은 영어로 작성한다.
<sup>[[link](#english-comments)]</sup>

* <a name="hash-space"></a>
  `#`뒤에 한 칸 뛰고 주석 내용을 작성한다.
<sup>[[link](#hash-space)]</sup>

* <a name="english-syntax"></a>
  한 단어 이상의 주석은 대문자 표기법과 구두점 규칙을 사용한다. 마침표 뒤에는
  [공백](http://en.wikipedia.org/wiki/Sentence_spacing)을 사용한다.
<sup>[[link](#english-syntax)]</sup>

* <a name="no-superfluous-comments"></a>
  불필요한 주석은 피한다.
<sup>[[link](#no-superfluous-comments)]</sup>

  ```Ruby
  # 나쁜 예
  counter += 1 # Increments counter by one.
  ```

* <a name="comment-upkeep"></a>
  주석은 최신 상태로 유지한다. 코드내용과 맞지 않은 주석은 없는 것이 낫다.
<sup>[[link](#comment-upkeep)]</sup>

> 좋은 주석은 좋은 유머이다. - 설명이 필요없다. <br/>
> -- Russ Olsen

* <a name="refactor-dont-comment"></a>
  나쁜 코드에 대해서 주석을 달지 마라. 코드가 스스로 설명할 수 있도록 리펙토링
  하라.(하거나 안 하거나 둘 중 하나다. 노력했다는 것은 없다. -- Yoda)
<sup>[[link](#refactor-dont-comment)]</sup>

### 주석 어노테이션

* <a name="annotate-above"></a>
  어노테이션은 관련된 코드 바로 위에 작성한다.
<sup>[[link](#annotate-above)]</sup>

* <a name="annotate-keywords"></a>
  어노테이션 키워드는 콜론과 공백 다음에 설명을 작성한다.
<sup>[[link](#annotate-keywords)]</sup>

* <a name="indent-annotations"></a>
  만약 설명이 여러 줄인 경우 다음 줄은 `#`을 쓰고 세 칸 들여쓰기 한다.(한 칸은
  일반적으로 하고, 두 칸은 들여쓰기 목적)
<sup>[[link](#indent-annotations)]</sup>

  ```Ruby
  def bar
    # FIXME: This has crashed occasionally since v3.2.1. It may
    #   be related to the BarBazUtil upgrade.
    baz(:quux)
  end
  ```

* <a name="rare-eol-annotations"></a>
  설명이 명확하지 않고 중복되는 경우 예외적으로 라인 뒤쪽에 어노테이션을
  작성한다.(규칙은 아님)
<sup>[[link](#rare-eol-annotations)]</sup>

  ```Ruby
  def bar
    sleep 100 # OPTIMIZE
  end
  ```

* <a name="todo"></a>
  `TODO`는 빠진 기능을 나중에 추가해야 할 때 사용한다.
<sup>[[link](#todo)]</sup>

* <a name="fixme"></a>
  `FIXME`는 코드가 깨져 고쳐야 할 때 사용한다.
<sup>[[link](#fixme)]</sup>

* <a name="optimize"></a>
  `OPTIMIZE`는 코드가 느리거나 비효율적이라서 성능상 문제가 생기는 경우에
  사용한다.
<sup>[[link](#optimize)]</sup>

* <a name="hack"></a>
  `HACK`은 코드에 냄새가 있는 것 같아 이야기해 보고 리팩토링이 필요한 경우
  사용한다.
<sup>[[link](#hack)]</sup>

* <a name="review"></a>
  `REVIEW`는 의도한 대로 동작하는지 확인해야 하는 경우에 사용한다. 예를 들어:
  `REVIEW: Are we sure this is how the client does X currently?`
<sup>[[link](#review)]</sup>

* <a name="document-annotations"></a>
  다른 어노테이션 키워드들은 필요에 따라 작성하고 `README` 같은 곳에 정리해둔다.
<sup>[[link](#document-annotations)]</sup>

## 클래스와 모듈

* <a name="consistent-classes"></a>
  클래스 정의는 일관된 구조를 사용한다.
<sup>[[link](#consistent-classes)]</sup>

  ```Ruby
  class Person
    # extend와 include가 먼저 나온다.
    extend SomeModule
    include AnotherModule

    # inner classes
    CustomErrorKlass = Class.new(StandardError)

    # 상수는 다음에 나온다.
    SOME_CONSTANT = 20

    # 그 뒤로 attribute 매크로가 온다.
    attr_reader :name

    # 다른 매크로들이 있다면 그 다음에 나온다.
    validates :name

    # public 클래스 메소드가 다음 줄에 온다.
    def self.some_method
    end

    # public 인스턴스 메소드가 따라서 나온다.
    def some_method
    end

    # protected와 private 메소드는 마지막 근처에 모아둔다.
    protected

    def some_protected_method
    end

    private

    def some_private_method
    end
  end
  ```

* <a name="file-classes"></a>
  한 줄 이상의 클래스는 클래스 안에 선언하지 않는다. 이런 경우에는 클래스 이름의
  폴더를 만들고 각각의 inner 클래스를 별도의 파일로 분리해 보는 것도 좋다.
<sup>[[link](#file-classes)]</sup>

  ```Ruby
  # 나쁜 예

  # foo.rb
  class Foo
    class Bar
      # 안에 30개의 메소드
    end

    class Car
      # 안에 20개의 메소드
    end

    # 안에 30개의 메소드
  end

  # 좋은 예

  # foo.rb
  class Foo
    # 안에 30개의 메소드
  end

  # foo/bar.rb
  class Foo
    class Bar
      # 안에 30개의 메소드
    end
  end

  # foo/car.rb
  class Foo
    class Car
      # 안에 20개의 메소드
    end
  end
  ```

* <a name="modules-vs-classes"></a>
  클래스 메소드만 가지는 클래스는 모듈로 선언하는 것이 더 좋다. 클래스는
  인스턴스를 생성해서 사용할 때만 사용한다.
<sup>[[link](#modules-vs-classes)]</sup>

  ```Ruby
  # 나쁜 예
  class SomeClass
    def self.some_method
      # body 생략
    end

    def self.some_other_method
    end
  end

  # 좋은 예
  module SomeModule
    module_function

    def some_method
      # body 생략
    end

    def some_other_method
    end
  end
  ```

* <a name="module-function"></a>
  모듈의 인스턴스 메소드를 클래스 메소드로 바꿀 때는 `extend self`보다는
  `module_function`을 더 선호한다.
<sup>[[link](#module-function)]</sup>

  ```Ruby
  # 나쁜 예
  module Utilities
    extend self

    def parse_something(string)
      # 여기에 뭔가
    end

    def other_utility_method(number, string)
      # 여기에 좀 더 뭔가
    end
  end

  # 좋은 예
  module Utilities
    module_function

    def parse_something(string)
      # 여기에 뭔가
    end

    def other_utility_method(number, string)
      # 여기에 좀 더 뭔가
    end
  end
  ```

* <a name="liskov"></a>
  클래스 계층을 디자인 할 때는 [리스코프 치환
  원칙](http://ko.wikipedia.org/wiki/리스코프_치환_원칙)에 따른다.
<sup>[[link](#liskov)]</sup>

* <a name="solid-design"></a>
  클래스는 가능한 한 [SOLID](http://ko.wikipedia.org/wiki/SOLID) 원칙을 따른다.
<sup>[[link](#solid-design)]</sup>

* <a name="define-to-s"></a>
  도메인 객체 클래스는 항상 적합한 `to_s` 메소드를 제공한다.
<sup>[[link](#define-to-s)]</sup>

  ```Ruby
  class Person
    attr_reader :first_name, :last_name

    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end

    def to_s
      "#{@first_name} #{@last_name}"
    end
  end
  ```

* <a name="attr_family"></a>
  특별한 일을 하지 않는 accesstor나 mutator는 `attr`류의 함수를 사용한다.
<sup>[[link](#attr_family)]</sup>

  ```Ruby
  # 나쁜 예
  class Person
    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end

    def first_name
      @first_name
    end

    def last_name
      @last_name
    end
  end

  # 좋은 예
  class Person
    attr_reader :first_name, :last_name

    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end
  end
  ```

* <a name="attr"></a>
  그냥 `attr`을 사용하지 말고 `attr_reader`나 `attr_accessor`을 사용한다.
<sup>[[link](#attr)]</sup>

  ```Ruby
  # 나쁜 예 - accessor를 하나 생성(루비 1.9에서 비추천됨)
  attr :something, true
  attr :one, :two, :three # attr_reader 처럼 동작한다.

  # 좋은 예
  attr_accessor :something
  attr_reader :one, :two, :three
  ```

* <a name="struct-new"></a>
  특별하지 않은 accessor와 생성자, 비교 연산자를 가지는 클래스는 `Struct.new`를
  사용해 보는 것도 좋다.
<sup>[[link](#struct-new)]</sup>

  ```Ruby
  # 좋은 예
  class Person
    attr_accessor :first_name, :last_name

    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end
  end

  # 더 좋은 예
  Person = Struct.new(:first_name, :last_name) do
  end
  ````

* <a name="no-extend-struct-new"></a>
  `Struct.new`에 의해 초기화된 인스턴스를 확장하지 않는다. `Struct.new`를
  확장하는 것은 쓸데없는 클래스 계층을 하나 더 만드는 것이고 만약 그 파일이
  여러 번 require 된다면 이상한 에러가 날지도 모른다.
<sup>[[link](#no-extend-struct-new)]</sup>

  ```Ruby
  # 나쁜 예
  class Person < Struct.new(:first_name, :last_name)
  end

  # 좋은 예
  Person = Struct.new(:first_name, :last_name)
  ````

* <a name="factory-methods"></a>
  어떤 클래스의 인스턴스를 생성할 때 좀 더 명확한 방법을 제공하는 팩토리
  메소드를 추가하는 것을 고려해보자.
<sup>[[link](#factory-methods)]</sup>

  ```Ruby
  class Person
    def self.create(options_hash)
      # body 생략
    end
  end
  ```

* <a name="duck-typing"></a>
  상속보다는 [duck-typing](http://ko.wikipedia.org/wiki/덕_타이핑)을 쓰는 것이 더 좋다.
<sup>[[link](#duck-typing)]</sup>

  ```Ruby
  # 나쁜 예
  class Animal
    # abstract 메소드
    def speak
    end
  end

  # superclass를 상속
  class Duck < Animal
    def speak
      puts 'Quack! Quack'
    end
  end

  # superclass를 상속
  class Dog < Animal
    def speak
      puts 'Bau! Bau!'
    end
  end

  # good
  class Duck
    def speak
      puts 'Quack! Quack'
    end
  end

  class Dog
    def speak
      puts 'Bau! Bau!'
    end
  end
  ```

* <a name="no-class-vars"></a>
  클래스 변수(`@@`)는 상속을 할 때 좋지 않기 때문에 사용을 피한다.
<sup>[[link](#no-class-vars)]</sup>

  ```Ruby
  class Parent
    @@class_var = 'parent'

    def self.print_class_var
      puts @@class_var
    end
  end

  class Child < Parent
    @@class_var = 'child'
  end

  Parent.print_class_var # => "child"가 출력된다.
  ```

  상속 계층에 있는 모든 클래스는 하나의 클래스 변수를 공유한다. 클래스
  변수보다는 클래스 인스턴스 변수를 사용하는 것이 더 좋다.

* <a name="visibility"></a>
  메소드에는 사용되는 목적에 맞는 접근 권한(`private`, `protected`)을 부여한다.
  전부 다 기본 접근 권한인 `public` 상태로 두지 마라. 우리는 지금 *파이썬*이
  아닌 *루비* 코딩을 하고 있다.(역자주 파이썬은 명시적인 private 메소드가 없다.)
<sup>[[link](#visibility)]</sup>

* <a name="indent-public-private-protected"></a>
  `public`, `protected`, `private`은 메소드 정의와 같은 레벨로 들여쓰기 한다.
  접근 제한자 아래로 모든 메소드들이 적용된다는 것을 명확하게 하기 위해 접근
  제한자 위, 아래로 빈 줄을 넣어 준다.
<sup>[[link](#indent-public-private-protected)]</sup>

  ```Ruby
  class SomeClass
    def public_method
      # ...
    end

    private

    def private_method
      # ...
    end

    def another_private_method
      # ...
    end
  end
  ```

* <a name="def-self-singletons"></a>
  싱글톤 메소드를 정의할 때는 `def self.method`를 사용한다. 이렇게 하면
  클래스명이 반복되지 않기 때문에 클래스명 변경으로 리펙토링할 때 좀 더 쉬워진다.
<sup>[[link](#def-self-singletons)]</sup>

  ```Ruby
  class TestClass
    # 나쁜 예
    def TestClass.some_method
      # body 생략
    end

    # 좋은 예
    def self.some_other_method
      # body 생략
    end

    # 싱글톤 메소드가 많은 경우 아래와 같이
    # 사용하면 편리하다.
    class << self
      def first_method
        # body 생략
      end

      def second_method_etc
        # body 생략
      end
    end
  end
  ```

* <a name="alias-method-lexically"></a>
  엘리아스 메소드가 문법적 클래스의 범위에 있고 이 문맥에서 `self`의 범위도
  문법적이고 alias의 접근이 명시적이지 않을 때의 실행시나 서브 클래스에서
  변경되지 않는 것을 유저가 명확히 이해할 때는`alias`를 사용한다.
<sup>[[link](#alias-method-lexically)]</sup>

  ```Ruby
  class Westerner
    def first_name
      @names.first
    end

    alias given_name first_name
  end
  ```

  `alias`가 `def`같은 키워드이기 때문에, 심볼이나 문자열 대신, 생 인자를
  사용한다. 다시 말하면, `alias :foo :bar`대신 `alias foo bar`를 사용한다.

  또 루비가 어떻게 alias와 상속을 처리하는지 알아야한다: alias는
  alias가 선언되었을 때의 메소드를 참조한다. alias는 동적으로 전달되지
  않는다.

  ```Ruby
  class Fugitive < Westerner
    def first_name
      'Nobody'
    end
  end
  ```

  이 예제에서, `Fugitive#given_name`는 `Fugitive#first_name`가 아니라
  여전히 원래의 `Westerner#first_name` 메소드를 호출한다.
  `Fugitive#given_name`의 행동으로 오버라이드 하려면 파생된 클래스에서도
  재정의 해주어야 한다.

  ```Ruby
  class Fugitive < Westerner
    def first_name
      'Nobody'
    end

    alias given_name first_name
  end
  ```

* <a name="alias-method"></a>
  모듈, 클래스, 싱글턴 클래스를 실행중에 alias 할 때는 항상 `alias_method`
  를 사용한다. 이런 경우에 `alias`의 문법적 범위로는 결과를 예측 하기 힘들다.
<sup>[[link](#alias-method)]</sup>

  ```Ruby
  module Mononymous
    def self.included(other)
      other.class_eval { alias_method :full_name, :given_name }
    end
  end

  class Sting < Westerner
    include Mononymous
  end
  ```

## 예외

* <a name="fail-method"></a>
  예외를 발생시킬 때는 `fail` 메소드를 사용한다. 예외를 잡고 다시 예외를
  발생시키는 경우에만 `raise`를 사용한다.(왜냐하면 여기에서는 실패한 것이
  아니고 명시적으로 예외를 발생시키는 것이기 때문이다.)
<sup>[[link](#fail-method)]</sup>

  ```Ruby
  begin
    fail 'Oops'
  rescue => error
    raise if error.message != 'Oops'
  end
  ```

* <a name="no-explicit-runtimeerror"></a>
  `fail/raise`를 사용할 때 `RuntimeError`를 첫 번째 인수로 하는 메소드는 사용하지
  않는다.
<sup>[[link](#no-explicit-runtimeerror)]</sup>

  ```Ruby
  # 나쁜 예
  fail RuntimeError, 'message'

  # 좋은 예 - 기본적으로 RuntimeError가 발생한다.
  fail 'message'
  ```

* <a name="exception-class-messages"></a>
  예외 인스턴스를 생성해서 `fail/raise`를 하는 것보다 `fail/raise`의 첫 번째
  인수에 예외 클래스를 넘기는 메소드를 사용하는 것이 더 좋다.
<sup>[[link](#exception-class-messages)]</sup>

  ```Ruby
  # 나쁜 예
  fail SomeException.new('message')
  # `fail SomeException.new('message'), backtrace` 이렇게 쓸 수 는 없다.

  # 좋은 예
  fail SomeException, 'message'
  # `fail SomeException, 'message', backtrace` 일관성 있는 방법이다.
  ```

* <a name="no-return-ensure"></a>
  `ensure` 블록에서 리턴하지 마라. `ensure` 안에서 명시적으로 리턴을 하면 예외가
  발생하기 전에 리턴이 되고 예외가 발생하지 않은 것처럼 동작할 것이다.
<sup>[[link](#no-return-ensure)]</sup>

  ```Ruby
  def foo
    fail
  ensure
    return '매우 안좋은 생각'
  end
  ```

* <a name="begin-implicit"></a>
  가능하면 *함축적인 begin 블록*을 사용한다.
<sup>[[link](#begin-implicit)]</sup>

  ```Ruby
  # 나쁜 예
  def foo
    begin
      # 메인 로직은 여기에
    rescue
      # 실패처리는 여기에
    end
  end

  # 좋은 예
  def foo
    # 메인 로직은 여기에
  rescue
    # 실패처리는 여기에
  end
  ```

* <a name="contingency-methods"></a>
  `begin` 블록이 많아지는 것을 줄이기 위해서 *contingency 메소드*를 사용한다.
  (용어는 Avdi Grimm가 만들었다).
<sup>[[link](#contingency-methods)]</sup>

  ```Ruby
  # 나쁜 예
  begin
    something_that_might_fail
  rescue IOError
    # IOError 처리
  end

  begin
    something_else_that_might_fail
  rescue IOError
    # IOError 처리
  end

  # 좋은 예
  def with_io_error_handling
     yield
  rescue IOError
    # IOError 처리
  end

  with_io_error_handling { something_that_might_fail }

  with_io_error_handling { something_else_that_might_fail }
  ```

* <a name="dont-hide-exceptions"></a>
  예외를 먹지 마라.
<sup>[[link](#dont-hide-exceptions)]</sup>

  ```Ruby
  # 나쁜 예
  begin
    # 여기에서 예외가 발생한다.
  rescue SomeError
    # rescue 절에서 아무것도 하지 않는다.
  end

  # 나쁜 예
  do_something rescue nil
  ```

* <a name="no-rescue-modifiers"></a>
  `rescue`를 사용할 때 구문 변경자 사용을 피한다.
<sup>[[link](#no-rescue-modifiers)]</sup>

  ```Ruby
  # 나쁜 예 - 여기서 StandardError 예외와 StandardError를 상속한 예외들을 잡는다.
  read_file rescue handle_error($!)

  # 좋은 예 - 여기서 Error::ENOENT 예외와 Error:ENOENT를 상속한 예외들만 잡는다.
  def foo
    read_file
  rescue Errno::ENOENT => ex
    handle_error(ex)
  end
  ```

* <a name="no-exceptional-flows"></a>
  예외를 흐름 제어에 사용하지 마라.
<sup>[[link](#no-exceptional-flows)]</sup>

  ```Ruby
  # 나쁜 예
  begin
    n / d
  rescue ZeroDivisionError
    puts 'Cannot divide by 0!'
  end

  # 좋은 예
  if d.zero?
    puts 'Cannot divide by 0!'
  else
    n / d
  end
  ```

* <a name="no-blind-rescues"></a>
  `Exception`을 rescue 하는 것을 피한다. 그렇게 하면 `exit`를 잡기 위해서
  프로세스에 `kill -9`가 필요하다.(역자주 Exception은 루비의 최상위 예외
  클래스인데 Interrupt나 SyntaxError 등도 포함된다. Interrupt를 rescue 하면
  Ctrl+C로 프로그램을 종료할 수 없다. `kill -9`로는 종료가 가능하다. 또
  eval 등으로 동적으로 코드를 로드할 때 발생할지도 모르는 SyntaxError도 예상치
  못하게 잡게 되어 적절한 처리를 못할지도 모른다.
  http://stackoverflow.com/questions/10048173/why-is-it-bad-style-to-rescue-exception-e-in-ruby)
<sup>[[link](#no-blind-rescues)]</sup>

  ```Ruby
  # 나쁜 예
  begin
    # exit를 호출하면 kill 시그널이 잡힌다.(kill -9는 제외)
    exit
  rescue Exception
    puts "you didn't really want to exit, right?"
    # 예외 처리
  end

  # 좋은 예
  begin
    # 많은 개발자들의 예상하는 Exception 대신 StandardError를 잡게된다.
  rescue => e
    # 예외 처리
  end

  # 이것도 좋은 예
  begin
    # 여기서 예외 발생

  rescue StandardError => e
    # 예외 처리
  end
  ```

* <a name="exception-ordering"></a>
  rescue를 이어서 사용할 때는 더 구체적인 예외부터 순서대로 작성한다. 그렇지
  않으면 rescue에 안 걸릴 수 있다.
<sup>[[link](#exception-ordering)]</sup>

  ```Ruby
  # 나쁜 예
  begin
    # 코드
  rescue Exception => e
    # 예외 처리
  rescue StandardError => e
    # 여기는 실행되지 않는다.
  end

  # 좋은 예
  begin
    # 코드
  rescue StandardError => e
    # 예외 처리
  rescue Exception => e
    # 에외 처리
  end
  ```

* <a name="release-resources"></a>
  `ensure` 블록에서 사용했던 자원을 모두 반환한다.
<sup>[[link](#release-resources)]</sup>

  ```Ruby
  f = File.open('testfile')
  begin
    # .. process
  rescue
    # .. handle error
  ensure
    f.close unless f.nil?
  end
  ```

* <a name="auto-release-resources"></a>
  가능한 한 자동으로 리소스를 정리해주는 버전의 메소드를 사용한다.
<sup>[[link](#auto-release-resources)]</sup>

  ```Ruby
  # 나쁜 예 - 파일 서술자를 명시적으로 닫아야 함
  f = File.open('testfile')
    # ...
  f.close

  # 좋은 예 - 파일 서술자가 자동으로 닫힘
  File.open('testfile') do |f|
    # ...
  end
  ```

* <a name="standard-exceptions"></a>
  표준 라이브러리에 있는 예외보다는 새로운 예외 클래스를 만들어 사용하는 것이
  더 좋다.
<sup>[[link](#standard-exceptions)]</sup>

## 컬렉션

* <a name="literal-array-hash"></a>
  배열과 해시 생성 노테이션을 사용한다.(생성자에 매개변수를 전달하지 않는다면)
<sup>[[link](#literal-array-hash)]</sup>

  ```Ruby
  # 나쁜 예
  arr = Array.new
  hash = Hash.new

  # 좋은 예
  arr = []
  hash = {}
  ```

* <a name="percent-w"></a>
  단어에 대한 배열이 필요할 때는 `%w` 리터럴을 사용한다.(공백이나 특수문자가
  없는 비어 있지 않은 문자열) 두 개 이상의 항목을 가질 때만 이 규칙을 적용한다.
<sup>[[link](#percent-w)]</sup>

  ```Ruby
  # 나쁜 예
  STATES = ['draft', 'open', 'closed']

  # 좋은 예
  STATES = %w(draft open closed)
  ```

* <a name="percent-i"></a>
  심볼에 대한 배열이 필요할 때는 `%i` 리터럴을 사용한다.(루비 1.9와 호환성이
  필요 없는 경우) 두 개 이상의 항목을 가질 때만 이 규칙을 적용한다.
<sup>[[link](#percent-i)]</sup>

  ```Ruby
  # 나쁜 예
  STATES = [:draft, :open, :closed]

  # 좋은 예
  STATES = %i(draft open closed)
  ```

* <a name="no-trailing-array-commas"></a>
  배열이나 해시의 마지막 항목에 콤마를 사용하지 마라. 특히 항목이 여러 줄로
  나뉘어 있는 경우가 아니라면 더 사용하지 마라.
<sup>[[link](#no-trailing-array-commas)]</sup>

  ```Ruby
  # 나쁜 예 - 항목을 이동/추가/삭제 하는 것이 쉽지만 사용하지 마라.
  VALUES = [
             1001,
             2020,
             3333,
           ]

  # 나쁜 예
  VALUES = [1001, 2020, 3333, ]

  # 좋은 예
  VALUES = [1001, 2020, 3333]
  ```

* <a name="no-gappy-arrays"></a>
  큰 빈 공간을 가진 배열을 생성하지 마라.
<sup>[[link](#no-gappy-arrays)]</sup>

  ```Ruby
  arr = []
  arr[100] = 1 # 많은 nil 값을 가지는 배열이 생성되었다.
  ```

* <a name="first-and-last"></a>
  배열의 첫 번째나 마지막 항목에 접근할 때 `[0]` 또는 `[-1]` 대신 `first`나
  `last`를 사용하라.
<sup>[[link](#first-and-last)]</sup>

* <a name="set-vs-array"></a>
  유일한 항목을 다룰 때는 `Array` 대신 `Set`을 사용하라. `Set`은 중복이 없고
  정렬되지 않은 항목을 다룰 수 있는 컬렉션 구현체이다. `Set`은 배열의 직관적인
  동작들과 `Hash`의 빠른 조회 특성을 모두 가지고 있다.
<sup>[[link](#set-vs-array)]</sup>

* <a name="symbols-as-keys"></a>
  해시 키는 문자열 보다 심볼을 사용하는 것이 좋다.
<sup>[[link](#symbols-as-keys)]</sup>

  ```Ruby
  # 나쁜 예
  hash = { 'one' => 1, 'two' => 2, 'three' => 3 }

  # 좋은 예
  hash = { one: 1, two: 2, three: 3 }
  ```

* <a name="no-mutable-keys"></a>
  변경 가능한 객체를 해시 키로 사용하지 마라.
<sup>[[link](#no-mutable-keys)]</sup>

* <a name="hash-literals"></a>
  해시 키가 심볼인 경우 루비 1.9 해시 리터럴을 사용하라.
<sup>[[link](#hash-literals)]</sup>

  ```Ruby
  # 나쁜 예
  hash = { :one => 1, :two => 2, :three => 3 }

  # 좋은 예
  hash = { one: 1, two: 2, three: 3 }
  ```

* <a name="no-mixed-hash-syntaces"></a>
  하나의 해시에 루비 1.9 해시 문법과 기존 해시 문법을 섞어 쓰지 마라. 심볼이
  아닌 키가 포함되어 있다면 이전의 해시 문법을 사용하라.
<sup>[[link](#no-mixed-hash-syntaces)]</sup>

  ```Ruby
  # 나쁜 예
  { a: 1, 'b' => 2 }

  # 좋은 예
  { :a => 1, 'b' => 2 }
  ```

* <a name="hash-key"></a>
  `Hash#has_key?` 대신 `Hash#key?`, `Hash#has_value?` 대신 `Hash#value?`를
  사용하라. Matz에 의하면 긴 문법은 폐지하는 것을 논의 중이다.
  [here](http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-core/43765)
<sup>[[link](#hash-key)]</sup>

  ```Ruby
  # 나쁜 예
  hash.has_key?(:test)
  hash.has_value?(value)

  # 좋은 예
  hash.key?(:test)
  hash.value?(value)
  ```

* <a name="hash-fetch"></a>
  해시 키로 명확히 있어야 하는 값을 다룰 때에는 `Hash#fetch`를 사용하라.
<sup>[[link](#hash-fetch)]</sup>

  ```Ruby
  heroes = { batman: 'Bruce Wayne', superman: 'Clark Kent' }
  # 나쁜 예 - 만약 실수가 있다고 한다면 알아채지 못할 수 있다.
  heroes[:batman] # => "Bruce Wayne"
  heroes[:supermann] # => nil

  # 좋은 예 - 문제를 명확하게 하기 위해서 KeyError 예외가 발생한다.
  heroes.fetch(:supermann)
  ```

* <a name="hash-fetch-defaults"></a>
  해시 값에 기본 값을 사용하는 경우 커스텀 로직보다는 `Hash#fetch`를 사용하라.
<sup>[[link](#hash-fetch-defaults)]</sup>

  ```Ruby
  batman = { name: 'Bruce Wayne', is_evil: false }

  # 나쁜 예 - 그냥 || 연산자를 사용한다면 예상하지 못한 결과를 얻을 수도 있다.
  batman[:is_evil] || true # => true

  # 좋은 예 - 제대로 된 false 값을 얻을 수 있다.
  batman.fetch(:is_evil, true) # => false
  ```

* <a name="use-hash-blocks"></a>
  `Hash#fetch` 기본 값 대신 블록을 사용하는 것이 좋다.
<sup>[[link](#use-hash-blocks)]</sup>

  ```Ruby
  batman = { name: 'Bruce Wayne' }

  # 나쁜 예 - 만약 기본 값을 사용하는 경우, 함수가 먼저 실행이 되므로
  # 여러 번 실행되는 경우 프로그램이 느려질 수 있다.
  batman.fetch(:powers, get_batman_powers) # get_batman_powers은 오래 걸리는 함수이다.

  # good - 블록은 나중에 실행된다. 그래서 KeyError 예외가 발생하는 경우만 실행된다.
  batman.fetch(:powers) { get_batman_powers }
  ```

* <a name="hash-values-at"></a>
  해시에서 여러 개의 값을 가져오고 싶다면 `Hash#values_at`을 사용하라.
<sup>[[link](#hash-values-at)]</sup>

  ```Ruby
  # 나쁜 예
  email = data['email']
  username = data['nickname']

  # 좋은 예
  email, username = data.values_at('email', 'nickname')
  ```

* <a name="ordered-hashes"></a>
  Ruby 1.9의 해시는 순서가 보장된다는 것을 기억하자.
<sup>[[link](#ordered-hashes)]</sup>

* <a name="no-modifying-collections"></a>
  컬렉션을 순회하는 동안 컬렉션을 수정하지 마라.
<sup>[[link](#no-modifying-collections)]</sup>

* <a name="accessing-elements-directly"></a>
  컬렉션의 요소에 접근할 때는, 가능한 한 리더 메소드의 다른 형식을 사용해 `[n]`을
  통한 직접 접근을 피한다. 이는 `nil`에 `[]`를 호출하는 것을 방지한다.
<sup>[[link](#accessing-elements-directly)]</sup>

  ```Ruby
  # 나쁜 예
  Regexp.last_match[1]

  # 좋은 예
  Regexp.last_match(1)
  ```

* <a name="provide-alternate-accessor-to-collections"></a>
  컬렉션의 접근자를 만들 때에는, 다른 형식을 제공해 사용자가 컬렉션의 요소에
  접근하기 전에 `nil`을 체크하지 않도록 한다.
<sup>[[link](#provide-alternate-accessor-to-collections)]</sup>

  ```Ruby
  # 나쁜 예
  def awesome_things
    @awesome_things
  end

  # 좋은 예
  def awesome_things(index = nil)
    if index && @awesome_things
      @awesome_things[index]
    else
      @awesome_things
    end
  end
  ```

## 문자열

* <a name="string-interpolation"></a>
  문자열을 합치는 것보다 포맷팅이나 문자열 삽입을 사용하는 것이 더 좋다.
<sup>[[link](#string-interpolation)]</sup>

  ```Ruby
  # 나쁜 예
  email_with_name = user.name + ' <' + user.email + '>'

  # 좋은 예
  email_with_name = "#{user.name} <#{user.email}>"

  # 좋은 예
  email_with_name = format('%s <%s>', user.name, user.email)
  ```

* <a name="pad-string-interpolation"></a>
  문자열 삽입 코드에 공백을 양쪽으로 주는 것을 고려해본다. 문자열로부터 분리되어
  코드가 좀 더 명확해진다.
<sup>[[link](#pad-string-interpolation)]</sup>

  ```Ruby
  "#{ user.last_name }, #{ user.first_name }"
  ```

* <a name="consistent-string-literals"></a>
  일관된 문자열 따옴표 스타일을 선택한다. 루비 커뮤니티에는 많이 사용하는 두 가지
  스타일이 있는데 둘 다 괜찮다. 하나는 작은따옴표를 사용하는 방식(A 방식)이고
  다른 하나는 큰따옴표를 사용하는 방식이다(B 방식).
<sup>[[link](#consistent-string-literals)]</sup>

  * **(A 방식)**`\t`, `\n`, `'` 등의 특수문자나 문자열 삽입이 필요 없는 경우는
    작은따옴표를 사용하는 것이 좋다.

    ```Ruby
    # 나쁜 예
    name = "Bozhidar"

    # 좋은 예
    name = 'Bozhidar'
    ```

  * **(B 방식)** `"`를 포함하지 않거나 이스케이프된 특수문자를 제한할 필요가
    없는 경우에는 큰따옴표를 사용한다.

    ```Ruby
    # 나쁜 예
    name = 'Bozhidar'

    # 좋은 예
    name = "Bozhidar"
    ```

  두 번째 스타일이 루비 커뮤니티에서 조금 더 일반적이다. 하지만 이 가이드에서는
  첫 번째 스타일로 통일한다.

* <a name="no-character-literals"></a>
  문자 리터럴인 `?x`는 사용하지 않는다. 루비 1.9에서는 기본적으로 필요 없다.
  `?x`는 `'x'`로 해석된다.(문자 하나가 포함된 문자열)
<sup>[[link](#no-character-literals)]</sup>

  ```Ruby
  # 나쁜 예
  char = ?c

  # 좋은 예
  char = 'c'
  ```

* <a name="curlies-interpolate"></a>
  인스턴스 변수나 글로벌 변수를 가지고 문자열 삽입하는 경우 `{}`를 없애지 마라.
<sup>[[link](#curlies-interpolate)]</sup>

  ```Ruby
  class Person
    attr_reader :first_name, :last_name

    def initialize(first_name, last_name)
      @first_name = first_name
      @last_name = last_name
    end

    # 나쁜 예 - 동작하지만 어색함
    def to_s
      "#@first_name #@last_name"
    end

    # 좋은 예
    def to_s
      "#{@first_name} #{@last_name}"
    end
  end

  $global = 0
  # 나쁜 예
  puts "$global = #$global"

  # 좋은 예
  puts "$global = #{$global}"
  ```

* <a name="no-to-s"></a>
  문자열 삽입에 `Object#to_s`를 사용하지 마라. 이건 자동으로 호출된다.
<sup>[[link](#no-to-s)]</sup>

  ```Ruby
  # 나쁜 예
  message = "This is the #{result.to_s}."

  # 좋은 예
  message = "This is the #{result}."
  ```

* <a name="concat-strings"></a>
  큰 문자열 데이터가 필요할 때 `String#+`를 사용하지 마라. 대신 `String#<<`를
  사용하라. 문자열 자체를 변경하는 것이 새로운 문자열 객체를 생성하는
  `String#+`보다 항상 빠르다.
<sup>[[link](#concat-strings)]</sup>

  ```Ruby
  # 좋고 더 빠르다
  html = ''
  html << '<h1>Page title</h1>'

  paragraphs.each do |paragraph|
    html << "<p>#{paragraph}</p>"
  end
  ```

* <a name="dont-abuse-gsub"></a>
  다른 더 빠른 대안이 있을 때 `String#gsub`를 사용하지 마라.
<sup>[[link](#dont-abuse-gsub)]</sup>

    ```Ruby
    url = 'http://example.com'
    str = 'lisp-case-rules'

    # 나쁜 예
    url.gsub("http://", "https://")
    str.gsub("-", "_")

    # 좋은 예
    url.sub("http://", "https://")
    str.tr("-", "_")
    ```

* <a name="heredocs"></a>
  여러 줄로 heredoc을 사용할 때 공백 문자들이 유지된다는 사실을 잊지 말자. 특정
  기준을 정하고 나머지 불필요한 공백을 모두 없애는 것이 좋은 방법이다.
<sup>[[link](#heredocs)]</sup>

  ```Ruby
  code = <<-END.gsub(/^\s+\|/, '')
    |def test
    |  some_method
    |  other_method
    |end
  END
  # => "def test\n  some_method\n  other_method\nend\n"
  ```

## 정규식

> 어떤 사람들은 문제에 직면했을 때 다음과 같이 생각한다.<br/>
> "음 알았어, 난 정규식을 사용 할 거야." 이제 그들에게는 두개의 문제가 생겼다.<br/>
> -- Jamie Zawinski

* <a name="no-regexp-for-plaintext"></a>
  문자열 안에 단순한 텍스트를 찾는 것이라면 정규식을 사용하지 마라. `string['text']`
<sup>[[link](#no-regexp-for-plaintext)]</sup>

* <a name="regexp-string-index"></a>
  간단한 생성을 위해서 문자열 인덱스에 정규식을 바로 사용할 수 있다.
<sup>[[link](#regexp-string-index)]</sup>

  ```Ruby
  match = string[/regexp/]             # regexp과 매칭 되는 문자열을 가져온다.
  first_group = string[/text(grp)/, 1] # 정규식 그룹에 있는 값을 뽑아 낸다.
  string[/text (grp)/, 1] = 'replace'  # 정규식 그룹에 있는 값을 새로운 값으로 바꾼다.
  ```

* <a name="non-capturing-regexp"></a>
  정규식 그룹에서 값을 뽑아서 사용하지 않는다면 non-capturing 그룹을 사용하라.
<sup>[[link](#non-capturing-regexp)]</sup>

  ```Ruby
  /(first|second)/   # 나쁜 예
  /(?:first|second)/ # 좋은 예
  ```

* <a name="no-perl-regexp-last-matchers"></a>
  정규식 그룹에서 값을 사용할 때(`$1`, `$2` 등)처럼 암호문 같은 펄 변수
  기호를 사용하지 마라. 대신 `Regexp.last_match(n)`를 사용하라.
<sup>[[link](#no-perl-regexp-last-matchers)]</sup>

  ```Ruby
  /(regexp)/ =~ string
  ...

  # 나쁜 예
  process $1

  # 좋은 예
  process Regexp.last_match(1)
  ```

* <a name="no-numbered-regexes"></a>
  정규식 그룹에서 값을 사용할 때 숫자 형식은 안에 뭐가 있는지 알아보기 힘들기
  때문에 사용을 피한다. 대신 이름 기반의 정규식 그룹을 사용한다.
<sup>[[link](#no-numbered-regexes)]</sup>

  ```Ruby
  # 나쁜 예
  /(regexp)/ =~ string
  ...
  process Regexp.last_match(1)

  # 좋은 예
  /(?<meaningful_var>regexp)/ =~ string
  ...
  process meaningful_var
  ```

* <a name="limit-escapes"></a>
  문자들 중에 몇 개의 문자(`^`, `-`, `\`, `]`)만 특수문자로 다뤄지기 때문에
  `[]` 안에서 `.`을 이스케이프 하면 안 된다.
<sup>[[link](#limit-escapes)]</sup>

* <a name="caret-and-dollar-regexp"></a>
  줄의 시작과 끝을 다루는 `^`와 `$`는 문자열의 시작과 끝이 아니기 때문에
  주의해서 사용해야 한다. 만약 문자열 전체를 매칭하는 경우에는 `\A`와 `\z`를
  사용한다.(`/\n?\z/`와 같은 `\Z`와 혼동하지 않는다.)
<sup>[[link](#caret-and-dollar-regexp)]</sup>

  ```Ruby
  string = "some injection\nusername"
  string[/^username$/]   # 찾음
  string[/\Ausername\z/] # 못 찾음
  ```

* <a name="comment-regexes"></a>
  복잡한 정규식에 `x`를 사용한다. `x`를 사용하면 좀 더 읽기 좋아지고 유용한
  주석도 추가할 수 있다. 공백이 무시되는 것에 주의 한다.
<sup>[[link](#comment-regexes)]</sup>

  ```Ruby
  regexp = /
    start         # some text
    \s            # white space char
    (group)       # first group
    (?:alt1|alt2) # some alternation
    end
  /x
  ```

* <a name="gsub-blocks"></a>
  `sub`/`gsub`를 사용해서 복잡한 치환을 하는 경우 블록이나 해시를 사용할 수 있다.
<sup>[[link](#gsub-blocks)]</sup>

## 퍼센트 리터럴

* <a name="percent-q-shorthand"></a>
  큰따옴표와 문자열 삽입이 필요한 한 줄 문자열에만 `%()`(`%Q`의 짧은 표현)를
  사용한다. 여러 줄의 문자열은 heredoc을 사용한다.
<sup>[[link](#percent-q-shorthand)]</sup>

  ```Ruby
  # 나쁜 예(문자열 삽입이 없다)
  %(<div class="text">Some text</div>)
  # should be '<div class="text">Some text</div>'

  # 나쁜 예(큰따옴표가 없다)
  %(This is #{quality} style)
  # should be "This is #{quality} style"

  # 나쁜 예(여러 줄이다)
  %(<div>\n<span class="big">#{exclamation}</span>\n</div>)
  # should be a heredoc.

  # 좋은 예(한 줄에 큰따옴표와 문자열 삽입이 필요하다)
  %(<tr><td class="name">#{name}</td>)
  ```

* <a name="percent-q"></a>
  `'`와 `"`가 둘 다 들어있는 문자열이 아닌 경우에 `%q` 사용을 피한다. 일반 문자열
  리터럴이 더 읽기 좋고 이스케이프 할 문자가 많지 않은 경우에는 더 좋다.
<sup>[[link](#percent-q)]</sup>

  ```Ruby
  # 나쁜 예
  name = %q(Bruce Wayne)
  time = %q(8 o'clock)
  question = %q("What did you say?")

  # 좋은 예
  name = 'Bruce Wayne'
  time = "8 o'clock"
  question = '"What did you say?"'
  ```

* <a name="percent-r"></a>
  *적어도* 하나의 '/' 문자가 있는 경우에만 `%r`을 사용한다.
<sup>[[link](#percent-r)]</sup>

  ```Ruby
  # 나쁜 예
  %r(\s+)

  # 좋은 예
  %r(^/(.*)$)
  %r(^/blog/2011/(.*)$)
  ```

* <a name="percent-x"></a>
  실행하려는 명령어 안에 역따옴표가 있는 경우에만(흔하지는 않지만) `%x`를 사용한다.
<sup>[[link](#percent-x)]</sup>

  ```Ruby
  # 나쁜 예
  date = %x(date)

  # 좋은 예
  date = `date`
  echo = %x(echo `date`)
  ```

* <a name="percent-s"></a>
  `%s`의 사용은 피한다. 루비 커뮤니티에서는 공백이 포함된 심볼을 만들 때는
  `:"문자열"`을 사용하기로 결정한 것으로 보인다.
<sup>[[link](#percent-s)]</sup>

* <a name="percent-literal-braces"></a>
  `%r`을 빼고 모든 `%` 리터럴의 구분자는 `()`를 사용한다. 정규식에서는 괄호가
  나오는 경우가 흔하기 때문에 `%r`은 구분자로 `{`를 사용하는 것이 더 좋다.
<sup>[[link](#percent-literal-braces)]</sup>

  ```Ruby
  # 나쁜 예
  %w[one two three]
  %q{"Test's king!", John said.}

  # 좋은 예
  %w(one two three)
  %q("Test's king!", John said.)
  ```

## 메타프로그래밍

* <a name="no-needless-metaprogramming"></a>
  쓸데없는 메타프로그래밍은 하지 마라.
<sup>[[link](#no-needless-metaprogramming)]</sup>

* <a name="no-monkey-patching"></a>
  라이브러리를 작성할 때 코어 클래스를 망쳐놓지 마라.(거기에 Monkey-patch를
  하지 마라.)
<sup>[[link](#no-monkey-patching)]</sup>

* <a name="block-class-eval"></a>
  `class_eval` 폼 블록은 문자열 삽입 폼보다 더 좋다.
  - 문자열 삽입 폼을 사용할 때는 백트레이스를 위해서 항상 `__FILE__`과
    `__LINE__`을 써야 한다.
<sup>[[link](#block-class-eval)]</sup>

  ```ruby
  class_eval 'def use_relative_model_naming?; true; end', __FILE__, __LINE__
  ```

  - `define_method`가 `class_eval{ def ... }`보다 좋다.

* <a name="eval-comment-docs"></a>
  문자열 삽입과 함께 `class_eval`(또는 다른 `eval`)을 사용할 때는 실행되어
  보여지게 될 코드를 주석으로 추가한다.(레일즈 코드를 참고)
<sup>[[link](#eval-comment-docs)]</sup>

  ```ruby
  # from activesupport/lib/active_support/core_ext/string/output_safety.rb
  UNSAFE_STRING_METHODS.each do |unsafe_method|
    if 'String'.respond_to?(unsafe_method)
      class_eval <<-EOT, __FILE__, __LINE__ + 1
        def #{unsafe_method}(*params, &block)       # def capitalize(*params, &block)
          to_str.#{unsafe_method}(*params, &block)  #   to_str.capitalize(*params, &block)
        end                                       # end

        def #{unsafe_method}!(*params)              # def capitalize!(*params)
          @dirty = true                           #   @dirty = true
          super                                   #   super
        end                                       # end
      EOT
    end
  end
  ```

* <a name="no-method-missing"></a>
  백트레이스 할 때 `#methods` 리스트에 출력되지 않고 메소드 호출에 오타가 있는
  경우에(예를 들어 `nukes.launch_state = false`) 발견되지 않기 때문에 메타
  프로그래밍에서 `method_missing`을 사용하지 않는다. 대신 델리게이션이나 프록시
  `define_method`를 사용한다. 만약 `method_missing`을 사용해야 한다면:
<sup>[[link](#no-method-missing)]</sup>

  - [`respond_to_missing?`](http://blog.marc-andre.ca/2010/11/methodmissing-politely.html)도
    정의해야 한다.
  - `find_by_*` 같은 잘 알려진 prefix를 가진 메소드만 잡는다 -- 가능한 한 코드를
    단정적으로 만든다.
  - 구문 끝에서 `super`를 호출한다.
  - 일반 메소드에 단정적으로 위임한다.

    ```ruby
    # 나쁜 예
    def method_missing?(meth, *params, &block)
      if /^find_by_(?<prop>.*)/ =~ meth
        # ... find_by 하는 코드가 많이
      else
        super
      end
    end

    # 좋은 예
    def method_missing?(meth, *params, &block)
      if /^find_by_(?<prop>.*)/ =~ meth
        find_by(prop, *params, &block)
      else
        super
      end
    end

    # 가장 좋은 것은 찾을 수 있는 모든 속성에 define_method를 선언하는 것이다.
    ```

* <a name="prefer-public-send"></a>
  `private`/`protected` 범위를 회피하지 않도록, `send`대신 `public_send`를
  사용한다.
<sup>[[link](#prefer-public-send)]</sup>

## 그 밖에

* <a name="always-warn"></a>
  `ruby -w`로 안전한 코드를 작성한다.
<sup>[[link](#always-warn)]</sup>

* <a name="no-optional-hash-params"></a>
  Optional 매개변수로 해시를 사용하지 않는다.(객체 생성자는 이 규칙에서 예외다.)
<sup>[[link](#no-optional-hash-params)]</sup>

* <a name="short-methods"></a>
  메소드는 10줄을 넘지 않게 하라. 이상적으로 대부분의 메소드는 5줄 이하여야 한다.
  빈 줄은 제외한다.
<sup>[[link](#short-methods)]</sup>

* <a name="too-many-params"></a>
  3개 또는 4개 이상의 매개변수 리스트는 사용하지 않는다.
<sup>[[link](#too-many-params)]</sup>

* <a name="private-global-methods"></a>
  전역 메소드가 정말로 필요하다면 private으로 만들고 Kernel에 추가하라.
<sup>[[link](#private-global-methods)]</sup>

* <a name="instance-vars"></a>
  전역 변수 대신에 모듈 변수를 사용하라.
<sup>[[link](#instance-vars)]</sup>

  ```Ruby
  # 나쁜 예
  $foo_bar = 1

  # 좋은 예
  module Foo
    class << self
      attr_accessor :bar
    end
  end

  Foo.bar = 1
  ```

* <a name="optionparser"></a>
  복잡한 명령어 라인에서 인수를 가져올 때 `OptionParser`를 사용하고 간단한 옵션은
  `ruby -s`를 사용한다.
<sup>[[link](#optionparser)]</sup>

* <a name="time-now"></a>
  현재 시스템 시간을 가져올 때 `Time.new` 대신 `Time.now`를 사용하라.
<sup>[[link](#time-now)]</sup>

* <a name="functional-code"></a>
  코드에서 되도록 변경을 피하고 함수형 방식을 사용하라.
<sup>[[link](#functional-code)]</sup>

* <a name="no-param-mutations"></a>
  메소드의 목적이 매개변수의 수정이 아닌 경우 매개변수를 수정하면 안 된다.
<sup>[[link](#no-param-mutations)]</sup>

* <a name="three-is-the-number-thou-shalt-count"></a>
  블록 안에 3단 이상의 블록을 포함하지 마라.
<sup>[[link](#three-is-the-number-thou-shalt-count)]</sup>

* <a name="be-consistent"></a>
  일관성을 지켜라. 이 가이드 라인을 가지고 일관성을 유지하는 것이 이상적이다.
<sup>[[link](#be-consistent)]</sup>

* <a name="common-sense"></a>
  상식에 맞게 하라.
<sup>[[link](#common-sense)]</sup>

## 도구들

이 가이드를 대신해서 자동으로 루비 코드를 체크해주는 도구들이 몇 가지 있다.

### RuboCop

[RuboCop][]은 이 가이드를 기반으로 해서 루비 코드 스타일을 체크해준다. 이
가이드의 상당 부분을 커버하는 RuboCop은 MRI 1.9와 MRI 2.0을 지원하고 Emacs와
통합에 좋다.

### RubyMine

[RubyMine](http://www.jetbrains.com/ruby/)의 코드 인스펙션은
[부분적으로](http://confluence.jetbrains.com/display/RUBYDEV/RubyMine+Inspections)
이 가이드에 기반한다.

# 참여하기

이 가이드는 아직 완성되지 않았다. - 몇 가지 규칙은 예제가 없고, 몇 가지 규칙은
충분하고 명확한 설명이 없다. 그런 규칙을 보완해 루비 커뮤니티를 훌륭히(또 간단히)
도울 수 있다.

(바라건대)이러한 문제들은 곧 해결될 것이다. - 일단 그렇다는 걸 기억하고 있으면
된다.

이 가이드는 확정된 가이드가 아니다. 나는 루비 코딩 스타일에 흥미를 가지고 있는
사람들과 함께 만들어가고 싶다. 그래서 모든 루비 커뮤니티에서 유용하게 사용될
자료로 사용되면 좋겠다.

개선을 위해서 티켓을 열거나 풀 리퀘스트를 마음껏 보내라. 당신의 도움에 미리
감사한다!

또 이 프로젝트(와 RuboCop)에 금전적인 기부는 [gittip](https://www.gittip.com/bbatsov)을
통해서 할 수 있다.

[![Support via Gittip](https://rawgithub.com/twolfson/gittip-badge/0.2.0/dist/gittip.png)](https://www.gittip.com/bbatsov)

## 어떻게 참여하나요?

[contribution guidelines](https://github.com/bbatsov/ruby-style-guide/blob/master/CONTRIBUTING.md)을
따라서 하면 쉽다!

# 라이센스

![Creative Commons License](http://i.creativecommons.org/l/by/3.0/88x31.png)
[Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/deed.en_US)에
따라 이용가능하다.

# 공유합시다!

커뮤니티 기반 스타일 가이드는 이걸 모르는 곳에서는 거의 쓸모가 없다. 이 가이드를
친구나 동료에게 트윗하거나 공유하라. 우리가 받는 모든 댓글이나 의견, 제안은 이
가이드를 좀 더 좋게 만들 수 있다. 더 좋은 가이드를 가지고 싶지 않은가?

화이팅,<br/>
[Bozhidar](https://twitter.com/bbatsov)

[PEP-8]: http://www.python.org/dev/peps/pep-0008/
[rails-style-guide]: https://github.com/bbatsov/rails-style-guide
[pickaxe]: http://pragprog.com/book/ruby4/programming-ruby-1-9-2-0
[trpl]: http://www.amazon.com/Ruby-Programming-Language-David-Flanagan/dp/0596516177
[transmuter]: https://github.com/TechnoGate/transmuter
[RuboCop]: https://github.com/bbatsov/rubocop
