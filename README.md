# elarune-plugins

웹소설 · 웹툰 작가 도구 **Elarune** 의 플러그인 저장소입니다. 펜시브(pensiv) 공식 플러그인 저장소
[pensiv-so/pensiv-plugins](https://github.com/pensiv-so/pensiv-plugins)(MIT)를 포크했습니다.

> The plugin repository for Elarune, forked from pensiv-so/pensiv-plugins (MIT). Plugin sources and the SDK
> contract are kept as upstream so the same plugins keep running in both pensiv and Elarune.

## 이 포크의 원칙

- **플러그인 소스와 SDK 는 원 저장소 그대로 둡니다.** `plugins/*` 와 `packages/plugin-sdk`(타입 계약
  `@pensiv/plugin-sdk`)를 고치지 않습니다. 같은 플러그인이 펜시브와 Elarune 양쪽에서 돌아야 하기 때문입니다.
  플러그인 id 이름 공간(`so.pensiv.*`), 꾸러미 이름(`@pensiv/*`), 매니페스트 스키마도 그대로입니다.
- **Elarune 은 앱 안에 이 SDK 계약을 받는 실행 자리를 만듭니다.** HostApi(편집기 · 저장 · 화면 · 칸 · 작품 접근)를
  Elarune 쪽에서 구현해, 이 저장소의 플러그인을 고치지 않고 그대로 싣습니다. 원 저장소 설명대로 SDK 는 펜시브 앱에서
  만들어 내는 거울이라 손으로 고치지 않습니다(원문은 [README.pensiv.md](README.pensiv.md) 'SDK source of truth').
- **원 저장소의 새 판은 merge 로 따라갑니다.** `upstream` 원격을 두고 받아 합칩니다.

  ```bash
  git remote add upstream https://github.com/pensiv-so/pensiv-plugins.git
  git fetch upstream
  git merge upstream/main
  ```

- **Elarune 에서만 필요한 플러그인은 새 폴더로 더합니다.** 원 플러그인을 고치지 않고, id 는 `so.pensiv.*` 가 아닌
  이름 공간을 씁니다(원 저장소가 `so.pensiv.*` 를 펜시브 자체 플러그인 몫으로 남겨 둠).

## 출처 · 라이선스

| 무엇 | 값 |
|---|---|
| 원 저장소 | https://github.com/pensiv-so/pensiv-plugins |
| 포크 시점 | `main` `92cf23f` (2026-10-15, "Merge pull request #36 from pensiv-so/develop") |
| 라이선스 | MIT — [LICENSE](LICENSE) 원문 그대로(Copyright (c) 2026 pensiv) |

Elarune 이 이 저장소의 코드를 들일 때는 들인 커밋 · MIT 원문 · 바꾼 곳을 함께 남기고, Elarune 웹 빌드의
오픈 소스 라이선스 목록(licenses.txt)에도 싣습니다(Elarune 저장소 결정기록 ADR-0002 덧붙임 2026-10-19).

## 구성

원 저장소와 같습니다.

```
packages/
  plugin-sdk/            @pensiv/plugin-sdk — 플러그인이 쓰는 타입 계약(Plugin, HostApi …)
  plugin-ui/             @pensiv/plugin-ui — 플러그인 화면 부품
  build-config/          플러그인 공용 vite 빌드 설정(react · SDK 는 밖으로 뺌)
  create-pensiv-plugin/  새 플러그인 뼈대 만들기(sample-plugin 을 복제)
plugins/                 플러그인 22개(아래 표)
AGENTS.md  llms.txt      플러그인 작성 계약 안내(원문)
```

## 플러그인

'펜시브 기본 제공' 은 펜시브 앱이 처음부터 넣어 두는 코어 플러그인입니다(펜시브 화면 묶음 2026-10-16 판에서 확인).
나머지는 펜시브 마켓에서 받아 설치합니다.

| 폴더 | id | 이름 | 판 | 펜시브 기본 제공 |
|---|---|---|---|---|
| `browser` | `so.pensiv.browser` | 브라우저 | 1.0.0 | 예 |
| `calculator` | `so.pensiv.calculator` | 계산기 | 1.0.1 | |
| `canvas-checklist` | `so.pensiv.canvas-checklist` | 캔버스 체크리스트 | 1.0.1 | |
| `daily-goal` | `so.pensiv.daily-goal` | 일일 목표 | 1.3.3 | 예 |
| `dangerous-writing` | `so.pensiv.dangerous-writing` | 위험한 글쓰기 | 1.1.0 | |
| `date-calculator` | `so.pensiv.date-calculator` | 날짜 계산기 | 1.0.1 | |
| `document-goal` | `so.pensiv.document-goal` | 문서 목표 | 1.0.0 | 예 |
| `foreshadowing` | `so.pensiv.foreshadowing` | 복선 | 1.2.0 | |
| `graph-tags` | `so.pensiv.graph-tags` | Graph Tags | 1.0.0 | |
| `panes-demo` | `so.pensiv.panes-demo` | Panes Demo | 1.0.0 | |
| `paragraph-analysis` | `so.pensiv.paragraph-analysis` | 단락 분석 | 1.0.1 | |
| `pomodoro-basic` | `so.pensiv.pomodoro-basic` | 뽀모도로 베이직 | 1.0.1 | |
| `project-explorer` | `so.pensiv.project-explorer` | Project Explorer | 1.0.0 | |
| `sample-plugin` | `so.pensiv.sample` | Sample Plugin | 1.0.0 | |
| `sentence-highlighter` | `so.pensiv.sentence-highlighter` | Sentence Highlighter | 1.0.0 | |
| `status-window` | `so.pensiv.status-window` | 상태창 | 1.2.0 | |
| `surface-actions` | `so.pensiv.surface-actions` | Surface Actions | 1.0.0 | |
| `timer` | `so.pensiv.timer` | 타이머 | 1.0.0 | 예 |
| `toolbox` | `so.pensiv.toolbox` | Toolbox | 1.0.0 | |
| `unit-converter` | `so.pensiv.unit-converter` | 단위 변환 | 1.0.1 | |
| `word-count-widget` | `so.pensiv.word-count-widget` | 단어 수 위젯 | 1.0.0 | |
| `writing-time` | `so.pensiv.writing-time` | 집필 시간 | 1.1.0 | |

## 플러그인 만들기

원 저장소 안내를 그대로 따릅니다. 펜시브와 Elarune 둘 다에서 돌게 하려면 SDK 계약(`@pensiv/plugin-sdk`)과
원 저장소가 허락한 호스트 모듈만 씁니다.

- 시작점: [`plugins/sample-plugin`](plugins/sample-plugin)
- 계약 전체: [AGENTS.md](AGENTS.md) · [llms.txt](llms.txt)
- 만들기 · 빌드 · 펜시브 마켓 올리기: [README.pensiv.md](README.pensiv.md)(원 저장소 README 원문)

Elarune 쪽 플러그인 마켓은 아직 없습니다. Elarune 이 이 저장소의 플러그인을 어떻게 싣고 관리하는지는
Elarune 저장소의 작업목록(S22-12 플러그인)에 적습니다.
