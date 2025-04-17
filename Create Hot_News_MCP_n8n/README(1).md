# n8n 카카오톡 메세지 전송 노드 생성

## 1. 카카오 개발자 계정 설정

- 카카오 개발자 사이트 (Kakao Developers) 접속
- 애플리케이션 등록 > 앱 키
    - REST API Key (Client ID) 발급  : 
- 앱 설정 > 플랫폼 등록 (Web)
    - 카카오톡 메세지 버튼 클릭시 이동할 주소 : https://github.com/devkylo
- 앱 설정 > 비즈앱 등록 (선택) : 친구에게 보내기 기능 활용
- 앱 설정 > 팀 관리 (선택) : 친구에게 보내기 기능 활용
- 제품 설정 > 카카오 로그인
    - 카카오 로그인 활성화
    - Redirect URI 설정 : http://localhost:5678/rest/oauth2-credential/callback
- 제품 설정 > 카카오 로그인 > 동의항목
    - talk_message(필수), friends (선택)
- 제품 설정 > 카카오 로그인 > 보안
    - Client Secret 발급 : 

## 2. n8n Credential 만들기

1. Oauth Redirect URL
http://localhost:5678/rest/oauth2-credential/callback
2. Grant Type
Authorization Code
3. Authorization URL
https://kauth.kakao.com/oauth/authorize
4. Authorization Token URL
https://kauth.kakao.com/oauth/token
5. Client id (rest api key)
카카오톡 개발자 > 내 어플리케이션 -> 앱 키 에서 확인 가능
21ef602b72735f1812f0b067daa53e7c
6. Client secret
카카오톡 개발자 > 내 어플리케이션 -> 보안 에서 확인 가능
36IxaG78RMqFvg359ZkGyKwNR0oGs9tm
7. Scope
talk_message,friends
8. Authentication
Body

## 3. n8n 카카오톡 Send me 노드 만들기

```bash
1) METHOD : POST

2) URL : https://kapi.kakao.com/v2/api/talk/memo/default/send

3) Header
{
	"Content-Type" : "application/x-www-form-urlencoded;charset=utf-8"
}

4) Body (text 방식 기준)
{
	"template_object" : '{     
		  "object_type": "text",     
		  "text": "{{ 메세지 내용 }}",
		  "link": {
		        "web_url": "https://example.com"
		    }
			}'
}
```

## 4. n8n 친구 목록 조회

```bash
1) METHOD : GET
2) URL : https://kapi.kakao.com/v1/api/talk/friends
```

## 5. n8n 카카오톡 Send to Friends 노드 만들기
