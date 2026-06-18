# DESIGN.md

> **항상 먼저 읽는 실행 가이드.** 디자인 철학 · 선호/비선호 스타일 · 공통 규칙 · 어떤 문서를 열지 안내.
> 상세 데이터는 아래 분리 문서에 있다. 이 문서는 가볍게 유지한다(목표 150~250줄).

## 0. 문서 구조와 로딩 규칙

### 0.1 File Index

| File | 내용 | 언제 읽나 |
| --- | --- | --- |
| `DESIGN.md` (이 문서) | 철학·우선순위·금지 스타일·공통 원칙·로딩 안내 | **항상** |
| `DESIGN_TOKENS.md` | 컬러/타이포/스페이싱/radius/shadow/motion/z-index/grid + `:root` CSS, 전체 팔레트 | 색·폰트·간격·토큰이 필요할 때 |
| `DESIGN_COMPONENTS.md` | Input/Select/Button/Modal/Table/Card/Pagination 등 상세 스펙(상태·사이즈 매트릭스) | 컴포넌트를 만들/고칠 때 |
| `DESIGN_PAGE_MAIN.md` | 메인페이지 시각 방향 + 메인 선호·비선호 분석 | **메인** 제작 시 |
| `DESIGN_PAGE_SUB.md` | 서브·게시판·갤러리·폼·기능형 페이지 방향 | **서브/게시판/폼** 제작 시 |

### 0.2 Loading Matrix (작업별로 열 문서)

| 작업 | 읽을 문서 |
| --- | --- |
| 색/폰트/간격/토큰만 확인·정의 | `DESIGN.md` + `DESIGN_TOKENS.md` |
| 컴포넌트 1개 제작·수정 | `DESIGN.md` + `DESIGN_COMPONENTS.md`(해당 절) + (값 필요 시)`DESIGN_TOKENS.md` |
| 새 메인페이지 | `DESIGN.md` + `DESIGN_PAGE_MAIN.md` + `DESIGN_TOKENS.md` |
| 새 서브페이지 | `DESIGN.md` + `DESIGN_PAGE_SUB.md` + `DESIGN_COMPONENTS.md`(등장 컴포넌트) + `DESIGN_TOKENS.md` |
| 게시판/갤러리/폼 페이지 | `DESIGN.md` + `DESIGN_PAGE_SUB.md` + `DESIGN_COMPONENTS.md` |

> 필요한 문서만 열어 컨텍스트를 가볍게 유지한다. 전체를 한 번에 다 읽지 않는다.

### 0.3 Single Source of Truth

| Rule | Description |
| --- | --- |
| 토큰값 | HEX·사이즈·스케일 값은 `DESIGN_TOKENS.md`에만 정의한다. 다른 문서는 **토큰 이름으로만** 참조한다. |
| 컴포넌트 상태/사이즈 | 공통 상태·사이즈는 `DESIGN_COMPONENTS.md` C0에서 한 번만 정의하고, 각 컴포넌트는 다른 점만 적는다. |
| 중복 금지 | 같은 값을 두 문서에 적지 않는다. 한쪽이 출처, 나머지는 참조. |

## 1. Design Principles

| Principle | Description |
| --- | --- |
| System first | 공통 UI는 정의된 토큰·컴포넌트 규칙을 우선 사용한다. |
| Consistency | 같은 의미·기능 요소는 화면이 달라도 동일한 스타일과 동작을 유지한다. |
| Reuse | 버튼·입력·테이블·카드·모달 등 반복 UI는 새로 만들기보다 기존 패턴을 재사용한다. |
| Semantic first | 컴포넌트에서는 raw HEX 대신 Semantic 토큰을 먼저 사용한다. |
| Theme support | 새 UI도 Light/Dark 두 모드를 함께 고려한다. |
| Extend with care | 새 패턴은 사용성/가독성/브랜드 표현이 명확히 개선될 때만 추가하고, 이어지는 페이지·상세·모바일과의 연결성을 함께 정의한다. |

## 2. Core Brand Colors

핵심 6색만 여기 둔다. 전체 단계값·다크 페어·Semantic 매핑은 `DESIGN_TOKENS.md` 참조.

| Role | Token | Light | 용도 |
| --- | --- | --- | --- |
| Main | `--brand-main` | `#1EBFFF` | 주요 CTA, 활성, 핵심 강조 |
| Main Strong | `--brand-main-strong` | `#0095EE` | 링크, 아이콘 강조, hover 보조 |
| Sub Gray | `--sub-gray` | `#404040` | 고강도 텍스트·아이콘 |
| Sub Navy | `--sub-navy` | `#1D5CEE` | 보조 브랜드, 세컨더리 버튼 |
| Sub Yellow | `--sub-yellow` | `#FFA200` | 주의·하이라이트·배지 |
| Sub Red | `--sub-red` | `#FF2F59` | 오류·삭제·위험 |

**사용 원칙**: 넓은 배경은 흰색/연한 Gray/Dark Navy로, 포인트 컬러는 숫자·CTA·배지·아이콘에만 제한적으로. 커스텀 Main/Sub 컬러가 입력되면 그 값을 최우선으로 쓰고, 없으면 위 기본값을 사용한다. (Light/Dark 쌍·커스텀 정책 상세는 `DESIGN_TOKENS.md`.)

## 3. Preferred Style (선호 — 이 방향으로 만든다)

| Keyword | Direction |
| --- | --- |
| 여백 중심 | 화면을 빽빽이 채우기보다 섹션·요소 사이 여백을 살려 편안하고 정제된 인상. |
| 이미지 주도 | 히어로·소개·갤러리에서 이미지가 분위기를 먼저 만들고 텍스트가 보조. |
| 절제된 포인트 | 강조색은 핵심 지점에만. 여러 강조색을 동시에 흩뿌리지 않는다. |
| 부드러운 구조 | 카드·섹션은 부드러운 radius·약한 shadow·연한 배경으로 구분. |
| 섹션 리듬 | 흰 배경 / 연한 Gray / Dark / 컬러 블록을 교차해 긴 페이지의 호흡을 만든다. |
| 명확한 위계 | 한 섹션 안에서 Primary / Secondary / Support 요소를 분명히 나눈다. |
| 실용 우선 | 메인에서도 브랜드 감성보다 로그인·바로가기·공지·문의 등 실제 행동 흐름을 우선. |
| 신뢰 근거 | 숫자·인증·파트너 로고·전문가 이미지로 신뢰를 시각화. |

(레퍼런스 스타일·레이아웃 기법·페이지 유형별 상세는 메인=`DESIGN_PAGE_MAIN.md`, 서브·기능형=`DESIGN_PAGE_SUB.md`.)

## 4. Disliked Style / Anti-Pattern (금지 — 발견 시 수정)

| Anti-Pattern | 왜 문제 | 교정 방향 |
| --- | --- | --- |
| 가짜 여백감 | 바깥 여백은 넓지만 내부 요소·카드·줄간격이 다닥다닥 붙음 | 컨테이너 여백뿐 아니라 요소 간격·line-height·카드 padding을 함께 키운다. |
| 튀는 폰트 | 성격과 안 맞는 장식적 폰트로 톤이 분리됨 | 본문/UI는 기본 Sans, 특수 폰트는 제한된 강조에만. |
| 투박한 Dark | 어둡고 크고 강하지만 디테일 부족으로 무겁기만 함 | Dark는 대비·여백·타이포 굵기·이미지 품질을 함께 조절. |
| 카드 남발 | 모든 정보를 카드로만 처리해 조립식·단조로움 | 카드/리스트/이미지/텍스트/full-bleed 섹션을 섞어 리듬을 만든다. |
| 약한 위계 | 제목·설명·버튼·숫자가 비슷한 강도 | 섹션마다 Primary/Secondary/Support를 명확히 나눈다. |
| 압축된 작은 글씨 | 여백은 많은데 정보는 촘촘 | 본문을 짧게 나누고 행간·문단 간격 확보. |
| 템플릿 같은 무드 | 일반적 스톡 이미지/아이콘으로 브랜드 인상이 없음 | 실제 맥락의 이미지·데이터·메시지를 사용. |

## 5. Common Component Principles

| Rule | Description |
| --- | --- |
| 우선순위 | 새로 만들기 전에 기존 컴포넌트로 표현 가능한지 먼저 확인. (스펙: `DESIGN_COMPONENTS.md`) |
| 상태/사이즈 | 공통 상태(Default/Hover/Focus/Active/Disabled + Good/Weak/Error)와 사이즈(small/basic/large)는 `DESIGN_COMPONENTS.md` C0 정의를 따른다. |
| 모바일 | `Hover`는 PC 전용. 터치 환경은 충분한 클릭 영역을 확보한다. |
| 간격 | 컴포넌트 내부 여백과 컴포넌트 사이 여백을 같은 값으로 혼용하지 않는다. (4px 배수 토큰) |
| CTA | 한 화면/모달/섹션에서 주요 CTA는 1개만 강하게. 보조는 line/text 버튼. |
| 상태 표현 | 선택·비활성·오류·완료·진행 상태를 색만 약하게 바꾸지 말고 분명히 구분. |

## 6. Quick Review Checklist

| Check | Question |
| --- | --- |
| 목적 | 이 화면에서 사용자가 할 일이 빠르게 보이는가? |
| 위계 | 가장 먼저 봐야 할 이미지·문장·버튼이 명확한가? |
| 여백 | 여백은 넓되 요소가 흩어지거나 반대로 몰려 있지 않은가? |
| 포인트 | 강조색이 너무 많거나 서로 경쟁하지 않는가? |
| 일관성 | 토큰·공통 컴포넌트 기준을 따르는가? (raw HEX 직접 사용 금지) |
| 리듬 | 섹션 배경·높이·이미지가 반복만 되지 않고 리듬을 만드는가? |
| 모바일 | 세로 흐름 전환·터치 영역·작은 글자 가독성이 괜찮은가? |
| 테마 | Light/Dark 모두에서 대비가 유지되는가? |

> 페이지 유형별 상세 체크리스트는 `DESIGN_PAGE_MAIN.md` / `DESIGN_PAGE_SUB.md`의 각 Review Checklist 참조.

## 7. 향후 추가 (지금은 넣지 않음)

모바일 전용 가이드, 관리자/대시보드, 콘텐츠 페이지, 로딩/스켈레톤/빈 상태 등은 필요 시 별도 섹션 또는 문서로 추가한다. (현재 문서들의 인라인 반응형 규칙은 그대로 유지한다.)
