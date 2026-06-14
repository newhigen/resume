---
title: Claude 워밍업
description: 출근 전 Claude quota 윈도우를 미리 깨워 하루 토큰을 고르게 분산.
tags: [Claude Code, CLI]
period: "2026.05.29"
category: Better Claude Code
icon: "☀"
github: https://github.com/newhigen/claude-warmup
image: "/projects/claude-warmup.png"
dashboard: "/dashboards/claude-warmup.html"
intro:
  summary: "출근 전 Claude quota 윈도우를 미리 깨워, 하루 토큰이 한 시간대에 몰리지 않게 분산하는 CLI."
  use:
    - "워밍업 시각을 예약해둔다"
    - "출근 전 자동으로 quota 윈도우가 시작된다"
    - "윈도우 시각화로 몰림·분산을 확인한다"
---

## 문제 — quota가 근무시간과 어긋난다

Claude의 5시간 quota 윈도우는 첫 메시지부터 시작된다. 출근해서 처음 쓰는 순간 윈도우가 그 시각에 고정되는데, 근무 패턴과 안 맞으면 하루 가용량이 한 시간대에 몰리곤 했다.

## 어떻게 — 출근 전에 미리 깨운다

출근 몇 시간 전 자동으로 윈도우를 한 번 깨워두면, 출근 직후·점심 사이·퇴근 전 세 번에 걸쳐 새 quota가 들어온다. 시작점만 앞당겨도 근무시간에 쓸 수 있는 토큰이 꽤 늘어나는 편이다.

## 기능

- **예약 워밍업** — 출근 전 자동으로 quota 윈도우 시작
- **윈도우 시각화** — 몰림(문제)과 분산(해결)을 한눈에

## 배경

quota는 "언제 처음 쓰느냐"가 하루 가용량을 크게 좌우한다. 다만 근무 패턴이나 요금제가 바뀌면 효과는 달라질 수 있다.

## 성과

- 근무시간 토큰을 세 윈도우로 분산 — 전엔 한 시간대에 몰렸다
- 출근 전 자동 워밍업이라 매일 손대지 않아도 된다
- 다만 근무 패턴·요금제가 바뀌면 효과는 달라진다

## 후일담 — 공식 routine으로 은퇴 (2026.06)

Claude가 `/schedule`(크론 기반 scheduled remote agent)로 예약 실행을 공식 지원하면서 이 도구의 역할은 끝났다. 직접 만든 launchd 스케줄러는 공식 기능에 흡수됐다. 맥의 워밍업 잡은 제거했고, 저장소는 보관용으로 archive 처리했다. 플랫폼의 빈틈을 메우려 만든 도구가 그 빈틈이 공식 기능으로 채워지며 은퇴하는, 자연스러운 수명주기다.
