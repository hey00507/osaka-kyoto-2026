---
# gstack: design-md-format=spec
name: 오사카·교토 2026
description: 일본 지하철 안내판처럼 흰 바탕에 굵은 글자와 노선 색으로 읽히는 여행 일정표.
colors:
  surface: "#FFFFFF"
  surface-muted: "#F4F5F7"
  text: "#14171A"
  text-muted: "#5B6470"
  line: "#E1E4E8"
  primary: "#1B3A8C"
  on-primary: "#FFFFFF"
  day-1: "#D92643"
  day-2: "#C4500F"
  day-3: "#0E7C6B"
  day-4: "#1F6FD6"
  day-5: "#9A6B00"
  on-day: "#FFFFFF"
  success: "#1A7F4B"
  error: "#C2261F"
  warning: "#8A6A00"
  dark-surface: "#101214"
  dark-surface-muted: "#1A1D21"
  dark-text: "#F2F4F6"
  dark-text-muted: "#A3ACB8"
  dark-line: "#2C3138"
  dark-primary: "#9DB6FF"
typography:
  display:
    fontFamily: Do Hyeon
    fontWeight: 400
    fontSize: clamp(30px, 8.6vw, 44px)
    lineHeight: 1.12
  heading:
    fontFamily: Do Hyeon
    fontWeight: 400
    fontSize: 26px
    lineHeight: 1.15
  body:
    fontFamily: Pretendard Variable
    fontSize: 1rem
    lineHeight: 1.55
  label:
    fontFamily: Pretendard Variable
    fontWeight: 700
    fontSize: 0.8125rem
  mono:
    fontFamily: Pretendard Variable
    fontFeature: tnum
rounded:
  sm: 3px
  md: 8px
  full: 9999px
spacing:
  xs: 4px
  sm: 8px
  md: 14px
  lg: 18px
  xl: 22px
  2xl: 56px
components:
  band:
    backgroundColor: "{colors.day-1}"
    textColor: "{colors.on-day}"
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.md}"
  button-line:
    textColor: "{colors.primary}"
    rounded: "{rounded.md}"
  day-button:
    backgroundColor: "{colors.surface-muted}"
    rounded: "{rounded.md}"
  nav-link:
    textColor: "{colors.text-muted}"
---

# 오사카·교토 2026

## Overview

**Creative North Star:** 일본 지하철 안내판. 세 사람이 5일 내내 보게 될 노선도와 역 표지에서 따온 디자인으로, 한눈에 읽히는 것이 본업이고 장소감과 장난기가 따라온다.
**Product context:** 친구 세 명이 4박 5일 여행 중에 폰과 PC로 여는 일정표. 날짜별 타임라인, 예약 링크, 체크리스트, 날씨와 옷차림. 길에서 한 손으로 훑어보는 용도. 정적 페이지 한 장, GitHub Pages.
**Memorable thing:** 열자마자 다음 할 일이 보이고, 일본에 왔다는 느낌과 우리끼리 만든 재미가 묻어난다.
**Mode per surface:** 일정 = Operate, 예약·체크리스트·항공·숙소 = Operate.
**Reference sites:** https://tripsy.app, https://wanderlog.com, https://screensdesign.com/articles/travel-itinerary-app-design-examples/
**Key characteristics:**
- 날짜마다 상단 띠와 타임라인 선의 색이 바뀐다.
- 맨 위에는 다음 일정 하나가 가장 크게 나온다.
- 타임라인은 카드가 아니라 세로선과 역 점이다.
- 제목은 간판 글씨, 본문은 조용한 고딕.

## Colors

**Strategy:** Committed. 그날의 노선 색 하나가 띠, 타임라인 선, 강조 글자를 맡고 나머지는 흰색과 먹색이다.
**Light or dark:** 낮에 길에서 보는 용도라 밝은 화면이 기본이다. 기기가 다크 모드면 따라가고, 사용자가 버튼으로 바꾸면 그 기기에 기억한다.

`day-1`부터 `day-5`는 장식이 아니라 "지금 며칠째인지"를 알리는 정보다. 누를 수 있는 것은 모두 `primary`(라피트 열차 남색)로 표시하고 노선 색을 버튼에 쓰지 않는다. 상태는 `success`(확정, 무료), `error`(해야 할 예약), `warning`(당일 확인) 세 가지 글자 색과 네모 표시로만 구분한다. 다크 모드는 바탕과 글자만 바꾸고 노선 색은 그대로 둔다. 노선 색 위의 글자는 항상 흰색이며 모두 대비 4.5:1 이상으로 골랐다.

## Typography

제목은 Do Hyeon(Google Fonts). 오사카 골목 간판 같은 굵고 단순한 한글 글꼴이라 장소감과 재미를 맡는다. 굵기가 하나뿐이므로 강조는 크기와 색으로만 한다. 본문과 숫자는 Pretendard Variable(jsDelivr의 dynamic subset). 시간과 기온은 `tabular-nums`로 자릿수를 맞춘다. 본문 글꼴로 시스템 기본 글꼴을 주 글꼴로 쓰지 않는다. 대체 글꼴로만 둔다.

크기 단계: 다음 일정 제목 30~44px, 날짜·탭 제목 26px, 타임라인 항목 17px, 본문 14~16px, 보조 11.5~13px. 제목과 본문 사이에는 한 단계 이상 차이를 둔다.

## Layout

폰이 기준이다. 한 열로 위에서부터 띠, 지금/다음, 날짜 5칸, 그날 타임라인 순서. 한 번에 하루만 보여 준다. 탭은 하단 고정, 버튼 높이 44px 이상.

900px 이상에서는 두 열. 왼쪽 360px에 지금/다음과 세로 날짜 목록이 고정되고 오른쪽에 타임라인이 온다. 최대 폭 1080px. 목록 탭(예약, 체크리스트, 항공·숙소)은 720px 폭의 한 열.

## Elevation & Depth

그림자를 쓰지 않는다. 구분은 1px 선과 `surface-muted` 바탕색으로만 한다. 유일한 예외는 다음 일정 역 점 둘레의 옅은 테두리로, 현재 위치를 알리는 표시다.

## Shapes

모서리는 8px 하나로 통일한다(버튼, 날짜 칸). 타임라인 선 끝은 3px. 원은 역 점에만 쓴다. 알약 모양 버튼과 큰 둥근 카드는 쓰지 않는다.

## Components

- **띠(band):** 선택한 날의 노선 색. 날짜를 바꾸면 0.3초 동안 색이 넘어간다.
- **지금/다음:** 상태 라벨(노선 색), 제목, 날짜와 시간, 설명, 버튼 최대 2개. 여행 전, 여행 중, 내일 첫 일정, 마지막 날 이후 네 상태가 있다.
- **날짜 칸:** 날짜, 요일과 일차, 날씨 한 줄. 선택되면 노선 색으로 채워진다. 오늘은 점으로 표시한다.
- **타임라인 항목:** 시간, 제목, 설명, 상태 표시, 밑줄 링크. 다음 일정은 점이 채워지고 지난 일정은 흐려진다.
- **버튼:** 채운 버튼은 화면에서 가장 중요한 행동 하나에만. 나머지는 선 버튼이나 밑줄 링크.
- **포커스:** 모든 누를 수 있는 요소에 3px 남색 테두리.

## Do's and Don'ts

- Do: 새 일정 항목은 `DAYS` 배열에만 추가한다. 화면은 배열에서 그려진다.
- Do: 색은 정보일 때만 쓴다(며칠째, 상태, 누를 수 있음).
- Do: 시간은 `HH:MM` 형식으로 적어야 "다음 일정" 계산에 잡힌다.
- Do: 날씨 이모지는 날씨 표시에만 쓴다.
- Don't: 크림색 바탕에 붉은 벽돌색 포인트로 돌아가지 않는다.
- Don't: 둥근 카드에 그림자를 얹어 항목마다 감싸지 않는다.
- Don't: 노선 색을 버튼이나 링크에 쓰지 않는다.
- Don't: 제목 위에 작은 영문 꼬리표를 붙이지 않는다.

## Motion

- **Approach:** minimal-functional
- **Easing:** move(ease-in-out)
- **Duration:** short(300ms)
- **The one authored moment:** 날짜를 바꾸면 상단 띠가 그날 색으로 넘어간다. `prefers-reduced-motion`이면 끈다.

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-11-24 | 디자인 시스템 최초 작성 | /design-consultation으로 작성. Tripsy, Wanderlog, 일정 앱 화면 모음 조사와 "한눈에, 설렘, 재미를 섞자"는 요청 기준 |
| 2026-11-24 | 날짜별 노선 색 채택 | 며칠째인지 색만으로 알 수 있고 일본 철도 노선 색 체계와 닮음 |
| 2026-11-24 | 카드 대신 노선도 타임라인 | 한 화면에 더 많은 일정이 보이고 흔한 여행 앱 모양에서 벗어남 |
| 2026-11-24 | AI 목업 대신 실제 HTML 미리보기로 승인 | 유료 이미지 생성 없이 실제 화면으로 확인 |
