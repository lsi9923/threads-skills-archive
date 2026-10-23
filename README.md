# Threads 저장글 → 스킬 정리

내 Threads 저장글 전체를 훑어서, 안에 들어 있던 **GitHub 저장소·프롬프트·이미지 내용**을 뽑아내고
그걸 실제로 쓸 수 있는 **스킬**로 바꾼 기록입니다.

## 무엇이 들어 있나

| 파일 | 내용 |
|---|---|
| `github-repos.md` | 쓰레드에 링크된 GitHub 저장소 전부. 별 수·언어·최근 커밋·기존 스킬과 겹치는지 |
| `install-plan.md` | 저장소별 설치 판정. 실제로 설치한 것 / 보류한 것과 그 이유 |
| `prompts-all.md` | 글과 댓글에서 뽑은 프롬프트 **원문**. 요약하지 않았다 |
| `prompts-extracted.md` | 위와 같은 작업의 1차 추출본 (범위가 다르므로 합산하지 않음) |
| `skills/*/SKILL.md` | 프롬프트 원문에서 새로 만든 스킬 |
| `skill-dedup-plan.json` | 중복 스킬 판정 결과 (해시 기준) |
| `skill-inventory-after.json` | 정리 후 각 에이전트가 실제로 접근 가능한 스킬 수 |
| `USAGE-KO.md` | 설치·사용법. 유치원생도 따라할 수 있게 씀 |

## 새로 만든 스킬

총 **13개**. 전부 마스터(`~\.agents\skills`)에 있고 Claude·GJC·OmO가 정션으로 같은 파일을 본다.

| 스킬 | 언제 쓰나 | 출처 |
|---|---|---|
| `goal-prompt-builder` | 작업 지시문(/goal)을 만들 때. 목표·완료조건·검증증거·제약·중단조건까지 | @ai.corder |
| `multi-agent-session-brief` | 여러 에이전트에 일을 나눌 때. 역할·성공기준·금지사항 브리핑 | @ais.root |
| `image-prompt-portrait` | 인물 사진 이미지 프롬프트. 10개 섹션 구조 | @han45406480 |
| `video-shotlist-prompt` | 15~30초 멀티샷 영상 프롬프트. 샷별 시간·카메라·대사 | @reactor_art, @imusiro |
| `batch-image-gen-orchestrator` | 이미지 수십~수백 장 병렬 생성. 동시수·재시도·백오프 | @bunniesossdev |
| `gcp-vertex-adc-setup` | 구글 클라우드 가입 → ADC 연결 → gcloud 설치 → 동작 확인 | @autofrog.kr |
| `detailpage-skill-builder` | 상세페이지 작성법을 분석해 스킬로 만들고 이미지 도구 연결 | @gptaku_ai |
| `blog-content-pipeline` | 주제 조사 → 키워드 → 개요 → 초안 → 메타데이터. 발행은 사람이 확인 | @a_book_builder |
| `motion-video-brief-builder` | 광고·쇼릴·뮤직비디오 콘셉트 브리프와 초 단위 샷 리스트 | @chris_gomdori, @crome.ai |
| `side-hustle-design` | 경력·시간·자본 기준 부업 후보 → 검증 질문 → 가격 → 90일 계획 | @gpt_park |
| `thread-content-strategist` | 소재를 핵심 메시지 하나로 재구성. 후킹 10유형·통념 충돌·자가검수 | @hyun.doyun |
| `reference-video-editing-skill` | 레퍼런스 영상 분해 → 편집 규칙집 → 자동 편집기 → 계속 재사용 | @jachung__ |
| `hyperframes-renderer` | 음성·자막·B-roll을 Hyperframes CLI로 자동 합성해 mp4 빌드 | @ai_ohwoo_wow |

**스킬로 만들지 않은 것**: `@dak.korea`의 gjc OpenRouter 세팅 프롬프트는 Threads 화면에서 URL이 잘려 있고 API 키가 `<내 API key>` 자리표시자라 그대로는 실행되지 않는다. 88자만 확보되어 스킬화하지 않고 `prompts-extracted.md`에 원문 그대로 남겼다.

## 스킬 중복 정리

각 에이전트 폴더(Claude·GJC·OmO·Pi·Codex)에 같은 스킬이 여러 벌 복사돼 있었다.

- 실제 중복: **621개**
- 바이트 단위로 완전히 같음: **610개** → 마스터 1개만 남기고 정션으로 통합
- 내용이 달라 자동 통합 위험: **11개** → 보존
- 되돌릴 수 있게 백업 후 작업, 실패 0건

단일 원본: `~\.agents\skills`

## 수집 방법

1. 저장글 목록을 무한 스크롤로 끝까지 수집 (674건)
2. 글마다 개별 방문해 본문·댓글·링크 추출
3. 캐러셀 이미지는 DOM에 4장만 보이므로 **원본 HTML에서 전체 URL을 정규식으로 추출** 후 다운로드
4. 링크는 `l.threads.net/?u=` 래핑·이중 인코딩(`%252F`)·`&amp;`를 다단계 디코딩
5. 이미지 속 글자는 OCR로 추출 (tesseract kor+eng, scale=2, psm=6)

### 수집에서 확인된 한계

- Threads는 긴 텍스트를 **"더 보기"에서 접는다.** 처음에는 댓글 4건이 잘린 것으로 봤으나,
  실제로 클릭해 확인한 결과 **3건은 잘린 것이 아니었다** (`@ai.corder`, `@crome.ai`, `@han45406480`).
  "더 보기" 표시가 **완결된 본문 뒤에** 붙어 있었고 문장이 자연스럽게 끝난다.
  표시만 보고 잘렸다고 판단한 것이 오판이었다.
- **실제로 잘린 것은 1건**: `@hyun.doyun`. 댓글이 `예:`에서 끊기고 클릭해도 이후가 나오지 않는다.
  이 1건은 본문에 `[원문 접힘]`으로 표시했다.
- 펼치기 클릭은 **보이는 요소**를 눌러야 한다. Threads는 같은 "더 보기"를 0×0 숨은 복제본으로도
  렌더하므로, 좌표를 확인하지 않고 누르면 아무 일도 일어나지 않는다.
- 캡처 스크립트는 댓글당 4,000자를 넘기지 않는다. 4,000자에 닿은 항목은 절단으로 표시했다.
- 이미지 안에만 있는 프롬프트 원문은 **확인되지 않았다.** OCR로 나온 것은 디자인 스킬 이름 목록과 UI 스크린샷이었다 → OCR 경유 프롬프트 원문 0건.

## 민감정보

이 저장소에는 **판매자 주소·전화번호·사업자번호·토큰을 넣지 않았다.**
`make-repo.py`가 내보내기 전에 `gho_*`·`sk-*`·`010-\d{4}-\d{4}`·주소·상호를 정규식으로 검사하고, 걸리면 중단한다.
스킬 본문에 예시로 들어간 값은 전부 마스킹했거나 공개 API 안내문이다.

## 주의

- 수집 시점 기준이며, 쓰레드 저장글은 계속 늘어난다.
- `prompts-all.md`·`prompts-extracted.md` 는 **원문 보존이 원칙**이다. 추측해서 채우지 않았고, 원문이 없으면 "없다"고 적었다.
- 각 스킬은 특정 에이전트에 종속되지 않게 썼다. Claude·GJC·OmO 어디서든 같은 절차로 동작한다.
