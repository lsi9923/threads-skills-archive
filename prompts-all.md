# Threads 저장글 프롬프트 모음 — 1차 누적본

> 이 파일은 누적 작업본이다. 작성 중 마지막 감시 이벤트는 `details2` 355건을 보고했다. 현재 읽은 기존 `prompts-extracted.md`는 322건 스캔·후보 신호 42건·원문 항목 14건을 보고했고, 별도 프롬프트 감사는 시작 목록 142건의 본문과 댓글 667개를 확인해 원문이 든 게시글 4건·프롬프트 블록 8개를 판정했다. 두 집계는 범위와 판정 단위가 달라 합산하지 않았다.
>
> 아직 674건 전체를 검사한 결과가 아니다. 아래 원문은 기존 추출본과 직접 확인된 상세 JSON에서 옮겼다. 원문이 캡처에 없으면 추측하지 않고 `원문 미공개` 또는 이미지에만 있는 경우 `이미지에만 있음 — OCR 대기`로 표시했다. 원문 검증이 끝나지 않은 항목은 진행 중인 누적본으로 취급한다.

## 에이전트·오케스트레이션

### 1. Codex /goal 프롬프트 생성기

- 출처: @ai.corder — https://www.threads.com/@ai.corder/post/DYt_EiYmbdP
- 목적: 사용자의 작업 주제를 먼저 질문으로 구체화한 뒤 Codex용 `/goal`을 작성한다.
- 재사용성: 상 — 완료 조건, 증거, 제약, 중단 조건을 함께 만드는 일반 목적 메타프롬프트다.
- 스킬화 제안: `goal-prompt-builder`
- 원문: 캡처된 작성자 댓글의 전문. 댓글 뒤에 더보기 표기가 있어 캡처 범위 바깥 텍스트가 더 있는지는 미확인이다.

````text
당신은 “Codex / AI 에이전트용 /goal 프롬프트 생성기”이다.

당신의 역할은 사용자가 입력한 작업 주제나 아이디어를 바탕으로, 바로 최종 프롬프트를 작성하는 것이 아니라 먼저 필요한 정보를 질문하고, 최종적으로 Codex 또는 AI 에이전트가 사용할 수 있는 고품질 /goal 프롬프트를 완성하는 것이다.

핵심 목표는 단순한 작업 지시문이 아니라, 에이전트가 스스로 판단하며 작업할 수 있는 “목표 선언문 + 완료 조건 + 검증 증거 + 제약 조건 + 중단 조건”을 만드는 것이다.

---

## 1. 기본 진행 방식

사용자가 주제나 작업 아이디어를 입력하면 다음 순서로 진행한다.

1. 사용자의 주제를 분석한다.
2. 목표가 모호하면 필요한 정보를 질문한다.
3. 한 번에 너무 많은 질문을 하지 않는다.
4. 질문은 사용자가 쉽게 답할 수 있도록 선택지 중심으로 제시한다.
5. 사용자가 짧게 답해도 바로 추측하지 않는다.
6. 부족한 정보는 [가정]으로 표시하거나 추가 질문으로 확인한다.
7. 충분한 정보가 모이면 최종 /goal 프롬프트를 작성한다.
8. 최종 결과물은 바로 복사해서 사용할 수 있는 코드블록 형태로 제공한다.

---

## 2. 먼저 확인해야 할 정보

사용자의 주제가 들어오면 아래 항목 중 부족한 정보를 확인한다.

### A. 최종 목표

Codex 또는 AI 에이전트가 최종적으로 무엇을 완성해야 하는지 확인한다.

예:
- 버그 수정
- 새 기능 구현
- 리팩터링
- 테스트 추가
- 문서 작성
- 디자인/UI 개선
- 프롬프트 제작
- 자동화 워크플로우 설계
- 배포/운영 개선

### B. 결과물 형태

최종 산출물이 무엇인지 확인한다.

예:
- 코드 수정
- 새 파일 생성
- 테스트 코드
- README 문서
- PR 설명문
- 디자인 시안
- 프롬프트
- 실행 가능한 스크립트
- 배포 가능한 결과물

### C. 완료 조건

어떤 상태가 되면 “완료”라고 볼 수 있는지 확인한다.

예:
- 특정 기능이 정상 동작한다.
- 특정 버그가 재현되지 않는다.
- 테스트가 통과한다.
- 빌드가 성공한다.
- UI가 기존 디자인 시스템과 일치한다.
- 문서만 보고도 실행 가능하다.

### D. 검증 방법

결과가 제대로 되었는지 어떻게 확인해야 하는지 묻는다.

예:
- 테스트 실행
- 빌드 성공
- 린트 통과
- 타입 체크
- 스크린샷 비교
- API 응답 확인
- 수동 체크리스트
- 로그 확인
- 파일 변경 요약

### E. 제약 조건

절대 바꾸면 안 되는 것을 확인한다.

예:
- 기존 API 형식
- DB 스키마
- 인증 방식
- 폴더 구조
- 디자인 시스템
- 외부 라이브러리
- 기존 UI/UX
- 특정 파일
- 특정 기술 스택

### F. 작업 범위

어떤 파일, 폴더, 모듈, 화면, 기능까지만 작업할 수 있는지 확인한다.

예:
- 프론트엔드만
- 백엔드만
- 특정 컴포넌트만
- 특정 API 라우트만
- 테스트 파일만
- 문서만

### G. 우선순위

작업에서 무엇이 가장 중요한지 확인한다.

예:
- 최소 변경
- 안정성
- 성능
- 유지보수성
- 빠른 구현
- 사용자 경험
- 확장성

### H. 막힐 때의 행동

에이전트가 불확실한 상황에서 어떻게 행동해야 하는지 확인한다.

예:
- 추측하지 않고 멈춘다.
- 근거를 보고하고 질문한다.
- 가능한 대안을 제시한다.
- 안전한 범위 안에서만 진행한다.

---

## 3. 질문 방식

정보가 부족할 때는 짧고 명확하게 질문한다.

질문은 번호 선택형으로 제시한다.
한 번에 너무 많은 질문을 하지 않는다.
보통 3~5개 질문만 한다.

예시:

사용할 /goal 프롬프트를 만들기 위해 몇 가지만 정하면 됩니다.

1. 작업 유형은 무엇인가요?
A. 버그 수정
B. 새 기능 구현
C. 리팩터링
D. 테스트 추가
E. 문서 작성
F. 디자인/UI 개선
G. 기타

2. 최종 결과물은 무엇이어야 하나요?
A. 코드 수정 완료
B. 새 기능 완성
C. 테스트 통과
D. 문서/README 완성
E. 프롬프트 완성
F. PR 가능한 상태

3. 가장 중요한 기준은 무엇인가요?
A. 최소 변경
B. 안정성
C. 성능
D. 유지보수성
E. 빠른 구현
F. 사용자 경험

사용자는 번호, 알파벳, 짧은 문장, 자유 서술 중 어떤 방식으로 답해도 된다.

---

## 4. 사용자가 짧게만 답한 경우

사용자가 짧게 답하면 부족한 부분을 추측해서 확정하지 않는다.

필요하면 다음처럼 응답한다.

예시:

사용자:
로그인 버그 고치는 goal 만들어줘

응답:
좋습니다. 정확한 /goal 프롬프트를 만들기 위해 4가지만 확인하겠습니다.

1. 로그인 버그는 어떤 상황에서 발생하나요?
A. 로그인 자체가 안 됨
B. 특정 계정만 실패
C. 새로고침 후 로그아웃됨
D. 토큰/세션 문제
E. 아직 모름

2. 수정 대상은 어디인가요?
A. 프론트엔드
B. 백엔드
C. 둘 다
D. 아직 모름

3. 검증 방법은 무엇인가요?
A. 테스트 실행
B. 빌드 확인
C. 브라우저에서 직접 확인
D. API 응답 확인
E. Codex가 적절히 판단

4. 건드리면 안 되는 것이 있나요?
A. API 형식
B. DB 스키마
C. 인증 방식
D. 특정 파일
E. 없음 / 아직 모름

---

## 5. 최종 /goal 프롬프트 작성 규칙

정보가 충분하면 반드시 아래 구조로 최종 프롬프트를 작성한다.

최종 프롬프트는 코드블록 안에 제공한다.
바로 복사해서 Codex 또는 AI 에이전트에 붙여넣을 수 있어야 한다.

```text
/goal [최종 목표를 한 문장으로 명확히 작성한다]

## Background
[현재 상황, 문제, 작업 배경을 간단히 설명한다.]

## Objective
[Codex 또는 AI 에이전트가 최종적으로 달성해야 할 목표를 구체적으로 작성한다.]

## Scope
Allowed:
- [작업 가능한 범위]
- [수정 가능한 파일/기능/모듈]

Not Allowed:
- [수정하면 안 되는 범위]
- [건드리면 안 되는 파일/기능/정책]

## Requirements
- [반드시 충족해야 하는 요구사항 1]
- [반드시 충족해야 하는 요구사항 2]
- [반드시 충족해야 하는 요구사항 3]

## Success Criteria
The task is complete only when:
- [완료 조건 1]
- [완료 조건 2]
- [완료 조건 3]

## Verification Evidence
Before finishing, provide:
- [실행한 테스트 또는 검증 명령어]
- [검증 결과 요약]
- [수정한 파일 목록]
- [핵심 변경사항 요약]
- [남아 있는 리스크 또는 확인 필요 사항]

## Constraints
- [기술적 제약 조건]
- [비즈니스 제약 조건]
- [디자인/UX 제약 조건]
- [보안/성능/호환성 제약 조건]

## Decision Rules
During each iteration:
- [다음 행동을 선택하는 기준]
- [우선순위 판단 기준]
- [불확실할 때의 처리 방식]

## Stop Conditions
Stop and report instead of guessing if:
- [필수 정보가 부족한 경우]
- [권한이 부족한 경우]
- [테스트나 빌드가 실행 불가능한 경우]
- [요구사항 간 충돌이 있는 경우]
- [안전하지 않거나 범위를 벗어난 변경이 필요한 경우]

When stopped, report:
- What was attempted
- What evidence was found
- Where the blocker is
- What information or permission is needed next
```
````

### 2. Aside 블로그 글쓰기 자동화

- 출처: @a_book_builder — https://www.threads.com/@a_book_builder/post/DeeDL9imkAW
- 목적: 글감 수집부터 블로그 예약 발행까지 단계별로 지시한다.
- 재사용성: 상 — 5개 단계의 짧은 명령을 묶어 반복 사용 가능하다.
- 스킬화 제안: `blog-autopublish`
- 원문: 본문 3개와 작성자 댓글 2개.

```text
1단계: 글감이랑 키워드 자동 수집
"구글 트렌드랑 타깃 사이트 훑고 이번 주 조회수 터질 만한 키워드 3개 뽑아줘."
2단계: 뼈대랑 초안 한 번에 생성
"뽑은 키워드로 SEO 잘 먹히는 H2, H3 목차 짜고, 구체적 사례 넣어서 본문 초안 써줘."
3단계: 내 블로그 에디터에 자동 로그인 & 입력
"워드프레스(또는 티스토리) 관리자 페이지 들어가서 새 글 에디터 열고 제목, 본문, 태그 채워 넣어."
4단계: 대표 이미지 & 메타 디스크립션 세팅
"글 내용 요약해서 SEO용 메타 디스크립션 입력하고, 카테고리 설정해 줘."
5단계: 예약 발행으로 자동 파이프라인 완성
"즉시 발행 말고 '내일 오전 8시'로 예약 발행 버튼 클릭해 줘."
```

### 3. Hyperframes 렌더링 Claude Skill 생성 지시문

- 출처: @ai_ohwoo_wow — https://www.threads.com/@ai_ohwoo_wow/post/DeFeCIVE7h5
- 목적: 오디오·자막·비디오를 받아 B-roll 컷 편집과 자막을 적용하고 영상을 렌더링하는 스킬을 만든다.
- 재사용성: 상 — 입출력 파일과 실행 작업이 명시되어 있다.
- 스킬화 제안: `hyperframes-renderer`
- 원문: 작성자 댓글의 `comments[0]`.

```text
"hyperframes-renderer"라는 이름의 Claude Skill을 다음 지침에 따라 생성해 줘.
1. 입력 파일:
- 음성 파일: `output/audio_*.mp3`
- 자막 파일: `output/audio_*.srt`
- 비디오 소스: `downloads/raw_videos/source_*.mp4`
2. 실행 작업:
- Hyperframes 설정 파일(`render_config.json`)을 자동 생성할 것.
- 오디오 타임라인에 맞춰 원본 영상들을 1.5초~2.5초 단위의 B-roll 교체 구간으로 컷편집할 것.
- 교체된 영상 위에 모션 애니메이션이 적용된 자막을 오버레이할 것.
3. 출력:
- Hyperframes CLI 명령어를 실행하여 최종 영상 빌드: `hyperframes render render_config.json --output output/final_shorts.mp4`
```

### 4. 저조도 인물 사진 생성 프롬프트

- 출처: @han45406480 — https://www.threads.com/@han45406480/post/DeshhNyAQ0H
- 목적: 어두운 실내 인물 화보의 인물·구도·조명·색·질감을 섹션별로 지정한다.
- 재사용성: 상 — 구조화된 섹션을 다른 인물·장면에 맞게 바꿔 쓸 수 있다.
- 스킬화 제안: `image-prompt-portrait`
- 원문: 기존 추출본에서 확보한 문자열. 이 게시글의 현재 상세 JSON이 아닌 기존 `prompts-extracted.md`에서 가져온 항목이다.

```text
IDENTITY: A photorealistic low-light portrait of a 20-year-old Korean woman with clearly adult features; very long glossy dark hair with volume at the roots and curled ends freely framing the face, a few strands slightly smeared by a small turn of the head; styled brows, long separated lashes, pink glossy lips with a crisp sharp contour.
SUBJECT: A living atmospheric frame shot from below in almost complete darkness — she is turned toward the camera by one shoulder, face in half profile, eyes cast down into the lens from above, lips slightly parted; the visual accent rests on her collarbones and the open neckline, styled elegantly and covered.
WARDROBE: A black camisole top on thin straps, fully covered in black rhinestones that sparkle black-on-black, cut with a deep V-neckline kept as a pure fashion line; a thin chain with a small round diamond pendant lying in the neckline.
POSE: She stands with weight over her right leg, left knee soft; shoulders rotate so the right shoulder leads toward the lens, torso in three-quarter; her head turns into half profile, chin held a touch high because the camera sits low; her eyes drop to meet the lens, lips parting slightly on an exhale; hair swings softly across both sides of the face; the frame crops at mid-chest so no hands are visible.
ENVIRONMENT: An unidentifiable dark room — a sliver of wall behind her dissolving into pure black, nothing readable in the background.
CAMERA: Shot on an old iPhone 5 from a worm's-eye angle below chest height, tilted up about 25 degrees, portrait crop from face to mid-chest; soft lens sharpness with gentle corner falloff and slight vignette, minimal exposure pushed down, honest digital noise and light grain.
LIGHT: One faint sliver of ambient light raking from the side — like a distant lamp — grazing the collarbones, one cheekbone and the pendant; everything else falls into deep unlifted shadow; high contrast between the lit edge and the black field; a specular ping on the lip gloss and the diamond; no fill, no flash.
PALETTE: Single color strategy, physical Containment — a near-black achromatic field holding exactly two color islands: the pink of the glossy lips and the cold white-blue sparkle of the diamond; skin tones desaturated and muted into the dark.
TEXTURE: Real skin texture with pores resolved only where the light sliver touches, a soft sheen along the collarbones; faceted rhinestones catching micro-sparkle against matte black fabric; grouped glossy hair strands with blurred tips; fine digital noise and grain across the frame, no sharpening halos.
AVOID: plastic or airbrushed skin, HDR flatness, studio softbox look, blown highlights, colorful neon washes, modern-phone cleanliness, doll-like proportions, extra fingers, text, logos or watermark, over-sharpening, and any explicit exposure — the frame stays elegant, covered, atmospheric.
```

### 5. 15초 7샷 홈비디오 브이로그 영상 프롬프트

- 출처: @reactor_art — https://www.threads.com/@reactor_art/post/DcQEnKuGjiX
- 목적: 15초 멀티샷 영상에 인물 참조, 7개 샷, 대사, 사운드와 제외 조건을 지정한다.
- 재사용성: 상 — 샷별 시간표와 참조 이미지 우선순위를 다른 주제로 바꿀 수 있다.
- 스킬화 제안: `video-shotlist-prompt`
- 원문: 기존 추출본에서 확보한 문자열. 현재 details2에서 재검증하지 못한 항목이다.

```text
Create a 15-second, 16:9 photorealistic multi-shot handheld home-video vlog with exactly 7 distinct shots. Do not use a single camera angle, single continuous take, or one unchanging composition. Each shot must have a clearly different framing or camera position.
REFERENCE HIERARCHY:
@image_1 is the sole identity and wardrobe reference for the woman. Preserve her exact face, facial proportions, natural skin texture, dark brown eyes, black hair tied in a loose messy low bun, loose strands around her face, slim body proportions, and the exact soft grey sleeveless linen mini dress with thin shoulder straps, slightly wrinkled natural fabric, relaxed fit, and bare feet.
@image_2 is used only as a loose reference for the older brother’s bedroom, computer desk, monitor glow, black office chair, dark interior, and lived-in atmosphere. Do not copy or recreate the woman from @image_2. Do not use her face, hair, clothing, or identity.
CHARACTERS:
WOMAN — clearly adult, the same woman from @image_1 in every shot. She wears only the same soft grey sleeveless linen mini dress from @image_1, with thin straps and a relaxed above-the-knee hem. Barefoot. Natural makeup, realistic skin pores, subtle facial asymmetry, fine baby hairs, and believable human movement. Her behavior is casual, curious, and unperformed.
OLDER BROTHER — a different clearly adult Korean man in his late 20s to early 30s. Messy dark hair, slightly tired face, average build. He wears a loose charcoal-grey hoodie and dark navy sweatpants. He is not based on either reference image. His reaction is visibly urgent and embarrassed, but not aggressive or threatening. He moves quickly because he does not want his sister to inspect the mysterious folder.
LOCATION:
The older brother’s private bedroom, inspired by the atmosphere of @image_2: a slightly messy lived-in room with a computer desk, large monitor, black office chair, keyboard, mouse, tangled cables, books, a half-empty cup, scattered clothes, a bed, and miscellaneous personal objects. Warm late-afternoon light enters through curtains and mixes with a cool monitor glow. The room feels ordinary, private, and slightly cluttered. No other people appear. The phone camera is held by an unseen person; only the woman and her older brother are visible.
COMPUTER CONTENT:
The monitor shows a generic desktop with one unfamiliar folder and several ambiguous file icons. The folder name and file names are intentionally blurred and unreadable. Do not show explicit imagery, sexual content, illegal content, or recognizable copyrighted media. The screen only needs to communicate that the folder is private, strange, and embarrassing. No readable text, subtitles, logos, or user interface labels.
VISUAL STYLE:
One-handed smartphone home-video realism, snapshot-like image quality, slightly tilted framing, imperfect composition, visible handheld shake, small focus shifts, natural exposure changes, warm late-afternoon indoor light, subtle cool monitor glow, fine film grain, realistic motion blur, natural skin texture, ordinary household sound, and unperformed facial reactions. No polished commercial cinematography. No dramatic music.
SHOT 1 — 0.0–2.0 seconds:
The woman enters the older brother’s bedroom carrying a small stack of folded clothes. She places them on the edge of the bed and glances around at the messy room. The computer monitor is already on in the background. The phone camera follows her from the doorway in a loose, slightly low handheld framing, with a small natural wobble. She notices that the brother is not in the room.
SHOT 2 — 2.0–4.0 seconds:
She walks toward the computer desk and leans closer to the monitor. The camera shifts from a medium shot of her to an over-the-shoulder view of the screen. A strange unnamed folder is visible among generic file icons. She moves the mouse with one hand and opens the folder, looking mildly puzzled rather than frightened. Monitor light reflects softly on her face. She quietly says in natural Korean:
“어? 이게 뭐지?”
(“Huh? What is this?”)
SHOT 3 — 4.0–6.0 seconds:
Close handheld shot of her face and the computer screen from a side angle. She scrolls through a few ambiguous file thumbnails. The filenames remain unreadable and the contents are never shown explicitly. Her expression changes from casual curiosity to genuine confusion. She tilts her head slightly and says:
“오빠 방에 이런 게 있었어?”
(“You had something like this in your room?”)
The camera makes a small nervous wobble as if the person filming has just realized the situation is becoming awkward.
SHOT 4 — 6.0–8.5 seconds:
From the hallway, the older brother suddenly appears in the doorway and notices the open folder on the monitor. He freezes for half a second, then immediately rushes toward the desk. The camera quickly pans from the woman to him, creating imperfect motion blur and a brief loss of framing. His voice becomes visibly urgent:
“야, 잠깐만! 그거 보지 마!”
(“Hey, wait! Don’t look at that!”)
SHOT 5 — 8.5–11.0 seconds:
Chaotic close handheld shot from beside the desk. The brother reaches urgently for the mouse and keyboard, trying to close the folder while standing beside her. He does not grab or hurt her; he only tries to block the monitor and close the window. The woman steps slightly aside but keeps looking at him with a confused, suspicious expression. He stammers:
“아니, 그게 아니라… 그냥 아무것도 아니야!”
(“No, it’s not that… it’s nothing!”)
The mouse clicks rapidly, the chair rolls slightly, and the camera shakes with the sudden movement.
SHOT 6 — 11.0–13.0 seconds:
Medium two-shot of both siblings beside the computer. The brother finally closes the folder and awkwardly turns the monitor slightly away. He looks visibly flustered and out of breath. The woman crosses her arms lightly and looks from him to the screen. She asks in a calm but increasingly suspicious tone:
“아무것도 아닌데 왜 그렇게 급해?”
(“If it’s nothing, why are you in such a hurry?”)
He avoids eye contact and gives an embarrassed nervous laugh.
SHOT 7 — 13.0–15.0 seconds:
The brother quickly sits in the office chair and presses another key, keeping both hands over the keyboard as if guarding the computer. The woman leans toward him with a skeptical half-smile, then picks up the folded clothes from the bed and begins tidying the room again without leaving. She gives him one last look and says:
“나중에 설명해.”
(“Explain it to me later.”)
The brother answers immediately, still panicked:
“아니, 진짜 별거 아니야!”
(“Seriously, it’s really nothing!”)
The camera drifts backward toward the doorway, lingering on the messy room, the guarded computer, the suspicious woman, and the flustered brother.
SOUND DESIGN:
No music. Only natural live ambient sound: quiet footsteps on the floor, fabric rustling, clothes placed on the bed, mouse clicks, keyboard tapping, the office chair rolling, subtle computer fan noise, room ambience, distant household sounds, the woman’s quiet voice, the brother’s hurried footsteps, nervous breathing, stammering, and embarrassed laughter. Natural imperfect smartphone-recorded audio with realistic Korean dialogue timing and lip sync.
NEGATIVE:
No single continuous shot, no single camera angle, no cinematic crane movement, no polished commercial acting, no extra people, no duplicate woman, no copy of the woman from @image_2, no changed face, no changed hairstyle, no changed dress, no altered body proportions, no revealing wardrobe changes, no aggressive violence, no physical assault, no explicit content, no readable private files, no explicit images on the monitor, no subtitles, no captions, no logos, no watermarks, no readable text, no music, no fantasy elements, no exaggerated comedy acting, no cartoon, anime, illustration, CGI, plastic skin, beauty-filter smoothing, distorted hands, extra fingers, broken computer hardware, or impossible screen reflections.
```

### 6. 이미지 병렬 생성 지시문

- 출처: @bunniesossdev — https://www.threads.com/@bunniesossdev/post/Dax339VE9MA
- 목적: God-Tibo-Imagen 이미지 요청의 병렬 수, 백오프, 재시도, 진행 보고를 지정한다.
- 재사용성: 중 — 구체적인 도구와 운영 수치에 종속된다.
- 스킬화 제안: `batch-image-gen-orchestrator`
- 원문: 본문에서 “프롬프트는 이렇게 하면 됩니다”라고 밝힌 인용문.

```text
"gti (god-tibo-imagen) 이용해서 병렬로 이미지 뽑아서. 한 번에 최대 32장 리퀘스트 병렬로 들어가게 해주고 지수적 backoff & retry해줘. 반드시 asyncio 등 써서 병렬로 I/O 작업 해야함. 실패한 것은 총 5번까지 재시도, 끝까지 실패하면 실패 판정. 30분마다 polling으로 보고"
```

### 7. Vertex AI ADC 연결 지시문

- 출처: @autofrog.kr — https://www.threads.com/@autofrog.kr/post/DeGGJIOknKL
- 목적: Google Cloud 계정 준비 후 코덱스/클로드에 ADC 연결, gcloud 설치와 테스트 요청을 한다.
- 재사용성: 중 — 클라우드 환경·요금·모델 사용 조건에 따라 다시 검증해야 한다.
- 스킬화 제안: `gcp-adc-setup`
- 원문: 작성자 댓글의 복사 안내에서 실제 AI 입력으로 제시한 문장 3개. 나머지는 사용자를 위한 단계 설명이다.

```text
"구글 클라우드 가입했어. Vertex AI에 ADC로 연결해 줘"
"니가 설치하고 연결해 줘"
"Vertex AI 무료 크레딧으로 omni 1.1 5초 영상 만들어 줘"
```

### 8. 멀티 세션 에이전트 역할 분담 예시

- 출처: @ais.root — https://www.threads.com/@ais.root/post/DbGPmPRD5g8
- 목적: 같은 코드베이스를 여러 세션으로 나누어 백엔드와 프런트엔드 역할을 부여한다.
- 재사용성: 중 — 세션 ID와 역할을 실제 작업에 맞게 바꿔야 한다.
- 스킬화 제안: `multi-agent-session-brief`
- 원문: 본문의 역할 설정 예시. 별도 게시물에서 실제 운영 system prompt라고 밝히지는 않았다.

```text
Agent A:
역할:
- 백엔드 API 개발
- DB 구조 변경
- 인증 시스템 구현
Agent B:
"123 세션의 작업 내용을 참고해서
프론트엔드 React 화면을 구현해줘"
```

### 9. 상세페이지 제작 스킬 생성 커맨드 체인

- 출처: @gptaku_ai — https://www.threads.com/@gptaku_ai/post/DcyBiTfk92r
- 목적: 영상 분석, 상세페이지 작성법 추출, 스킬 생성, 이미지 도구 지정 명령을 연결한다.
- 재사용성: 중 — 링크가 축약돼 있고 세션에 존재하는 명령어에 의존한다.
- 스킬화 제안: `detailpage-skill-builder`
- 원문: 기존 추출본에서 확보한 문자열. 현재 상세 JSON 기준 재검증 전이다.

```text
/insane-search youtu.be/zJzdT… 영상 분석해서 매출 떡상하는 상세페이지 작성법을 분석해봐 이걸 바탕으로 내가 준 정보들을 가지고서 상세페이지 만드는 스킬을 만들어줘 /skillers-suda 이미지를 만들때는 /pumasi:image 사용해서 만들도록해줘
```

## 현재 상세파일에서 추가 확인된 지시 예시

### 10. Remotion 쇼츠 제작 예시

- 출처: @builder.ericc — https://www.threads.com/@builder.ericc/post/DWBXH9uEiU_
- 목적: Claude Code에 대본 JSON 생성, 비주얼 타입 변경, 새 비주얼 타입 추가를 요청한다.
- 재사용성: 중 — 전체 대본 생성용 프롬프트 전문은 없고, 세 개의 짧은 작업 예시만 공개됐다.
- 스킬화 제안: `remotion-shorts-workflow`
- 원문: 작성자 댓글의 따옴표 안 세 문장. 주변 설명은 프롬프트 원문으로 합치지 않았다.

```text
"이 주제로 대본 JSON 만들어줘"
"visual을 step-flow로 바꿔줘"
"새로운 visual 타입 추가해줘"
```

### 11. BananaTape 이미지 수정 피드백 예시

- 출처: @bunniesossdev — https://www.threads.com/@bunniesossdev/post/DXo4spikX0G
- 목적: 생성 이미지 위에 표시·주석을 붙여 수정 지점을 전달하는 사용 예시다.
- 재사용성: 중 — 특정 이미지 편집 도구와 시각적 표시 흐름이 전제된다.
- 스킬화 제안: `image-edit-feedback-bridge`
- 원문: 본문에서 설명을 위해 직접 인용한 두 문장. 정식 시스템 프롬프트가 아니라 짧은 수정 지시 예시다.

```text
"아니 오른쪽 아래에 있는 것을 지우라고!!"
"그 위에 글씨를 조금만 가운데쪽으로 움직여줘"
```

### 12. 에이전트 reasoning 설정 예시

- 출처: @bellman.pub — https://www.threads.com/@bellman.pub/post/DavLs8rEpm_
- 목적: 기본 에이전트·Executor·Architect·Critic·Planner의 reasoning 수준을 배치하는 설정 조언이다.
- 재사용성: 하 — 특정 모델 버전과 에이전트 프리셋에 종속되며, 복사 가능한 독립 프롬프트는 아니다.
- 스킬화 제안: `agent-role-reasoning-profile`
- 원문: 본문 전체. 프롬프트 원문이라기보다 에이전트 역할/추론 수준 구성 지시로 따로 분류한다.

```text
참고
내가 온갖 지랄병 해보니까
5.6은 리즈닝만 낮추면 딱 좋다
특히 가재코드 디폴트 에이전트
한 low 나 미듐 넣고 써보시길.
Executor 도 그냥 low (Terra 나 luna) 쓰고 아키텍은 하이 쓰고 크리틱만 xhigh / high 정도 넣으면 적당. 플래너는 대충 취향껏ㅋ ok?
```

## 원문 미공개 또는 불완전한 항목

아래는 프롬프트를 사용·배포·소개한다고 언급했지만, 캡처된 상세 JSON에 완성된 입력 문장이 없다. 근거 없는 원문을 만들어 넣지 않았다.

| 출처 | 목적/맥락 | 재사용성 | 스킬화 제안 | 원문 |
|---|---|---:|---|---|
| @5hyeons — https://www.threads.com/@5hyeons/post/DcFgVcyijHg | 유튜브 채널에서 투자 관점을 제외하고 온톨로지 내용을 추렸다고 설명. 실제 입력 문장은 제시하지 않음. | 중 | `multi-source-video-synthesis` | 원문 미공개 |
| @ai_margin_ — https://www.threads.com/@ai_margin_/post/DcuWzJKjwRv | 카드뉴스 제작 5단계를 홍보하지만 댓글은 단계별 설명만 제공하고 복사 자료를 안내함. | 중 | `card-news-prompt-pipeline` | 원문 미공개 |
| @min.__.ai — https://www.threads.com/@min.__.ai/post/DeviVcPDmd_ | 웹사이트 출시 전 점검 프롬프트 20가지를 댓글 후 DM으로 보낸다고만 표시. | 중 | `website-launch-checklist` | 원문 미공개 |
| @ai_sync_club — https://www.threads.com/@ai_sync_club/post/DYWxL_YCiU4 | Codex 상세페이지 제작 스킬의 동영상·다운로드 링크를 안내하지만 스킬 지시문 전문은 없음. | 중 | `detail-page-skill-runner` | 원문 미공개 |
| @aisolutiondev — https://www.threads.com/@aisolutiondev/post/DVxMoBFlPj9 | Codex용 서브에이전트 모음을 소개하고 댓글에서 GitHub 링크를 안내. 복사할 명령은 캡처에 없음. | 하 | `codex-subagent-team` | 원문 미공개 |
| @bamsaem_ai — https://www.threads.com/@bamsaem_ai/post/Dd83vv3kd5v | 동영상 프롬프트 링크를 댓글에서 안내. 저장 슬라이드에 짧은 지시 일부가 있지만 입력 전문은 확인되지 않음. | 중 | `hyperframes-motion-prompt` | 이미지에만 있음 — OCR 대기 |
| @bunniesossdev — https://www.threads.com/@bunniesossdev/post/Da4pPzAkYkB | 두 모델에 같은 슬라이드 프롬프트를 사용했다고만 언급. | 하 | `slide-deck-style-prompt` | 원문 미공개 |
| @bravomylife153 — https://www.threads.com/@bravomylife153/post/DZbZXm7CJgf | `taste-skill`을 프롬프트 라이브러리라고 소개하지만 구체적인 프롬프트는 없음. | 하 | `taste-check-prompt-filter` | 원문 미공개 |

## 중복과 집계 범위

- 기존 추출본의 9개 항목은 게시물 단위 목록이었다. 이 파일은 그 본문을 유지하면서 직접 확인한 추가 항목을 별도 번호로 붙였다.
- `a_book_builder`에는 개별 지시문 5개, `autofrog.kr`에는 AI에 입력하는 문장 3개, `builder.ericc`에는 짧은 작업 예시 3개가 포함된다. 따라서 게시물 수와 원문 프롬프트 블록 수는 다르다.
- 직접 원문으로 공개된 항목 사이에서 완전히 같은 문장을 확인하지 못했다. 짧은 예시·역할 설정·설명 문장은 장문 프롬프트 수와 분리했다.
- 기준 파일 수는 계속 증가한다. 마지막 감시 이벤트는 355건을 보고했으며, 이 누적본은 674건 전체를 다루지 않는다.

## 기존 추출본에서 새로 반영한 원문

### 13. Hermes용 뮤직비디오 스킬 저작·설치 프롬프트

- 출처: @crome.ai — https://www.threads.com/@crome.ai/post/DaK47GoCX8e
- 목적: 현재 호스트를 조사하고, 음악 분석부터 영상 조립·전달까지 수행할 재사용 가능한 뮤직비디오 제작 스킬을 정의한다.
- 재사용성: 상 — 입력·계획·검증·환경 발견·전달 조건을 함께 다룬다.
- 스킬화 제안: `music-video-workflow`
- 원문:

```
You are on a **new Hermes instance**. The operator wants you to **author and install** a reusable skill **`grok-skill`** (그록스킬) for **future** MV jobs on **this** machine. **Do not** run a full MV generation in this turn unless they also attach music and ask for it — this turn is primarily **skill authoring + host discovery**.

### Deliverables

1. Create or refresh **`grok-skill`** under `~/.hermes/skills/creative/grok-skill/` via `skill_manage` (`create` or `patch` + `write_file` for references/scripts).
2. Files to include:
- `SKILL.md` — full procedure (see below).
- `references/grok-only-fulltrack-assembly.md` — timeline math.
- `references/music-tempo-and-motion.md` — how BPM/energy maps to Grok camera prompts.
- `scripts/assemble_fulltrack_template.py` — ffmpeg template with **config block** (`ASPECT`, `CHORUS_START`, paths).
3. Confirm with `skill_view(name='grok-skill')`. Tell operator: `/reload-skills` or new session.
4. **Never** hardcode another machine’s `chat_id`, Comfy URLs, or donor `tmp` paths.

### Before encoding the skill — discover this host

- xAI: `~/.hermes/auth.json` or `XAI_API_KEY`
- `ffprobe -version`, `hermes tools list` (`video_gen` vs direct API only)
- Active profile, gateway platform, home channel / delivery pattern
- Whether `grok-native-image-video` exists → `related_skills`

### Pipeline the skill must describe (generic, not one song)

| Phase | What the skill tells the agent to do |
|-------|--------------------------------------|
| **Intake** | Music file + optional character image; if missing protagonist, offer to generate one |
| **User prefs (ask if not stated)** | **Aspect ratio** (9:16, 16:9, 1:1, …) — use `clarify` if missing; no silent default to 9:16 without user skip |
| **Music analysis** | Duration, lyrics/tags, BPM or energy (RMS / songsee). Classify **fast / mid / slow** → write **`MOTION_BRIEF.md`** (camera verbs, whether to avoid slow dolly, per-cut timeline length) **before** Grok video batch |
| **Plan** | `STORYBOARD.md` + `CREATIVE_BRIEF.md` from **this song** (K-pop multi-location = example only, not mandatory) |
| **Stills** | `/images/edits`, IDENTITY LOCK; aspect = user choice |
| **Grok video** | 1.5 preview; prompts follow **`MOTION_BRIEF.md`**; silent clips — no speaking/lip-sync dialogue in prompts |
| **Edit** | Intro → chorus highlight → outro; `CHORUS_START` from **this** track’s lyric/energy; highlight tail trim → extend outro, same order |
| **Mux** | Pad to **OUT_W×OUT_H** from aspect; full song |
| **Delivery** | This host only — discover home channel / `MEDIA:` / Bot token |

### Music → motion (must be in `music-tempo-and-motion.md`)

- **Fast:** whip/orbit/fast tracking; avoid slow motion & slow dolly; shorter timeline cuts (e.g. 2–3s).
- **Mid:** mixed motion; ~3–4s cuts.
- **Slow:** smooth push/drift OK; longer holds OK; avoid harsh whip pans.
- BPM unknown → ask user “편집상 빠른/느린 곡인지” + RMS heuristic.

### Aspect ratio

- Job start: **ask** if not specified.
- Map to xAI + ffmpeg; template uses `OUT_W` / `OUT_H`, not fixed 9:16.

### Skill rules

- `grok-skill`, description ≤1024 chars.
- Korean 그록스킬 trigger example: music + optional image, **비율 확인**, **음악 분석 후** 카메라 톤.
- Pitfalls: skipping music analysis, hardcoded ratio, hardcoded Telegram IDs, highlight sync ≠ `CHORUS_START`.

### Reply

Skill path, file list, sample `/skill grok-skill` user message, host discovery summary (auth, video tool, delivery).
```

### 14. Google Flow 모션그래픽 광고 프롬프트

- 출처: @chris_gomdori — https://www.threads.com/@chris_gomdori/post/DcVvXyMDWO_
- 목적: 지정한 광고 내러티브·색상·시각 스타일과 샷 타임코드로 10초 모션그래픽을 생성한다.
- 재사용성: 중 — 광고 소재·브랜드 BI·슬로건을 교체해 쓸 수 있지만 캡처가 4,000자에서 끊겼다.
- 스킬화 제안: `motion-graphic-ad-prompt`
- 원문: 캡처된 앞부분. 끝은 원본 상세 텍스트의 절단 위치다.

```
Create an EXACTLY 10.000-second ultra-high-impact motion graphics commercial optimized for Google Flow Omni Flash.

PROJECT

Create a premium, fast-paced technology advertisement for “광진AX / GWANGJIN AX”, an AI-powered administrative innovation concept created inside the public sector.

Use the attached official Gwangjin-gu BI and attached Gwangjin-gu Office building photograph as essential visual references.

Narrative:

GWANGJIN BI
→ GWANGJIN-GU OFFICE BUILDING
→ ADMINISTRATIVE WORK TRANSFORMS INTO AI
→ RAPID AI PROCESSING
→ IMPACT
→ KOREAN SLOGAN

Emotional contrast:

slow, repetitive, heavy public administration
→ fast, precise AI-assisted administration.

AI handles repetitive work so public officials can focus on judgment, policy, citizens, and essential work.

CORE MESSAGE

End with this EXACT Korean slogan:

광진AX,
반복업무는 AI에게,
우리는 본질에 집중.

Do not translate, paraphrase, or add extra Korean copy.

Korean characters must remain clean, correct, legible, and professionally typeset.

VISUAL STYLE

Premium Korean public-sector technology campaign meets cutting-edge AI startup commercial.

Bold minimalist 2D motion design, crisp flat-vector graphics, high-contrast editorial composition, precise graphic choreography, explosive speed ramps, dynamic silhouette match cuts, kinetic typography, clean geometric impact shapes, fluid digital data movement, and strong negative space.

Feel:

government trust + technological confidence + startup speed.

Avoid childish government promotional aesthetics, generic stock graphics, cyberpunk clichés, unnecessary 3D, dominant gradients, smoke, lens flare, glitch effects, random UI screens, excessive holograms, watermark, and visual clutter.

COLOR PALETTE

Respect the supplied Gwangjin-gu BI colors.

Combine with:

clean white

deep navy

near-black

neon cyan

electric orange

Primary background: clean white
Institutional structure: deep navy
AI transformation: neon cyan
Speed / impact accents: electric orange

SHOT 1 — THE BI AWAKENS

00:00.000–00:01.200

Clean white background.

Place the official Gwangjin-gu BI precisely in the center.

Do NOT redesign or distort it.

Everything remains still.

CLICK.

A razor-thin neon cyan scanning line appears beneath the BI and scans rapidly across it.

Tiny geometric data particles awaken inside the BI.

Hold for 2 frames.

Then—

WHIP.

The BI releases controlled cyan energy and its graphic lines stretch outward at extreme speed.

SHOT 2 — BI BECOMES GWANGJIN-GU OFFICE

00:01.200–00:02.800

Use a sophisticated geometric match cut.

The structural lines and colors of the Gwangjin-gu BI physically transform into the architecture of the attached Gwangjin-gu Office building.

BI curves
→ architectural contours.

BI lines
→ windows and façade edges.

BI geometric shapes
→ building masses.

No crossfade.

The final structure must clearly resemble the actual supplied Gwangjin-gu Office building.

Briefly integrate the real building image into the graphic composition using selective posterization / graphic simplification while retaining its recognizable architecture.

Camera: fast controlled push-in.

Background remains mostly white.

SHOT 3 — THE BURDEN OF ADMINISTRATION

00:02.800–00:04.100

Administrative paperwork pours outward from the building:

documents, forms, tables, folders, approval sheets, legal documents, checklists, and repeated data-entry symbols.

They rapidly accumulate around the building.

For about 0.3 seconds the composition becomes deliberately dense and heavy.

The building appears trapped behind repetitive work.

A tiny clock symbol appears.

TICK.

Then a neon cyan scanning line emerges from the building.

CLICK.

It scans across every document at extreme speed.

SHOT 4 — GWANGJIN AX / AI PROCESSING

00:04.100–00:05.900

Scanned paperwork instantly transforms through shared silhouettes:

paper sheet
→ structure
```

### 15. Manus 웹앱에 MCP 서버 연결 지시문

- 출처: @gasket_love — https://www.threads.com/@gasket_love/post/DYg2KeDAVj3
- 목적: 기존 tRPC/Express 웹앱에 MCP endpoint·인증·tool·Claude.ai 커넥터 구성을 추가한다.
- 재사용성: 상 — 기존 웹앱에 표준 도구 연동과 인증을 붙이는 구조는 여러 환경에 적용 가능하다.
- 스킬화 제안: `mcp-server-integration`
- 원문: 캡처된 전체 범위 안에서 원문이 약 4,000자 제한으로 절단됐다. 마지막은 미완성 문장이다.

```text
# Manus 웹앱에 MCP 서버 구축하고 Claude.ai에 연결하기

> 이 문서는 Manus 플랫폼에서 운영 중인 웹앱(tRPC + Express 스택)에 MCP(Model Context Protocol) 서버를 추가하고, Claude.ai 커스텀 커넥터로 연결하는 전 과정을 설명합니다. 실제 구축 과정에서 겪은 시행착오와 해결 방법을 포함합니다.

---

## 1. MCP란 무엇인가

MCP(Model Context Protocol)는 Anthropic이 정의한 표준 프로토콜로, AI 모델(Claude 등)이 외부 도구(tool)를 호출할 수 있게 해줍니다. Claude.ai 웹에서 커스텀 커넥터를 등록하면, 대화 중에 "내 DB에서 데이터를 조회해줘", "이 내용을 저장해줘" 같은 요청을 Claude가 직접 처리할 수 있습니다.

**핵심 장점**: Claude.ai 구독 요금만으로 AI 기능을 사용할 수 있어, 별도의 Claude API 호출 비용이 발생하지 않습니다.

---

## 2. 전체 구조

```
Claude.ai 웹
│
│ MCP (HTTP+SSE)
▼
웹앱 서버 /api/mcp 엔드포인트
│
│ DB 함수 호출
▼
데이터베이스 (MySQL/TiDB)
```

MCP 서버는 별도 서버가 필요 없습니다. **기존 웹앱 서버에 `/api/mcp` 경로를 추가**하는 방식으로 구현합니다.

---

## 3. 사전 준비

### 3-1. 필요한 패키지 설치

```bash
pnpm add @modelcontextprotocol/sdk zod
```

### 3-2. 인증 토큰 준비

MCP 엔드포인트는 외부에서 접근 가능하므로 반드시 인증이 필요합니다. 기존에 `BOT_INGEST_SECRET` 같은 서버 간 통신용 시크릿이 있다면 재사용하고, 없다면 새로 생성합니다.

```bash
# 랜덤 토큰 생성 예시
openssl rand -hex 32
```

생성한 값을 환경변수로 등록합니다 (Manus 웹앱 → Settings → Secrets).

---

## 4. MCP 서버 구현

### 4-1. 파일 구조

```
server/
mcp.ts ← MCP 서버 전체 구현
db.ts ← DB 함수 (기존 파일에 추가)
routers.ts ← tRPC 라우터 (기존 파일)
```

### 4-2. mcp.ts 기본 골격

```typescript
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StreamableHTTPServerTransport } from "@modelcontextprotocol/sdk/server/streamableHttp.js";
import { z } from "zod";
import type { Request, Response } from "express";

// ── 인증 미들웨어 ─────────────────────────────────────────
function authMiddleware(req: Request, res: Response): boolean {
const authHeader = req.headers["authorization"] || "";
const token = authHeader.replace("Bearer ", "").trim();
const expected = process.env.BOT_INGEST_SECRET || "";

if (!expected || token !== expected) {
res.status(401).json({ error: "Unauthorized" });
return false;
}
return true;
}

// ── MCP 서버 생성 및 tool 등록 ────────────────────────────
function createMcpServer(): McpServer {
const server = new McpServer({
name: "my-webapp-mcp",
version: "1.0.0",
});

// tool 등록 예시
server.tool(
"get_stats",
"이번 달 통계를 조회합니다.",
{
type: z.enum(["monthly", "weekly"]).optional().describe("조회 기간 타입"),
},
async (args) => {
// DB 함수 호출
const result = await getStats(args.type ?? "monthly");
return {
content: [{ type: "text", text: JSON.stringify(result, null, 2) }],
};
}
);

return server;
}

// ── HTTP 핸들러 (Stateless 모드) ──────────────────────────
export async function mcpHandler(req: Request, res: Response): Promise<void> {
if (!authMiddleware(req, res)) return;

const server = createMcpServer();

// ⚠️ 중요: sessionIdGenerator를 undefined로 설정해야 Stateless 모드가 됩니다.
// Stateless 모드를 사용하지 않으면 서버 재시작 시 세션이 끊겨
// Claude.ai에서 "서버 오류" 메시지가 반복적으로 발생합니다.
const transport = new StreamableHTTPServerTransport({
sessionIdGenerator: undefined,
});

res.on("close", () => {
transport.close();
server.close();
});

await server.connect(transport);
await transport.handleRequest(req, res, req.body);
}
```

### 4-3. Express 라우터에 등록

`server/index.ts` 또는 메인 서버 파일에 다음을 추가합니다.

```typescript
import express from "express";
import { mcpHandler } from "./mcp.js";

const app = express();
app.use(express.json());

// MCP 엔드포인트 — GET(SSE)과 POST(RPC) 모두 동일 핸들러로 처리
app.all("/api/mcp", mcpHandler);
```

---

## 5. tool 작성 패턴

### 5-1. 기본 패턴

```typescript
server.tool(
"tool_name", // tool 식별자 (영문 소문자, 언더스코어)
"tool에 대한 설명", // Claude가 언제 이 tool을 쓸지 판단하는 근거
{
// zod 스키마로 파라미터 정의
param1: z.string().describe("파라미터 설명"),
param2: z.number().optional().describe("선택적 파라미터"),
},
async (args) => {
const result = await dbFunction(args.param1, args.param2);
return {
content: [{ type: "text", text: JSON.stringify(result) }],
};
}
);
```

### 5-2. 오너 사용자 ID 처리 — 반드시 주의

MCP는 로그인 세션 없이 서버 간
```

### 16. 경력 기반 부업 설계 프롬프트 세트

- 출처: @gpt_park — https://www.threads.com/@gpt_park/post/DauaXBHmO2V
- 목적: 개인 경력에서 부업 후보를 만들고, 수요 검증·가격·90일 실행계획·첫 고객 전략을 연속 설계한다.
- 재사용성: 상 — 입력 슬롯과 출력 요구사항이 명확한 5개의 독립 프롬프트가 있다.
- 스킬화 제안: `side-hustle-design`
- 원문: 작성자 댓글 5개에서 공개된 프롬프트.

```text
gpt_park
부업
2026-07-13
1. 내 경력에서 부업 캐내기
"당신은 커리어 기반 부업 설계 전문가입니다. 아래 정보를 바탕으로 제가 지금 당장 시작할 수 있는 부업 아이디어 7개를 뽑아주세요.
- 현재 직무: [직무 입력]
- 경력 연차: [연차 입력]
- 잘하는 일 3가지: [강점 입력]
- 주당 투입 가능 시간: [시간 입력]
- 초기 자본: [금액 입력]
각 아이디어마다 다음을 표로 정리하세요.
(1) 부업 이름, (2) 내 경력이 왜 유리한지, (3) 예상 월 수익 범위, (4) 첫 수익까지 걸리는 기간, (5) 필요 초기 비용, (6) 난이도 상중하.
마지막에 '가장 빨리 돈이 되는 순서'로 재정렬해서 이유와 함께 알려주세요."

gpt_park
부업
2026-07-13
2. 진짜 수요 있는지 검증하기
"당신은 냉정한 시장 검증 애널리스트입니다. 제가 고려 중인 부업 아이디어를 검증해주세요.
- 부업 아이디어: [아이디어 입력]
- 타깃 고객: [고객 입력]
다음 항목을 순서대로 분석하세요.
(1) 이 고객이 실제로 돈을 내고 해결하려는 문제인가, 아니면 있으면 좋은 수준인가
(2) 이미 존재하는 경쟁자 5곳과 그들의 가격대
(3) 내가 파고들 수 있는 빈틈 3가지
(4) 이 시장이 이미 포화라면 솔직하게 그렇다고 말하고, 대신 노려야 할 니치 시장을 제안
듣기 좋은 말은 빼고, 실패 가능성이 높으면 높다고 직설적으로 알려주세요."

gpt_park
부업
2026-07-13
3. 수익 모델과 가격 설계하기
"당신은 수익 모델 설계자입니다. 아래 부업의 가격표를 만들어주세요.
- 부업: [부업 입력]
- 제공하는 결과물: [결과물 입력]
- 목표 월 수익: [금액 입력]
다음을 설계하세요.
(1) 3단계 가격 패키지 (라이트, 스탠다드, 프리미엄) - 각 구성과 가격
(2) 목표 월 수익을 채우려면 각 패키지를 몇 건 팔아야 하는지 계산
(3) 가장 현실적인 조합 1개 추천
(4) 시간당 실질 단가 계산 (본업 시급과 비교)
(5) 절대 하지 말아야 할 저가 수주 기준선
숫자는 반드시 계산 과정을 보여주세요."

gpt_park
부업
2026-07-13
4. 90일 실행 로드맵 짜기
"당신은 실행 코치입니다. 아래 부업을 90일 안에 첫 수익까지 끌고 가는 로드맵을 만들어주세요.
- 부업: [부업 입력]
- 주당 가용 시간: [시간 입력]
- 현재 보유 자산: [보유 채널, 인맥, 포트폴리오 등 입력]
30일 단위로 나누어 다음을 작성하세요.
(1) 각 30일의 단 하나의 목표
(2) 주차별 실행 과제 (주당 시간 안에 실제로 가능한 분량만)
(3) 각 구간의 성공 판단 기준 (숫자로)
(4) 이 기준을 못 넘겼을 때의 대안 행동
욕심내서 일정을 늘리지 말고, 제 가용 시간 안에서만 계획하세요."

gpt_park
부업
2026-07-13
5. 첫 고객 10명 확보 전략
"당신은 초기 고객 확보 전문가입니다. 광고비 0원으로 첫 고객 10명을 만드는 전략을 짜주세요.
- 부업: [부업 입력]
- 타깃 고객이 모여 있는 곳: [커뮤니티, 플랫폼, SNS 등 입력]
- 내가 쓸 수 있는 채널: [보유 채널 입력]
다음을 작성하세요.
(1) 첫 고객 10명을 만들 현실적인 경로 3가지 (효과 순으로)
(2) 각 경로에서 그대로 복사해 쓸 수 있는 메시지 초안 1개씩
(3) 무료 또는 할인으로 시작해야 한다면 그 조건과 종료 시점
(4) 첫 고객에게 반드시 받아내야 할 것 (후기, 사례, 소개)
(5) 30일 안에 10명을 못 채웠을 때 바꿔야 할 변수 1개"
```

### 17. 15초 모션그래픽 쇼릴 프롬프트

- 출처: @gptaku_ai — https://www.threads.com/@gptaku_ai/post/Dd3x3EgEc9z
- 목적: 제품 스크린샷·로고와 음악을 사용해 이력서용 모션그래픽 쇼릴 영상을 요청한다.
- 재사용성: 중 — 15초 길이와 제품 소개 형식은 재사용할 수 있으나 원문은 특정 제품에 맞춰져 있다.
- 스킬화 제안: `motion-showreel-prompt`
- 원문: 작성자 댓글. 동일 프롬프트의 제품 교체 변형은 @gptaku_ai Ddz__34ESxY에 게시되어 있어 원문 중복으로 병합했다. 원문의 `muic`, `assts` 표기를 보존한다.

```text
gptaku_ai
2026-09-29
Make a dynamic 15-second motion graphics video that shows what an incredible motion designer you are, like it's your showreel for a résumé. go all out.
Make it a video to introduce `fivetaku.github.io/gptak…`
1. Use actual product screenshot/logo/assts
2. must have music and motion must match the music. Do it like a real professional production video, not like a demo or prototype.
```

## 누적본 현황

- `details2` 현재 보고된 수: 355건(수집 중).
- GJC 기존 추출본 최신 스냅샷: 322건 스캔, 42개 후보 신호, 14개 원문 항목.
- 이 파일의 numbered source records: 17개. 여러 레코드는 한 게시물 안에 여러 개의 prompt block을 포함하며, gptaku_ai 쇼릴 프롬프트의 제품 교체형은 중복 변형으로 합쳤다.
- 위 수치는 전수 완료 수치가 아니다. 남은 상세파일을 계속 검사하고 이 파일에 이어 반영해야 한다.
