# GEOINT 발행 가이드 (필독)

> **제1원칙 — 리포트를 만들면 반드시 GitHub에 푸시한다.**
> 분석·리포트·영상카드를 새로 만들었으면, 그 자리에서 즉시 `aifactory-team/geoint-agent` 에 푸시한다.
> 로컬에만 만들고 끝내면 안 된다. "만들었다 = 푸시했다" 가 한 세트다.

대상 리포: **aifactory-team/geoint-agent** (공개, main 브랜치 + Wiki)
토큰: `~/.config/geoint/gh_token` (PAT, user=tykimos). 없으면 푸시 불가.

---

## 일일 루틴 (기본) — 발견→검증 흐름
하루 4회(02/08/14/20) cron 이 이걸 실행한다:
```bash
bash /home/aifactory_ds3/tykimos/geowert/routines/discover_publish.sh
```
**흐름 (핵심 방법론):**
1. **발견** — 한국 주요 수역에서 가장 최신의 *새* Sentinel-2 장면을 찾는다(이미 보고한 장면은 `discover_state.json`으로 건너뜀 → 중복 없음).
2. **인사이트** — 그 최신 1장에서 NDCI(녹조/클로로필) 등 신호를 추출.
3. **시계열 검증** — 그 주장이 의미 있는지, 동일 지역 *과거* 청천 영상들과 비교해 "과거 대비 높음/평년 수준" 판정.
4. **발행** — main + Wiki 푸시. 새 장면이 없으면 발행 스킵.
- 슬롯은 실행 시각(`date +%H`).

## 서울 10년 변화(정적) — 수동/비정기
`publish.sh` 는 고정 데이터셋 기반이라 매일 같은 내용이 나온다 → **일일 발행 금지**. 데이터 갱신 시에만 수동 실행.

## 새 토픽(산불·녹조 등)을 직접 만들었을 때 — 체크리스트
1. 분석·대시보드·영상카드(`videocards/`) 생성.
2. `build_report.place_report(WORK, date, slot, title, md, assets, cards, topic)` 로 `reports/<date>/<slot>/` 에 배치 (+ meta.json).
3. `build_report.build_readme(WORK)` + `build_report.build_wiki(WIKI, WORK)` 로 인덱스·위키 재생성.
4. **푸시 (절대 빠뜨리지 말 것)**:
   ```bash
   cd ~/.cache/geoint-agent-repo  && git add -A && git commit -m "..." && git push origin main
   cd ~/.cache/geoint-agent-wiki && git add -A && git commit -m "..." && git push origin master
   ```
5. GitHub API로 반영 확인(`contents/reports/<date>`).

## 발행 전 점검 (claim·포맷 규칙)
- [ ] **영상카드 ≤ 5개** (한 게시물 최대 5. 초과 시 병합. 예: 개포+용산 → 1개)
- [ ] **AI 결과는 단정 금지** — "약/신호/경향/흐름/~로 보임" 등으로 완화. 단, "추정"을 남발하지 말 것.
- [ ] **표준 면책 배너** 포함 (리포트 본문 + 영상카드 하단).
- [ ] 구조: `reports/<YYYY-MM-DD>/<HH>/{REPORT.md, assets/, videocards/, meta.json}`
- [ ] 푸시 후 main + Wiki 둘 다 반영됐는지 확인.

## 잊지 않기 위한 한 줄
**“리포트 만들었으면 push 했나?”** — 응답 마치기 전에 항상 자문한다.
