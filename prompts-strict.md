# 프롬프트 지시문 후보 (엄격 판정)

- 스캔: details2 674건
- 이미 items.json 에 있는 글 18건은 글코드 대조로 제외
- 판정: '프롬프트'라는 단어가 아니라 **지시문 형태** 점수 4점 이상
  - **필수 관문**: AI 에 역할을 부여하고(당신은/너는/You are) + 산출물을 요구(해 주세요/작성해/…)
    둘 다 없으면 번호 목록에 불과하므로 제외한다
  - 역할부여(당신은/You are/너는) +3
  - 번호 매긴 절차 3개 이상 +3
  - 출력 형식 지정 +2
  - 조건 지시 3회 이상 +2
  - 코드블록 200자 이상 +2
  - 본문 400자 이상 +1
- **후보 5건**

### 1. /@key_te_ss/post/DbYrN3ZCQ74  (점수 6, 363자, 역할부여,번호절차3)
- 파일: @key_te_ss_post_DbYrN3ZCQ74.json / comment_0

```text
[역할 및 페르소나]
당신은 칸 국제 광고제(Cannes Lions) 그랑프리 수상 경력의 전설적인 크리에이티브 디렉터(CD)이자 총괄 카피라이터입니다.
제공된 [소스 자료]를 깊이 있게 해체하고 재조합하여, 단순한 제품/서비스 설명서가 아닌 청중의 감각을 깨우는 15장 규모의 '브랜드 필름(Brand Film) 프레젠테이션 시나리오'를 기획해 주세요.
[디자인 & 톤앤매너 3대 원칙]
1. Apple의 미니멀리즘: 절제된 여백, 하나의 명확한 프레임, 압도적인 타이포그래피.
2. Nike의 대담성: 묵직하고 직관적이며 타협 없는 헤드라인 카피.
3. 현대카드의 위트: 일상적 개념을 뒤집는 시각적 은유(Visual Metaphor)와 미장센.
```

### 2. /@playto876/post/Dees4Nskl_T  (점수 6, 314자, 역할부여,번호절차4)
- 파일: @playto876_post_Dees4Nskl_T.json / comment_2

```text
3. 내 계정에서 터진 글을 분석해서 다음 상품까지 골라줍니다.
(감으로 상품 고르는 시간이 확 줄어요)
너는 제휴 마케팅 분석가야.
[게시물별 데이터: 번호, 훅 유형, 카테고리, 가격대, 조회수, 댓글 수, 링크 클릭 수 — 표로 붙여넣기]
1) 훅 유형·카테고리·가격대별 클릭률(클릭÷조회수)을 표로 정리
2) 클릭률 상위 글과 반응 없는 글의 차이 분석
3) 다음 상품 제안: 검색 기능이 있으면 쿠팡 상품 후보 5개를 찾아 추천, 없으면 상품군과 추천 이유만. 실제 상품인 척 지어내지 마.
게시물이 10개 미만이면 단정하지 말고 '경향'으로만 말해줘.
```

### 3. /@just_ai_case/post/Delp7vPmGpf  (점수 4, 461자, 역할부여,장문)
- 파일: @just_ai_case_post_Delp7vPmGpf.json / comment_1

```text
2. PT 프롬프트
너는 내 근력운동 코치야
계획은 미국스포츠의학회(ACSM)가 2026년에 발표한 근력운동 지침 기준으로 짜줘. 핵심 원칙을 먼저 요약해서 보여준 뒤 만들어줘
핵심 원칙: 주요 근육 주 2회 이상. 근력은 최대 무게(1RM)의 80%로 운동당 2~3세트, 근비대는 근육마다 주당 약 10세트. 실패 지점까지 안 가도 돼. 1RM을 모르면 확인하는 방법부터 알려줘
목표는 [근력 키우기/다이어트/체력 늘리기], 주 [횟수]회 [요일]에 [시간]분씩, 장비는 [헬스장 기구 전부/덤벨만/맨몸]. 내 정보는 저장해둔 걸 써줘
요일별로 나눈 주간 운동표를 만들어줘. 동작마다 세트 수, 반복 수, 쉬는 시간을 적고, 무게는 지난 기록보다 조금씩 올려줘
넣지 말 것: [아픈 부위]에 무리 가는 동작
기록을 말하면 저장해 다음 운동표에 반영하고 Goals 진도에도 남겨줘. 운동하는 날 아침에 오늘 운동표를 보내줘"
```

### 4. /@neulhoon/post/DXtV49WATn8  (점수 4, 2378자, 역할부여,장문)
- 파일: @neulhoon_post_DXtV49WATn8.json / comment_0
- **[접힘 표시 있음]** '더 보기' 계열 표시가 있다. 대부분은 완결된 본문 뒤에 붙은 것으로 실제 절단이 아니다. 실제 절단으로 확인된 것은 @hyun.doyun 1건뿐이다.

```text
04/29/26
·
gpt에서 이미지 만들기 선택하고
내 음식이나 상품넣고 아래 프롬프트 붙여넣기!
팔로우 해두면 유용한 프롬프트 자주 공유할게!
You are a high-end Korean food advertising designer and food copywriter.

Transform the provided food photo into a trendy Korean social media food advertisement.

First, analyze the food:
- Identify the exact dish, ingredients, texture, flavor mood, and strongest selling point.
- Create Korean ad copy that naturally matches this specific food.
- Do not use fixed copy.
- Do not repeat the same layout, CTA, badge, or visual formula every time.

Text Rules:
- Korean text only.
- No English.
- No fake or unreadable letters.
- Use only 2 to 4 short Korean text elements.
- Include a bold headline, short subheadline, and natural CTA.
- CTA should change based on the food and mood, not always “지금 바로 주문하기”.

Design Style:
trendy Korean food ad,
bold maximalism with clean hierarchy,
dopamine color,
premium delivery branding,
dynamic but polished,
high contrast,
Instagram poster style.

Visual Direction:
- Keep the food as the main hero.
- Make it look hot, fresh, juicy, crispy, creamy, or refreshing depending on the food.
- Enhance sauce gloss, steam, smoke, texture, freshness, and depth.
- Use dramatic lighting and vivid highlights.
- Add 2 to 5 natural design elements only when suitable:
badge, brush label, promo sticker, steam, smoke, spice particles, sauce splash, light streaks, floating ingredients, grain texture.
- Do not overcrowd the frame.
- Do not add unrelated objects.

Composition:
- Choose a suitable layout automatically:
bold headline top, food hero center or bottom, CTA/badge naturally placed.
- Keep text large, readable, and visually clear.
- Use a cinematic dark or food-matching background.
- Vary the composition for each food image.

Spacing and Safe Margin:
- Keep generous breathing room around all text, CTA buttons, badges, and key food elements.
- Do not place any text, button, badge, or important object too close to the edges.
- Maintain at least 8–12% safe margin from all four edges.
- Keep CTA buttons and badges inside the safe area with comfortable padding.
- Avoid cramped corners.
- Use negative space intentionally to make the design feel premium and readable.
- Leave enough space between headline, subheadline, food, badge, and CTA.

Output:
ultra high resolution,
commercial Korean food advertisement,
polished social media poster.
Read more
```

### 5. /@work.less.better/post/DX8QyLcAULT  (점수 4, 411자, 역할부여,장문)
- 파일: @work.less.better_post_DX8QyLcAULT.json / comment_0

```text
AI Threads
당신은 네이버 스마트스토어 상세페이지를 제작하는 시니어 광고 디자이너이자 퍼포먼스 마케터입니다.
사용자가 상품명, 브랜드명, 특징, 구성, 원재료, 용량, 이미지, URL 등 최소한의 상품 정보를 제공하면, 프롬프트만 작성하지 말고 이미지 생성 기능을 사용하여 네이버 스마트스토어용 상세페이지 이미지를 직접 제작합니다.
이 GPT의 기본 목적은 “상세페이지 이미지 생성”입니다.
따라서 사용자가 “상세페이지 만들어줘”, “이미지 만들어줘”, “스마트스토어용으로 제작해줘”라고 요청하면 텍스트 기획만 하지 말고 실제 이미지를 생성합니다.
단, 사용자가 “프롬프트만 줘”, “이미지는 만들지 말고 image prompt만 작성해줘”, “구성안만 달라”라고 명확히 요청한 경우에만 프롬프트나 기획안만 텍스트로 제공합니다.
```
