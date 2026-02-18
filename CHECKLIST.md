# 🚀 프로젝트 업로드 체크리스트

## ✅ 1단계: 현재 상태 확인

- [ ] Git이 설치되어 있는지 확인
  ```powershell
  git --version
  ```

- [ ] 프로젝트 폴더로 이동
  ```powershell
  cd C:\Users\10HOME\Desktop\travel
  ```

- [ ] 현재 Git 상태 확인
  ```powershell
  git status
  ```
  (아직 저장소가 없으면 "not a git repository" 오류가 나옵니다 - 정상입니다)

---

## ✅ 2단계: Git 저장소 초기화

- [ ] Git 저장소 초기화
  ```powershell
  git init
  ```

- [ ] 기본 브랜치 이름을 main으로 설정
  ```powershell
  git branch -M main
  ```

---

## ✅ 3단계: 민감한 정보 최종 확인

- [ ] `.env` 파일이 있는지 확인 (있어도 괜찮음 - .gitignore에 포함됨)
  ```powershell
  Get-ChildItem -Recurse -Filter ".env*" -ErrorAction SilentlyContinue
  ```

- [ ] `application.yml`에 하드코딩된 비밀번호가 없는지 확인
  - 파일 열어서 `password: 1104` 같은 하드코딩이 없어야 함
  - 환경 변수 `${DB_PASSWORD:}` 형태여야 함 ✅

---

## ✅ 4단계: 파일 추가 및 커밋

- [ ] 모든 파일 추가 (무시 규칙 적용됨)
  ```powershell
  git add .
  ```

- [ ] 추가된 파일 목록 확인
  ```powershell
  git status
  ```
  
  **확인 사항:**
  - `.env` 파일이 목록에 없어야 함 ✅
  - `node_modules/` 폴더가 없어야 함 ✅
  - `venv/` 폴더가 없어야 함 ✅
  - `chroma_db/` 폴더가 없어야 함 ✅

- [ ] 첫 커밋 생성
  ```powershell
  git commit -m "Initial commit: Travel Planner project"
  ```

---

## ✅ 5단계: GitHub 저장소 생성

- [ ] GitHub 웹사이트 접속: https://github.com
- [ ] 로그인
- [ ] 우측 상단 `+` 버튼 → `New repository` 클릭
- [ ] Repository name 입력: `travel` (또는 원하는 이름)
- [ ] Description 입력 (선택사항): "Travel Planner - 여행 계획 및 추천 애플리케이션"
- [ ] Public 또는 Private 선택
- [ ] ⚠️ **중요**: 아래 항목들은 모두 체크하지 않기
  - ❌ Add a README file
  - ❌ Add .gitignore
  - ❌ Choose a license
- [ ] `Create repository` 버튼 클릭
- [ ] 생성된 페이지에서 HTTPS URL 복사
  - 예: `https://github.com/your-username/travel.git`

---

## ✅ 6단계: 원격 저장소 연결

- [ ] 원격 저장소 추가 (위에서 복사한 URL 사용)
  ```powershell
  git remote add origin https://github.com/your-username/travel.git
  ```
  ⚠️ `your-username`을 실제 GitHub 사용자명으로 변경하세요!

- [ ] 원격 저장소 확인
  ```powershell
  git remote -v
  ```
  origin이 두 번 표시되면 정상입니다.

---

## ✅ 7단계: 코드 푸시

- [ ] GitHub에 코드 업로드
  ```powershell
  git push -u origin main
  ```

- [ ] 인증 요청이 나오면:
  - **Username**: GitHub 사용자명 입력
  - **Password**: GitHub Personal Access Token 입력 (일반 비밀번호 아님!)
  
  Personal Access Token이 없으면:
  1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
  2. Generate new token (classic)
  3. `repo` 권한 체크
  4. Generate 후 토큰 복사 (한 번만 보여줌!)

---

## ✅ 8단계: 업로드 확인

- [ ] GitHub 저장소 페이지 새로고침
- [ ] 다음 항목 확인:
  - [ ] README.md가 제대로 표시되는지
  - [ ] 모든 폴더와 파일이 보이는지
  - [ ] `.env` 파일이 없는지 (보안)
  - [ ] `node_modules/` 폴더가 없는지
  - [ ] `venv/` 폴더가 없는지

---

## 🎉 완료!

프로젝트가 성공적으로 업로드되었습니다!

---

## 🆘 문제 발생 시

### "remote origin already exists" 오류
```powershell
git remote remove origin
git remote add origin https://github.com/your-username/travel.git
```

### "Permission denied" 오류
- Personal Access Token을 사용했는지 확인
- 또는 SSH 키 설정 필요

### "Large files" 경고
- 큰 이미지 파일이 있으면 Git LFS 사용 고려
- 또는 이미지 파일을 제외하고 업로드

---

**자세한 설명은 `DEPLOYMENT_GUIDE.md` 파일을 참고하세요!**
