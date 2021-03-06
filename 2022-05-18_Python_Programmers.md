# 프로그래머스_Python_방문길이


## Problem link (https://programmers.co.kr/learn/courses/30/lessons/49994)


### 접근

- 시작 좌표는 (0, 0) 위치 ⇒ 움직이는 경우의 수를 딕셔너리로 묶어서 `{'U':[0,1], 'D':[0,-1], 'R':[1,0], "L":[-1,0]}`
- 좌표평면 오버한 경우 카운팅0 으로 간주 ⇒ 이동 좌표를 5 초과되지 않게 제한
- 이전 좌표 -> 이후 좌표를 알아야 하기 때문에 4차원 배열이 필요 => 갈때, 올때 경로를 set()에 (set는 중복값 X)


### 풀이

    
    def solution(dirs):
       route = {'U':[0,1], 'D':[0,-1], 'R':[1,0], "L":[-1,0]}
       now = [0,0]
       visited = set()
       answer = 0
    
    for i in dirs:
        move_x, move_y = route[i]   #딕셔너리의 요소에 따라 이동
        nx = now[0] + move_x   #다음 좌표
        ny = now[1] + move_y 
        if nx> 5 or nx< -5 or ny> 5 or ny< -5 :
            continue
        if (now[0], now[1], nx, ny) not in visited: 
            visited.add((now[0], now[1], nx, ny))   #양방향 이동 모두 추가해줌
            visited.add((nx, ny, now[0], now[1]))
            answer += 1 
        now[0], now[1] = nx, ny   #좌표 이동 업데이트
        
    return answer



### 오답(trial)


    def solution(dirs):
        x, y = 0, 0
        answer = 0
        dict = { 'U' : (x , y+1), 'D' : (x , y-1), 'L' : (x-1 , y), 'R' : (x+1 , y) }
        
        for i in range(len(dirs)):
            if dirs[i] == 'U' and y < 5:
                nx = x  
                ny = y - 1
                answer += 1
            elif dirs[i] == 'D' and y > -5:
                nx = x 
                ny = y + 1
                answer += 1
            elif dirs[i] == 'L' and x > -5:
                nx = x - 1
                ny = y 
                answer += 1
            elif dirs[i] == 'R' and x < 5:
                nx = x + 1
                ny = y
                answer += 1

        return answer
![image](https://user-images.githubusercontent.com/99947811/168960357-831e5b92-c27a-41be-83e0-2c127fa6bc40.png)




## 다른 사람 풀이

    def solution(dirs):
        s = set()
        d = {'U': (0,1), 'D': (0, -1), 'R': (1, 0), 'L': (-1, 0)}
        x, y = 0, 0
        for i in dirs:
            nx, ny = x + d[i][0], y + d[i][1]
            if -5 <= nx <= 5 and -5 <= ny <= 5:
                s.add((x,y,nx,ny))
                s.add((nx,ny,x,y))
                x, y = nx, ny
        return len(s)//2    # 이동한 길이 나누기 2
        
        
        
