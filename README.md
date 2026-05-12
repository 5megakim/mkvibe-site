# mkvibe.com

메가킴이 AI와 함께 바이브 코딩으로 만드는 도구들의 홈.

## 폴더 구조

```
mkvibe-site/
├── index.html              # 메인 랜딩 페이지
├── assets/
│   ├── icon.png           # 파비콘
│   ├── og-image.png       # 소셜 공유 카드
│   └── ...
├── megabite/              # MK 유튜브 다운로더 관련
│   ├── announcement.json  # 앱 팝업 공지 (앱이 호출)
│   ├── version.json       # 앱 버전 체크 (옵션)
│   └── download/          # 인스톨러 .exe 호스팅
└── README.md
```

## 배포 — Cloudflare Pages

### 1회 설정
1. GitHub 새 레포: `megakim/mkvibe-site`
2. 이 폴더 git push
3. Cloudflare Dashboard → Pages → Create project
4. GitHub 연동 → 레포 선택
5. Build command: (비워둠 - 정적 사이트)
6. Output directory: `/`
7. 배포 완료 → `<random>.pages.dev` 자동 URL

### 커스텀 도메인 연결
1. Cloudflare Pages → Custom domains
2. `mkvibe.com` 추가
3. Cloudflare가 DNS 자동 설정 (이미 도메인이 Cloudflare에 있으면 1-click)
4. 5분 안에 https://mkvibe.com 활성화

### 이후 업데이트
- 파일 수정 → git push
- 1~2분 안에 mkvibe.com 자동 갱신

## announcement.json 사용법

앱이 시작 시 `https://mkvibe.com/megabite/announcement.json` 을 호출합니다.

### 공지 끄기
```json
{ "id": "" }
```

### 신제품 출시 공지
```json
{
  "id": "v2-launch-2026-09",
  "title": "🎉 새 버전 v2.0 출시!",
  "body": "AI 쇼츠 자동 생성 기능 추가...",
  "image_url": "https://mkvibe.com/assets/v2-banner.png",
  "link_url": "https://mkvibe.com/changelog/v2",
  "button_text": "변경사항 보기",
  "show_from": "2026-09-01",
  "show_until": "2026-10-01",
  "accent": "#a855f7"
}
```

각 공지는 `id`로 관리되어, 사용자가 한 번 닫으면 같은 ID는 다시 안 뜸.
새 공지 보내려면 `id` 값을 새로 줘야 함.

## 인스톨러 호스팅

`megabite/download/` 폴더에 `.exe` 파일 업로드.

또는 GitHub Releases 사용 권장 (대용량 파일에 더 적합):
- 레포: `megakim/mkdownloader`
- Release 페이지에 .exe 업로드
- index.html의 다운로드 링크를 GitHub Releases URL로 변경

## 로컬 미리보기

```bash
# Python (있으면)
python -m http.server 8000
# → http://localhost:8000

# 또는 Node.js
npx serve .

# 또는 그냥 브라우저로 index.html 열기
```
