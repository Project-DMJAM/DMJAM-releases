# DMJAM

DMJAM 의 Windows, Mac 배포본을 올리는 저장소입니다. 소스 코드는 없습니다.

## 내려받기

[Releases](../../releases/latest) 에서 가장 최근 버전을 받습니다.

| 파일 | 대상 |
|---|---|
| `DMJAM-x.y.z-setup.exe` | Windows 10, 11 (64비트) 설치 프로그램. 처음 설치할 때 받습니다 |
| `DMJAM-x.y.z-mac.zip` | macOS (Apple Silicon, Intel) |
| `DMJAM-x.y.z-windows-x64.zip` | Windows 설치 프로그램 없이 쓰는 압축본. 게임의 자동 업데이트가 받는 파일입니다 |

`latest.json`, `latest.json.sig` 는 게임이 자동 업데이트에 쓰는 파일입니다. 받지 않아도 됩니다.

## 설치

### Windows

1. `DMJAM-x.y.z-setup.exe` 를 실행합니다.
   - "Windows의 PC 보호" 창이 뜨면 **추가 정보** > **실행** 을 누릅니다. 코드 서명 인증서를 쓰지 않아서 뜨는 창입니다.
2. 안내에 따라 설치합니다. 관리자 권한은 묻지 않습니다.
   - 설치 위치는 `%LOCALAPPDATA%\Programs\DMJAM` 입니다. 게임이 이 폴더를 직접 고쳐 자동 업데이트를 하기 때문에 위치를 고르지 않습니다.
   - 바탕화면 바로가기와 시작 메뉴 바로가기를 만듭니다. 바탕화면 바로가기는 설치할 때 끌 수 있습니다.
3. 지울 때는 설정 > 앱 에서 **DMJAM** 를 제거합니다. 설정, 기록, 곡은 지워지지 않습니다.

### Mac

1. zip 을 풀어 나온 `DMJAM.app` 을 **응용 프로그램** 폴더로 옮깁니다.
   - 다운로드 폴더에서 바로 실행하면 macOS 가 앱을 임시 위치에서 실행해서 자동 업데이트를 하지 못합니다.
2. 처음 한 번 터미널에서 아래 명령을 실행합니다. Apple 공증을 받지 않은 앱이라 이 명령 없이 열면 "손상되었기 때문에 열 수 없습니다" 로 막힙니다.
   ```
   xattr -dr com.apple.quarantine /Applications/DMJAM.app
   ```
   명령 대신 시스템 설정 > 개인정보 보호 및 보안 에서 **그래도 열기** 를 눌러도 됩니다.

## 자동 업데이트

- 게임을 켜면 새 버전이 있는지 확인하고, 있으면 메인 메뉴에 업데이트 창을 띄웁니다.
- **업데이트** 를 누르면 진행 막대가 보이고, 끝나면 게임이 꺼졌다가 새 버전으로 다시 켜집니다. 따로 할 일은 없습니다.
- 받는 중에 창을 닫으면 멈추고, 다음에 업데이트하면 받은 데부터 이어받습니다.
- 게임은 이 저장소의 `latest.json` 서명과 파일의 SHA-256 이 맞을 때만 새 버전을 설치합니다.
- 설정, 기록, 리플레이, 추가한 곡은 설치 폴더 밖 (Windows `%USERPROFILE%\AppData\LocalLow\FujiGraphics\DMJAM`, Mac `~/Library/Application Support/com.FujiGraphics.DMJAM`) 에 있어서 업데이트해도 그대로 남습니다.
- 자동 업데이트가 들어가기 전 버전을 쓰고 있다면, 한 번은 이곳에서 새 버전을 받아 설치합니다.

## 업데이트가 안 될 때

- 업데이트 창에 막힌 이유가 나옵니다.
- 교체 기록은 아래 파일에 남습니다. 문제를 알릴 때 같이 보내 주세요.
  - Windows: 설치 폴더의 `.update\update.log`
  - Mac: `~/Library/Application Support/com.FujiGraphics.DMJAM/Updates/update.log`
- 언제든 이곳에서 새 설치 프로그램을 받아 다시 설치하면 됩니다. 설정, 기록, 곡은 그대로 남습니다.
