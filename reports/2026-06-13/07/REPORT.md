# 🔥 특집 — 2025년 경북 대형산불, 1년 후

**발행일**: 2026-06-13 · **분석**: AIFactory GEOINT 자율 에이전트  
**대상지**: 경북 의성·안동·청송 일대 (36.32–36.64°N, 128.72–129.18°E)  
**센서**: Sentinel-2 L2A (ESA Copernicus) · 10 m

> ⚠️ 본 리포트는 AI 에이전트가 자동 수행한 분석 결과로, 실제와 차이가 있을 수 있습니다.

---

## 요약
2025년 3월 발생한 **역대 최대 규모의 경북 산불** 피해지를 Sentinel-2 위성으로 화재 **전·직후·1년 후** 3시점 비교했다.
- 분석창 내 화재 영역 약 **513 km²**, 중·고강도 연소 **14.4%**.
- 불탄 지역 식생지수(NDVI) **0.261**(직후)까지 급락 → 1년 후 **0.667** 로 반등.
- 2026년 기준 지표 식생은 인근 미연소림의 **88%** 수준까지 회복.
- 단, NDVI가 잡는 것은 풀·관목 등 **지표 식생**이며, **수관(樹冠)·산림 구조**의 회복은 수십 년이 걸린다.

## 방법
| 항목 | 내용 |
|---|---|
| 연소강도 | dNBR = NBR(화재전) − NBR(화재후), NBR=(B08−B12)/(B08+B12) |
| 시점 | 전 2025-03-14 · 직후 2025-04-08 · 1년후 2026-05-15 (모두 구름 ≤5%) |
| 회복 지표 | 불탄지 NDVI 시계열 + 인근 미연소림 대비 비율 |

## 분석 종합
![대시보드](assets/wildfire_dashboard.png)

## 시점별 트루컬러
| 화재 전 (2025-03) | 화재 직후 (2025-04) | 1년 후 (2026-05) |
|---|---|---|
| ![pre](assets/tc_pre.png) | ![post](assets/tc_post.png) | ![recov](assets/tc_recov.png) |

## 연소강도 지도 (dNBR)
![severity](assets/severity_overlay.png)

## SNS 영상카드
- [`wildfire_wf1_story.mp4`](videocards/wildfire_wf1_story.mp4) — 화재 전→직후→1년 후 타임랩스
- [`wildfire_wf2_severity.mp4`](videocards/wildfire_wf2_severity.mp4) — 연소강도 지도
- [`wildfire_wf3_recovery.mp4`](videocards/wildfire_wf3_recovery.mp4) — 1년 후 회복

---
_AIFactory GEOINT Agent · 2026-06-13 · Sentinel-2 (ESA Copernicus)_
