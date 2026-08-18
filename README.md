# MCM Hidden Boarding — 이벤트 페이지

보딩패스 티켓의 QR을 찍은 손님이 만나는 **숨은 이벤트** 페이지입니다.
닫힌 티켓을 누르면 뒤집히며 "히든 탑승객" 당첨 연출과 혜택 안내가 열립니다.

- 빌드 없는 정적 페이지 — `index.html` 하나가 전부입니다
- 티켓 QR이 실어 보낸 패스 코드는 쿼리로 받습니다: `/?pass=MCM-A1B2C3D4`
  (없이 열어도 `HIDDEN-GUEST`로 동작)
- CTA는 메인 서비스(`boardingpass-seven.vercel.app/boarding-pass`)로 잇습니다
- 색·무드는 메인 앱의 보딩패스 무대 토큰을 그대로 씁니다

## 배포

정적 호스팅 어디든 됩니다.

- **Vercel**: 이 저장소를 Import → 프레임워크 "Other" → 빌드 명령 없음, 출력 디렉터리 `.`
- **GitHub Pages**: Settings → Pages → Branch `main` / root

## 배포 후 메인 앱 연결

메인 앱(FE)의 티켓 QR 값을 이 페이지 주소로 바꿉니다:

```js
// src/features/boarding-pass/boarding-ticket/BoardingTicketCard.jsx
const qrValue = `https://<배포 주소>/?pass=${encodeURIComponent(passCode)}`
```

## 문구 수정

혜택 안내는 `index.html`의 `<!-- 혜택 문구는 ... -->` 주석 아래 한 곳입니다.
