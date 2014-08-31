#SS Better alternative to netstat

ss은 netstat의 대체 툴이다.

netstat은 대부분의 네트워크 도구에서 사용 중지 되었고, ss로 바뀌었다.
ss 명령어는 netstat보다 더 상세한 정보를 보여줄 뿐 아니라 더 빠르기까지 하다.
netstat 명령어는 정보를 모으기 위해 /proc 아래 파일들을 읽는다. 이는 표시할 네트워크 연결이 많을 때 느리다는 약점이 있다.

반면, ss 명령어는 정보를 커널 영역으로 부터 직접 가져온다. ss에 사용되는 옵션은 netstat과 매우 유사해서 쉽게 대체할수 있다.

###Options
1. ss | less # 모든 연결 표시
2. ss -t # listen 상태가 아닌 모든 tcp 연결 표시
3. ss -u # listen 사애가 아닌 모든 udp 연결 표시
4. ss -x # unix socket pipe 연결 표시
5. ss -ta # 모든 tcp 연결 표시
6. ss -a -A tcp # ss -ta와 동일
7. ss -ua # 모든 udp 연결 표시
8. ss -a -A udp # ss -ua와 동일
9. ss -nt # 호스트명 없이 모든 연결 표시
10. ss -ltn # 호스트명 없이 listening tcp 표시
11. ss -ltp # pid와 프로세스 이름고 함께 listening tcp 표시
12. ss -s # 통게 표시
13. ss -tn -o # tcp 연결을 도메인명과 keepalive timer도 함께 표시
14. ss -tl4 # ip4 연결 표시
15. ss -tl -f inet # 위와 동일
16. ss -tl6 # ip6 연결 표시
17. ss -tl -f inet6 # 위와 동일

###ss 필터 기능
 - ss [options] [state-filter] [address-filter]
 - ss -t4 state estalished
 - ss -t4 state time-wait
 - ss -at dst :http
 - ss -at dst :http or dst :443
 - ss -nt dst 323.123.12.12
 - ss -nt dst 323.123.12.12/16
 - ss -nt src 127.0.0.1 sport gt :5000
 - ss -nt state connected dport = :http

참고
 - http://gokulvanan.tumblr.com/post/95730763016/linux-tips-ss-better-alternative-to-netstat