# claude-code

## 1. claude code란?
- 엔트로픽의 최신 모델인 Claude Opus4를 기반으로 터미널에서 실행하는 에이전틱 도구
- 개발자가 자연어로 요청하면 클로드 코드는 스스로 계획 수립후, 파일을 탐색, 코드를 작성하고, 테스트를 수행하는 등 개발작업 수행

1. 프로젝트 시작
   - 기존 코드베이스 탬색
   - 사용 중인 프레임웍과 라이브러리 파악
   - 코드 스타일 및 패턴 학습

2. 작업 계획 수집
   - 컴포넌트 식별
   - 구현 순서 확인
   - 종속성 확인

3. 작업 실행
   - 파일 생성 및 수정
   - 코드 작성
   - 필요한 패키지 설치
   - 테스트 코드 작성, 실행
  
4. 검증 및 개선
   - 작성한 코드 테스트
   - 오류 자동 수정
   - 코드 스타일 및 패턴 학습
  
## 2. claude code key
- Ctrl + C     현재 입력 또는 생성중인 아웃풋 중단
- Ctrl + D     클로드 세션 종료
- Esc + Esc    직전 메시지로 회귀
- Ctrl + j     줄바꿈
- Shift + tab  모드 전환 (일반, ??)
- / 명령어     슬래시 명령어 실행    (/model, /config, /memory, /doctor)

<img width="631" height="248" alt="image" src="https://github.com/user-attachments/assets/229c87bb-f3c2-4b5b-bb8b-c771fd9a9cff" />

## 3. claude code 메모리
- ./claude.local.md   : 특정 프로젝트 관련 설정이지만 팀원에게 공유할 필요가 없는 설정
- ./claude/CLAUDE.md  : 프로젝트 전반에 걸쳐 적용하고 싶은 설정
- ./CLAUDE.md         : 특정 프로젝트 관련 설정이거나 팀원에게 공유 설정

## 4. 커스컴 슬래시 커맨드
- 프로젝트 커스텀 슬래시 커맨드 : .claude/commands/   (.md 작성)
- 사용자 커스텀 슬래시 커맨드  : ~/.claude/commands/   (.md 작성)

## 5. MCP 추가 
1. 로컬 서버 방식으로 MCP 추가 (.mcp.json 추가, "type":"stdio")
   - claude mcp add <name> <command> ...args..
   - claude mcp add context7 -- npx -y @ups~~

2. SSE MCP추가 (.mcp.json 추가, "type":"sse")
   - claude mcp add --transport sse <name> <commmand> ...args...
   - claude mcp add --trnsport sse conect7 https://mcp~
     
3. HTTP MCP 추가 (.mcp.json 추가, "type":"http")
   - claude mcp add --transport http <name> <command> ...args...
   - claude mcp add --transport http context7 https://

4. MCP 리스트 확인
   - claude mcp list

| 구분 | stdio 서버 | SSE 서버 | HTTP 서버 |
|---|:---|:---|:---|
| `실행 위치` | 로컬 컴퓨터 | 원격 서버 | 원격 서버 |
| `통신 방향` | 양방향 (프로세스 통신) | 단방향(서버 --> 클라이언트) | 양방향 (요청/응답) |
| `연결 방식` | 프로세스 실행 | 지속적 연결 | 요청 기반 연결 |
| `핵심 용도` | 로컬 도구 및 스크립트 연동 | 실시간 데이터 스트리밍 | 일반적인 원격API 연동 |
