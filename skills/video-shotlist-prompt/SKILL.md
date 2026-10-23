---
name: video-shotlist-prompt
description: 짧은 영상(15~30초) 멀티샷 프롬프트를 샷 리스트로 설계한다. 샷마다 시간·카메라·인물·대사·사운드·네거티브를 고정해 한 번의 생성으로 여러 컷을 뽑는다. "영상 프롬프트", "샷 리스트", "멀티샷 프롬프트", "브이로그 영상 만들어줘", "15초 영상 프롬프트" 요청에 쓴다.
---

# 영상 샷리스트 프롬프트

## 언제 쓰나
Veo·Kling·Hailuo·Runway 같은 영상 모델에 넣을 **다중 컷 프롬프트**를 만들 때.
한 문장으로 "영상 만들어줘"라고 쓰면 모델이 한 앵글로만 간다. 샷을 명시해야 컷이 나뉜다.

## 핵심 원칙
1. **총 길이와 샷 개수를 먼저 못 박는다.** 예: "15초, 정확히 7개 샷".
2. **금지 조건을 명시한다.** "단일 앵글 금지, 원테이크 금지, 동일 구도 금지".
3. **참조 이미지 우선순위를 정한다.** 어느 이미지가 인물용이고 어느 것이 배경용인지 명시. 배경 이미지의 인물을 복사하지 말라고 못 박는다.
4. **인물은 성인임을 명시한다.**
5. **샷마다 6개 항목**을 채운다: 시간·프레이밍·카메라·행동·대사·사운드.

## 출력 형식

```text
Create a [N]-second, [비율] photorealistic multi-shot [장르] with exactly [N] distinct shots.
Do not use a single camera angle, single continuous take, or one unchanging composition.
Each shot must have a clearly different framing or camera position.

REFERENCE HIERARCHY:
@image_1 is the sole identity and wardrobe reference for [인물]. Preserve [얼굴·머리·체형·의상 디테일].
@image_2 is used only as a reference for [배경 요소]. Do not copy or recreate the person from @image_2.

CHARACTERS:
[이름] — clearly adult. [외모·의상 고정 문장]. Same person in every shot.

NEGATIVE:
- no text overlays, no watermark, no logo
- no extra limbs, no face morphing between shots
- no [장르에 맞지 않는 것]

SHOTS:
SHOT 1 (0.0–2.0s)
  FRAMING: [와이드/미디엄/클로즈업]
  CAMERA: [핸드헬드/고정/팬/돌리], [앵글]
  ACTION: [무엇을 하는가]
  DIALOGUE: "[대사 또는 없음]"
  SOUND: [환경음·음악]

SHOT 2 (2.0–4.5s)
  ...
```

## 샷 설계 규칙
- **첫 샷은 공간을 보여준다.** 마지막 샷은 감정이나 여운으로 닫는다.
- **인접 샷의 프레이밍을 바꾼다.** 와이드→미디엄→클로즈업처럼.
- **한 샷에 행동 하나.** 두 가지를 시키면 모델이 뭉갠다.
- **대사가 있으면 짧게.** 2초 샷에 긴 대사는 립싱크가 깨진다.
- **시간 합이 총 길이와 정확히 맞아야 한다.**

## 체크리스트
- [ ] 총 길이 = 샷 시간 합
- [ ] 샷 개수가 프롬프트 첫 줄과 실제 SHOT 수가 일치
- [ ] 인물 성인 명시
- [ ] 참조 이미지 우선순위 명시
- [ ] NEGATIVE 에 텍스트·워터마크 금지 포함
- [ ] 인접 샷 프레이밍이 다른가

---

출처: @reactor_art Threads 저장글 (15초 7샷 브이로그)
