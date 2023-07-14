# 프로그래머스 달리기 경주

난이도: Lv. 1<br>
사용 언어: 자바스크립트

### 통과한 코드
~~~js
function solution(players, callings) {
    const map = new Map();
    for(let i=0; i<players.length; i++) {   // 모든 플레이어를 맵 객체에 담기
        map.set(players[i], i);             // key에 배열값, value에 인덱스 정보(순서)를 담는다
    }

    for(let i=0; i<callings.length; i++) {
        const idx = map.get(callings[i]);                                   // callings[i] 값으로 map에 저장된 해당 플레이어의 인덱스 값을 가져옴
        [players[idx], players[idx-1]] = [players[idx-1], players[idx]];    // 구조분해할당 표현식을 이용해서 players 배열에서 idx 인덱스에 저장된 값을 앞의 값과 바꿈 
        map.set(players[idx-1], map.get(players[idx]));                     // 뒤로 이동한 플레이어는 앞의 인덱스 값 저장
        map.set(players[idx], map.get(players[idx])+1);                     // 앞으로 이동한 플레이어에는 인덱스 값 증가시킴
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