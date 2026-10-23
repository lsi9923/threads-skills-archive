---
name: hyperframes-renderer
description: Hyperframes CLI로 음성·자막·B-roll을 자동 컷편집해 최종 mp4를 빌드하는 스킬 생성 지시문과 실행 절차. "하이퍼프레임즈로 영상 렌더", "쇼츠 자동 합성", "음성+자막+B롤 자동 편집" 요청에 쓴다. Claude Skill 형태로 만들 때 이 문서를 그대로 지시문으로 쓴다.
---

# Hyperframes 자동 렌더러

## 언제 쓰나
음성 파일·자막(srt)·B-roll 원본 영상이 이미 있고, 이걸 규칙대로 자동 합성해 mp4로 뽑을 때.

## 입력 파일 규약

| 역할 | 경로 패턴 |
|---|---|
| 음성 | `output/audio_*.mp3` |
| 자막 | `output/audio_*.srt` |
| B-roll 원본 | `downloads/raw_videos/source_*.mp4` |

## 실행 작업

1. **설정 파일 자동 생성** — `render_config.json`을 만든다.
2. **컷편집** — 오디오 타임라인에 맞춰 원본 영상들을 **1.5초~2.5초 단위**로 교체한다.
3. **자막 오버레이** — 교체된 영상 위에 모션 애니메이션이 적용된 자막을 올린다.
4. **빌드** — 아래 명령으로 최종 영상 생성.

```bash
hyperframes render render_config.json --output output/final_shorts.mp4
```

## render_config.json 골격

```json
{
  "audio": "output/audio_001.mp3",
  "subtitles": "output/audio_001.srt",
  "sources": ["downloads/raw_videos/source_01.mp4"],
  "cut": { "min": 1.5, "max": 2.5, "sync": "audio_timeline" },
  "caption": { "animation": "slide", "position": "bottom" },
  "output": "output/final_shorts.mp4"
}
```

## 검수 체크리스트

- [ ] 자막과 음성이 어긋나지 않는가
- [ ] 컷 길이가 1.5~2.5초 범위를 벗어나지 않는가
- [ ] 자막이 화면 밖으로 나가지 않는가
- [ ] 원본 영상에 개인정보·워터마크가 남아 있지 않은가
- [ ] 결과물 길이가 음성 길이와 일치하는가

## 스킬로 만들 때 (Claude Skill 생성 지시문 원문)

```
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
- Hyperframes CLI 명령어를 실행하여 최종 영상 빌드:
  hyperframes render render_config.json --output output/final_shorts.mp4
```

## 주의
- Hyperframes는 **HTML/CSS/JS를 MP4로 변환**하는 엔진이다. 헤드리스 크롬으로 프레임을 캡처한 뒤 ffmpeg로 합친다.
- 대량 렌더는 시간이 오래 걸린다. 진행 로그를 남기고 중간에 끊겨도 이어서 할 수 있게 만든다.

출처: @ai_ohwoo_wow Threads 저장글 (쇼핑 쇼츠 완전 자동화 4탄)
