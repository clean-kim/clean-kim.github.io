# 프로그래머스 추억 점수

난이도: Lv. 1<br>
사용 언어: 자바스크립트

### 통과한 코드
~~~js
function solution(name, yearning, photo) {
    var answer = [];
    const map = new Map();

    for(let i=0; i<name.length; i++) {
        map.set(name[i], yearning[i]);
    }

    for(let i=0; i<photo.length; i++) {
        let res = 0;
        let get = 0;
        for(let j=0; j<photo[i].length; j++) {
            get = map.get(photo[i][j]);
            if(get) res+=get;
        }
        answer.push(res);
    }

    return answer;
}
~~~