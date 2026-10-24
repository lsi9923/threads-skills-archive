# install-plan 보충 판정 (159개 미판정 → 157개 고유)

- 생성: 2026-10-24T08:00:52
- 근거: `repos-api-check.json`(GitHub API 160건), `_install_cmds.txt`(150개 저장소 설치명령 추출), `_readme2/`(README 148개 실물)
- **정직 고지**: 아래 유형은 README의 설치 명령 패턴으로 **기계 분류**한 것입니다. 사람이 README 전문을 읽고 내린 판정이 아닙니다. "설치명령 유무"와 "저장소 실존"은 실측입니다.

## 숫자

| 항목 | 값 |
|---|---|
| 입력(미판정) | 159 |
| 중복 제거 후 고유 | **157** |
| GitHub 실존 확인 | 148 |
| 절단링크(말줄임 복원) | 3 |
| 404 (삭제·비공개) | 6 |
| 설치명령 추출됨 | 119 |
| README 실물 확보 | 142 |

### 유형 분포

| 유형 | 개수 |
|---|---|
| A (에이전트 스킬·플러그인) | 31 |
| B (MCP 서버) | 5 |
| C (CLI·라이브러리) | 73 |
| E (데스크톱 앱) | 5 |
| F (자료·템플릿·앱) | 43 |

## 전체 판정표

| # | repo | 유형 | 설치명령(첫 줄) | 명령수 | README | 실존 | ★ | 언어 | 최근푸시 | 언급 |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | NousResearch/hermes-agent | E (데스크톱 앱) | `curl -fsSL https://hermes-agent.nousresearch.com/install.sh \| bash` | 2 | O | O | 256,519 | Python | 2026-10-23 | 3 |
| 2 | anthropics/skills | A (Claude 플러그인) | `/plugin marketplace add anthropics/skills` | 3 | O | O | 183,284 | Python | 2026-10-09 | 1 |
| 3 | github/spec-kit | C (CLI·라이브러리) | `uv tool install specify-cli` | 1 | O | O | 142,597 | Python | 2026-10-23 | 1 |
| 4 | garrytan/gstack | C (소스 빌드) | `git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack &` | 6 | O | O | 137,385 | TypeScript | 2026-10-23 | 1 |
| 5 | openai/codex | C (CLI·라이브러리) | `curl -fsSL https://chatgpt.com/codex/install.sh \| sh` | 6 | O | O | 130,642 | Rust | 2026-10-23 | 1 |
| 6 | shadcn-ui/ui | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 126,358 | TypeScript | 2026-10-23 | 1 |
| 7 | VoltAgent/awesome-design-md | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 123,152 | - | 2026-10-14 | 1 |
| 8 | JuliusBrussee/caveman | A (Claude 플러그인) | `npx @caveman-ai/cli@latest` | 6 | O | O | 114,620 | Go | 2026-10-23 | 1 |
| 9 | vllm-project/vllm | C (CLI·라이브러리) | `pip install vllm` | 1 | O | O | 95,246 | Python | 2026-10-23 | 1 |
| 10 | bytedance/deer-flow | C (CLI·라이브러리) | `git clone https://github.com/bytedance/deer-flow.git` | 6 | O | O | 84,341 | Python | 2026-10-23 | 1 |
| 11 | unslothai/unsloth | C (CLI·라이브러리) | `curl -fsSL https://unsloth.ai/install.sh \| sh` | 6 | O | O | 78,483 | Python | 2026-10-23 | 1 |
| 12 | headroomlabs-ai/headroom | C (CLI·라이브러리) | `uv tool install --python 3.13 "headroom-ai[all]" # CLI in a self-contained env` | 6 | O | O | 77,649 | Python | 2026-10-22 | 1 |
| 13 | juliangarnier/anime | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 73,785 | JavaScript | 2026-08-21 | 1 |
| 14 | cline/cline | C (CLI·라이브러리) | `npm i -g cline` | 2 | O | O | 70,784 | TypeScript | 2026-10-23 | 1 |
| 15 | heygen-com/hyperframes | A (에이전트 스킬) | `npx hyperframes skills update` | 6 | O | O | 70,755 | TypeScript | 2026-10-23 | 2 |
| 16 | code-yeongyu/oh-my-openagent | C (CLI·라이브러리) | `curl -fsSL https://get.omo.dev/install.sh \| bash` | 5 | O | O | 70,291 | TypeScript | 2026-10-23 | 5 |
| 17 | Alishahryar1/free-claude-code | F (자료·템플릿) | `curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/in` | 4 | O | O | 62,890 | Python | 2026-10-23 | 1 |
| 18 | twentyhq/twenty | A (에이전트 스킬) | `npm install -g twenty` | 2 | O | O | 59,604 | TypeScript | 2026-10-23 | 1 |
| 19 | Zie619/n8n-workflows | C (CLI·라이브러리) | `git clone https://github.com/Zie619/n8n-workflows.git` | 5 | O | O | 57,065 | Python | 2026-06-24 | 1 |
| 20 | HKUDS/CLI-Anything | A (Claude 플러그인) | `pip install cli-anything-hub` | 6 | O | O | 56,564 | Python | 2026-09-22 | 1 |
| 21 | zhaoxuya520/reverse-skill | C (소스 빌드) | `git clone https://github.com/zhaoxuya520/reverse-skill.git` | 1 | O | O | 43,143 | PowerShell | 2026-09-22 | 1 |
| 22 | wshobson/agents | A (Claude 플러그인) | `/plugin marketplace add wshobson/agents` | 4 | O | O | 41,611 | Python | 2026-10-19 | 1 |
| 23 | lyogavin/airllm | C (CLI·라이브러리) | `pip install git+https://github.com/huggingface/transformers.git` | 5 | O | O | 40,474 | Jupyter Notebook | 2026-10-23 | 1 |
| 24 | Yeachan-Heo/oh-my-claudecode | A (Claude 플러그인) | `/plugin install (recommended for most Claude Code users).` | 6 | O | O | 40,207 | TypeScript | 2026-10-23 | 1 |
| 25 | JCodesMore/ai-website-cloner-template | C (컨테이너 앱) | `docker compose up app --build # build and run the app` | 2 | O | O | 37,230 | TypeScript | 2026-10-19 | 1 |
| 26 | webadderall/Recordly | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | O | 34,905 | TypeScript | 2026-10-17 | 2 |
| 27 | hesamsheikh/awesome-openclaw-usecases | C (CLI·라이브러리) | `irm attendance, collect notes, and compile a summary — fully automated via AI voice` | 2 | O | O | 31,651 | - | 2026-03-24 | 1 |
| 28 | alirezarezvani/claude-skills | A (Claude 플러그인) | `git clone -c core.symlinks=true` | 6 | O | O | 28,606 | Python | 2026-10-23 | 1 |
| 29 | enescingoz/awesome-n8n-templates | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 26,071 | - | 2026-09-12 | 1 |
| 30 | ahmedkhaleel2004/gitdiagram | C (소스 빌드) | `git clone https://github.com/ahmedkhaleel2004/gitdiagram.git` | 3 | O | O | 18,409 | TypeScript | 2026-10-23 | 1 |
| 31 | microsoft/playwright-cli | C (CLI·라이브러리) | `npm install -g @playwright/cli@latest` | 3 | O | O | 14,556 | TypeScript | 2026-10-19 | 1 |
| 32 | cursor/plugins | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 13,775 | TypeScript | 2026-10-23 | 1 |
| 33 | NangoHQ/nango | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 12,961 | TypeScript | 2026-10-23 | 1 |
| 34 | jub0t/Concat | C (CLI·라이브러리) | `brew install ffmpeg` | 1 | O | O | 11,070 | Rust | 2026-10-23 | 1 |
| 35 | averygan/reclip | C (CLI·라이브러리) | `brew install yt-dlp ffmpeg # or apt install ffmpeg && pip install yt-d` | 3 | O | O | 10,814 | HTML | 2026-07-09 | 1 |
| 36 | NanoNets/Graft | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | O | 10,709 | TypeScript | 2026-10-23 | 1 |
| 37 | YouMind-OpenLab/awesome-gpt-image-2 | F (자료·템플릿) | `bun wears a {argument name="character 1 color theme" default="red and white"} Chines` | 1 | O | O | 10,160 | TypeScript | 2026-10-23 | 1 |
| 38 | ibelick/ui-skills | C (CLI·라이브러리) | `npx ui-skills start` | 4 | O | O | 10,109 | TypeScript | 2026-10-20 | 1 |
| 39 | MervinPraison/PraisonAI | C (CLI·라이브러리) | `curl -fsSL https://praison.ai/install.sh \| bash` | 6 | O | O | 9,287 | Python | 2026-10-23 | 1 |
| 40 | revfactory/harness | A (Claude 플러그인) | `/plugin marketplace add revfactory/harness` | 2 | O | O | 9,243 | - | 2026-09-28 | 1 |
| 41 | Nutlope/logocreator | C (소스 빌드) | `git clone https://github.com/Nutlope/logocreator` | 1 | O | O | 8,881 | TypeScript | 2026-10-23 | 1 |
| 42 | SimoneAvogadro/android-reverse-engineering-skill | A (Claude 플러그인) | `/plugin marketplace add SimoneAvogadro/android-reverse-engineering-skill` | 4 | O | O | 8,280 | Shell | 2026-10-12 | 1 |
| 43 | CopilotKit/openbot | C (CLI·라이브러리) | `bun install` | 6 | O | O | 7,004 | TypeScript | 2026-10-23 | 1 |
| 44 | yournextstore/yournextstore | C (소스 빌드) | `git clone https://github.com/yournextstore/yournextstore.git` | 6 | O | O | 5,531 | TypeScript | 2026-10-22 | 1 |
| 45 | Jakeschincariol/replica-skill | A (Claude 플러그인) | `/plugin marketplace add Jakeschincariol/replica-skill` | 4 | O | O | 5,014 | Python | 2026-10-03 | 2 |
| 46 | zhongerxin/iPhone-use | C (소스 빌드) | `git clone https://github.com/zhongerxin/iPhone-use.git` | 1 | O | O | 4,562 | Python | 2026-10-22 | 1 |
| 47 | Manavarya09/design-extract | C (CLI·라이브러리) | `npx designlang https://stripe.com # extract everything` | 6 | O | O | 4,342 | HTML | 2026-10-23 | 2 |
| 48 | microsoft/apm | A (에이전트 스킬) | `git clone <org/repo> && cd <repo>` | 5 | O | O | 4,116 | Python | 2026-10-23 | 1 |
| 49 | nowork-studio/toprank | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | O | 4,052 | Python | 2026-10-23 | 1 |
| 50 | T-Auto/dsh-ops | C (CLI·라이브러리) | `npx --yes dsh-ops@latest install --profile desktop` | 6 | O | O | 3,997 | JavaScript | 2026-10-21 | 1 |
| 51 | code-yeongyu/lazycodex | C (CLI·라이브러리) | `npx lazycodex-ai install` | 6 | O | O | 3,817 | TypeScript | 2026-10-23 | 5 |
| 52 | jakubkrehel/make-interfaces-feel-better | A (에이전트 스킬) | `npx skills add jakubkrehel/make-interfaces-feel-better` | 1 | O | O | 3,788 | Markdown | 2026-08-29 | 1 |
| 53 | onehumanbeing/esp32-iphone-agent | F (자료·템플릿) | `irm ...)` | 1 | O | O | 3,626 | C | 2026-10-22 | 1 |
| 54 | rlaope/oh-my-hermes | C (CLI·라이브러리) | `curl -fsSL https://raw.githubusercontent.com/rlaope/oh-my-hermes/main/install.sh \| sh` | 6 | O | O | 3,582 | Python | 2026-10-23 | 4 |
| 55 | b-nnett/grok-bot-0.18-reconstructed | C (소스 빌드) | `git clone <your-repository-url>` | 1 | O | O | 3,536 | TypeScript | 2026-08-23 | 1 |
| 56 | deedy5/ddgs | B (MCP 서버) | `pip install -U ddgs # Base install` | 6 | O | O | 3,028 | Python | 2026-08-26 | 1 |
| 57 | restyler/awesome-n8n | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 2,999 | - | 2026-01-20 | 1 |
| 58 | kaitranntt/ccs | C (CLI·라이브러리) | `curl -fsSL https://ccs.kaitran.ca/docker-compose.yaml -o docker-compose.yaml` | 6 | O | O | 2,893 | TypeScript | 2026-10-20 | 1 |
| 59 | nano-muse/nanoMuse | C (컨테이너 앱) | `docker compose up -d app` | 1 | O | O | 2,428 | Swift | 2026-10-23 | 1 |
| 60 | facebookincubator/muse-gadget-sdk | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 2,381 | C | 2026-10-21 | 1 |
| 61 | P4nda0s/reverse-skills | A (에이전트 스킬) | `npx skills add P4nda0s/reverse-skills` | 4 | O | O | 2,310 | - | 2026-05-06 | 1 |
| 62 | Dryxio/reagent | C (CLI·라이브러리) | `pip install --upgrade "auto-re-agent[ghidra-bridge]>=0.4.0"` | 6 | O | O | 2,161 | Python | 2026-09-09 | 1 |
| 63 | shaongitbd/doory | C (컨테이너 앱) | `docker compose up -d --build` | 2 | O | O | 1,795 | TypeScript | 2026-10-23 | 1 |
| 64 | jtydhr88/screenwriting-skills | A (Claude 플러그인) | `/plugin marketplace add jtydhr88/screenwriting-skills` | 3 | O | O | 1,764 | Python | 2026-10-03 | 1 |
| 65 | lucaswalter/n8n-ai-automations | F (자료·템플릿) | `irm directories, identifies individual attorney profiles, evaluates their practice a` | 1 | O | O | 1,670 | - | 2026-03-02 | 1 |
| 66 | agentlas-ai/Agentlas-OS | E (데스크톱 앱) | `curl -fsSL https://raw.githubusercontent.com/agentlas-ai/Agentlas-OS/main/scripts/install-a` | 6 | O | O | 1,588 | Python | 2026-10-20 | 1 |
| 67 | boyang-hu/website-rebuild-skill | C (CLI·라이브러리) | `npx website-rebuild-skill # → ~/.claude/skills/website-rebuild` | 5 | O | O | 1,553 | JavaScript | 2026-10-12 | 1 |
| 68 | pingdotgg/ts-rust | C (CLI·라이브러리) | `bun check` | 4 | O | O | 1,503 | Rust | 2026-10-23 | 1 |
| 69 | Anil-matcha/awesome-muse-connectors | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 1,381 | Python | 2026-10-13 | 1 |
| 70 | first-fluke/oh-my-agent | C (CLI·라이브러리) | `curl -fsSL https://raw.githubusercontent.com/first-fluke/oh-my-agent/main/cli/install.sh \|` | 6 | O | O | 1,353 | TypeScript | 2026-10-22 | 1 |
| 71 | revfactory/harness-100 | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 1,309 | - | 2026-03-22 | 1 |
| 72 | kessler/gemma-gem | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 974 | TypeScript | 2026-05-29 | 1 |
| 73 | leopard627/fire-your-seo-agency | A (Claude 플러그인) | `/plugin marketplace add leopard627/fire-your-seo-agency` | 6 | O | O | 952 | Python | 2026-09-25 | 4 |
| 74 | stripe/link-cli | A (에이전트 스킬) | `npm i -g @stripe/link-cli` | 6 | O | O | 869 | TypeScript | 2026-10-23 | 1 |
| 75 | XHToken/Spark-X2.5 | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | O | 841 | - | 2026-10-20 | 1 |
| 76 | dragon1086/prism-insight | C (CLI·라이브러리) | `git clone https://github.com/dragon1086/prism-insight.git` | 4 | O | O | 784 | Python | 2026-10-23 | 2 |
| 77 | Danitilahun/n8n-workflow-templates | C (CLI·라이브러리) | `pip install -r requirements.txt` | 2 | O | O | 723 | Python | 2025-07-11 | 1 |
| 78 | IsuruMaduranga/harness-engineering-101 | C (CLI·라이브러리) | `cargo install mdbook mdbook-mermaid # or: brew install mdbook (+ mdbook-mermaid binary)` | 1 | O | O | 525 | Python | 2026-10-19 | 1 |
| 79 | oil-oil/draw-ui | A (에이전트 스킬) | `npx skills add oil-oil/draw-ui` | 2 | O | O | 509 | Python | 2026-10-04 | 1 |
| 80 | OnlyTerp/UltraCode-Shim | C (CLI·라이브러리) | `npm i -g @anthropic-ai/claude-code` | 4 | O | O | 439 | Python | 2026-08-22 | 1 |
| 81 | Paidax01/web-to-design-md | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 437 | JavaScript | 2026-04-18 | 1 |
| 82 | dance-of-tal/dot-studio | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | O | 437 | TypeScript | 2026-06-03 | 2 |
| 83 | prekuter/dryforge | A (Claude 플러그인) | `/plugin marketplace add prekuter/dryforge` | 2 | O | O | 426 | Python | 2026-10-16 | 1 |
| 84 | Hybirdss/Hycli | F (자료·템플릿) | `irm does it run` | 1 | O | O | 419 | Rust | 2026-10-22 | 2 |
| 85 | cellebrite-labs/ghidra-rpc | C (CLI·라이브러리) | `uv tool install /path/to/ghidra-rpc` | 1 | O | O | 388 | Python | 2026-09-17 | 1 |
| 86 | onewave-ai/claude-skills | C (소스 빌드) | `git clone https://github.com/OneWave-AI/claude-skills.git ~/.claude/skills` | 3 | O | O | 369 | Python | 2026-10-20 | 1 |
| 87 | ttalkkak-lab/opencode-contexty | C (CLI·라이브러리) | `npx @ttalkkak-lab/opencode-contexty init` | 2 | O | O | 222 | TypeScript | 2026-04-25 | 1 |
| 88 | julianromli/ai-skills | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 202 | JavaScript | 2026-10-23 | 1 |
| 89 | ericshang98/perfect-web-clone-skill | C (CLI·라이브러리) | `pip install "git+https://github.com/ericshang98/Perfect-Web-Clone.git"` | 1 | O | O | 189 | - | 2026-08-22 | 1 |
| 90 | vgrichina/re-skill | C (CLI·라이브러리) | `git clone https://github.com/USER/re-skill.git` | 2 | O | O | 175 | Shell | 2026-03-05 | 1 |
| 91 | revfactory/skills | C (소스 빌드) | `git clone https://github.com/revfactory/skills.git` | 1 | O | O | 161 | Python | 2026-10-12 | 1 |
| 92 | unclejobs-ai/motion-video-skill | A (에이전트 스킬) | `npx skills add unclejobs-ai/motion-video-skill --skill motion-video-production` | 3 | O | O | 129 | Python | 2026-10-18 | 1 |
| 93 | incogbyte/android-reverse-engineering-claude-skill | C (CLI·라이브러리) | `pip install frida-tools==<server-version>` | 6 | O | O | 128 | Shell | 2026-06-20 | 1 |
| 94 | fivetaku/insane-review | A (Claude 플러그인) | `/plugin marketplace add https://github.com/fivetaku/gptaku_plugins.git` | 4 | O | O | 125 | Python | 2026-10-14 | 1 |
| 95 | haikow/claude-reverse-skills | C (CLI·라이브러리) | `git clone https://github.com/haikow/claude-reverse-skills && cd claude-reverse-skills` | 6 | O | O | 122 | PowerShell | 2026-06-30 | 1 |
| 96 | Q00/rlm-forge | C (CLI·라이브러리) | `curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install` | 4 | O | O | 121 | Python | 2026-05-10 | 1 |
| 97 | revfactory/claude-code-harness | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 121 | HTML | 2026-03-06 | 1 |
| 98 | tihanyin/REx-skill | E (데스크톱 앱) | `curl -fsSL https://claude.ai/install.sh \| bash` | 4 | O | O | 114 | Python | 2026-09-23 | 1 |
| 99 | incogbyte/iOS-reverse-engineering-claude-skill | C (CLI·라이브러리) | `brew install blacktop/tap/ipsw` | 2 | O | O | 112 | Shell | 2026-07-01 | 1 |
| 100 | duclm1x1/Muse-Chat-MCP | B (MCP 서버) | `git clone https://github.com/duclm1x1/Muse-Chat-MCP.git` | 1 | O | O | 61 | JavaScript | 2026-09-30 | 1 |
| 101 | braxtonROSE4/clone-any-website | E (데스크톱 앱) | `curl -fsSL https://raw.githubusercontent.com/braxtonROSE4/clone-any-website/main/install.sh` | 2 | O | O | 57 | JavaScript | 2026-08-03 | 1 |
| 102 | nikships/muse-cli | C (CLI·라이브러리) | `uv tool install muse-cli # or: pipx install muse-cli / pip install muse-cli` | 5 | O | O | 54 | Python | 2026-10-22 | 1 |
| 103 | diggerhq/openmuse | C (CLI·라이브러리) | `git clone https://github.com/diggerhq/openmuse.git` | 2 | O | O | 49 | TypeScript | 2026-09-11 | 1 |
| 104 | raphaelsalaja/skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 42 | - | 2026-03-17 | 1 |
| 105 | dance-of-tal/dance-of-tal | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | O | 39 | TypeScript | 2026-05-07 | 1 |
| 106 | LeeYudok/agents-scaffold | C (소스 빌드) | `curl -fsSL https://raw.githubusercontent.com/leeyudok/agents-scaffold/main/bin/agents-scaff` | 3 | O | O | 36 | Shell | 2026-10-19 | 1 |
| 107 | JJenglert1/esp32-muse-agent | C (CLI·라이브러리) | `brew install cmake ninja dfu-util python3 git` | 4 | O | O | 32 | Shell | 2026-10-04 | 1 |
| 108 | minpeter/global-egress | C (컨테이너 앱) | `docker compose up -d --build` | 2 | O | O | 32 | Go | 2026-10-15 | 1 |
| 109 | aicodedecode/awesome-muse-skills | A (에이전트 스킬) | `irm current terms in the app):` | 2 | O | O | 31 | Python | 2026-10-10 | 1 |
| 110 | johunsang/tauri-dev-screen-cli | C (CLI·라이브러리) | `npm install -g github:johunsang/tauri-dev-screen-cli` | 2 | O | O | 30 | JavaScript | 2026-05-16 | 1 |
| 111 | w-partners/Wbrowser | C (CLI·라이브러리) | `curl -fsSL https://raw.githubusercontent.com/w-partners/Wbrowser/main/setup.sh \| bash` | 4 | O | O | 30 | JavaScript | 2026-10-12 | 1 |
| 112 | INONONO66/harness-manager | C (CLI·라이브러리) | `curl -fsSL https://raw.githubusercontent.com/INONONO66/harness-manager/main/scripts/install` | 4 | O | O | 28 | Rust | 2026-06-25 | 1 |
| 113 | johunsang/smartku | C (CLI·라이브러리) | `brew install node` | 3 | O | O | 28 | Rust | 2026-08-01 | 1 |
| 114 | kleprevost/muse-mcp | B (MCP 서버) | `git clone <this-repository> muse-mcp` | 4 | O | O | 24 | Python | 2026-09-17 | 1 |
| 115 | tmdgusya/omp-alibaba-maas | E (데스크톱 앱) | `curl -fsSL https://raw.githubusercontent.com/tmdgusya/omp-alibaba-maas/master/bin/alibaba-m` | 3 | O | O | 24 | Python | 2026-07-21 | 1 |
| 116 | Gyu-bot/codex-image-generation-skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 20 | Python | 2026-05-13 | 1 |
| 117 | santowilem/skills | A (에이전트 스킬) | `npx skills add santowilem/skills --skill <skill-name>` | 2 | O | O | 18 | Python | 2026-05-11 | 1 |
| 118 | dalsoop/diy-device-os-bootstrap | C (소스 빌드) | `git clone https://github.com/dalsoop/diy-device-os-bootstrap.git` | 3 | O | O | 16 | Shell | 2026-10-22 | 1 |
| 119 | RandyNorthrup/muse-spark-code | C (CLI·라이브러리) | `irm it; unattended v2 delivery is disabled,` | 6 | O | O | 14 | TypeScript | 2026-10-22 | 1 |
| 120 | Birkenpapier/ai-app-cloner | C (CLI·라이브러리) | `git clone https://github.com/Birkenpapier/ai-app-cloner` | 2 | O | O | 13 | JavaScript | 2026-07-16 | 1 |
| 121 | Mineru98/codex-cron-skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 13 | JavaScript | 2026-07-01 | 1 |
| 122 | sevzq/screenshot-to-html | A (에이전트 스킬) | `npx skills add sevzq/screenshot-to-html` | 6 | O | O | 12 | HTML | 2026-06-14 | 1 |
| 123 | EncidXVII/claude-reverse-engineering-skill | A (Claude 플러그인) | `npx skills add` | 6 | O | O | 11 | Python | 2026-10-19 | 1 |
| 124 | Core-Mate/Pixel-Perfect-Web-Replica | C (CLI·라이브러리) | `curl -fsSL https://raw.githubusercontent.com/Core-Mate/Pixel-Perfect-Web-Replica/main/scrip` | 2 | O | O | 10 | Python | 2026-05-09 | 1 |
| 125 | ssamssae/codex-telegram-bridge | C (CLI·라이브러리) | `brew install tmux` | 6 | O | O | 9 | Python | 2026-10-18 | 1 |
| 126 | groundroot/muse-orchestration | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 7 | - | 2026-10-15 | 1 |
| 127 | sodam-ai/SoDam-Design-Kit | A (Claude 플러그인) | `npx create-next-app@latest` | 6 | O | O | 7 | JavaScript | 2026-10-21 | 1 |
| 128 | fitoe/DesignToCode | A (에이전트 스킬) | `npx skills add fitoe/DesignToCode` | 1 | O | O | 6 | JavaScript | 2026-05-25 | 1 |
| 129 | shinsooshinsoo/Ddara_Jaengi | C (CLI·라이브러리) | `pip install -r requirements.txt` | 1 | O | O | 5 | Python | 2026-05-22 | 1 |
| 130 | ozaysahin/screenshot-to-qml | A (Claude 플러그인) | `npx skills` | 6 | O | O | 4 | HTML | 2026-10-20 | 1 |
| 131 | ssamssae/claude-telegram-bridge | C (CLI·라이브러리) | `irm tap, auto-send never fires \| off \|` | 6 | O | O | 4 | Python | 2026-10-18 | 1 |
| 132 | KeiaiLab/webEmbedding | A (Claude 플러그인) | `npm install -g web-embedding` | 4 | O | O | 3 | Python | 2026-10-14 | 1 |
| 133 | ssamssae/grok-telegram-bridge | C (소스 빌드) | `git clone https://github.com/ssamssae/grok-telegram-bridge.git` | 1 | O | O | 3 | Python | 2026-10-15 | 1 |
| 134 | GeReV/ghidra-iterative-re | C (소스 빌드) | `git clone https://github.com/GeReV/ghidra-iterative-re.git` | 1 | O | O | 2 | Python | 2026-10-23 | 1 |
| 135 | Vagabond-K/SearXngSearch | B (MCP 서버) | `docker run -d --name searxng -p 8080:8080 -v ./searxng:/etc/searxng sea` | 5 | O | O | 2 | C# | 2026-09-29 | 1 |
| 136 | bluman1/muse-connectors | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 2 | Python | 2026-09-16 | 1 |
| 137 | lycoco067/claude-seo-skill | C (소스 빌드) | `git clone https://github.com/YOUR_USERNAME/claude-seo-skill.git` | 1 | O | O | 2 | - | 2026-03-01 | 1 |
| 138 | thenavidm/remaster | A (Claude 플러그인) | `npx -y @thenavidm/remaster install` | 6 | O | O | 2 | JavaScript | 2026-10-04 | 1 |
| 139 | vishnu-madhavan-git/9designer-skills | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 2 | Python | 2026-05-11 | 1 |
| 140 | Amanuel2x/clone-skill | B (MCP 서버) | `npx -y @playwright/mcp@latest` | 4 | O | O | 1 | - | 2026-06-15 | 1 |
| 141 | glebrati-cloud/screenshot-to-code | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 1 | - | 2026-03-23 | 1 |
| 142 | inliver233/reverse-skills | C (CLI·라이브러리) | `git clone https://github.com/inliver233/reverse-skills.git ~/.claude/skills/reverse-skills` | 3 | O | O | 1 | Python | 2026-06-28 | 1 |
| 143 | niuniu122/pixel-perfect-website-clone-skill | C (소스 빌드) | `git clone https://github.com/<owner>/pixel-perfect-website-clone-skill.git "$env:USERPROFILE\.codex\` | 2 | O | O | 1 | Python | 2026-06-27 | 1 |
| 144 | th3vib3coder/RevEng | C (CLI·라이브러리) | `git clone https://github.com/th3vib3coder/RevEng.git` | 3 | O | O | 1 | Python | 2026-05-23 | 1 |
| 145 | xintongw431-arch/webgl-runtime-cloner-skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | 1 | TypeScript | 2026-07-31 | 1 |
| 146 | MengTo/Skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **절단링크** | - | - | 실제 MengTo/Skills | 0 |
| 147 | Q00/r | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **절단링크** | - | - | 실제 Q00/rlm-forge | 0 |
| 148 | gugu9999gu/PC-CONTROL-MCP | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **404** | - | - | - | 0 |
| 149 | johunsang/octo-terminal-releases | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **404** | - | - | - | 0 |
| 150 | kjhbond/claude-gpt-usage-tray | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | O | O | - | Python | 2026-09-30 | 1 |
| 151 | kyungpyokim/model-effort-router | C (CLI·라이브러리) | `git clone https://github.com/kyungpyokim/model-effort-router.git` | 3 | O | O | - | Python | 2026-10-19 | 1 |
| 152 | lexnlin/taste-skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **절단링크** | - | - | 실제 Leonxlnx/taste-skill | 0 |
| 153 | minosdevs/copycat-skill | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **404** | - | - | - | 0 |
| 154 | nontext75/vibe-coding-design-polish | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **404** | - | - | - | 0 |
| 155 | rakanki911/DLSS5-Swapper | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **404** | - | - | - | 0 |
| 156 | xxmisaoxx/t-rex | A (에이전트 스킬) | `npx skills add xxmisaoxx/t-rex --skill reverse-engineering-investigator` | 2 | O | O | - | Python | 2026-10-11 | 1 |
| 157 | yelixir-dev/hermes-memory-stack | F (라이브러리·앱·자료집) | `README에 설치 명령 없음` | 0 | - | **404** | - | - | - | 0 |

## 절단 링크 복원 (404가 아니었다)

Threads가 링크 라벨을 `github.com/Q00/o…` 처럼 말줄임으로 표시하는데, 수집기가 그 **표시 문자열을 실제 주소로 저장**했다. 같은 글의 전체 URL을 대조해 원래 저장소를 찾았다. 3건 모두 본표에 이미 있는 저장소다.

- `MengTo/Skill` → **`MengTo/Skills`** (본표 #112, 6,972★). 같은 글(@keke_appa `DbTH1i3kmgi`)의 links 배열에 전체 URL이 있다.
- `lexnlin/taste-skill` → **`Leonxlnx/taste-skill`** (본표 #18, 101,626★). 대소문자만 다르다. 같은 글(@unclejobs.ai `DV7oKhnidGz`).
- `Q00/r` → **`Q00/rlm-forge`** (본표 #207, 121★). 같은 글(@jisang0914 `DYH9z1rGkh9`).

같은 원인으로 1차 표의 `Q00/o`도 **`Q00/ouroboros`** (본표 #115, 6,265★)의 절단 링크였다. 언급 글 3건 모두 화면 라벨이 `github.com/Q00/o…`다.

## 404 저장소 (실존 확인 실패 — 6건)

- `gugu9999gu/PC-CONTROL-MCP` — GitHub API 404 + 이름검색에 같은 소유자 저장소 없음.
- `johunsang/octo-terminal-releases` — GitHub API 404 + 이름검색에 같은 소유자 저장소 없음.
- `minosdevs/copycat-skill` — GitHub API 404. **소유자 계정 `minosdevs` 자체가 404.**
- `nontext75/vibe-coding-design-polish` — GitHub API 404 + 이름검색에 같은 소유자 저장소 없음.
- `rakanki911/DLSS5-Swapper` — GitHub API 404. **소유자 계정 `rakanki911` 자체가 404.**
- `yelixir-dev/hermes-memory-stack` — GitHub API 404 + 이름검색에 같은 소유자 저장소 없음.
