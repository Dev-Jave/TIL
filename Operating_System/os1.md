# Chapter 04. Threads & Concurrency
## **Thread Concept**
스레드의 주요 구성은 다음과 같다.
* Thread ID
* Program counter(PC)
* Register set
* Stack space

멀티 프로세스와 멀티 스레드의 차이점   
멀티 프로세스 : 자원이 각각 다른 걸 사용할 때  
멀티 스레드 : 자원은 같은 걸 쓰지만 일이 다를 때  

## **멀티 스레딩(Multi Threading)**
#### 1) Multi Threaded process 예시
* 웹 브라우저에는 한 스레드가 임이지나 텍스트를 보여주는 동안, 다른 슬데드는 네트워크에서 데이터를 검색할 수 있음.
* 워드 프로세서에는 편집 화면을 보여주는 스레드, 사용자의 키 입력에 응답하는 스레드, 백그라운드에서 맞춤법 및 문법 검사를 수행하는 세 번째 스레드가 있음.   
* 운영 체제 커널도 일반적으로 각 스레드는 장치 관리, 메모리 관리 또는 인터럽트 처리와 같은 작업을 따로 수행하는 멀티 스레드임. (multi thread와 multi process를 동시에 사용)

#### 2) 멀티 스레드의 장점
1) **Responsiveness**  
interactive application의 멀티스레딩은, 일부가 차단되거나 긴 작업을 수행하는 경우에도 application이 계속 실행되도록 하여 사용자에 대한 응답성을 높일 수 있다. 사용자의 인터페이스를 디자인할 때 특히 유용하다.   
example)  
    * single-threaded process는 작업이 완료될 때 까지 사용자에게 응답하지 않음.
    * multithreaded processs는 그 작업을 수행하는 스레드 외에는 모두 동작하므로, application은 사용자에게 계속 응답함.  

2) **Resource Sharing**
3) **Economy**  
일반적으로 스레드 생성은 프로세스 생성보다 시간과 메모리를 덜 소모한다. 일반적으로 프로세스 간보다 스레드 간의 Context Switch가 더 빠르기 때문에 경제적이다.

4) **Scalability**  
single-threaded process는 사용 가능한 코어 수에 관계없이 하나만 실행 가능하다.  
그러나, multithreaded process는 **각 코어마다 다른 스레드가 병렬로 실행 가능**하다. 즉, 같은 시간 동안 더 많은 일을 수행할 수 있기 때문에 확장에 용이하다.
> 스레드와 관련된 개념을 살펴볼 때 process, thread, task등을 제대로 구분하기 위해 프로그램 단위로 설명하고 있는 지, 일 단위로 설명하고 있는 지 등을 주의깊게 살펴보아야 한다.

 #### 3) Programming Challenge
 1. Idetifying tasks  
 별도의 동시 task로 나눌 수 있는 영역을 찾기 위해 application을 체크할 필요가 있다.
 2. Balance  
 개발자는 병렬로 실행할 수 있는 task의 영역을 나눌 때, task가 동일한 가치인지 확인이 팔요하다. 
 3. Data splitting
 4. Data Dependency  
 한 task의 데이터에 의존 하는 경우, 개발자는 task가 Data dependency를 수용하도록 동기화가 되었는지 확인해야 한다.
 5. Testing and debugging  
 멀티스레딩 프로그램을 테스트 및 디버깅하는 겻은 본질적으로 싱글스레드 프로그램보다 어렵다.

## **MultiThreading Models**
### 스레드의 분류
* 유저 스레드 : 스레드의 기능을 제공하는 라이브러리를 활용하는 방식이며, 커널 지원 없이 관리한다.  
    * 장점 - 성능 저하가 없다
    * 단점 - 스레드 하나에 문제가 발생하면 같은 프로세스 전체 스레드가 중단되기 때문에 안정성이 떨어진다.
* 커널 스레드 : 운영 체제에서 직접 지원 및 관리한다.  
    * 장점 - 안정적이다.
    * 단점 - 유저 모드에서 커널 모드로 context switching이 필요하여 성능이 저하된다.  

### Many-to-One Model
하나의 커널 스레드에 여러 개의 유저 스레드를 연결하는 방식이다. 한 번에 하나의 유저 스레드만 커널에 접근할 수 있기 때문에 멀티코어 시스템에서 병렬적인 수행을 할 수가 없다.


![](/image/os_01.png)





### One-to-One Model
### Many-to-Many Model
### Tow-level Model

### Impliciting Threading

### Thread Pools
멀티 스레딩을 이용할 때, 무제한으로 스레드를 생성할 경우 시스템 리소스를 고갈시킬 수 있다. 이에 대한 해결책이 **스레드 풀**을 사용하는 것이다.
>**Thread Pools**: 시작 시 여러 스레드를 미리 만들고 풀에 배치해둔 후, 필요 시에 할당하는 것이다. 

### Fork-Join Model
여러개로 나누어 계산한 후 결과를 모으는 작업에 해당한다. 메인 스레드가 여러개의 자식 스레드들을 만들고(fork) 자식 스레드들이 일을 마치고 다시 합쳐진다(join)
(Hadoop..? 참고해보자!)

### OpenMP
컴파일러가 스레드 사용을 도와주는 것이다.(compiler directives)
```C
#pragma cmp parallel for
for (i = 0; i < N; i++) {
    c[i] = a[i] + b[i];
}
```


