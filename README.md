# Travel Planner 프로젝트

여행 계획 및 추천을 위한 풀스택 애플리케이션입니다.

## 📁 프로젝트 구조

```
travel/
├── backend-fastapi/          # FastAPI 백엔드 (Python)
├── travel-backend-springboot/ # Spring Boot 백엔드 (Java)
└── travel-frontend/          # React 프론트엔드 (JavaScript)
```

## 🚀 시작하기

### 사전 요구사항

- **Python 3.8+** (FastAPI 백엔드용)
- **Java 17+** (Spring Boot 백엔드용)
- **Node.js 18+** (프론트엔드용)
- **MariaDB/MySQL** (데이터베이스)
- **Redis** (캐시 및 세션 관리)
- **MongoDB** (문서 저장소)

### 1. FastAPI 백엔드 설정

```bash
cd backend-fastapi

# 가상환경 생성 및 활성화
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate

# 의존성 설치
pip install -r requirements.txt

# 환경 변수 설정 (.env 파일 생성)
# GOOGLE_API_KEY=your_api_key
# MARIADB_HOST=127.0.0.1
# MARIADB_PASSWORD=your_password

# 서버 실행
uvicorn main:app --reload
```

서버는 `http://127.0.0.1:8000`에서 실행됩니다.

자세한 내용은 [backend-fastapi/RUN.md](backend-fastapi/RUN.md)를 참고하세요.

### 2. Spring Boot 백엔드 설정

```bash
cd travel-backend-springboot

# 환경 변수 설정
# Windows PowerShell
$env:GOOGLE_CLIENT_ID="your_client_id"
$env:GOOGLE_CLIENT_SECRET="your_client_secret"
$env:JWT_SECRET="your_jwt_secret"
$env:DB_USERNAME="root"
$env:DB_PASSWORD="your_password"

# Linux/Mac
export GOOGLE_CLIENT_ID=your_client_id
export GOOGLE_CLIENT_SECRET=your_client_secret
export JWT_SECRET=your_jwt_secret
export DB_USERNAME=root
export DB_PASSWORD=your_password

# Gradle로 빌드 및 실행
./gradlew bootRun
# 또는 Windows
gradlew.bat bootRun
```

서버는 `http://localhost:8080`에서 실행됩니다.

### 3. React 프론트엔드 설정

```bash
cd travel-frontend

# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 프로덕션 빌드
npm run build
```

## 🔧 환경 변수 설정

### FastAPI 백엔드 (.env)

```env
# Google Gemini API
GOOGLE_API_KEY=your_api_key

# MariaDB 설정
MARIADB_HOST=127.0.0.1
MARIADB_PASSWORD=your_password

# 타임아웃 설정 (선택사항)
LLM_TIMEOUT_SEC=25
GRAPH_TIMEOUT_SEC=60
```

### Spring Boot 백엔드

환경 변수로 설정하거나 `application.yml`에서 기본값을 변경할 수 있습니다:

- `GOOGLE_CLIENT_ID`: Google OAuth 클라이언트 ID
- `GOOGLE_CLIENT_SECRET`: Google OAuth 클라이언트 시크릿
- `JWT_SECRET`: JWT 토큰 서명용 시크릿 (Base64 인코딩, 최소 64바이트)
- `DB_USERNAME`: 데이터베이스 사용자명 (기본값: root)
- `DB_PASSWORD`: 데이터베이스 비밀번호

## 📚 주요 기능

- **여행 스타일 분석**: 사용자의 여행 선호도를 분석하여 맞춤형 추천 제공
- **여행지 추천**: AI 기반 여행지 및 숙소 추천
- **OAuth 인증**: Google OAuth를 통한 소셜 로그인
- **실시간 채팅**: WebSocket을 통한 실시간 상담 기능

## 🛠 기술 스택

### Backend (FastAPI)
- FastAPI
- LangChain / LangGraph
- ChromaDB (벡터 DB)
- Google Gemini AI
- MariaDB
- Sentence Transformers

### Backend (Spring Boot)
- Spring Boot
- Spring Security
- Spring Data JPA
- MariaDB
- Redis
- MongoDB
- JWT

### Frontend
- React
- Vite
- React Router
- Axios
- SockJS / STOMP (WebSocket)

## 📝 API 문서

- **FastAPI**: `http://127.0.0.1:8000/docs`
- **Spring Boot**: `http://localhost:8080/swagger-ui.html`

## ⚠️ 주의사항

1. **민감한 정보**: `.env` 파일과 `application.yml`의 비밀번호는 절대 Git에 커밋하지 마세요.
2. **데이터베이스**: 프로덕션 환경에서는 반드시 환경 변수를 사용하여 데이터베이스 비밀번호를 설정하세요.
3. **API 키**: Google API 키는 환경 변수로 관리하고 공개 저장소에 노출하지 마세요.

## 📄 라이선스

이 프로젝트는 개인 프로젝트입니다.
