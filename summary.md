# Threads 저장글 분석 요약 (2026-10-24)

## 범위

- 저장 목록: `posts-partial.json` 기준 **674개 글**
- 상세 수집(details2): 본문·댓글·링크·이미지 URL
- 캐러셀 수집(media): 글당 이미지 전체 URL
- OCR: 캐러셀 이미지 안의 글자를 tesseract `kor+eng`로 추출

## 수집 방법과 한계

1. 무한 스크롤로 저장글 목록을 끝까지 받는다.
2. 글마다 개별 방문해 본문·댓글·링크를 뽑는다.
3. 캐러셀은 DOM에 4장만 있어 **원본 HTML에서 `scontent.*.fbcdn.net` URL을 정규식으로 전수 추출**한다.
4. 링크는 `l.threads.net/?u=` 래핑, 이중 인코딩(`%252F`), `&amp;`를 다단계 디코딩한다.
5. 이미지 속 글자는 OCR로 뽑는다.

**한계 (숨기지 않고 적는다)**
- Threads는 긴 텍스트를 "더 보기"로 접는다. 처음에는 댓글 4건이 잘린 것으로 봤으나,
  **"더 보기"를 클릭해 실제로 확인한 결과 3건은 잘린 것이 아니었다**
  (@ai.corder, @crome.ai, @han45406480). "더 보기" 표시가 **완결된 본문 뒤에** 붙어 있었고,
  문장이 자연스럽게 끝난다. 즉 표시만 보고 잘렸다고 판단한 것이 오판이었다.
- **실제로 잘린 것은 1건**: @hyun.doyun `DdhBSS2E9L2`. 댓글이 `예:`에서 끊긴다.
  "더 보기"를 클릭해도 그 지점 이후가 나오지 않아, 서버 쪽에서 잘린 것으로 보인다.
  이 1건은 `prompts-strict.md`에 `[원문 접힘]`으로 표시했다.
- 펼치기 클릭은 **보이는 요소**를 눌러야 한다. Threads는 같은 "더 보기"를 0×0 숨은 복제본으로도
  렌더해서, 좌표를 안 보고 누르면 아무 일도 일어나지 않는다(이걸로 한 번 헛돌았다).
- 캡처 스크립트는 댓글당 4,000자를 넘기지 않는다. 4,000자에 닿은 항목은 절단으로 표시했다.
- bsk 세션이 조용히 죽는 문제가 있었다. 수집이 멈춘 채로 진행률만 세던 구간이 있어, 이후 `bsk session list` + 파일 생성 시각으로 교차 확인했다.

## 프롬프트

- 전수 스캔 후 **프롬프트 후보 신호 글 84건**을 사람이 다시 읽었다.
- 그중 **원문 확보 23건**을 `prompts-extracted.md`에 원문 그대로 실었다.
- 요약하지 않았다. 원문이 없으면 "없다"고 적었다.
- 후보였지만 채택하지 않은 것은 각 차수 갱신 이력에 이유와 함께 남겼다.

### 추가 스캔 및 병합 (2026-10-24)

1차 자동 스캔은 "프롬프트"라는 **단어가 들어간 잡담**까지 후보로 잡아 90~104건을 쏟아냈다.
예: "후자입니다! 프롬프트 한번으로 알아서 해주더라고요" — 이건 지시문이 아니라 감상이다.

그래서 판정을 **단어가 아니라 형태**로 바꿨다(`scan_strict.py`).

**필수 관문** — 아래 둘을 모두 만족해야 지시문으로 인정한다:
1. AI에게 역할을 부여한다: `당신은`/`너는`/`You are` + (이다·역할·전문가·디렉터·You are a…)
2. 산출물을 요구한다: `~해 주세요`/`작성해`/`정리해`/`write`/`generate` …

번호만 죽 나열한 목록(사업자 진단 질문지, AI 도구 소개 등)은 역할 부여가 없으므로 **탈락**한다.
점수는 보조 지표일 뿐이고, 관문을 못 넘으면 점수와 무관하게 버린다.

결과: details2 **674건 전체**를 훑어 **실제 신규 지시문 5건**만 남았다.
기존 18건에 이어 신규 5건을 병합해 23건으로 갱신했다.

| # | 출처 | 내용 |
|---|---|---|
| 1 | @key_te_ss `DbYrN3ZCQ74` | 광고제 CD 페르소나 — 15장 브랜드 필름 시나리오 |
| 2 | @playto876 `Dees4Nskl_T` | 제휴 마케팅 분석가 — 클릭률 표·다음 상품 제안 |
| 3 | @just_ai_case `Delp7vPmGpf` | 근력운동 코치 — ACSM 지침 기반 주간 운동표 |
| 4 | @neulhoon `DXtV49WATn8` | 한국 음식 광고 디자이너 — 이미지 광고 프롬프트(영문) |
| 5 | @work.less.better `DX8QyLcAULT` | 네이버 스마트스토어 상세페이지 **이미지 생성** 디자이너 |

원문은 `prompts-strict.md`에 그대로 있다.
5번은 사용자가 지금 하는 스마트스토어 상세페이지 작업과 직접 맞물린다.

### OCR에서 나온 프롬프트: 0건

이미지 1,403장에서 의미 있는 텍스트 1,118장·약 196만 자를 뽑았지만,
같은 관문(역할 부여 + 산출물 요구)을 통과한 지시문은 **0건**이다.
캐러셀 이미지는 대부분 광고 카드·스크린샷이고, 프롬프트 원문은 본문이나 댓글에 있었다.

### 채택 기준

| 신호 | 설명 |
|---|---|
| 명시적 표기 | 프롬프트·prompt·지시문·system prompt·instruction |
| 역할 부여 | "You are", "당신은", "너는" |
| 구조 | 코드블록 안의 다단계 지시, 출력 형식 지정 |
| 재사용성 | 제품명만 바꾸면 다른 작업에 쓸 수 있는가 |

### 스킬로 만든 것 (13개)

| 스킬 | 원문 출처 |
|---|---|
| `goal-prompt-builder` | @ai.corder |
| `multi-agent-session-brief` | @ais.root |
| `image-prompt-portrait` | @han45406480 |
| `video-shotlist-prompt` | @reactor_art, @imusiro |
| `batch-image-gen-orchestrator` | @bunniesossdev |
| `gcp-vertex-adc-setup` | @autofrog.kr |
| `detailpage-skill-builder` | @gptaku_ai |
| `blog-content-pipeline` | @a_book_builder |
| `motion-video-brief-builder` | @chris_gomdori, @crome.ai |
| `side-hustle-design` | @gpt_park |
| `thread-content-strategist` | @hyun.doyun |
| `reference-video-editing-skill` | @jachung__ |
| `hyperframes-renderer` | @ai_ohwoo_wow |

**스킬화하지 않은 것**: @dak.korea의 gjc OpenRouter 세팅 프롬프트. Threads 화면에서 URL이 잘려 있고 API 키가 `<내 API key>` 자리표시자라 그대로는 실행되지 않는다. 88자만 확보되어 스킬로 만들지 않고 원문 그대로 보존했다.

## GitHub 저장소

- 저장글 674개에서 확인된 **고유 저장소 299개**
- 각 저장소의 별 수·언어·최근 푸시·아카이브 여부를 GitHub API로 수집 (`repos-api-check.json`, 160건 실존 확인)
- 판정: `install-plan.md` — **총 297개 판정 완료** (고유 297, 중복 0)
  - 1차 40개: README를 직접 열어 설치 명령까지 확인
  - 2차 100개: 설명 기반 분류 → 설치 가능 62 / 보류 27 / 미확인 11
  - 3차 157개: README 설치명령 패턴으로 기계 분류 → 설치 가능 109 / 보류 39 / 404로 설치불가 9
- **정직 고지**: 3차 157개는 사람이 README 전문을 읽고 내린 판정이 아니라 **설치 명령 패턴 기반 기계 분류**다. 저장소 실존(148개 OK)과 설치 명령 추출 여부(119개)는 실측이다.
- 2·3차 분류는 **설명·명령 패턴만 보고 내린 판정**이다. 실제 설치·실행 결과는 설치 단계에서 갱신한다.
- 404로 확인된 10개(`MengTo/Skill`, `Q00/o`, `Q00/r`, `gugu9999gu/PC-CONTROL-MCP`, `johunsang/octo-terminal-releases`, `lexnlin/taste-skill`, `minosdevs/copycat-skill`, `nontext75/vibe-coding-design-polish`, `rakanki911/DLSS5-Swapper`, `yelixir-dev/hermes-memory-stack`)는 GitHub API와 인증 `gh api` 양쪽에서 모두 404였다. 삭제·비공개·이름변경 중 하나이며 확인 불가.

### 설치 원칙

- 전역 설치는 허용하되, 사용자 에이전트·MCP 설정을 바꾸는 설치는 확인 후 진행
- API 키·유료 구독이 필수인 것은 보류
- Linux·macOS 전용은 보류
- Chrome 확장·Claude 대화형 `/plugin` 명령은 셸에서 설치 불가 → 목록으로만 남김

## 스킬 중복 정리

각 에이전트 폴더에 같은 스킬이 여러 벌 복사돼 있었다.

| 구분 | 수 |
|---|---|
| 실제 중복 | 621 |
| 바이트 단위 완전 동일 → 정션 통합 | 610 |
| 내용이 달라 자동 통합 위험 → 보존 | 11 |
| 실패 | 0 |

단일 원본: `~\.agents\skills`

Windows에서 Python `Path.is_symlink()`가 정션을 감지하지 못한다. PowerShell `LinkType -eq 'Junction'`으로 확인하고 `cmd /c rmdir`로 제거해야 한다.

## OCR

- 캐러셀 이미지를 4개 워커로 샤딩 처리
- `kor+eng`, `scale=2`, `psm=6`
- 이미지 안에만 있는 프롬프트 원문은 확인되지 않았다. 나온 것은 디자인 스킬 이름 목록과 UI 스크린샷이었다 → **OCR로만 얻은 프롬프트 원문은 0건**

## 다음에 할 일

- 설치 2차 결과(성공·실패·불가)를 `install-plan.md`에 반영
- 수집 완료 후 `threads-rows.json` → Excel → GitHub 저장소 재생성
