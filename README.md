# Web Game Homepage

Krafton Jungle 10기 WEEK14 프로젝트 - 게임을 플레이하고 커뮤니티에 참여할 수 있는 웹 게임 홈페이지 플랫폼

## 프로젝트 개요

게시판 기능과 임베디드 게임을 제공하는 풀스택 웹 애플리케이션입니다. 사용자는 계정을 생성하고, 게임을 플레이하며, 커뮤니티 게시판을 통해 소통할 수 있습니다.

## 프로젝트 구조

```
Krafton_Jungle_10th_WebPage_WEEK14/
├── my-board/                          # React 프론트엔드 (Vite)
│   ├── src/
│   │   ├── components/
│   │   │   ├── Auth.jsx              # 인증 UI (로그인, 회원가입, 비밀번호 찾기)
│   │   │   ├── Board.jsx             # 게임 게시판 & 게시글 관리
│   │   │   └── MyPage.jsx            # 사용자 프로필 & 비밀번호 관리
│   │   ├── App.jsx                   # 메인 앱 라우팅 & 상태 관리
│   │   ├── main.jsx                  # React 엔트리 포인트
│   │   └── *.css                     # 스타일 시트
│   ├── vite.config.js               # Vite 빌드 설정
│   ├── tailwind.config.js           # Tailwind CSS 설정
│   └── package.json                 # 프론트엔드 의존성
│
├── board-backend/                     # Python FastAPI 백엔드
│   ├── main.py                       # 백엔드 서버 (모든 API 라우트)
│   ├── create_sample_posts.py        # 샘플 게임 게시글 생성 스크립트
│   └── static/
│       ├── games/                    # 임베디드 WebGL 게임들
│       │   ├── alicepang/            # Alice Pang (모바일 퍼즐 게임)
│       │   ├── AntCompany/           # Ant Company 게임
│       │   └── watermelon/           # 수박 게임 (Three.js)
│       └── images/                   # 정적 이미지 파일
│
└── README.md                         # 프로젝트 문서
```

## 웹페이지 스크린샷
  <img width="994" height="542" alt="image" src="https://github.com/user-attachments/assets/aa1b5d2d-1e95-4ed2-9c31-6fd4e78095f4" />


## 주요 기능

### 인증 시스템
- **회원가입**: 아이디, 이메일, 비밀번호, 성별, 생년월일 입력
- **로그인/로그아웃**: JWT 토큰 기반 인증 (30분 만료)
- **토큰 자동 갱신**: 25분마다 자동으로 토큰 갱신
- **아이디 찾기**: 이메일 + 생년월일로 아이디 조회
- **비밀번호 초기화**: 이메일로 임시 비밀번호 발송
- **관리자 계정**: 특별 권한을 가진 관리자 모드
- **마이페이지**: 비밀번호 변경 및 프로필 관리

### 게임 게시판
- **게임 플레이**: Unity WebGL 및 Three.js 게임 임베디드
- **게임 카테고리**: "Unity 게임", "Three.js 게임", "시뮬레이터"
- **게시글 관리**: 작성, 조회, 수정, 삭제
- **조회수 추적**: 게시글 조회 시 자동 증가
- **카테고리 필터링**: 카테고리별 게시글 분류
- **댓글 시스템**: 게시글에 댓글 작성 및 삭제

### 포함된 게임
- **Alice Pang**: 모바일 퍼즐 게임
- **Ant Company**: Unity 기반 시뮬레이션 게임
- **Watermelon Game**: Three.js 기반 수박 게임

### 사용자 기능
- 프로필 이미지 설정
- 비밀번호 변경
- 작성자별 게시글 관리
- 댓글 작성 및 관리

## 기술 스택

### 프론트엔드
- **React 19.1.1**: 최신 React 프레임워크
- **React Router 7.9.4**: 클라이언트 사이드 라우팅
- **Vite**: 빠른 빌드 도구 및 HMR
- **Tailwind CSS 3.4**: 유틸리티 퍼스트 CSS 프레임워크
- **Axios 1.12**: HTTP 클라이언트
- **ESLint**: 코드 린팅

### 백엔드
- **Python**: 코어 언어
- **FastAPI**: 모던 비동기 웹 프레임워크
- **MongoDB (Motor)**: 비동기 MongoDB 드라이버
- **JWT (PyJWT)**: 토큰 기반 인증
- **bcrypt**: 비밀번호 암호화
- **SMTP**: 이메일 발송 (Gmail 연동)
- **Uvicorn**: ASGI 서버

### 데이터베이스
- **MongoDB**: NoSQL 데이터베이스
  - `users_collection`: 사용자 계정 및 프로필
  - `posts_collection`: 게임 게시글
  - `comments_collection`: 게시글 댓글
  - `scores_collection`: 게임 점수

## 설치 및 실행

### 사전 요구사항
- Python 3.8 이상
- Node.js 16 이상
- MongoDB 4.0 이상

### 1. MongoDB 설치 및 실행

MongoDB가 `localhost:27017`에서 실행 중이어야 합니다.

```bash
# MongoDB 실행 확인
mongod --version
```

### 2. 백엔드 설치 및 실행

```bash
cd board-backend

# 의존성 설치
pip install fastapi motor pymongo bcrypt pyjwt python-multipart uvicorn

# 서버 실행
python main.py
```

백엔드는 `http://localhost:8000`에서 실행됩니다.

#### 샘플 데이터 생성 (선택사항)

```bash
python create_sample_posts.py
```

### 3. 프론트엔드 설치 및 실행

```bash
cd my-board

# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 프로덕션 빌드
npm run build
```

프론트엔드는 `http://localhost:5173`에서 실행됩니다.

## 환경 설정

### 이메일 설정 (필수)

비밀번호 찾기 기능을 사용하려면 Gmail SMTP 설정이 필요합니다.

[board-backend/main.py](board-backend/main.py)의 이메일 설정을 수정하세요:

```python
EMAIL_ADDRESS = "your-email@gmail.com"
EMAIL_PASSWORD = "your-app-password"
```

#### Gmail 앱 비밀번호 생성 방법:
1. Google 계정 → 보안 → 2단계 인증 활성화
2. 앱 비밀번호 생성
3. 생성된 16자리 코드를 `EMAIL_PASSWORD`에 입력

### JWT Secret Key 설정 (프로덕션 환경)

보안을 위해 [board-backend/main.py](board-backend/main.py)의 JWT Secret Key를 변경하세요:

```python
SECRET_KEY = "your-secure-random-secret-key"
```

### 관리자 계정

기본 관리자 계정:
- 아이디: `admin`
- 비밀번호: `admin`

> **주의**: 프로덕션 환경에서는 반드시 관리자 비밀번호를 변경하세요.

## API 엔드포인트

### 인증 (`/api/auth/`)
| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| POST | `/register` | 회원가입 |
| POST | `/login` | 로그인 (JWT 토큰 반환) |
| POST | `/refresh` | 토큰 갱신 |
| GET | `/me` | 현재 사용자 정보 조회 |
| POST | `/find-userid` | 아이디 찾기 |
| POST | `/reset-password` | 비밀번호 초기화 (이메일 발송) |
| POST | `/change-password` | 비밀번호 변경 |
| GET | `/check-admin` | 관리자 권한 확인 |

### 게시판 (`/api/posts/`)
| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| GET | `/` | 전체 게시글 조회 (필터링 가능) |
| POST | `/` | 게시글 작성 |
| GET | `/{postId}` | 게시글 상세 조회 (조회수 증가) |
| PUT | `/{postId}` | 게시글 수정 |
| DELETE | `/{postId}` | 게시글 삭제 |

### 댓글 (`/api/posts/{postId}/comments`)
| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| GET | `/` | 게시글 댓글 조회 |
| POST | `/` | 댓글 작성 |
| DELETE | `/{commentId}` | 댓글 삭제 |

### 게임 점수 (`/api/scores/`)
| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| POST | `/save` | 게임 점수 저장 |
| GET | `/leaderboard` | 리더보드 조회 |

## 주요 기술 특징

### 보안
- **비밀번호 암호화**: bcrypt를 사용한 안전한 해싱
- **JWT 인증**: 30분 만료 토큰, 자동 갱신 메커니즘
- **CORS 설정**: 안전한 Cross-Origin 요청 처리

### 성능
- **비동기 처리**: Motor를 사용한 논블로킹 MongoDB 쿼리
- **빠른 빌드**: Vite의 HMR로 개발 생산성 향상
- **최적화된 번들**: 프로덕션 빌드 최적화

### 사용자 경험
- **반응형 디자인**: Tailwind CSS로 모바일 친화적 UI
- **자동 토큰 갱신**: 사용자 세션 자동 유지
- **실시간 피드백**: 폼 유효성 검사 및 에러 메시지

## 문제 해결

### MongoDB 연결 오류
```bash
# MongoDB 실행 상태 확인
mongod --version

# MongoDB 서비스 시작 (Windows)
net start MongoDB

# MongoDB 서비스 시작 (Linux/Mac)
sudo systemctl start mongod
```

### 포트 충돌
- 백엔드 포트 변경: [board-backend/main.py](board-backend/main.py)에서 `port` 수정
- 프론트엔드 포트 변경: [my-board/vite.config.js](my-board/vite.config.js)에서 `port` 수정

### CORS 에러
[board-backend/main.py](board-backend/main.py)의 CORS 설정에서 프론트엔드 URL 확인:
```python
origins = [
    "http://localhost:5173",  # Vite 개발 서버
]
```

## 개발 로드맵

### 완료된 기능
- ✅ JWT 기반 인증 시스템
- ✅ 게시판 CRUD 기능
- ✅ 댓글 시스템
- ✅ 이메일 인증 및 비밀번호 찾기
- ✅ 게임 임베딩
- ✅ 관리자 모드

### 향후 계획
- 🔲 게임 점수 랭킹 시스템 고도화
- 🔲 소셜 로그인 (Google, Kakao)
- 🔲 실시간 채팅 기능
- 🔲 게시글 검색 기능
- 🔲 파일 업로드 기능

## 기여

기여를 환영합니다! 다음 단계를 따라주세요:

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 라이선스

MIT License

## 개발자

Krafton Jungle 10기 프로젝트

## 문의

프로젝트에 대한 문의사항이나 버그 리포트는 Issues 탭을 이용해주세요.
