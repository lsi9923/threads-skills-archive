# Threads GitHub 도구 설치 판정 및 실행 기록

- 초기 생성: 2026-10-24T03:37:43
- 기준: github-repos.md, 40개 저장소 README 수집·열람 40/40 (2026-10-24); 5개 단위 8회 저장 완료
- 완료 기준: README 설치 지시 검증 + 비전역 설치 + 실제 동작 확인

| repo | 유형 | 설치명령 | 난이도 | 위험 | 설치결과 | 사용법한줄 |
|---|---|---|---|---|---|---|
| morluto/rea | B (MCP+CLI) | `npx rea-agents setup` | 보통 | 에이전트 MCP 설정 변경·네이티브 엔진은 선택 설치 | 기설치 검증 완료: `rea --version` → `6.7.0`; Claude `.claude.json`과 Codex `config.toml` 양쪽 `rea` 등록 확인 | `rea`로 앱·코드 역공학을 요청한다. |
| obra/superpowers | A (스킬 프레임워크·Claude 플러그인) | `/plugin install superpowers@claude-plugins-official` | 쉬움 | Claude 사용자 플러그인 설정 변경 | 보류: Claude 내부 `/plugin` 설치 필요; `claude plugin list`에 없음; 미실행 | Claude에서 `/plugin install superpowers@claude-plugins-official` 실행 후 스킬을 사용한다. |
| msitarzewski/agency-agents | D (에이전트 역할 프롬프트 모음) | `./scripts/install.sh --tool claude-code` 또는 `cp engineering/*.md ~/.claude/agents/` | 보통 | 대량 에이전트 정의 전역 추가·기존 파일 충돌 가능 | 보류: Claude 사용자 에이전트 전체 변경; 설치 미실행 | 필요한 개발자·디자이너 역할 프롬프트를 Claude에 연결한다. |
| harry0703/MoneyPrinterTurbo | C (CLI + WebUI 영상 앱) | `python -m venv .venv` → `.venv\Scripts\Activate.ps1` → `python -m pip install mpt` | 보통 | 온라인 영상 모델·음성·소재 기능에 API Key 필요; 런타임 파일 생성 | 보류: 핵심 외부 서비스의 API Key 필요; `python -m pip show mpt` 미설치 확인 | API Key 준비 후 `mpt webui`로 영상 제작 화면을 연다. |
| stablyai/orca | E (데스크톱 앱) | README에 설치법 없음 (Windows 설치 파일 `orca-windows-setup.exe` 다운로드 안내) | 보통 | Windows 앱 설치·에이전트 계정 연결 필요 가능 | 보류: Windows 설치 프로그램 실행 및 계정 연동 범위; 미설치 | Orca 앱을 실행해 여러 코딩 에이전트를 한 화면에서 관리한다. |
| D4Vinci/Scrapling | C (크롤링 CLI·Python 라이브러리; 선택 MCP) | `pip install scrapling` | 쉬움 | 브라우저 기능 추가 시 별도 다운로드·사이트 정책 준수 | 기설치 검증 완료: `scrapling --help` 정상, Python 패키지 0.4.5 확인 | `scrapling extract`로 사이트의 필요한 정보를 수집한다. |
| storytold/photocraft | E (Rust PSD 편집 애플리케이션) | `git clone https://github.com/storytold/photocraft` → `cargo run --release -p photocraft -- image.psd` | 어려움 | Rust 전체 컴파일·Windows 앱 실행·대규모 의존성 | 보류: Rust 앱 전체 빌드와 데스크톱 환경 영향; 미설치 | PSD 파일을 열어 레이어를 편집한다. |
| blader/humanizer | A (Claude Skill) | `npx skills add blader/humanizer --global --agent claude-code` | 쉬움 | Claude 사용자 스킬 디렉터리 추가 | 설치 검증 완료: `~/.claude/skills/humanizer/SKILL.md` 존재; Claude 플러그인 로드 3.1.0 확인 | Claude에게 `/humanizer`로 문장 다듬기를 요청한다. |
| abhigyanpatwari/GitNexus | C (저장소 분석 CLI·선택 MCP 설정) | `npx gitnexus analyze` / `npx gitnexus setup` (`npm install -g gitnexus` 선택) | 보통 | `setup`은 코딩 에이전트 설정 변경·전역 npm 설치 옵션 | 설치 검증 완료: `npx gitnexus --version` → `1.6.12`; `setup`은 에이전트 설정 변경으로 미실행 | 프로젝트 폴더 안에서 `npx gitnexus analyze`로 코드 관계를 색인한다. |
| cloudflare/security-audit-skill | A (Claude Skill·보안 감사) | `npx skills add https://github.com/cloudflare/security-audit-skill --skill security-audit --global` | 쉬움 | 감사 실행 시 강한 격리 환경 권장·사용자 스킬 추가 | 설치 검증 완료: `~/.agents/skills/security-audit/SKILL.md` 생성 후 Claude `~/.claude/skills/security-audit/SKILL.md` 복사 및 SHA256 일치; PromptScript 연동만 실패 | Claude에게 현재 코드의 보안 감사를 요청한다. |
| vercel-labs/skills | C (스킬 설치 CLI) | `npx skills add vercel-labs/agent-skills` | 쉬움 | 선택한 에이전트의 스킬 디렉터리 변경 가능 | 기설치 검증 완료: `npx skills --version` → `1.7.4`; 기존 Humanizer·Cloudflare 설치에 사용 | `npx skills find`로 스킬을 찾고 `npx skills add`로 추가한다. |
| Yeachan-Heo/oh-my-codex | C (Codex 오케스트레이션 CLI) | `npm install -g oh-my-codex` | 보통 | 전역 npm 설치·Codex 워크플로 설정 변경 | 기설치 검증 완료: `omx --version` → `0.16.4`; 재설치로 덮어쓰기 하지 않음 | `omx doctor`로 Codex 도구 연결 상태를 검사한다. |
| AIDC-AI/Pixelle-Video | E (로컬 영상 제작 Web 앱) | `git clone https://github.com/AIDC-AI/Pixelle-Video.git` → `cd Pixelle-Video` → `uv run streamlit run web/app.py` | 어려움 | 영상 생성 모델 API Key 또는 로컬 ComfyUI·FFmpeg 필요 | 보류: 영상 모델 인증 또는 대규모 로컬 모델 연동 필요; 미실행 | 웹 화면에서 텍스트를 넣어 AI 영상을 만든다. |
| virattt/dexter | C (금융 분석 에이전트 CLI) | `git clone https://github.com/virattt/dexter.git` → `cd dexter` → `bun install` → `bun start` | 보통 | OpenAI·Financial Datasets API 키 필수, 투자 데이터 처리 | 보류: README의 필수 2종 API Key 미제공; 미설치 | 금융 관련 질문을 에이전트에게 입력해 조사한다. |
| elizaos/eliza | E (에이전트 런타임·웹 앱) | `git clone --filter=blob:none https://github.com/elizaos/eliza.git` → `cd eliza` → `bun install` → `bun run dev` | 어려움 | 광범위한 의존성·네이티브 빌드·환경 자동 설정 | 보류: 대형 모노레포 설치로 시스템·빌드 환경 변경 범위가 큼 | Eliza 실행 화면에서 에이전트와 대화한다. |
| citrolabs/ego-lite | A (ego-browser 스킬·브라우저 앱) | `npx skills add citrolabs/ego-lite` | 쉬움 | 브라우저 앱이 로그인·쿠키 상태에 접근 가능 | 기설치 검증 완료: `~/.claude/skills/ego-browser/SKILL.md`와 로컬 `ego-browser.exe` 존재 | `/ego-browser`로 로그인한 브라우저에서 자동화 작업을 지시한다. |
| open-jarvis/OpenJarvis | C (로컬 AI Jarvis CLI) | `irm https://open-jarvis.github.io/OpenJarvis/install.ps1  /  iex` | 어려움 | 설치 스크립트가 uv·Ollama·로컬 모델·예약작업을 변경 | 보류: Windows 원라이너가 시스템 및 모델 설치를 광범위하게 변경; 미실행 | 설치 후 `jarvis`로 로컬 AI 비서와 대화한다. |
| MiniMax-AI/MiniMax-H3 | A (h3-prompt-writing 스킬; 대형 영상 모델 동봉) | `npx skills add https://github.com/MiniMax-AI/MiniMax-H3 --skill h3-prompt-writing` | 쉬움 (스킬만) | 영상 모델 전체 다운로드는 매우 큼; 스킬 자체는 Markdown | 설치 검증 완료: `h3-prompt-writing/SKILL.md` 설치 후 `~/.claude/skills/`에 복사·해시 일치; 모델 미다운로드 | Claude에게 H3 동영상 프롬프트를 만들어 달라고 요청한다. |
| rehan-remade/universal-modder | A (게임 모딩 스킬·플러그인/CLI) | `uv tool install git+https://github.com/rehan-remade/universal-modder` | 보통 | 전역 CLI·에이전트 플러그인·게임 파일 검사/변경·일부 유료 API | 보류: uv tool 전역 설치 및 게임 폴더 접근 위험; 미설치 | `um scan`으로 게임 환경을 점검한다. |
| storytold/effectcraft | E (모션그래픽 앱·보조 MCP) | `git clone https://github.com/storytold/effectcraft` → `cargo run --release -p effectcraft` | 어려움 | Rust GUI 대형 빌드·Windows MSI 설치 | 보류: GUI/네이티브 빌드로 설치 범위 큼; 미설치 | 앱에서 레이어 애니메이션을 만들고 영상으로 저장한다. |
| The-Swarm-Corporation/AutoHedge | C (Python 패키지·에이전트 도구) | `pip install -U autohedge` | 쉬움 | JUPITER_API_KEY·OPENAI_API_KEY·ANTHROPIC_API_KEY 등 외부 서비스 인증 필요 | 보류: README 환경변수 필수; 인증 없이 동작 확인 불가능해 미설치 | API 키를 연결한 뒤 AutoHedge 금융 자동화 에이전트를 실행한다. |
| 21st-dev/magic-mcp | B (HTTP MCP 서버) | `npx @21st-dev/cli@latest init --client cursor` (README: claude / vscode / windsurf / codex 선택 가능) | 보통 | 21st API 키 필수; 원격 서비스 연결·MCP 클라이언트 설정 변경 | 보류: README에 API 키 발급 요구; 키 없이 MCP 연결 불가 | 21st 계정 API 키를 발급받아 MCP를 연결하고 UI 생성 도구를 호출한다. |
| Yeachan-Heo/gajae-code | C (GJC 에이전트 CLI) | `Invoke-WebRequest -UseBasicParsing https://raw.githubusercontent.com/Yeachan-Heo/gajae-code/v0.15.3/scripts/install.ps1 -OutFile gjc-install.ps1` → `powershell -File gjc-install.ps1` | 쉬움 | 기존 GJC 설정·버전을 덮어쓸 수 있어 신규 설치 생략 | 기설치 검증 완료: `gjc --version` → `gjc/0.18.12` (기존 설치 유지) | 터미널에서 `gjc`를 실행해 에이전트에게 개발 작업을 지시한다. |
| rohitg00/awesome-claude-code-toolkit | A+D (Claude 플러그인·스킬/에이전트 모음) | `/plugin marketplace add rohitg00/awesome-claude-code-toolkit` → `/plugin install claude-code-toolkit` | 보통 | 135개 에이전트·훅·설정 등 광범위한 사용자 환경 변경 | 보류: 대량 에이전트/훅 전역 변경; 개별 스킬 충돌 검토 필요 | Claude Code에서 마켓플레이스를 추가하고 필요한 기능만 선택한다. |
| EpicGames/unreal-engine-skills-for-claude-code-plugin | A+B (Claude 스킬+Unreal MCP) | `/plugin install unreal-engine-skills-for-claude-code@claude-plugins-official` | 보통 | Unreal Editor·MCP 서버와 Git Bash/WSL 환경 필요 | 보류: Unreal Editor 기반 외부 프로그램 및 MCP 서버가 필수; 미실행 | Unreal Editor에서 MCP 서버를 연 뒤 Claude로 블루프린트 등을 조작한다. |
| Jakeschincariol/arena-skill | A (Claude Code Skill) | `git clone https://github.com/Jakeschincariol/arena-skill.git` → `cp -r arena-skill/skills/arena ~/.claude/skills/` | 쉬움 | 서브에이전트 호출 비용 가능; API 키·별도 패키지 불필요 | 설치 검증 완료: `~/.claude/skills/arena/SKILL.md` 존재(19,382 bytes); 이전 설치 확인 | Claude Code에서 `/arena`로 여러 에이전트의 답변을 비교한다. |
| Salomondiei08/oh-my-hermes | A (Hermes 에이전트 스킬·워크플로) | `git clone https://github.com/salomondiei08/oh-my-hermes /tmp/oh-my-hermes` → `bash /tmp/oh-my-hermes/install.sh` | 어려움 | Hermes/Telegram 또는 Slack 게이트웨이·36개 스킬·6개 워크플로 등 전역 변경 | 보류: 기존 Hermes 환경·외부 인증과 광범위한 스킬 설치 요구; 미실행 | Hermes 봇에 작업을 메시지로 보내 여러 코딩 에이전트를 관리한다. |
| HarimxChoi/google-surf-mcp | B (Chrome 검색 MCP 서버) | `npx google-surf-mcp`; Claude MCP 설정에 npx -y google-surf-mcp 등록 (README 예시) | 보통 | Chrome 필요; 첫 실제 검색에서 브라우저 프로필 자동 초기화, 선택형 API 키는 불필요 | 설치·등록 검증 완료: `npx -y google-surf-mcp --version` → `1.1.4`; Claude `~/.claude.json`의 `mcpServers.google-surf` 등록/JSON 유효 확인; 실시간 도구 호출은 미검증 | Claude 재시작 후 Google Surf MCP로 웹 검색과 자료 관계 분석을 요청한다. |
| 3x-haust/oh-my-design | A+C (스킬+디자인 CLI) | `npm install -g @3xhaust/oh-my-design` → `oh-my-design install` → `oh-my-design doctor` | 보통 | 전역 npm 설치 및 Claude·Codex 에이전트 설정/훅 자동 수정 | 보류: README 설치 절차가 글로벌 CLI·에이전트 설정을 변경; 미실행 | 설치된 호스트에서 디자인 스킬로 UI 구성·품질 검사를 요청한다. |
| AlexAI-MCP/hermes-CCC | A (Claude 스킬·에이전트 46종) | `git clone https://github.com/AlexAI-MCP/hermes-CCC` → `.\install.ps1` (Windows README) | 보통 | 46개 스킬 및 MCP·도구를 Claude 사용자 환경에 대량 배포 | 보류: 기존 Claude 스킬·도구 충돌 위험; 전체 전역 설치 미실행 | 원하는 Hermes 기반 Claude 스킬을 선택해 개발·검색 자동화를 맡긴다. |
| 686f6c61/alfred-dev | A+B (Claude 플러그인·에이전트+MCP) | `irm https://raw.githubusercontent.com/686f6c61/alfred-dev/main/install.ps1  /  iex` (README Windows) | 보통 | 원격 PowerShell 설치 스크립트 즉시 실행·사용자 플러그인/훅/MCP 변경 | 보류: 글로벌 Claude 플러그인/훅/MCP 설정 변경하는 원격 스크립트; 미실행 | Claude에서 `/alfred-dev:alfred`를 호출해 개발팀 에이전트를 실행한다. |
| project820/gjc-multivendor-setup-guide | E (GJC 다중 모델 설정 템플릿) | `curl -fsSL https://raw.githubusercontent.com/project820/gjc-multivendor-setup-guide/main/install.sh  /  bash` | 어려움 | GJC 기본 프로필·모델 설정 광범위 변경; Anthropic/OpenAI/Google/xAI 로그인·구독·API 키 필요 | 보류: 계정 로그인 및 GJC 전역 설정 변경 요구; 미실행 | 각 제공자에 로그인한 후 설정 프로필별로 모델을 전환한다. |
| CopikProjeckId/audio-drama-release | E (Windows 영상 제작 앱) | `AudioDramaStudio-Free-Setup-0.9.0.exe` (README: Releases 다운로드 후 설치; 셸 설치 명령 없음) | 보통 | Windows 시스템 설치형 프로그램·인터넷 AI API 키; 유료 강의판은 별도 | 보류: Windows 설치 실행 파일로 시스템에 앱 설치해야 함; 미실행 | 무료판 실행 후 사연을 입력하고 음성·삽화·영상을 만든다. |
| brianhong-dev/omo-jev-plugin | E (OmO 에이전트 확장 플러그인) | `omo install npm:omo-jev-plugin` | 보통 | Jev 또는 OpenRouter API 키 필요·사용 통계 텔레메트리 기본 활성화 | 보류: 결정 모델 API 키 및 OmO 확장 설정 필요; 미설치 | OmO에서 결정 보조 플러그인을 연결해 도구·스킬 선택 조언을 받는다. |
| abruption/dots-tailscale | C (Dots 리눅스 네트워크 CLI) | `git clone --branch v0.4.0 --depth 1 https://github.com/abruption/dots-tailscale.git` → `bash tailscale-setup.sh check` → `bash tailscale-setup.sh install` | 어려움 | Linux x86_64·Dots 전용 /workspace·SSH 22포트·Tailscale 로그인 필요 | 보류: 현재 Windows와 호환되지 않는 Dots Linux 환경 및 로그인 필요; 미실행 | Dots 클라우드 컴퓨터에 Tailscale과 SSH를 구성해 원격 접속한다. |
| yazzang-homelab/wb-openai-gateway | B (로컬 MCP·OpenAI 호환 게이트웨이) | `cd wb-agent-gateway` → `npm install` (README: 선택형 테스트 의존성) → `node bin/wb-agent-gateway.js serve --spawn-upstream` | 어려움 | CodeBuddy 계정 인증·로컬 HTTP OAuth 서버·클라이언트 연결 필요 | 보류: CodeBuddy 서버와 최초 접속 인증/승인 필요; 실행·등록 미시도 | CodeBuddy 상류 모델을 로컬 MCP나 OpenAI 호환 API로 연결한다. |
| Yeachan-Heo/ifllm-learn | C (Apple MLX 머신러닝 CLI) | `python3.12 -m venv .venv` → `source .venv/bin/activate` → `python -m pip install -e '.[mlx,test]'` | 어려움 | Apple Silicon·Metal·약 9.3GB 모델 다운로드 필요, 현재 Windows 미지원 | 보류: 학습·추론 경로는 macOS Apple Silicon 전용; Windows에 미설치 | Mac에서 분류 정책 LoRA를 학습하고 결과를 비교한다; 데모 뷰어만 별도 실행 가능. |
| NewTurn2017/hermes-profile-kit | C (Hermes 프로필 CLI) | `pipx install hermes-profile-kit` → `hpk setup` | 보통 | Hermes Agent 요구; 프로필·환경변수/토큰 저장 및 플러그인 변경 가능 | 보류: 대화형 설정에서 각 제공자 인증·토큰 필요; `hpk` 미설치 확인 | Hermes용 용도별 프로필을 만들어 필요할 때 선택한다. |
| yazzang-homelab/gjc-acct | C (GJC 계정 분리 CLI) | `git clone https://github.com/yazzang-homelab/gjc-acct.git` → `cd gjc-acct` → `./install.sh` | 보통 | Claude/Codex 로그인 슬롯과 사용자별 GJC 설정·자격증명 연동 필요 | 보류: 선행 로그인 슬롯 및 사용자 계정 설정 변경 필요; `gjc-acct` 미설치 확인 | Claude/Codex 로그인 슬롯마다 GJC 실행 계정을 바꿔 사용한다. |
| yazzang-homelab/opencode-cli-gateway | C (Node.js 게이트웨이 서버) | `git clone https://github.com/yazzang-homelab/opencode-cli-gateway.git` → `cd opencode-cli-gateway` → `npm ci` → `GATEWAY_HOST=127.0.0.1 GATEWAY_PORT=8940 npm start` | 어려움 | Linux와 상류 CLI 계정 인증·로컬 토큰/상태 디렉터리·네트워크 설정 필요 | 보류: README의 실행 환경 Linux, 현재 Windows 및 상류 인증 미확인; 미설치 | OpenCode 호환 API로 로컬 에이전트 CLI를 연결한다. |










## 설치 성공

- morluto/rea — 기설치 검증 완료: `rea --version` → `6.7.0`; Claude `.claude.json`과 Codex `config.toml` 양쪽 `rea` 등록 확인
- D4Vinci/Scrapling — 기설치 검증 완료: `scrapling --help` 정상, Python 패키지 0.4.5 확인
- blader/humanizer — 설치 검증 완료: `~/.claude/skills/humanizer/SKILL.md` 존재; Claude 플러그인 로드 3.1.0 확인
- abhigyanpatwari/GitNexus — 설치 검증 완료: `npx gitnexus --version` → `1.6.12`; `setup`은 에이전트 설정 변경으로 미실행
- cloudflare/security-audit-skill — 설치 검증 완료: `~/.agents/skills/security-audit/SKILL.md` 생성 후 Claude `~/.claude/skills/security-audit/SKILL.md` 복사 및 SHA256 일치; PromptScript 연동만 실패
- vercel-labs/skills — 기설치 검증 완료: `npx skills --version` → `1.7.4`; 기존 Humanizer·Cloudflare 설치에 사용
- Yeachan-Heo/oh-my-codex — 기설치 검증 완료: `omx --version` → `0.16.4`; 재설치로 덮어쓰기 하지 않음
- citrolabs/ego-lite — 기설치 검증 완료: `~/.claude/skills/ego-browser/SKILL.md`와 로컬 `ego-browser.exe` 존재
- MiniMax-AI/MiniMax-H3 — 설치 검증 완료: `h3-prompt-writing/SKILL.md` 설치 후 `~/.claude/skills/`에 복사·해시 일치; 모델 미다운로드
- Yeachan-Heo/gajae-code — 기설치 검증 완료: `gjc --version` → `gjc/0.18.12` (기존 설치 유지)
- Jakeschincariol/arena-skill — 설치 검증 완료: `~/.claude/skills/arena/SKILL.md` 존재(19,382 bytes); 이전 설치 확인
- HarimxChoi/google-surf-mcp — 설치·등록 검증 완료: `npx -y google-surf-mcp --version` → `1.1.4`; Claude `~/.claude.json`의 `mcpServers.google-surf` 등록/JSON 유효 확인; 실시간 도구 호출은 미검증

## 설치 실패

- 없음

## 설치 보류

- obra/superpowers — 보류: Claude 내부 `/plugin` 설치 필요; `claude plugin list`에 없음; 미실행
- msitarzewski/agency-agents — 보류: Claude 사용자 에이전트 전체 변경; 설치 미실행
- harry0703/MoneyPrinterTurbo — 보류: 핵심 외부 서비스의 API Key 필요; `python -m pip show mpt` 미설치 확인
- stablyai/orca — 보류: Windows 설치 프로그램 실행 및 계정 연동 범위; 미설치
- storytold/photocraft — 보류: Rust 앱 전체 빌드와 데스크톱 환경 영향; 미설치
- AIDC-AI/Pixelle-Video — 보류: 영상 모델 인증 또는 대규모 로컬 모델 연동 필요; 미실행
- virattt/dexter — 보류: README의 필수 2종 API Key 미제공; 미설치
- elizaos/eliza — 보류: 대형 모노레포 설치로 시스템·빌드 환경 변경 범위가 큼
- open-jarvis/OpenJarvis — 보류: Windows 원라이너가 시스템 및 모델 설치를 광범위하게 변경; 미실행
- rehan-remade/universal-modder — 보류: uv tool 전역 설치 및 게임 폴더 접근 위험; 미설치
- storytold/effectcraft — 보류: GUI/네이티브 빌드로 설치 범위 큼; 미설치
- The-Swarm-Corporation/AutoHedge — 보류: README 환경변수 필수; 인증 없이 동작 확인 불가능해 미설치
- 21st-dev/magic-mcp — 보류: README에 API 키 발급 요구; 키 없이 MCP 연결 불가
- rohitg00/awesome-claude-code-toolkit — 보류: 대량 에이전트/훅 전역 변경; 개별 스킬 충돌 검토 필요
- EpicGames/unreal-engine-skills-for-claude-code-plugin — 보류: Unreal Editor 기반 외부 프로그램 및 MCP 서버가 필수; 미실행
- Salomondiei08/oh-my-hermes — 보류: 기존 Hermes 환경·외부 인증과 광범위한 스킬 설치 요구; 미실행
- 3x-haust/oh-my-design — 보류: README 설치 절차가 글로벌 CLI·에이전트 설정을 변경; 미실행
- AlexAI-MCP/hermes-CCC — 보류: 기존 Claude 스킬·도구 충돌 위험; 전체 전역 설치 미실행
- 686f6c61/alfred-dev — 보류: 글로벌 Claude 플러그인/훅/MCP 설정 변경하는 원격 스크립트; 미실행
- project820/gjc-multivendor-setup-guide — 보류: 계정 로그인 및 GJC 전역 설정 변경 요구; 미실행
- CopikProjeckId/audio-drama-release — 보류: Windows 설치 실행 파일로 시스템에 앱 설치해야 함; 미실행
- brianhong-dev/omo-jev-plugin — 보류: 결정 모델 API 키 및 OmO 확장 설정 필요; 미설치
- abruption/dots-tailscale — 보류: 현재 Windows와 호환되지 않는 Dots Linux 환경 및 로그인 필요; 미실행
- yazzang-homelab/wb-openai-gateway — 보류: CodeBuddy 서버와 최초 접속 인증/승인 필요; 실행·등록 미시도
- Yeachan-Heo/ifllm-learn — 보류: 학습·추론 경로는 macOS Apple Silicon 전용; Windows에 미설치
- NewTurn2017/hermes-profile-kit — 보류: 대화형 설정에서 각 제공자 인증·토큰 필요; `hpk` 미설치 확인
- yazzang-homelab/gjc-acct — 보류: 선행 로그인 슬롯 및 사용자 계정 설정 변경 필요; `gjc-acct` 미설치 확인
- yazzang-homelab/opencode-cli-gateway — 보류: README의 실행 환경 Linux, 현재 Windows 및 상류 인증 미확인; 미설치

## 유치원생용 사용법

- **morluto/rea**: `rea`로 앱·코드 역공학을 요청한다.
- **obra/superpowers**: Claude에서 `/plugin install superpowers@claude-plugins-official` 실행 후 스킬을 사용한다.
- **msitarzewski/agency-agents**: 필요한 개발자·디자이너 역할 프롬프트를 Claude에 연결한다.
- **harry0703/MoneyPrinterTurbo**: API Key 준비 후 `mpt webui`로 영상 제작 화면을 연다.
- **stablyai/orca**: Orca 앱을 실행해 여러 코딩 에이전트를 한 화면에서 관리한다.
- **D4Vinci/Scrapling**: `scrapling extract`로 사이트의 필요한 정보를 수집한다.
- **storytold/photocraft**: PSD 파일을 열어 레이어를 편집한다.
- **blader/humanizer**: Claude에게 `/humanizer`로 문장 다듬기를 요청한다.
- **abhigyanpatwari/GitNexus**: 프로젝트 폴더 안에서 `npx gitnexus analyze`로 코드 관계를 색인한다.
- **cloudflare/security-audit-skill**: Claude에게 현재 코드의 보안 감사를 요청한다.
- **vercel-labs/skills**: `npx skills find`로 스킬을 찾고 `npx skills add`로 추가한다.
- **Yeachan-Heo/oh-my-codex**: `omx doctor`로 Codex 도구 연결 상태를 검사한다.
- **AIDC-AI/Pixelle-Video**: 웹 화면에서 텍스트를 넣어 AI 영상을 만든다.
- **virattt/dexter**: 금융 관련 질문을 에이전트에게 입력해 조사한다.
- **elizaos/eliza**: Eliza 실행 화면에서 에이전트와 대화한다.
- **citrolabs/ego-lite**: `/ego-browser`로 로그인한 브라우저에서 자동화 작업을 지시한다.
- **open-jarvis/OpenJarvis**: 설치 후 `jarvis`로 로컬 AI 비서와 대화한다.
- **MiniMax-AI/MiniMax-H3**: Claude에게 H3 동영상 프롬프트를 만들어 달라고 요청한다.
- **rehan-remade/universal-modder**: `um scan`으로 게임 환경을 점검한다.
- **storytold/effectcraft**: 앱에서 레이어 애니메이션을 만들고 영상으로 저장한다.
- **The-Swarm-Corporation/AutoHedge**: API 키를 연결한 뒤 AutoHedge 금융 자동화 에이전트를 실행한다.
- **21st-dev/magic-mcp**: 21st 계정 API 키를 발급받아 MCP를 연결하고 UI 생성 도구를 호출한다.
- **Yeachan-Heo/gajae-code**: 터미널에서 `gjc`를 실행해 에이전트에게 개발 작업을 지시한다.
- **rohitg00/awesome-claude-code-toolkit**: Claude Code에서 마켓플레이스를 추가하고 필요한 기능만 선택한다.
- **EpicGames/unreal-engine-skills-for-claude-code-plugin**: Unreal Editor에서 MCP 서버를 연 뒤 Claude로 블루프린트 등을 조작한다.
- **Jakeschincariol/arena-skill**: Claude Code에서 `/arena`로 여러 에이전트의 답변을 비교한다.
- **Salomondiei08/oh-my-hermes**: Hermes 봇에 작업을 메시지로 보내 여러 코딩 에이전트를 관리한다.
- **HarimxChoi/google-surf-mcp**: Claude 재시작 후 Google Surf MCP로 웹 검색과 자료 관계 분석을 요청한다.
- **3x-haust/oh-my-design**: 설치된 호스트에서 디자인 스킬로 UI 구성·품질 검사를 요청한다.
- **AlexAI-MCP/hermes-CCC**: 원하는 Hermes 기반 Claude 스킬을 선택해 개발·검색 자동화를 맡긴다.
- **686f6c61/alfred-dev**: Claude에서 `/alfred-dev:alfred`를 호출해 개발팀 에이전트를 실행한다.
- **project820/gjc-multivendor-setup-guide**: 각 제공자에 로그인한 후 설정 프로필별로 모델을 전환한다.
- **CopikProjeckId/audio-drama-release**: 무료판 실행 후 사연을 입력하고 음성·삽화·영상을 만든다.
- **brianhong-dev/omo-jev-plugin**: OmO에서 결정 보조 플러그인을 연결해 도구·스킬 선택 조언을 받는다.
- **abruption/dots-tailscale**: Dots 클라우드 컴퓨터에 Tailscale과 SSH를 구성해 원격 접속한다.
- **yazzang-homelab/wb-openai-gateway**: CodeBuddy 상류 모델을 로컬 MCP나 OpenAI 호환 API로 연결한다.
- **Yeachan-Heo/ifllm-learn**: Mac에서 분류 정책 LoRA를 학습하고 결과를 비교한다; 데모 뷰어만 별도 실행 가능.
- **NewTurn2017/hermes-profile-kit**: Hermes용 용도별 프로필을 만들어 필요할 때 선택한다.
- **yazzang-homelab/gjc-acct**: Claude/Codex 로그인 슬롯마다 GJC 실행 계정을 바꿔 사용한다.
- **yazzang-homelab/opencode-cli-gateway**: OpenCode 호환 API로 로컬 에이전트 CLI를 연결한다.

진행: 40/40 판정. 설치 완료 12 / 실패 0 / 보류 28 / 미판정 0
