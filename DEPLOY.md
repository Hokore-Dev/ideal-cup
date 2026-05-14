# 🚀 GitHub Pages 배포 가이드

처음부터 끝까지 따라 하면 5분 안에 배포할 수 있어요.

---

## 사전 준비

- [ ] GitHub 계정
- [ ] Git 설치 (`git --version`으로 확인)
- [ ] 업로드할 사진 파일들

---

## Step 1. GitHub 레포 만들기

1. [github.com/new](https://github.com/new) 접속
2. **Repository name** 입력 (예: `ideal-cup`)
3. **Public** 선택 ⚠️ (Private은 GitHub Pages 유료 플랜 필요)
4. **"Add a README file" 체크 안 함** (이미 있음)
5. **Create repository** 클릭

---

## Step 2. 로컬에서 푸시

### 옵션 A: 명령줄 사용 (추천)

```bash
# 이 ideal-cup 폴더 안에서
cd ideal-cup

# Git 초기화
git init
git add .
git commit -m "initial commit"

# main 브랜치로 변경
git branch -M main

# 원격 레포 연결 (URL은 본인 것으로 변경)
git remote add origin https://github.com/[your-username]/ideal-cup.git

# 푸시
git push -u origin main
```

### 옵션 B: GitHub Desktop 사용

1. [GitHub Desktop](https://desktop.github.com/) 설치
2. **File → Add Local Repository**로 이 폴더 추가
3. 커밋 메시지 입력 후 **Commit to main**
4. **Publish repository** 클릭

---

## Step 3. GitHub Pages 활성화

1. 본인 레포 페이지로 이동
2. 상단 **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 클릭
4. **Build and deployment** 섹션에서:
   - **Source**: `GitHub Actions` 선택 ⚠️ (Deploy from branch ❌)
5. 저장 완료

---

## Step 4. 배포 확인

1. 레포 상단 **Actions** 탭 클릭
2. "Deploy to GitHub Pages" 워크플로우가 실행 중인지 확인
3. 1-2분 뒤 ✅ 초록 체크 뜨면 배포 완료
4. **Settings → Pages**로 다시 가면 상단에 URL이 표시됨:
   ```
   Your site is live at https://[your-username].github.io/ideal-cup/
   ```

---

## Step 5. 사진 추가하기

### 첫 사진 업로드

```bash
# 사진들을 images/ 폴더에 복사
cp ~/Downloads/photo1.jpg images/
cp ~/Downloads/photo2.jpg images/
# ... 더 많이

# manifest.json 수정 (텍스트 에디터로 열기)
# images 배열에 파일명 추가

git add .
git commit -m "add photos"
git push
```

### manifest.json 예시

```json
{
  "images": [
    "photo1.jpg",
    "photo2.jpg",
    "photo3.jpg",
    "photo4.jpg"
  ]
}
```

푸시하면 자동으로 1-2분 후에 사이트에 반영됩니다.

---

## 🐛 문제 해결

### "사진이 안 보여요"
- `images/manifest.json` 파일명과 실제 파일명이 정확히 일치하는지 확인
- 대소문자 구분 (`Photo.JPG` ≠ `photo.jpg`)
- 브라우저 캐시 강제 새로고침: `Ctrl + Shift + R` (Mac: `Cmd + Shift + R`)

### "manifest.json을 찾을 수 없어요"
- `images/` 폴더 안에 `manifest.json`이 있는지 확인 (루트가 아님)
- 푸시가 완료됐는지 Actions 탭에서 확인

### "Actions 탭에 워크플로우가 안 보여요"
- `.github/workflows/deploy.yml` 파일이 푸시됐는지 확인
- 폴더명이 `.github` (점 포함)인지 확인

### "404 페이지가 떠요"
- Settings → Pages에서 Source가 **GitHub Actions**로 되어있는지 확인
- 첫 배포는 시간이 좀 걸릴 수 있음 (최대 10분)

---

## 🔄 매번 사진 업데이트할 때

```bash
# images/ 폴더에 사진 추가
# manifest.json 수정

git add .
git commit -m "update photos"
git push
```

끝. 1-2분 후 자동 반영.
