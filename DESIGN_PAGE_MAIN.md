# DESIGN_PAGE_MAIN.md

> 메인페이지 시각 방향 + 메인 한정 선호/비선호 분석.
> 메인 제작 시 `DESIGN.md` + 이 문서를 본다. (서브·게시판·폼은 `DESIGN_PAGE_SUB.md`)
> 토큰값은 `DESIGN_TOKENS.md`, 컴포넌트 스펙은 `DESIGN_COMPONENTS.md`.

## 21. Main Page Visual Direction

본 파트는 실제 메인페이지 작업 사례를 기준으로 한 화면 스타일 방향을 정의한다.  
현재 디자인 방향은 넓은 여백, 깔끔한 정보 구조, 이미지 중심의 첫인상, 필요한 지점에서만 강한 포인트를 사용하는 것을 기본으로 한다.

### 21.1 Design Tone

| Principle | Description |
| --- | --- |
| Clean spacing | 화면을 빽빽하게 채우기보다 섹션 사이에 충분한 여백을 두어 시선을 편하게 이동시킨다. |
| Focused accent | 모든 요소를 강조하지 않고, 숫자, CTA, 배지, 핵심 이미지처럼 중요한 지점에만 컬러를 사용한다. |
| Image-led mood | 히어로와 주요 섹션은 이미지가 분위기를 먼저 만들고, 텍스트는 이를 보조한다. |
| Soft structure | 카드, 섹션, 리스트는 부드러운 radius와 약한 shadow 또는 연한 배경으로 구분한다. |
| Functional clarity | 장식보다 정보 탐색과 사용 흐름을 우선한다. 메뉴, 버튼, 리스트는 역할이 분명해야 한다. |

### 21.2 Layout Characteristics

| Pattern | Rule |
| --- | --- |
| Hero | 큰 이미지 또는 비주얼을 사용해 첫 화면의 분위기를 결정한다. 텍스트는 좌측 또는 중앙에 명확하게 배치한다. |
| Section rhythm | 섹션마다 충분한 상하 여백을 두고, 배경색 전환으로 영역을 자연스럽게 나눈다. |
| Grid | 3열 카드, 2열 콘텐츠, 넓은 단일 이미지 등 단순한 그리드를 우선 사용한다. |
| Content width | 본문 콘텐츠는 중앙 정렬된 고정 폭 컨테이너를 사용해 읽기 흐름을 안정시킨다. |
| Footer | 하단은 어두운 배경을 사용해 화면을 단단하게 마무리할 수 있다. |

### 21.3 Visual Patterns

| Pattern | Description |
| --- | --- |
| Wide hero image | 첫 화면에 큰 이미지, 제품, 공간, 인물, 브랜드 비주얼을 배치한다. |
| Metric cards | 숫자와 아이콘을 조합해 핵심 정보를 짧게 보여준다. |
| Split content | 텍스트와 이미지를 좌우로 나누어 설명성과 시각성을 함께 제공한다. |
| Feature cards | 서비스나 제품의 주요 항목을 카드 형태로 정리한다. |
| Gallery section | 이미지가 중요한 콘텐츠는 넓은 썸네일과 카드형 목록으로 보여준다. |
| Notice list | 공지나 뉴스는 날짜와 제목 중심의 간결한 리스트로 구성한다. |

### 21.4 Color Usage Direction

| Usage | Rule |
| --- | --- |
| Base | 흰색, 밝은 Gray, Dark Navy 계열을 넓은 배경으로 사용한다. |
| Accent | Blue, Orange, Red, Green 등은 핵심 숫자, CTA, 배지, 아이콘에 제한적으로 사용한다. |
| Large color block | 브랜드 인상이 필요한 경우 넓은 컬러 블록을 사용할 수 있지만, 주변 여백과 대비를 충분히 둔다. |
| Dark section | 기술, 프리미엄, 신뢰감이 필요한 섹션은 Dark 배경과 밝은 텍스트를 사용할 수 있다. |

### 21.5 Page Composition Guide

메인페이지는 아래 흐름을 기본으로 구성할 수 있다.

| Order | Section | Purpose |
| --- | --- | --- |
| 1 | Header / Navigation | 브랜드와 주요 메뉴를 제공한다. |
| 2 | Hero | 브랜드의 첫인상과 핵심 메시지를 전달한다. |
| 3 | Metric / Quick cards | 주요 수치, 빠른 메뉴, 핵심 기능을 짧게 보여준다. |
| 4 | Brand / Company intro | 서비스 또는 회사의 정체성을 설명한다. |
| 5 | Product / Service section | 주요 상품, 서비스, 기능을 카드나 split layout으로 소개한다. |
| 6 | Portfolio / Gallery | 실제 사례, 이미지, 콘텐츠를 보여준다. |
| 7 | Notice / News | 공지, 새 소식, 업데이트를 제공한다. |
| 8 | Contact / Support | 문의, 고객센터, 위치, 관련 링크를 제공한다. |
| 9 | Footer | 회사 정보와 보조 링크를 제공한다. |

### 21.6 Do / Don't

| Do | Don't |
| --- | --- |
| 여백을 충분히 두고 섹션별 호흡을 만든다. | 모든 콘텐츠를 첫 화면에 과하게 밀어 넣지 않는다. |
| 이미지를 크게 사용해 페이지의 성격을 빠르게 전달한다. | 의미 없는 장식 이미지나 흐릿한 분위기 이미지만 사용하지 않는다. |
| 포인트 컬러는 핵심 정보에만 제한적으로 사용한다. | 여러 강조색을 동시에 사용해 시선을 분산시키지 않는다. |
| 카드와 리스트는 단순하고 읽기 쉽게 만든다. | 카드 안에 다시 카드처럼 보이는 복잡한 구조를 만들지 않는다. |
| 새 디자인을 추가할 때 다음 페이지와 상세 화면의 연결성을 고려한다. | 한 화면에서만 성립하는 스타일을 반복 검토 없이 확장하지 않는다. |

### 21.7 Current Gap

현재 DESIGN.md는 공통 컴포넌트와 기본 화면 패턴을 정리한 문서다.  
실제 메인페이지 스타일을 더 정확히 반영하려면 아래 항목을 추가로 정의한다.

| Needed | Description |
| --- | --- |
| Brand mood | 프로젝트별 분위기. 예: 의료/프리미엄, 공공/신뢰, 연구/테크, 교회/따뜻함 등 |
| Main page templates | 히어로 중심형, 카드 대시보드형, 스토리텔링형, 갤러리형 등 대표 메인 구조 |
| Section spacing | 메인페이지 섹션별 권장 상하 여백과 컨테이너 폭 |
| Image rules | 히어로, 카드, 갤러리, 배경 이미지의 비율과 크롭 기준 |
| Responsive layout | PC, tablet, mobile에서 메인 섹션이 접히는 방식 |

### 21.8 Personal Design Style Keywords

본 파트는 실제 작업 사례에서 반복적으로 보이는 화면 감도를 정리한다.

| Keyword | Direction |
| --- | --- |
| 여백 중심 | 화면을 가득 채우기보다 콘텐츠 주변의 여백을 살려 고급스럽고 편안한 인상을 만든다. |
| 정돈된 정보 | 제목, 설명, 버튼, 카드, 리스트의 역할을 명확히 나누어 사용자가 빠르게 훑어볼 수 있게 한다. |
| 이미지 주도 | 히어로, 회사 소개, 제품, 갤러리 섹션에서 이미지를 크게 사용해 페이지의 첫인상과 신뢰감을 만든다. |
| 절제된 포인트 | 강조가 필요한 숫자, CTA, 배지, 아이콘에만 강한 색을 사용하고 나머지는 차분하게 유지한다. |
| 부드러운 카드 | 카드에는 약한 그림자, 연한 배경, 적당한 radius를 사용해 친근하지만 과하지 않은 구조를 만든다. |
| 섹션 대비 | 흰 배경, 연한 Gray 배경, Dark footer, 컬러 블록을 번갈아 사용해 긴 페이지의 리듬을 만든다. |
| 실용적 구성 | 메인페이지에서도 브랜드 감성보다 사용 흐름을 우선한다. 빠른 메뉴, 공지, 고객센터, 위치, 링크처럼 실제 행동으로 이어지는 영역을 명확히 둔다. |

### 21.9 Main Page Template Types

메인페이지는 프로젝트 성격에 따라 아래 패턴을 조합해 사용한다.

| Type | Use Case | Composition |
| --- | --- | --- |
| Brand Hero Type | 제품, 회사, 기관의 첫인상을 강하게 보여줄 때 | Hero image -> Metric cards -> Company intro -> Product/Gallery -> Footer |
| Dashboard Entry Type | 로그인, 빠른 메뉴, 공지, 고객센터처럼 즉시 사용이 중요한 사이트 | Login/Quick area -> Banner -> Shortcut cards -> Notice/Support -> Footer |
| Storytelling Type | 기관 소개, 사업 소개, 브랜드 스토리가 중요한 사이트 | Hero -> Intro -> Alternating image/text sections -> News -> Footer |
| Gallery Content Type | 이미지, 포트폴리오, 사례 중심 사이트 | Hero -> Category/Metric -> Gallery grid -> Detail cards -> Contact/Footer |
| Dark Impact Type | 기술, 연구, 프리미엄, 집중감이 필요한 사이트 | Dark hero or dark section -> Light content -> Dark footer |

### 21.10 Main Page Spacing Guide

| Area | PC Guide | Mobile Guide |
| --- | --- | --- |
| Header | 메뉴 간격을 넓게 두고, 로고와 CTA가 답답하지 않게 배치한다. | 메뉴는 접고, 핵심 액션만 우선 노출한다. |
| Hero | 화면 첫 인상에 충분한 높이를 부여하되 다음 섹션이 자연스럽게 이어지도록 한다. | 텍스트와 이미지가 겹칠 경우 가독성을 우선해 세로 배치로 전환한다. |
| Section | 섹션 사이에는 넓은 상하 여백을 사용하고, 배경 전환으로 구분한다. | 여백은 줄이되 섹션 경계가 붙어 보이지 않게 유지한다. |
| Card grid | 3열 또는 2열을 기본으로 하며 카드 사이 간격을 일정하게 유지한다. | 1열 또는 2열로 접고, 카드 내부 여백을 줄여 정보 밀도를 조정한다. |
| Footer | 어두운 배경으로 안정감 있게 마무리한다. | 정보 우선순위를 정해 세로로 정리한다. |

### 21.11 Image Direction

| Image Type | Rule |
| --- | --- |
| Hero image | 제품, 공간, 인물, 상징 이미지를 크게 사용한다. 텍스트가 올라가는 경우 대비를 확보한다. |
| Product image | 제품의 형태와 색이 잘 보이도록 밝고 선명한 이미지를 우선한다. |
| Company image | 건물, 공간, 작업 현장 등 신뢰를 주는 이미지를 사용한다. |
| Gallery image | 썸네일 비율을 통일하고, 리스트 안에서 크롭 위치가 흔들리지 않게 한다. |
| Background image | 분위기용 이미지는 어둡게 덮거나 흐리게 처리해 텍스트와 충돌하지 않게 한다. |

### 21.12 Additional Observed Main Patterns

본 파트는 추가 메인페이지 작업 사례에서 확인되는 패턴을 정리한다.

| Pattern | Description | Use Case |
| --- | --- | --- |
| Dark product story | 검은 배경 위에 강한 이미지, 컬러 아이콘, 짧은 문장을 배치해 몰입감을 만든다. | 보안, 기술, 솔루션, 브랜드 임팩트가 필요한 페이지 |
| Blue service block | 넓은 Blue 배경 안에 서비스 설명과 이미지를 배치해 신뢰감과 명확한 구획을 만든다. | B2B, 공공, 서비스 소개, 솔루션 소개 |
| Campaign character | 캐릭터와 큰 타이포, 밝은 색상 블록을 사용해 친근하고 기억하기 쉬운 인상을 만든다. | 이벤트, 캠페인, 참여형 페이지 |
| Portal dashboard | 로그인, 공지, 빠른 메뉴, 고객센터를 첫 화면에 배치해 즉시 사용 가능한 구조를 만든다. | 입찰, 업무 포털, 회원 기반 서비스 |
| Community home | 히어로와 게시글 리스트를 함께 보여주어 방문자가 바로 읽고 참여할 수 있게 한다. | 내부 커뮤니티, 게시판 중심 서비스 |
| Mixed light/dark flow | 밝은 섹션과 어두운 섹션을 교차해 긴 페이지의 지루함을 줄인다. | 콘텐츠가 많은 회사 소개, 제품 소개 페이지 |

### 21.13 Main Page Selection Guide

메인페이지는 예쁜 화면보다 목적에 맞는 구조를 먼저 선택한다.

| Goal | Recommended Type | Notes |
| --- | --- | --- |
| 브랜드 첫인상 강화 | Brand Hero Type, Dark Impact Type | 히어로 이미지와 짧은 카피를 가장 먼저 설계한다. |
| 서비스 탐색 유도 | Storytelling Type, Blue service block | 섹션별로 사용자가 이해해야 하는 순서를 만든다. |
| 빠른 업무 처리 | Dashboard Entry Type, Portal dashboard | 로그인, 바로가기, 공지, 고객센터를 첫 화면에 배치한다. |
| 캠페인 참여 유도 | Campaign character, Gallery Content Type | 캐릭터, 배지, 이벤트 카드처럼 기억에 남는 요소를 사용한다. |
| 커뮤니티 활성화 | Community home | 최근 게시글, 인기 주제, 작성 버튼을 명확히 노출한다. |

### 21.14 Accent Strength

포인트는 화면 성격에 따라 강도를 조절한다.

| Strength | Usage |
| --- | --- |
| Low | 공공, 기관, 회사 소개처럼 신뢰와 차분함이 중요한 화면. 흰 배경과 연한 Gray를 중심으로 사용한다. |
| Medium | 일반 서비스, 제품 소개, 포트폴리오 화면. CTA, 숫자, 아이콘에만 컬러를 사용한다. |
| High | 캠페인, 이벤트, 기술 임팩트 화면. 큰 컬러 블록, 캐릭터, 강한 이미지, 어두운 배경을 사용할 수 있다. |

### 21.15 Main Page Review Checklist

메인페이지를 검토할 때 아래 항목을 확인한다.

| Check | Question |
| --- | --- |
| First impression | 첫 화면만 봐도 이 사이트가 무엇을 하는 곳인지 알 수 있는가? |
| Visual focus | 가장 먼저 봐야 할 이미지, 문장, 버튼이 명확한가? |
| Spacing | 섹션 사이에 충분한 여백이 있고, 콘텐츠가 답답하지 않은가? |
| Accent | 강조색이 너무 많거나 서로 경쟁하지 않는가? |
| Flow | Hero 이후 사용자가 자연스럽게 다음 섹션으로 이동하는가? |
| Practical action | 문의, 로그인, 공지, 바로가기 등 실제 행동 지점이 명확한가? |
| Extendability | 서브페이지, 목록, 상세, 폼 화면으로 확장해도 어색하지 않은가? |

### 21.16 Preferred Reference Style

본 파트는 선호하는 외부 레퍼런스에서 추출한 메인페이지 스타일 방향을 정의한다.

| Direction | Description |
| --- | --- |
| Editorial hero | 히어로는 단순 배너가 아니라 첫 장면처럼 구성한다. 큰 이미지, 강한 문장, 여백, 슬라이드 요소를 조합해 브랜드의 태도를 보여준다. |
| Wide visual section | 중간 섹션에도 넓은 이미지 영역을 사용해 페이지 흐름을 전환한다. 이미지 위 텍스트는 짧고 강하게 배치한다. |
| Calm premium tone | 색을 많이 쓰기보다 흰 배경, 크림/라이트 Gray, Dark Navy, Black 계열을 넓게 사용해 차분하고 정제된 인상을 만든다. |
| Point color minimal | Orange, Blue, Green, Purple 등 포인트 컬러는 버튼, 작은 라벨, 아이콘, 숫자, 강조 단어에 제한적으로 사용한다. |
| Large typography | 핵심 메시지는 크고 굵게 배치하되, 보조 설명은 짧고 얇게 처리해 정보 위계를 분명히 한다. |
| Modular sections | 뉴스, 서비스, 제품, 공지, 파트너, 다운로드 등 반복 섹션은 모듈처럼 정리해 확장하기 쉽게 만든다. |
| Soft interactive cards | 둥근 카드, 넓은 카드, 그림자, floating control, arrow button 등을 사용해 정적인 화면 안에 조작감을 준다. |
| Data and trust | 숫자, 인증서, 파트너 로고, 실적, 네트워크, 의사/전문가 이미지 등 신뢰를 주는 근거를 시각화한다. |

### 21.17 Preferred Layout Techniques

| Technique | Rule |
| --- | --- |
| Split hero | 좌측에는 메시지와 버튼, 우측에는 큰 이미지나 오브젝트를 배치한다. 한쪽을 어둡게 처리하면 시선 집중을 만들 수 있다. |
| Overlapped card | 히어로 아래에 흰 카드, 검색 박스, quick card를 살짝 겹쳐 배치해 첫 화면과 다음 영역을 연결한다. |
| Horizontal story | 이미지와 텍스트를 좌우로 교차 배치해 긴 페이지에서도 리듬을 만든다. |
| Full-bleed impact | 특정 섹션은 화면 폭 전체를 이미지 또는 컬러 배경으로 채워 강한 전환점을 만든다. |
| Centered statement | 브랜드 철학, 핵심 슬로건, 가치 선언은 중앙 정렬과 넓은 여백으로 문장 자체에 힘을 준다. |
| Card cluster | 기능, 메뉴, 보험/서비스, 자료, 공지처럼 많은 항목은 작은 카드 묶음으로 정리한다. |
| Logo strip | 파트너, 인증, 참여 기업은 로고 스트립으로 정리해 신뢰감을 만든다. |
| Floating utility | 상담, 챗봇, quick menu, top button 등은 필요할 때 우측 floating 요소로 제공한다. |

### 21.18 Preferred Reference Patterns

| Pattern | Description | Good For |
| --- | --- | --- |
| Premium corporate | 큰 사진, 짙은 overlay, 넓은 white space, 정제된 뉴스룸 구성. | 기업, 제조, 글로벌, ESG, 기술 브랜드 |
| Modern SaaS / Tech | dark card, split hero, floating search, purple/blue accent, product module. | 솔루션, 데이터, AI, 소프트웨어 |
| Medical / Lab clean | 흰 배경, 푸른 포인트, 과학 이미지, 인증서, 전문가 이미지. | 병원, 연구소, 의료, 검사센터 |
| Financial portal | 둥근 pastel 카드, quick action, 공지 카드, floating menu. | 보험, 은행, 연금, 회원형 포털 |
| Campaign friendly | 캐릭터, 큰 그래픽, 밝은 Green 계열, 참여 카드. | 캠페인, 이벤트, 공공 참여 서비스 |
| Service hub | 검색, 바로가기, 메뉴 카드, 상담 카드, 최근 소식이 한 화면에 정리된 구조. | 고객센터, 사이버창구, 업무형 메인 |

### 21.19 Refinement Direction

앞으로 메인페이지를 디자인할 때는 아래 방향으로 발전시킨다.

| Current Base | Refinement |
| --- | --- |
| 깔끔한 카드 중심 구성 | 카드 간 간격과 높이를 더 정교하게 맞추고, 카드마다 역할을 명확히 나눈다. |
| 이미지 중심 히어로 | 히어로를 더 editorial하게 구성해 이미지, 카피, CTA, 슬라이드 컨트롤의 관계를 명확히 만든다. |
| 포인트 컬러 사용 | 포인트 컬러의 강도를 화면 목적에 따라 Low / Medium / High로 조절한다. |
| 섹션별 배경 전환 | 밝은 섹션, Dark 섹션, 컬러 섹션의 전환 리듬을 더 의도적으로 설계한다. |
| 공지/뉴스 목록 | 날짜, 카테고리, 제목, 썸네일 여부에 따라 목록형과 카드형을 구분한다. |
| 실용형 메인 | 로그인, 바로가기, 상담, 공지, 고객센터는 예쁜 장식보다 사용자의 행동 흐름을 우선한다. |

### 21.20 Reference-Based Do / Don't

| Do | Don't |
| --- | --- |
| 히어로는 이미지와 메시지가 하나의 장면처럼 보이게 만든다. | 히어로에 의미 없는 배경 이미지만 크게 넣지 않는다. |
| 긴 페이지는 강한 이미지 섹션과 조용한 정보 섹션을 교차한다. | 모든 섹션을 같은 밝기, 같은 카드 톤으로 반복하지 않는다. |
| 버튼과 arrow는 작아도 명확한 클릭 지점으로 만든다. | 클릭 가능한 요소를 텍스트처럼 흐리게 숨기지 않는다. |
| 포인트 컬러는 화면의 핵심 흐름을 안내하도록 쓴다. | 예쁘다는 이유로 포인트 컬러를 여러 곳에 흩뿌리지 않는다. |
| 숫자, 인증, 파트너, 전문가 이미지로 신뢰 근거를 만든다. | 설명 문장만 길게 늘려 신뢰를 설득하려 하지 않는다. |
| 업무형 메인은 사용자가 바로 할 수 있는 행동을 첫 화면에 둔다. | 메인 화면을 브랜드 감성만으로 채워 실사용 진입을 늦추지 않는다. |

### 21.21 Disliked Style / Anti-Pattern

본 파트는 선호하지 않는 메인페이지 스타일을 정의한다.  
넓은 여백이 있어 보이더라도 실제 콘텐츠 간격, 폰트 선택, 카드 밀도, 섹션 리듬이 맞지 않으면 답답하고 투박한 화면으로 느껴질 수 있다.

| Anti-Pattern | Why It Feels Wrong | Avoid |
| --- | --- | --- |
| Fake spaciousness | 화면 바깥 여백은 넓지만 제목, 설명, 카드, 버튼이 내부에서 다닥다닥 붙어 있어 답답하게 느껴진다. | 컨테이너 여백뿐 아니라 요소 사이 간격, 줄 간격, 카드 내부 padding을 함께 조정한다. |
| Detached font | 사이트 성격과 어울리지 않는 장식적이거나 지나치게 개성 강한 폰트를 사용해 전체 톤이 분리된다. | 기본 폰트는 정제된 Sans 계열을 우선하고, 특수 폰트는 브랜드 타이틀이나 제한된 강조 영역에만 사용한다. |
| Rough composition | 섹션 구조는 있어도 시선 흐름이 매끄럽지 않고, 이미지와 텍스트의 크기 관계가 어색해 투박하게 보인다. | 히어로, 섹션 제목, 카드, CTA의 위계를 먼저 정리한 뒤 배치한다. |
| Heavy block without refinement | 짙은 배경, 큰 글자, 강한 컬러를 사용했지만 디테일이 부족해 고급스럽기보다 무겁고 둔해 보인다. | Dark 섹션은 대비, 여백, 타이포 굵기, 이미지 품질을 함께 조절한다. |
| Over-carded layout | 모든 정보를 카드로만 처리해 화면이 단조롭고 조립식처럼 보인다. | 카드, 리스트, 이미지 섹션, 텍스트 섹션, full-bleed 섹션을 섞어 리듬을 만든다. |
| Dense small text | 설명이 작고 촘촘해 읽기 어렵고, 여백이 많아도 실제 정보는 압축되어 보인다. | 본문은 짧게 나누고 line-height와 문단 간격을 충분히 확보한다. |
| Weak visual hierarchy | 제목, 설명, 버튼, 숫자, 이미지가 비슷한 강도로 보여 어디를 먼저 봐야 할지 애매하다. | 한 섹션 안에서 Primary / Secondary / Support 요소를 명확히 나눈다. |
| Generic business stock mood | 사진과 아이콘이 너무 일반적이어서 브랜드만의 인상 없이 템플릿처럼 보인다. | 실제 서비스 맥락과 맞는 이미지, 데이터, 메시지를 사용한다. |

### 21.22 Anti-Pattern Checklist

메인페이지 시안을 검토할 때 아래 항목 중 하나라도 강하게 해당하면 조정한다.

| Check | Question |
| --- | --- |
| Font fit | 폰트가 브랜드/서비스 성격과 자연스럽게 어울리는가? |
| Inner spacing | 카드와 섹션 내부의 요소들이 서로 붙어 보이지 않는가? |
| Rhythm | 섹션별 높이, 배경, 이미지 크기가 반복만 되지 않고 리듬을 만드는가? |
| Refinement | 버튼, 라벨, 아이콘, 카드 radius, shadow가 세련되게 정리되어 있는가? |
| Density | 여백은 넓지만 실제 텍스트와 카드가 한곳에 몰려 있지 않은가? |
| Tone consistency | 이미지, 폰트, 컬러, 아이콘 스타일이 서로 동떨어져 보이지 않는가? |
| Premium feel | 어두운 배경이나 큰 타이포를 썼을 때 고급스러움보다 투박함이 먼저 느껴지지 않는가? |

### 21.23 Correction Direction

선호하지 않는 스타일이 발견되면 아래 방향으로 수정한다.

| Problem | Correction |
| --- | --- |
| 요소가 붙어 보임 | 카드 내부 padding, 텍스트 line-height, 제목과 본문 사이 간격을 먼저 늘린다. |
| 폰트가 튐 | 장식성이 강한 폰트를 줄이고, 본문과 UI는 기본 폰트 체계로 맞춘다. |
| 투박한 dark section | 배경을 단순히 어둡게 하지 말고 이미지, overlay, 대비, 작은 포인트 컬러를 함께 조절한다. |
| 카드가 많아 단조로움 | 일부 카드는 리스트, split layout, full-width visual section으로 바꾼다. |
| 정보가 압축됨 | 한 섹션에 담긴 메시지를 줄이고, 다음 섹션으로 나누어 호흡을 만든다. |
| 템플릿처럼 보임 | 실제 브랜드 문장, 서비스 데이터, 고유 이미지, 명확한 CTA를 추가한다. |

