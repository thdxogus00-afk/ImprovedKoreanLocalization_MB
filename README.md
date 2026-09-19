# Improved Korean Localization — MourningBound

**다크타이드 한국어 현지화 개선 · 송신 후속판**

Polarmingo / DARKS0UND의 **ImprovedKoreanLocalization**을 이어받아 게임의 영문·한국어 원문과 대조하고, 확인한 수정 사항을 누적하는 비공식 후속 프로젝트입니다.

- **원작:** Polarmingo / DARKS0UND
- **후속 작업:** 송신 (Songshin / MourningBound)
- **검토·구현 지원:** Codex
- **현재 기준:** `260920 TEST3` — 게임 내 확인이 필요한 시험판

원작자의 공식 업데이트를 뜻하지 않습니다. 원본과 이전 수정 기록을 함께 보존합니다.

## 설치

1. 게임을 완전히 종료합니다.
2. 이 저장소의 [`ImprovedKoreanLocalization`](ImprovedKoreanLocalization) 폴더를 게임의 `mods` 폴더에 넣습니다. 기존 설치가 있으면 해당 폴더를 덮어씁니다.
3. Darktide Mod Framework와 WhatTheLocalization이 필요합니다. 로드 목록에서 WhatTheLocalization을 먼저, ImprovedKoreanLocalization을 그 뒤에 둡니다. 이름을 중복 추가하지 않습니다.
4. 한국어로 실행합니다. 기본/커스텀 번역 스타일을 바꾼 뒤에는 게임을 재시작합니다.

저장소 이름의 `_MB`는 게임 설치 폴더명에 붙이지 않습니다. `handoff` 폴더는 게임에 설치할 필요가 없습니다.

## 현재 작업 범위

| 항목 | 수량 |
| --- | ---: |
| 원작 기준 번역 등록 | 8,425개 |
| TEST2에서 적용한 수정 ID | 738개 |
| TEST3에서 의미를 대조한 ID | 497개 |
| TEST3에서 추가 적용한 수정 ID | 92개 |
| 새로 확보한 영문 목록의 의미 검수 대기 | 128,084개 |

TEST3에서는 스키타리 재능 204개, 관련 UI·고행·튜토리얼 74개, 감염 관련 대화와 모로 회상 195개, 오류 후보 UI·재능 24개를 대조했습니다. 밀치기 재능의 뒤바뀐 변수, 능력 조건과 회복 대상, 의료 서보 스컬 등의 이름, 영어로 남은 안내와 자막 오역을 수정했습니다.

새로 확보한 영문이 모두 신규 콘텐츠이거나 미번역 문구라는 뜻은 아닙니다. 자동 검사와 의미 검수는 구분합니다. 5개 기존 대사는 음성 또는 계급 대응 확인을 보류했습니다.

## 검증 상태

- 설치용 파일 4개의 Lua 5.1 문법 검사 통과.
- 실제 WhatTheLocalization과 공개 LocalizationManager 코드를 사용한 모의 실행에서 기본/커스텀, 한국어/영어, 활성화/비활성화 출력 검사 통과.
- 신규 수정 92개를 두 모드로 검사한 184회에서 원문 토큰 보존 및 치환 확인.
- 한·영 공통 141,416개 ID를 두 모드로 점검한 282,832회에서 변수·매크로 대응 불일치 없음.
- TEST2 파일 전체를 바이트 단위로 보존하고 새 수정 등록을 덧붙였습니다.

**실제 게임 화면, 줄바꿈, 음성 타이밍과 능력 동작은 아직 검증하지 않았습니다.** 공개 게임 소스 스냅샷과 현재 실행 파일의 동일성도 인증하지 않습니다.

[상세 검증 결과](handoff/VALIDATION_TEST3.json) · [변경 전후와 수정 이유](handoff/REVIEW_CHANGES_TEST3.md) · [한국어 상세 안내](README_KO.md)

## 소스와 검수 자료

- [`handoff/CHANGES_TEST3.json`](handoff/CHANGES_TEST3.json): 이번 수정 92개의 영문, 이전 번역, 최종 번역, 이유.
- [`handoff/REVIEW_TEST3.jsonl`](handoff/REVIEW_TEST3.jsonl): 이번 의미 검수 497개 기록.
- [`handoff/CONTINUE_HERE.md`](handoff/CONTINUE_HERE.md): 다음 작업의 시작점.
- [`handoff/NEXT_REVIEW_BATCH.jsonl`](handoff/NEXT_REVIEW_BATCH.jsonl): 다음에 검토할 후보 200개.
- [`handoff/inherited_TEST2`](handoff/inherited_TEST2): TEST2의 변경 기록과 원작 기준본.
- [`handoff/previous_TEST2`](handoff/previous_TEST2): TEST2 설치용 모드. 되돌릴 때 사용할 수 있습니다.
- [`handoff/COMPRESSED_DATA.json`](handoff/COMPRESSED_DATA.json): 압축된 원문과 전체 검수 큐의 경로·원본 해시.

큰 JSONL 파일은 gzip으로 보관합니다. 원문을 복원하고 동일한 설치용 Lua를 재생성하려면 저장소 루트에서 실행합니다.

```sh
python handoff/restore_data.py
python handoff/build_patch.py
python handoff/validate_release.py
```

빌드에는 Python, 검증에는 추가로 Node.js와 liblua5.4가 필요합니다. Lua 5.1 파서와 해당 라이선스를 포함했습니다. 설치만 할 때는 이 명령을 실행할 필요가 없습니다.

이전에 전달한 설치 ZIP의 기록은 [`release/260920_TEST3_PACKAGE.json`](release/260920_TEST3_PACKAGE.json)에 있습니다. 이 저장소의 설치용 모드 파일은 그 ZIP과 동일하며, 저장소용 문서와 압축 자료 보관 구조가 추가되었습니다.

## English

An unofficial MourningBound continuation of **Improved Korean Localization** for **Warhammer 40,000: Darktide**. Original work by **Polarmingo and DARKS0UND**, continued by **Songshin**, with review and implementation assistance from **Codex**.

Install the `ImprovedKoreanLocalization` directory without renaming it. The project retains the original source and prior revisions, records translation decisions, and separates automated checks from semantic review. `260920 TEST3` is a test build; in-game validation and substantial further review remain outstanding.
