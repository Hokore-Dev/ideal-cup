# 이상형 월드컵 (Ideal Cup)

토너먼트 형식으로 좋아하는 사진을 골라가는 이상형 월드컵 웹앱.
사진 개수에 따라 자동으로 토너먼트 라운드가 결정되고, 2의 제곱수가 아닐 경우 부전승으로 처리됩니다.

🔗 **Live Demo**: `https://[your-username].github.io/[repo-name]/`

---

## ✨ 기능

- 📸 사진 개수에 따라 자동 라운드 계산 (2강 / 4강 / 8강 / 16강 / 32강 ...)
- 🎲 부전승 자동 처리 (사진이 2의 제곱수가 아닐 때)
- 🔀 매 게임마다 랜덤 셔플
- 🏆 우승 사진 하이라이트 결과 화면
- 📱 모바일/데스크탑 반응형
- ⚡ 빌드 없음, 순수 HTML/CSS/JS

---

## 📁 폴더 구조

```
ideal-cup/
├── index.html              # 메인 페이지
├── README.md
├── .gitignore
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Pages 자동 배포
└── images/
    ├── manifest.json       # 사진 파일명 목록 (필수)
    ├── 1.jpg
    ├── 2.jpg
    └── ...
```

---

## 🚀 사진 추가하기

### 1. `images/` 폴더에 사진 업로드

원하는 사진을 `images/` 폴더에 넣어주세요. 파일명은 자유롭게 지을 수 있어요.
(`yoona.jpg`, `cat_01.png`, `참가자A.webp` 등 한글/영문 모두 가능)

### 2. `images/manifest.json`에 파일명 추가

```json
{
  "images": [
    "yoona.jpg",
    "iu.jpg",
    "karina.jpg",
    "winter.jpg"
  ]
}
```

> **주의**: 사진은 최소 2장 이상이어야 합니다.

### 3. Git에 푸시

```bash
git add .
git commit -m "add new photos"
git push
```

GitHub Actions가 자동으로 GitHub Pages에 배포해줍니다 (1-2분 소요).

---

## 🛠 GitHub Pages 배포 방법

자세한 단계는 [DEPLOY.md](DEPLOY.md)를 참고하세요.

요약:
1. GitHub에 새 레포 만들기 (Public)
2. 이 폴더 통째로 푸시
3. Settings → Pages → Source를 **"GitHub Actions"**로 설정
4. `https://[username].github.io/[repo-name]/` 에서 확인

---

## 💡 팁

- **사진 압축**: 1장당 500KB 이하 권장. [tinypng.com](https://tinypng.com)에서 무료 압축 가능
- **사진 비율**: 세로 3:4 비율이 가장 예쁘게 나옴 (가로 사진도 잘 보임)
- **파일 이름**: 공백보다는 `_`나 `-` 사용 권장 (`my_photo.jpg`)
- **로컬 테스트**: 브라우저에서 `index.html` 직접 열면 CORS 문제로 안 됨. 아래 명령어로 로컬 서버 띄우기:
  ```bash
  # Python
  python3 -m http.server 8000

  # Node.js (npx)
  npx serve
  ```
  그 후 `http://localhost:8000` 접속

---

## 🎨 커스터마이징

`index.html` 상단의 CSS 변수에서 색상을 바꿀 수 있어요:

```css
:root {
  --bg: #0e0e10;         /* 배경색 */
  --ink: #f5f1e8;        /* 글자색 */
  --accent: #ff3d2e;     /* 강조색 (빨강) */
  --accent-2: #ffd23f;   /* 보조 강조색 (노랑) */
}
```

---

## 📄 License

MIT
