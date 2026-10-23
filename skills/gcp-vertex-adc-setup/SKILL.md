---
name: gcp-vertex-adc-setup
description: 구글 클라우드 가입부터 Vertex AI ADC 연결, gcloud 설치, 동작 확인까지 순서대로 안내하고 에이전트에게 설치를 시킨다. "Vertex AI 연결해줘", "ADC 설정", "gcloud 설치", "구글 클라우드 연동", "제미나이 영상 API" 요청에 쓴다.
---

# 구글 클라우드 Vertex AI ADC 연결

## 언제 쓰나
Vertex AI(제미나이 이미지·비디오 모델)를 코드나 에이전트에서 쓰려는데 인증이 없을 때.
ADC = Application Default Credentials. 구글 계정 로그인 한 번으로 API 키 없이 인증하는 방식이다.

## 3단계 (사람이 하는 것)

### 1단계 — 가입 (사람만 가능)
1. 구글에서 **"구글 클라우드 콘솔"** 검색
2. **무료로 시작하기** → 약관 동의
3. 주소·카드 입력 (무료 크레딧 구간에서는 청구되지 않지만, 카드 등록은 필요하다)
4. 프로젝트 생성

> 카드 정보는 절대 채팅·로그·파일에 남기지 않는다. 사용자가 직접 브라우저에 입력한다.

### 2단계 — ADC 연결 (에이전트가 실행)
```powershell
gcloud auth application-default login
```
- 브라우저 로그인 창이 뜨면 방금 만든 계정으로 로그인 → **허용** 클릭
- 창이 안 뜨면 URL이 콘솔에 출력된다. 그걸 복사해 브라우저에 붙여넣는다.

### 3단계 — gcloud 설치 (없을 때)
```powershell
winget install --id Google.CloudSDK -e
```
- 설치 후 **새 터미널**을 열어야 PATH가 잡힌다.
- 확인: `gcloud --version`

## 연결 확인 (반드시 실행)

```powershell
gcloud auth application-default print-access-token
```
- 토큰 문자열이 나오면 성공.
- `ERROR: (gcloud.auth.application-default.print-access-token) There is no active credential` → 2단계 미완료.

```powershell
gcloud config get-value project
```
- 프로젝트 ID가 나와야 한다. `(unset)` 이면:
```powershell
gcloud config set project <프로젝트ID>
```

## 실제 동작 확인
```powershell
python -c "from google.auth import default; c,p=default(); print('OK', p)"
```
`OK <프로젝트ID>` 가 나오면 파이썬에서 바로 쓸 수 있다.

## 자주 막히는 곳
| 증상 | 원인 | 해결 |
|---|---|---|
| `gcloud` 인식 안 됨 | PATH 미반영 | 새 터미널 열기, 안 되면 재부팅 |
| 로그인 창이 안 뜸 | 헤드리스 환경 | 출력된 URL 복사해 직접 열기 |
| `permission denied` | API 미활성 | 콘솔에서 Vertex AI API 사용 설정 |
| 결제 오류 | 무료 크레딧 소진 | 콘솔에서 결제 상태 확인 — **임의로 결제하지 않는다** |

## 체크리스트
- [ ] `print-access-token` 이 토큰을 반환
- [ ] `config get-value project` 가 프로젝트 ID를 반환
- [ ] 파이썬 `google.auth.default()` 가 OK
- [ ] 카드·토큰이 채팅·파일에 남지 않았다

---

출처: @autofrog.kr Threads 저장글 (구글 클라우드 무료 가입 → ADC)
