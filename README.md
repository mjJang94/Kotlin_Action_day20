# 자바 함수형 인터페이스 활용
어떻게 코틀린 람다를 자바 api에서 활용할 수 있을까?
<pre>
<code>
button.setOnClickListener{ } <- 람다를 인자로 넘김
</pre>
</code>

Button 클래스는 setOnclickListener 메소드를 이ㅛㅇ하여 버튼의 리스너를 설정하고, 이 때 인자의 타입은 OnclickListener 이다.   

자바8 이전의 자바에서는 setOnclickListener 메소드에게 인자로 넘기기 위해 무명 클래스의 인스턴스를 만들어야 했다.
<pre>
<code>
button.setOnclickListener(new OnclickListener()) {
    @Overrride
    public void onClick(View v){
      ...
  }
}
</pre>
</code>
 
코틀린에서는 무명 클래스 인스턴스 대신 람다로 넘길 수 있다.

<pre>
<code>
button.setOnclickListener { view -> ...}
</pre>
</code>

OnClickListener를 구현하기 위해 사용한 람다에는 view라는 파라미터가 있다. view의 타입은 View이다. onClick 메소드의 인자 타입과 같다.   
이런 코드가 작동하는 이유는 OnclickListener에 추상 메소드가 단 하나만 있기 때문이다. 그런 인터페이스를 함수형 인터페이스 또는 SAM 인터페이스라고 한다.   
SAM은 단일 추상 메소드라는 뜻으로 자바의 API에서는 Runnable이나 Callable과 같은 함수형 인터페이스와 그러한 함수형 인터페이스를 활용하는 메소드가 많다.   
코틀린은 함수형 인터페이스를 인자로 취하는 자바 메소드를 호출할 때 람다를 넘길 수 있게 해주므로 코틀린 코드는 무명 클래스 인스턴스를 정의하고 활용할 필요가 없어서 깔끔한 코드가 된다.
