#JDK 배포판에 포함된 Utilities
1. javap
  - class에 대한 정보가 필요할 때
  - -1 : 라인과 지역 변수를 출력
  - -p : 모든 class와 member들을 출력
  - -c : 메서드 바이트 코드 출력

2. jjs
  - terminal에서 js runtime이 필요할 때
  - node.js를 설치하기 싫을 때

3. jhat
  - java heap 분석 툴
  - -XX:+HeapDumpOnOutOfMemoryError 으로 생성된 힙덤프 분석
  - default로 java\_pidxxxx.hprof 힙덤프 파일 생성
  - jhat으로 힙덤프 파일을 분석하면, localhost:7000으로 결과를 확인할 수 있음

4. jmap
  - 메모리 매핑 도구 (OutOfMemoryError를 발생시키지 않아도 됨)
  - jmap -heap pid : memory 사용현황에 대한 정보를 보임
  - jmap -dump:live,format=b,file=heap.bin pid : 추후에 분석할 덤프를 생성, 나중에 Heap 분석 도구를 이용해 분석

5. jps
  - process 상태를 확인하는 도구, java pid를 확인하기 위해 주로 사용
  - OS 독립적인 툴(매우 편리)
  - jmap으로 분석할 pid를 찾을때 사용
  - jps -mlv 를 사용하면 대부분의 경우에 원하는 정보를 얻을 수 있음
  - mlv : main 메서드 args, 전체 패키지 명, jvm 옵션 표시함

6. jstack
  - thread의 stacktrace를 생성하는 도구
  - deadlock이 있는지 thread가 어떻게 동작하는지 검증할때 사용
  - jstack -F -l pid
  - -F를 이용하여 행이 걸린 프로세스에 대해서도 강제 덤프
  - -l을 이용하여 synchronisation과 lock에 대한 정보를 출력

참고 : http://zeroturnaround.com/rebellabs/the-6-built-in-jdk-tools-the-average-developer-should-learn-to-use-more
