---
name: image-prompt-portrait
description: 인물 사진 이미지 생성 프롬프트를 섹션 구조(IDENTITY/SUBJECT/WARDROBE/POSE/LIGHT/CAMERA/ENVIRONMENT/COLOR/MOOD/QUALITY)로 만들어 준다. "인물 사진 프롬프트", "화보 프롬프트 만들어줘", "저조도 인물 사진", "이미지 프롬프트 구조", "포트레이트 프롬프트" 요청에 쓴다.
---

# 인물 사진 프롬프트 빌더

## 언제 쓰나
이미지 생성 모델(Midjourney·Flux·SD·Seedream 등)에 넣을 **인물 사진 프롬프트**를 만들 때.
한 덩어리 문장으로 쓰면 모델이 일부만 반영한다. 섹션으로 나눠 쓰면 재현성이 올라간다.

## 10개 섹션 구조

| 섹션 | 반드시 들어갈 것 |
|---|---|
| **IDENTITY** | 나이(성인 명시), 인종, 얼굴형, 머리카락 길이·질감·볼륨, 눈썹, 속눈썹, 입술 |
| **SUBJECT** | 화면에 무엇이 잡히는가, 프레이밍(상반신/전신), 시선 방향 |
| **WARDROBE** | 의상 소재·컷·디테일, 액세서리 |
| **POSE** | 체중 중심, 어깨 회전, 고개 각도, 손 위치, 시선 |
| **LIGHT** | 광원 위치·세기·색온도, 그림자 방향 |
| **CAMERA** | 초점거리(mm), 앵글(로우/아이레벨), 심도, 필름/디지털 |
| **ENVIRONMENT** | 배경, 공간감, 거리 |
| **COLOR** | 주조색, 대비, 채도, 그레이딩 |
| **MOOD** | 감정·분위기 한 문장 |
| **QUALITY** | 해상도·질감·피부 표현 (예: "photorealistic, skin texture visible, no plastic look") |

## 작성 규칙

1. **성인임을 명시한다.** 나이를 쓰고 "clearly adult features"를 넣는다. 이 규칙은 예외 없다.
2. **한 섹션에 한 주제만.** LIGHT에 옷 이야기를 섞지 않는다.
3. **형용사보다 물리적 사실.** "예쁜" 대신 "광대에 하이라이트가 떨어지고 턱 아래는 그림자".
4. **모순 금지.** "완전한 어둠"과 "선명한 얼굴 조명"을 같이 쓰지 않는다.
5. **부정문 최소화.** "no plastic look" 정도만. "not ugly" 같은 표현은 역효과.
6. **의상은 노출이 아니라 재단으로 묘사한다.** 소재·라인·디테일로 쓴다. 성적 대상화 묘사는 쓰지 않는다.

## 출력 형식

```text
IDENTITY: ...
SUBJECT: ...
WARDROBE: ...
POSE: ...
LIGHT: ...
CAMERA: ...
ENVIRONMENT: ...
COLOR: ...
MOOD: ...
QUALITY: ...
```

한 줄로 합쳐야 하는 모델이면 위를 `, `로 연결해 한 문단으로 준다.

## 예시 (저조도 화보)

```text
IDENTITY: A photorealistic portrait of a 28-year-old Korean woman with clearly adult features; long glossy dark hair with volume at the roots and curled ends framing the face.
SUBJECT: Half-body frame from a low angle in a dim room; she turns toward the camera by one shoulder, face in half profile, eyes cast down into the lens.
WARDROBE: A black silk camisole with a clean V neckline; a thin chain with a small round pendant resting at the collarbone.
POSE: Weight over the right leg, shoulders rotated so the right leads; chin slightly high because the camera sits low.
LIGHT: Single soft key from camera-left at low intensity, 3200K warm; a faint rim from behind the right shoulder.
CAMERA: 85mm equivalent, low angle, f/1.8, shallow depth of field, digital full-frame.
ENVIRONMENT: Dark interior, background falls off to black within two meters.
COLOR: Near-monochrome with warm skin tones, deep shadows, low saturation overall.
MOOD: Quiet, intimate, self-possessed.
QUALITY: Photorealistic, visible skin texture and fine hair detail, natural pore structure, no plastic or airbrushed look.
```

## 체크리스트
- [ ] 10개 섹션이 모두 있다
- [ ] 성인 명시가 있다
- [ ] LIGHT 와 CAMERA 가 서로 모순되지 않는다
- [ ] 형용사보다 물리적 서술이 많다

---

출처: @han45406480 Threads 저장글 (IDENTITY 구조 이미지 프롬프트)
