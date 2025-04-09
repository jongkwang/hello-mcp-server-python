# MCP Server Python

*Languages: [English](#english) | [한국어](#korean)*

<a id="english"></a>
## English

A Python server example project using the Model Context Protocol.

### Table of Contents
- [Overview](#overview)
- [Reference](#reference)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Connecting to Cursor and Claude for Desktop](#connecting-to-cursor-and-claude-for-desktop)
- [Project Structure](#project-structure)
- [Features](#features)
- [Weather API Setup](#weather-api-setup)
- [License](#license)
- [References](#references)

### Overview

This project is a server example that provides tools to LLMs such as Claude AI using the Model Context Protocol (MCP). It offers BMI calculation and weather information lookup functions.

### Reference

This project was created based on the following open source project:
- [Model Context Protocol Python SDK](https://github.com/modelcontextprotocol/python-sdk)

### Prerequisites

- Python 3.9 or higher
- pip or pip3 (package manager)
- httpx (asynchronous HTTP client)
- MCP Python SDK

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/hello-mcp-server-python.git
cd hello-mcp-server-python
```

2. Install the required packages:
```bash
pip install httpx "mcp[cli]"
```

3. Run the server: (Optional if connecting through Cursor or Claude for Desktop)
```bash
python server.py
# or
mcp run server.py
```

### Connecting to Cursor and Claude for Desktop

#### Connecting to Cursor

1. Open Cursor IDE and load the project.
2. Create an `mcp.json` file in the project root and add the following content:
```json
{
  "mcpServers": {
      "mcp-server-python": {
            "command": "mcp",
            "args": [
                "run",
                "/_____PATH_OF_FILE_____/server.py"
                ]
      }
  }
}
```
3. MCP tools will be automatically recognized when chatting with Claude in Cursor. The server will run automatically according to the mcp.json settings.

#### Connecting to Claude for Desktop

1. Install Claude for Desktop.
2. Run the server in the terminal:
```bash
python server.py
```
3. Go to the MCP server section in Claude for Desktop settings and add a local MCP server.
4. Configure the server URL or port as needed.
5. When chatting with Claude, you can use the BMI calculation and weather lookup tools.

### Project Structure

```
hello-mcp-server-python/
├── server.py       # MCP server main file
└── requirements.txt  # Dependency package list (optional)
```

### Features

The server currently provides two tools:

1. `calculate_bmi`: Calculates BMI from height and weight inputs.
2. `fetch_weather`: Retrieves weather information for a given city name. (API key required)

### Weather API Setup

To use the weather API, you need an API key. Open the `server.py` file and modify it as follows:

```python
@mcp.tool()
async def fetch_weather(city: str) -> str:
    """Fetch current weather for a city"""
    API_KEY = "your_api_key_here"  # Enter your API key here
    async with httpx.AsyncClient() as client:
        response = await client.get(f"https://api.weather.com/{city}?apiKey={API_KEY}")
        return response.text
```

### License

This project is distributed under the MIT License. See the LICENSE file for details.

### References

- [Model Context Protocol Documentation](https://modelcontextprotocol.io)
- [Model Context Protocol Python SDK Documentation](https://github.com/modelcontextprotocol/python-sdk)
- [httpx Documentation](https://www.python-httpx.org/)
- [Claude AI Documentation](https://docs.anthropic.com)

---

<a id="korean"></a>
## 한국어

Model Context Protocol을 활용한 Python 서버 예제 프로젝트입니다.

### 목차
- [개요](#개요)
- [참조한 사이트 주소](#참조한-사이트-주소)
- [사전 설치 사항](#사전-설치-사항)
- [설치 방법](#설치-방법)
- [Cursor와 Claude for Desktop에 연결 방법](#cursor와-claude-for-desktop에-연결-방법)
- [프로젝트 구조](#프로젝트-구조)
- [기능](#기능)
- [날씨 API 설정](#날씨-api-설정)
- [라이센스](#라이센스)
- [참고문서](#참고문서)

### 개요

이 프로젝트는 Model Context Protocol(MCP)을 사용하여 Claude AI와 같은 LLM에 도구(Tool) 기능을 제공하는 서버 예제입니다. BMI 계산과 날씨 정보 조회 기능을 제공합니다.

### 참조한 사이트 주소

이 프로젝트는 다음 오픈소스 프로젝트를 참고하여 만들어졌습니다:
- [Model Context Protocol Python SDK](https://github.com/modelcontextprotocol/python-sdk)

### 사전 설치 사항

- Python 3.9 이상
- pip 또는 pip3 (패키지 관리자)
- httpx (비동기 HTTP 클라이언트)
- MCP Python SDK

### 설치 방법

1. 저장소를 클론합니다:
```bash
git clone https://github.com/yourusername/hello-mcp-server-python.git
cd hello-mcp-server-python
```

2. 필요한 패키지를 설치합니다:
```bash
pip install httpx "mcp[cli]"
```

3. 서버 실행: (Cursor나 Claude for Desktop을 통해 연결하는 경우 이 단계는 선택 사항)
```bash
python server.py
# 또는
mcp run server.py
```

### Cursor와 Claude for Desktop에 연결 방법

#### Cursor에 연결하기

1. Cursor IDE를 열고 프로젝트를 로드합니다.
2. Cursor 프로젝트 루트에 `mcp.json` 파일을 생성하고 다음 내용을 추가합니다:
```json
{
  "mcpServers": {
      "mcp-server-python": {
            "command": "mcp",
            "args": [
                "run",
                "/_____PATH_OF_FILE_____/server.py"
                ]
      }
  }
}
```
3. Cursor에서 Claude와 채팅할 때 MCP 도구가 자동으로 인식됩니다. 서버는 mcp.json 설정에 따라 자동으로 실행됩니다.

#### Claude for Desktop에 연결하기

1. Claude for Desktop을 설치합니다.
2. 터미널에서 서버를 실행합니다:
```bash
python server.py
```
3. Claude for Desktop 설정에서 MCP 서버 섹션으로 이동하여 로컬 MCP 서버를 추가합니다.
4. 서버 URL 또는 포트를 필요에 따라 구성합니다.
5. Claude와 대화하면 BMI 계산과 날씨 조회 도구를 사용할 수 있습니다.

### 프로젝트 구조

```
hello-mcp-server-python/
├── server.py       # MCP 서버 메인 파일
└── requirements.txt  # 의존성 패키지 목록 (선택 사항)
```

### 기능

현재 서버는 두 가지 도구를 제공합니다:

1. `calculate_bmi`: 키와 몸무게를 입력받아 BMI를 계산합니다.
2. `fetch_weather`: 도시 이름을 입력받아 해당 도시의 날씨 정보를 가져옵니다. (API 키 설정 필요)

### 날씨 API 설정

날씨 API를 사용하기 위해서는 API 키가 필요합니다. `server.py` 파일을 열고 다음과 같이 수정하세요:

```python
@mcp.tool()
async def fetch_weather(city: str) -> str:
    """Fetch current weather for a city"""
    API_KEY = "your_api_key_here"  # 여기에 API 키를 입력하세요
    async with httpx.AsyncClient() as client:
        response = await client.get(f"https://api.weather.com/{city}?apiKey={API_KEY}")
        return response.text
```

### 라이센스

이 프로젝트는 MIT 라이센스 하에 배포됩니다. 자세한 내용은 LICENSE 파일을 참조하세요.

### 참고문서

- [Model Context Protocol 문서](https://modelcontextprotocol.io)
- [Model Context Protocol Python SDK 문서](https://github.com/modelcontextprotocol/python-sdk)
- [httpx 문서](https://www.python-httpx.org/)
- [Claude AI 문서](https://docs.anthropic.com)
