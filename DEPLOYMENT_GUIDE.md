# 프로젝트 업로드 가이드

GitHub/GitLab 등에 프로젝트를 업로드하기 위한 단계별 가이드입니다.

## 📋 사전 체크리스트

### 1단계: 민감한 정보 확인 ✅

다음 파일들이 `.gitignore`에 포함되어 있는지 확인:
- `.env` 파일들
- `application.yml`의 비밀번호 (이미 환경 변수로 변경됨)
- 데이터베이스 비밀번호
- API 키

**확인 방법:**
```powershell
# 프로젝트 루트에서 실행
Get-ChildItem -Recurse -Filter ".env*" | Select-Object FullName
```

### 2단계: Git 저장소 초기화

```powershell
# 프로젝트 루트로 이동
cd C:\Users\10HOME\Desktop\travel

# Git 초기화
git init

# 기본 브랜치 이름 설정 (main)
git branch -M main
```

### 3단계: .gitignore 확인

`.gitignore` 파일이 제대로 작동하는지 확인:

```powershell
# 무시될 파일들 확인
git status --ignored
```

다음 항목들이 무시되는지 확인:
- `node_modules/`
- `venv/`, `.venv/`
- `.env` 파일들
- `chroma_db/`
- `build/`, `dist/`, `target/`
- `__pycache__/`

### 4단계: 파일 추가 및 첫 커밋

```powershell
# 모든 파일 추가 (무시된 파일 제외)
git add .

# 추가된 파일 확인
git status

# 첫 커밋
git commit -m "Initial commit: Travel Planner project"
```

### 5단계: GitHub 저장소 생성

1. **GitHub 웹사이트 접속**
   - https://github.com 로그인

2. **새 저장소 생성**
   - 우측 상단 `+` 버튼 클릭 → `New repository`
   - Repository name: `travel` (또는 원하는 이름)
   - Description: "Travel Planner - 여행 계획 및 추천 애플리케이션"
   - Public 또는 Private 선택
   - ⚠️ **중요**: "Initialize this repository with a README" 체크하지 않기
   - "Add .gitignore" 선택하지 않기 (이미 있음)
   - "Choose a license" 선택하지 않기
   - `Create repository` 클릭

3. **원격 저장소 URL 복사**
   - 생성된 페이지에서 HTTPS 또는 SSH URL 복사
   - 예: `https://github.com/your-username/travel.git`

### 6단계: 원격 저장소 연결 및 푸시

```powershell
# 원격 저장소 추가 (위에서 복사한 URL 사용)
git remote add origin https://github.com/your-username/travel.git

# 원격 저장소 확인
git remote -v

# 메인 브랜치에 푸시
git push -u origin main
```

**인증이 필요한 경우:**
- GitHub Personal Access Token 사용 (비밀번호 대신)
- 또는 SSH 키 설정

### 7단계: 업로드 확인

1. GitHub 저장소 페이지 새로고침
2. 모든 파일이 올라갔는지 확인
3. `.env` 파일이 올라가지 않았는지 확인 (보안)

## 🔒 보안 체크리스트

업로드 전에 반드시 확인:

- [ ] `.env` 파일이 커밋되지 않았는지
- [ ] `application.yml`에 하드코딩된 비밀번호가 없는지
- [ ] API 키가 코드에 직접 작성되지 않았는지
- [ ] 데이터베이스 비밀번호가 노출되지 않았는지

**확인 명령어:**
```powershell
# 커밋된 파일 중 민감한 정보 검색
git log --all --full-history --source -- "*env*"
git log --all --full-history --source -- "*password*"
git log --all --full-history --source -- "*secret*"
```

## 📝 추가 설정 (선택사항)

### GitHub Actions 설정 (CI/CD)

`.github/workflows/` 폴더에 워크플로우 파일 추가 가능

### Issues 및 Projects 설정

- GitHub 저장소에서 Issues 활성화
- Projects 탭에서 프로젝트 관리 보드 생성

### Branch Protection Rules

메인 브랜치 보호 규칙 설정 (Settings → Branches)

## 🆘 문제 해결

### "fatal: remote origin already exists" 오류

```powershell
# 기존 원격 저장소 제거 후 다시 추가
git remote remove origin
git remote add origin https://github.com/your-username/travel.git
```

### "Permission denied" 오류

- GitHub Personal Access Token 생성 필요
- 또는 SSH 키 설정

### 큰 파일 업로드 오류

```powershell
# Git LFS 설치 및 설정 (이미지 파일 등)
git lfs install
git lfs track "*.jpg"
git lfs track "*.png"
git add .gitattributes
```

## ✅ 완료 확인

업로드가 성공적으로 완료되면:

1. ✅ GitHub 저장소에 모든 파일이 표시됨
2. ✅ README.md가 제대로 렌더링됨
3. ✅ `.gitignore`가 작동하여 불필요한 파일이 제외됨
4. ✅ 민감한 정보가 노출되지 않음

---

**다음 단계:** 팀원들과 협업하거나 배포 환경 설정을 진행하세요!
