#Column & tr - data를 표기 편하게

1. ```cat data.dat | tail -n 10 | column -t```
 - column 사이 폭을 보기 좋게 일정하게 맞춤
2. ```cat data.dat | tail -n 10 | tr ' ' ', '```
 - 공백 문자를 ', '로 치환

참고 : https://sysadmincasts.com/episodes/36-cli-monday-column-and-tr