# Live Wire

차분한 회로 퍼즐 게임. 15개 모드, 3,300 스테이지, 무한 모드.

- 게임 본체: [`index.html`](index.html) (단일 파일, 브라우저에서 바로 실행)
- 안드로이드 앱: [`android/`](android) (WebView로 `index.html`을 감싼 앱)

## APK 받기

`main` 브랜치에 push할 때마다 GitHub Actions가 APK를 자동으로 빌드합니다.

- 최신 APK: **Releases → `LiveWire.apk`**
  (`https://github.com/<owner>/<repo>/releases/latest/download/LiveWire.apk`)
- 또는 **Actions → Build APK → 실행 기록 → Artifacts**
- 수동 빌드: **Actions → Build APK → Run workflow**

폰에서 APK를 열면 설치됩니다. 처음엔 "출처를 알 수 없는 앱 설치"를 허용해야 할 수 있어요.
모든 빌드는 같은 키로 서명되므로, 새 버전을 덮어 설치해도 진행 기록이 유지됩니다.

## 직접 빌드

JDK 17+, Android SDK(platform 35)가 필요합니다.

```sh
cd android
./gradlew assembleRelease
# → android/app/build/outputs/apk/release/app-release.apk
```

## 앱 구성

- 빌드할 때 `index.html`을 앱 assets로 복사하고, Google Fonts 링크를 앱에 포함된 폰트로 바꿔 오프라인에서도 동작합니다.
- 전체 화면, 화면 꺼짐 방지, 뒤로가기 버튼으로 게임 화면 이동(타이틀에서 누르면 앱 나가기).
- 서명 키(`android/app/livewire.keystore`, 비밀번호 `livewire`)는 개인 배포용입니다. Play 스토어에 올릴 땐 별도 키로 바꾸세요.
- 폰트: Rubik, IBM Plex Mono (SIL Open Font License 1.1)
