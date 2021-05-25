[이전글 - 파일의 접근권한](https://godtaehee.tistory.com/9)도 시간되시면 읽어보시면 좋습니다.

# echo

`echo`명령어는 C언어의 printf함수에 준하는 화면 출력을 담당하는 명령어이다.

그럼 실제로 다음과 같이 hello world를 출력해보자

[##_Image|kage@XdPRg/btq5HMKcoZM/paT2ve1mvjNycR37t4fJe0/img.png|alignCenter|width="100%" data-origin-width="574" data-origin-height="185" data-ke-mobilestyle="widthOrigin"|||_##]

여기서 총 hello world를 `echo`명령어 3번을 통해 3번 출력하고 있는데 각각의 차이점이 무엇인지 유심히 생각해보자

첫번째는 그냥 평범한 echo명령어의 사용이지만 두번째 명령문을 잘 보면 hello와 world사이에 많은 띄어쓰기를 했음에도 불구하고 출력결과는 1번과 같이 띄어쓰기가 한번된 'hello world'가 출력되고있다. 이것은 리눅스 쉘에서 공백문자는 한개가 있던 여러개가 있던 똑같기때문이다. 즉 아무리 스페이스바를 연타해도 한개의 띄어쓰기로 취급한다는 것이며, 이 공백은 리눅스에서 '단어와 단어', '명령어와 옵션', '옵션과 전달인자' 사이의 구분자로 사용한다.  
만약 공백을 많이 사용하고 싶다면 3번째 출력처럼 인용부호(큰따옴표, 작은따옴표)를 사용하면 된다.

### \-e 옵션

`echo`명령어의 옵션중 `-e`옵션이 있는데 특수문자(대표적으로 줄바꿈기호인 \\n)를 화면에 출력할때 사용하는 옵션이다. 먼저 -e옵션을 주지않으면 어떻게 되는지 보자

[##_Image|kage@05UZQ/btq5JD7ga20/1Scp8lvtEU6qxrnxk4mtk0/img.png|alignCenter|width="100%" data-origin-width="722" data-origin-height="88" data-ke-mobilestyle="widthOrigin"|||_##]

이렇게 옵션이 없으면 특수문자들이 그대로 출력이된다 그리고 아래처럼 옵션을 주게되면 정상적으로 특수문자(\\n)의 기능을 하는걸 볼수있다.

[##_Image|kage@1Kqz8/btq5Ob9v4SM/dsToaX6OKPhL17wArh4Jc1/img.png|alignCenter|width="100%" data-origin-width="228" data-origin-height="63" data-ke-mobilestyle="widthOrigin"|||_##]

근데 나는 iterm2를 사용하고 있는데 그냥 echo만 쳐도 특수문자 인식이 되긴했다.

또다른 특수문자로 `\a`가 있다. 이것은 알람음을 나게하는 특수문자인데 이것또한 `-e`옵션과 같이 사용해야한다.

### \-n옵션

명령어 입력후 원래 줄바꿈처리되어 깔끔하게 줄바꿈 처리가되는데 -n옵션은 아래와 같이 줄바꿈이 일어나지않는다. 그래서 좀 가독성이 떨어진다.

[##_Image|kage@0W7D1/btq5Mvm6qFl/BVZPAHuvMhqFVp6xiVQ7x1/img.png|alignCenter|width="100%" data-origin-width="671" data-origin-height="104" data-ke-mobilestyle="widthOrigin"|||_##]

### echo \*

ls명령어와 비슷하게 현재폴더의 전체 목록을 볼수있다. 근데 ls는 보기좋게 출력해주는데 이거는 공백을 기준으로 보여준다.

이렇게 공백을 기준으로 모든 파일과 폴더의 이름을 뽑아내는것을 `substring`이라고 하는데 많은 언어들의 split함수로 공백을 기준으로 파일명과 폴더명을 가져와야할때 유용하게 쓸수있는 하나의 데이터가 될수있다.

이러한 목록을 바로 파일로 추출하기위해서는 `echo * > 원하는파일명`으로 하면 `원하는파일명`으로 목록을 터미널에 뿌려주는것 뿐만아니라 파일로 변환할수 있다. 예시는 다음과 같다. `echo * > result.txt`