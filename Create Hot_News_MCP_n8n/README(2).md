#claude_desktop_config 설정 // MCP 정의
{
    "mcpServers":{
        "mcp_scrap_news":{
            "command":"npx",
            "args":[
                "-y",
                "supergateway",
                "--sse",
                "n8n MCP SERVER URL 등록"
            ]
        },
        "mcp_send_kakao_msg":{
            "command":"npx",
            "args":[
                "-y",
                "supergateway",
                "--sse",
                "n8n MCP SERVER URL 등록"
            ]
        }
    }
}

# Gemini API 설정 // API 값을 n8n 과 바로 연동 가능(OPEN AI 가 더 편하고 좋다면 OPEN AI API 발급 후 n8n 등록 및 모델 사용)
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=GEMINI_API_KEY" \
-H 'Content-Type: application/json' \
-X POST \
-d '{
  "contents": [{
    "parts":[{"text": "Explain how AI works"}]
    }]
   }'

#GCP API 활성화 (https://console.cloud.google.com/welcome/new?project=n8n-connect-457116)
Google Drive & Sheet Use
