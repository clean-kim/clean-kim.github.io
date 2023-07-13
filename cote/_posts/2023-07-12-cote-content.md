# 프로그래머스 달리기 경주

난이도: Lv. 1<br>
사용 언어: 자바스크립트

### 통과한 코드
~~~js
function solution(players, callings) {
    const map = new Map();
    for(let i=0; i<players.length; i++) {
        map.set(players[i], i);
    }

    for(let i=0; i<callings.length; i++) {
        const idx = map.get(callings[i]);
        [players[idx], players[idx-1]] = [players[idx-1], players[idx]];
        map.set(players[idx-1], map.get(players[idx]));
        map.set(players[idx], map.get(players[idx])+1);
    }
    return players;
}
~~~

### 시도했던 코드들

~~~js
function solution2(players, callings) {
    let idx = 0;
    let temp = null;
    for(let i=0; i<callings.length; i++) {
        idx = players.indexOf(callings[i]);
        if(idx > 0) {
            temp = players[idx-1];
            players[idx-1] = callings[i];
            players[idx] = temp;
        }
    }
    return players;
}

function solution3(players, callings) {
    let idx = 0;
    let temp = null;
    for(let i=0; i<callings.length; i++) {
        idx = players.indexOf(callings[i]);
        temp = players.splice(idx-1, 1, callings[i]);
        players.splice(idx, 1, temp[0]);
    }
    return players;
}
~~~

👉🏻 위 코드들은 테스트 10~13은 실패 나머지는 통과