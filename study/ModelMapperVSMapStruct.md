## 구글 트렌드로 알아본 ModelMapper과 MapStruct의 지역별 관심도
![modelmapping](uploads/6465ca4dc689e2d9329313d0c06f3cf9/modelmapping.png)

최근 5년간의 지역별 관심도를 보면 세계적으로 MapStruct를 가장 많이 사용하는 것을 볼 수 있다.

시간의 추이로 보더라도 ModelMapper보다는 MapStruct의 관심도가 큰 폭으로 증가했다는 것을 알 수 있다.

특이한 것은 한국과 일본만 특히 ModelMapper에 대한 관심도가 높게 나왔다는 것이다.

## 차이점

![objectMapper1](uploads/dadf9fc30a64ed75f32601bfc6c95a14/objectMapper1.png)

두 라이브러리의 관심도가 차이나는 가장 큰 이유는 바로 성능에 있었다.

CPU 사용량은 ModelMapper가 조금 더 적은 모습이고, 메모리 사용량은 많게 나온다.

하지만 실행속도 측면에서 보면 MapStruct가 압도적으로 이긴다.

이러한 성능 차이는 두 라이브러리가 오브젝트를 매핑하는 과정에 있다.

ModelMapper는 **runtime 시점에 reflection**을 통해 맵핑을 하기 때문에 Mapping 객체의 사이즈가 커질수록 선형적으로 메모리를 많이 사용하게 되고, 결국 성능도 저하될 수 밖에 없다.

> Reflection : 동적으로 로딩되는 자바 콤포넌트(클래스)에서 속성을 얻는 Java 기능

그에 반해 MapStruct는 Lombok과 같이 Annotation Processor를 통해서 런타임 도중이 아닌 컴파일 시점에 객체간 Mapping이 이루어지기 때문에 매우 월등한 성능을 보일 수 있다.

## 결론

Object Mapper에 관하여 찾는 도중 Orika 라는 라이브러리도 찾았는데, ModelMapper보다 성능이 떨어진다는 말이 있어 비교 선상에서 제외하였다. 

> ModelMapper가 Orika보다 실행속도가 약간 더 빠르지만, 메모리를 더 많이 사용한다.

ModelMapper의 경우 한국에서 많이 사용하고, 관련 한글 레퍼런스(블로그 글..)이 많지만, 성능이 훨씬 우월하고 세계적으로 많이 사용하는 MapStruct를 사용하기로 결정하였다.