# Ch.09 Main Memory

## MMU (Memory Management Unit)
> MMU는 가상에서 물리적 주소로의 런타임 매핑을 수행하는 장치이다. 여기서는 base register를 relocation register라고 한다.

![](/image/os_02.png)

## Dynamic loading
> 메모리 공간을 효율적으로 사용하기 위해 프로그램, 루틴을 한꺼번에 로딩하지 않고 필요할 때마다 로딩하는 방식이다.

relocatable linking loader는 필요할 때마다 호출되어 주소 테이블 (adress table)을 업데이트할 수 있다.
* **linking** : 다른 프로그램이나 외부 라이브러리를 가져와 연결하는 것
* **DLL(dynamically linked library)** : 프로그램 실행 중간에 사용자 프로그램에 Linking 되어 사용할 수 있는 시스템 라이브러리

### Linking
* 정적 링킹(static linking): 실행 파일을 만들 때, 모든 라이브러리의 모듈을 복사하는ㅠ 식이다. 모두 한 실행파일에 포함되어 동적 링킹보다 빠르지만, 파일 크기가 매우 커져 보통 잘 사용하지 않는다. (임베디드와 같이 속도가 중요한 경우에 주로 사용)

* 동적 링킹(dynamic linking)


## Contiguous Memory Allocation
> 연속 메모리 할당(Contiguous Memory Allcation)은 프로세스를 단일 구역(single section)에 할당하는 방식으로, 여러 곳에 나눠 할당되어 있지 않고 한 구역에 할당되어 연속적이다.



## Paging
> 프로세스의 물리적 주소 공간을 불 연속적(non-contiguous)으로 쪼개서 관리하는 것을 의미한다.  

페이징의 기본적인 방법은 메모리를 동일한 크기로 쪼개는 것이다.
* 프레임(frame) : 물리 메모리를 고정 크기의 블록으로 나눈 것이다.
* 페이지 (page) : 논리 메모리를 같은 크기로 나눈 것이다.

