# DESIGN_TOKENS.md

> 디자인 토큰 단일 출처(Single Source of Truth). 컬러·타이포·스페이싱·radius·shadow·motion·z-index·grid.
> **HEX/토큰값은 이 문서에만 정의한다.** 다른 문서(DESIGN.md/COMPONENTS/PAGE_PATTERNS)는 토큰 이름으로만 참조한다.
> 전체 Material 팔레트와 Brand 전체 단계값도 여기(아래 1.5~1.6)에만 둔다.

## 1. Color System

본 파트는 디자인 시스템에서 사용하는 컬러 토큰의 구조와 적용 기준을 정의한다.  
서비스의 기본 컬러는 아래에 정리한 색상을 기준으로 사용하며, 기본 브랜드 컬러는 Main/Sub 컬러 체계를 따른다. 추후 프로젝트별 컬러 또는 커스텀 컬러가 입력되면 해당 커스텀 값을 우선 적용한다.

### 1.1 Token Layers

| Layer | Purpose |
| --- | --- |
| Primitive | 실제 HEX 값을 가진 원시 팔레트. Material 계열 컬러와 Brand 컬러를 포함한다. |
| Semantic | 버튼, 텍스트, 보더, 아이콘 등 UI 역할에 연결되는 의미 기반 컬러. |
| Brand | 컬러시스템의 기본 Main/Sub 팔레트. Light/Dark 모드별 대응 색상을 가진다. |

### 1.2 Custom Color Policy

기본값이 없거나 별도 커스텀 컬러가 설정되지 않은 경우, 이 문서의 기본 Main/Sub 컬러를 사용한다.

| Priority | Rule |
| --- | --- |
| 1 | 사용자가 설정한 커스텀 Main/Sub 컬러를 최우선으로 사용한다. |
| 2 | 커스텀 컬러가 없으면 디자인시스템의 Brand 컬러 기본값을 사용한다. |
| 3 | UI 컴포넌트에서는 직접 HEX를 쓰기보다 Semantic 토큰을 먼저 사용한다. |
| 4 | Light/Dark 모드 전환 시 동일한 단계 번호의 `Brand/* Dark` 토큰을 대응값으로 사용한다. |

### 1.3 Default Main And Sub Colors

| Role | Light Token | Light HEX | Dark Token | Dark HEX | Usage |
| --- | --- | --- | --- | --- | --- |
| Main | `Brand/Blue/300` | `#1EBFFF` | `Brand/Blue Dark/300` | `#00AEFF` | 브랜드 핵심 컬러, 주요 CTA, 활성 상태, 주요 강조 |
| Main Strong | `Brand/Blue/600` | `#0095EE` | `Brand/Blue Dark/600` | `#44C8FF` | 텍스트 링크, 아이콘 강조, hover/pressed 보조 |
| Sub Grayscale | `Brand/Gray/800` | `#404040` | `Brand/Gray Dark/800` | `#ECF4FF` | 고강도 텍스트, 중요한 아이콘, 다크모드의 밝은 텍스트 |
| Sub Navy | `Brand/Navy/800` | `#1D5CEE` | `Brand/Navy Dark/800` | `#BBE0FB` | 보조 브랜드 컬러, 정보성 강조, 세컨더리 버튼 |
| Sub Yellow | `Brand/Yellow/700` | `#FFA200` | `Brand/Yellow Dark/700` | `#FFF69B` | 주의, 하이라이트, 배지, 일시적 강조 |
| Sub Red | `Brand/Red/400` | `#FF2F59` | `Brand/Red Dark/400` | `#E23E5F` | 오류, 삭제, 위험 액션, 실패 상태 |

### 1.4 Default Sub Color Set

디자인시스템에 정의된 `Sub Color` 조합은 기본 보조 컬러 세트로 사용한다.

| Color | Light Token | Light HEX | Dark Token | Dark HEX |
| --- | --- | --- | --- | --- |
| Navy | `Brand/Navy/800` | `#1D5CEE` | `Brand/Navy Dark/800` | `#BBE0FB` |
| Red | `Brand/Red/400` | `#FF2F59` | `Brand/Red Dark/400` | `#E23E5F` |
| Yellow | `Brand/Yellow/700` | `#FFA200` | `Brand/Yellow Dark/700` | `#FFF69B` |

### 1.5 Base Color Palette

기본 컬러 모음은 Primitive 토큰의 기준 팔레트다. 화면에서 직접 사용할 색상을 고르기 위한 원본 값이며, 실제 컴포넌트 적용 시에는 가능한 Semantic 또는 Brand 토큰을 우선 사용한다.

| Color | 50 | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | A100 | A200 | A400 | A700 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Red | `#FFEBEE` | `#FFCDD2` | `#EF9A9A` | `#E57373` | `#EF5350` | `#F44336` | `#E53935` | `#D32F2F` | `#C62828` | `#B71C1C` | `#FF8A80` | `#FF5252` | `#FF1744` | `#D50000` |
| Pink | `#FCE4EC` | `#F8BBD0` | `#F48FB1` | `#F06292` | `#EC407A` | `#E91E63` | `#D81B60` | `#C2185B` | `#AD1457` | `#880E4F` | `#FF80AB` | `#FF4081` | `#F50057` | `#C51162` |
| Purple | `#F3E5F5` | `#E1BEE7` | `#CE93D8` | `#BA68C8` | `#AB47BC` | `#9C27B0` | `#8E24AA` | `#7B1FA2` | `#6A1B9A` | `#4A148C` | `#EA80FC` | `#E040FB` | `#D500F9` | `#AA00FF` |
| Deep Purple | `#EDE7F6` | `#D1C4E9` | `#B39DDB` | `#9575CD` | `#7E57C2` | `#673AB7` | `#5E35B1` | `#512DA8` | `#4527A0` | `#311B92` | `#B388FF` | `#7C4DFF` | `#651FFF` | `#6200EA` |
| Indigo | `#E8EAF6` | `#C5CAE9` | `#9FA8DA` | `#7986CB` | `#5C6BC0` | `#3F51B5` | `#3F51B5` | `#303F9F` | `#283593` | `#1A237E` | `#8C9EFF` | `#536DFE` | `#3D5AFE` | `#304FFE` |
| Blue | `#E3F2FD` | `#BBDEFB` | `#90CAF9` | `#64B5F6` | `#42A5F5` | `#2196F3` | `#1E88E5` | `#1976D2` | `#1565C0` | `#0D47A1` | `#82B1FF` | `#448AFF` | `#2979FF` | `#2962FF` |
| Light Blue | `#E1F5FE` | `#B3E5FC` | `#81D4FA` | `#4FC3F7` | `#29B6F6` | `#03A9F4` | `#039BE5` | `#0288D1` | `#0277BD` | `#01579B` | `#80D8FF` | `#40C4FF` | `#00B0FF` | `#0091EA` |
| Cyan | `#E0F7FA` | `#B2EBF2` | `#80DEEA` | `#4DD0E1` | `#26C6DA` | `#00BCD4` | `#00ACC1` | `#0097A7` | `#00838F` | `#006064` | `#84FFFF` | `#18FFFF` | `#00E5FF` | `#00B8D4` |
| Teal | `#E0F2F1` | `#B2DFDB` | `#80CBC4` | `#4DB6AC` | `#26A69A` | `#009688` | `#00897B` | `#00796B` | `#00695C` | `#004D40` | `#A7FFEB` | `#64FFDA` | `#1DE9B6` | `#00BFA5` |
| Green | `#E8F5E9` | `#C8E6C9` | `#A5D6A7` | `#81C784` | `#66BB6A` | `#4CAF50` | `#43A047` | `#388E3C` | `#2E7D32` | `#1B5E20` | `#B9F6CA` | `#69F0AE` | `#00E676` | `#00C853` |
| Light Green | `#F1F8E9` | `#DCEDC8` | `#C5E1A5` | `#AED581` | `#9CCC65` | `#8BC34A` | `#7CB342` | `#689F38` | `#558B2F` | `#33691E` | `#CCFF90` | `#B2FF59` | `#76FF03` | `#64DD17` |
| Lime | `#F9FBE7` | `#F0F4C3` | `#E6EE9C` | `#DCE775` | `#D4E157` | `#CDDC39` | `#C0CA33` | `#AFB42B` | `#9E9D24` | `#827717` | `#F4FF81` | `#EEFF41` | `#C6FF00` | `#64DD17` |
| Yellow | `#FFFDE7` | `#FFF9C4` | `#FFF59D` | `#FFF176` | `#FFEE58` | `#FFEB3B` | `#FDD835` | `#FBC02D` | `#F9A825` | `#F57F17` | `#FFFF8D` | `#FFFF00` | `#FFEA00` | `#FFD600` |
| Amber | `#FFF8E1` | `#FFECB3` | `#FFE082` | `#FFD54F` | `#FFCA28` | `#FFC107` | `#FFB300` | `#FFA000` | `#FF8F00` | `#FF6F00` | `#FFE57F` | `#FFD740` | `#FFC400` | `#FFAB00` |
| Orange | `#FFF3E0` | `#FFE0B2` | `#FFCC80` | `#FFB74D` | `#FFA726` | `#FF9800` | `#FB8C00` | `#F57C00` | `#EF6C00` | `#E65100` | `#FFD180` | `#FFAB40` | `#FF9100` | `#FF6D00` |
| Deep Orange | `#FBE9E7` | `#FFCCBC` | `#FFAB91` | `#FF8A65` | `#FF7043` | `#FF5722` | `#F4511E` | `#E64A19` | `#D84315` | `#BF360C` | `#FF9E80` | `#FF6E40` | `#FF3D00` | `#FF6D00` |
| Brown | `#EFEBE9` | `#D7CCC8` | `#BCAAA4` | `#A1887F` | `#8D6E63` | `#795548` | `#6D4C41` | `#5D4037` | `#4E342E` | `#3E2723` | `-` | `-` | `-` | `-` |
| Gray | `#FAFAFA` | `#F5F5F5` | `#EEEEEE` | `#E0E0E0` | `#BDBDBD` | `#9E9E9E` | `#757575` | `#616161` | `#424242` | `#212121` | `-` | `-` | `-` | `-` |
| Blue Gray | `#ECEFF1` | `#CFD8DC` | `#B0BEC5` | `#90A4AE` | `#78909C` | `#607D8B` | `#546E7A` | `#455A64` | `#37474F` | `#263238` | `-` | `-` | `-` | `-` |

### 1.6 Brand Palettes

#### Brand Blue

| Step | Light | Dark |
| --- | --- | --- |
| 50 | `#DFF4FF` | `#065AB3` |
| 100 | `#ADE3FF` | `#007BD5` |
| 200 | `#72D1FF` | `#008CEA` |
| 300 | `#1EBFFF` | `#00AEFF` |
| 400 | `#00B2FF` | `#00AEFF` |
| 500 | `#00A3FD` | `#00BBFF` |
| 600 | `#0095EE` | `#44C8FF` |
| 700 | `#0082DA` | `#7FD8FF` |
| 800 | `#0071C5` | `#B3E7FF` |
| 900 | `#0051A2` | `#E1F6FF` |

#### Brand Navy

| Step | Light | Dark |
| --- | --- | --- |
| 50 | `#E2F2FF` | `#004DA5` |
| 100 | `#B9DEFF` | `#006BC3` |
| 200 | `#88CAFF` | `#007CD5` |
| 300 | `#4CB4FF` | `#0B8EE8` |
| 400 | `#00A3FF` | `#139DF6` |
| 500 | `#0092FF` | `#3FABF7` |
| 600 | `#0083FF` | `#63BAF7` |
| 700 | `#096FFF` | `#90CEFA` |
| 800 | `#1D5CEE` | `#BBE0FB` |
| 900 | `#2C36CE` | `#E3F3FD` |

#### Brand Yellow

| Step | Light | Dark |
| --- | --- | --- |
| 50 | `#FFF8E1` | `#FC830E` |
| 100 | `#FFEDB3` | `#FFAD1F` |
| 200 | `#FFE183` | `#FFC528` |
| 300 | `#FFD650` | `#FFDE31` |
| 400 | `#FFCB29` | `#F9E82B` |
| 500 | `#FFC309` | `#FBED50` |
| 600 | `#FFB401` | `#FEF272` |
| 700 | `#FFA200` | `#FFF69B` |
| 800 | `#FF9100` | `#FFFAC3` |
| 900 | `#FF7100` | `#FFFEE7` |

#### Brand Red

| Step | Light | Dark |
| --- | --- | --- |
| 50 | `#FFEAF0` | `#81284A` |
| 100 | `#FFC9D6` | `#A73053` |
| 200 | `#F7919F` | `#BC3457` |
| 300 | `#F1637A` | `#D1395C` |
| 400 | `#FF2F59` | `#E23E5F` |
| 500 | `#FF003F` | `#E75175` |
| 600 | `#F8003E` | `#EC6C8C` |
| 700 | `#E50037` | `#F294AC` |
| 800 | `#D9002F` | `#F7BECD` |
| 900 | `#C90022` | `#FCE5EB` |

#### Brand Gray

| Step | Light | Dark |
| --- | --- | --- |
| white | `#FFFFFF` | - |
| 50 | `#F1F1F1` | `#171D25` |
| 100 | `#EDEDED` | `#373E46` |
| 200 | `#E8E8E8` | `#565C66` |
| 300 | `#DBDBDB` | `#69707A` |
| 400 | `#BDBDBD` | `#9299A3` |
| 500 | `#9E9E9E` | `#B1B8C3` |
| 600 | `#737373` | `#D4DCE7` |
| 700 | `#5F5F5F` | `#E4EBF6` |
| 800 | `#404040` | `#ECF4FF` |
| 900 | `#202020` | `#F2FAFF` |
| black | `#202020` | - |

### 1.7 Semantic Color Mapping

Semantic 토큰은 컴포넌트 구현 시 우선 사용한다. Primitive 또는 Brand HEX를 직접 참조해야 하는 경우는 새로운 Semantic 역할이 아직 정의되지 않은 경우로 제한한다.

#### Button Background

| Token | HEX | Alias |
| --- | --- | --- |
| `Button/Background/Primary` | `#1EBFFF` | `Brand/Blue/300` |
| `Button/Background/Secondary` | `#1D5CEE` | `Brand/Navy/800` |
| `Button/Background/Light Sky` | `#DFF4FF` | `Brand/Blue/50` |
| `Button/Background/Blue` | `#1E88E5` | `Blue/600` |
| `Button/Background/Red` | `#F44336` | `Red/500` |
| `Button/Background/Green` | `#2E7D32` | `Green/800` |
| `Button/Background/Purple` | `#6A1B9A` | `Purple/800` |
| `Button/Background/Orange` | `#EF6C00` | `Orange/800` |
| `Button/Background/Gray Low emphasis` | `#F1F1F1` | `Brand/Gray/50` |
| `Button/Background/Gray High emphasis` | `#BDBDBD` | `Brand/Gray/400` |
| `Button/Background/White` | `#FFFFFF` | `Brand/Gray/white` |
| `Button/Background/Disabled` | `#F8F8F8` | - |

#### Button Border

| Token | HEX | Alias |
| --- | --- | --- |
| `Button/Border/Primary` | `#1EBFFF` | `Brand/Blue/300` |
| `Button/Border/Secondary` | `#1D5CEE` | `Brand/Navy/800` |
| `Button/Border/Gray Low emphasis` | `#E8E8E8` | `Brand/Gray/200` |
| `Button/Border/Gray High emphasis` | `#DBDBDB` | `Brand/Gray/300` |
| `Button/Border/Gray400` | `#BDBDBD` | `Brand/Gray/400` |
| `Button/Border/Gray800` | `#404040` | `Brand/Gray/800` |
| `Button/Border/Blue` | `#66B4E9` | - |
| `Button/Border/Red` | `#F58E8A` | - |
| `Button/Border/Green` | `#73B471` | - |
| `Button/Border/Purple` | `#9B7AC5` | - |
| `Button/Border/Orange` | `#FAB87F` | - |
| `Button/Border/Disabled` | `#F8F8F8` | - |

#### Button Text And Icon

| Token | HEX | Alias |
| --- | --- | --- |
| `Button/Icon/Gray` | `#737373` | `Brand/Gray/600` |
| `Button/Icon/Primary` | `#0095EE` | `Brand/Blue/600` |
| `Button/Icon/Color` | `#F44336` | `Red/500` |
| `Button/Text/Primary` | `#0095EE` | `Brand/Blue/600` |
| `Button/Text/Gray Low emphasis` | `#9E9E9E` | `Brand/Gray/500` |
| `Button/Text/Gray800` | `#404040` | `Brand/Gray/800` |
| `Button/Text/White` | `#FFFFFF` | - |
| `Button/Text/Blue` | `#1E88E5` | `Blue/600` |
| `Button/Text/Red` | `#F44336` | `Red/500` |
| `Button/Text/Green` | `#2E7D32` | `Green/800` |
| `Button/Text/Purple` | `#6A1B9A` | `Purple/800` |
| `Button/Text/Orange` | `#EF6C00` | `Orange/800` |

### 1.8 Dark Mode Rules

| Rule | Description |
| --- | --- |
| Brand pair | `Brand/Blue`, `Brand/Navy`, `Brand/Red`, `Brand/Yellow`, `Brand/Gray`는 각각 동일 단계의 `* Dark` 팔레트와 짝을 이룬다. |
| Same-step mapping | Light 모드에서 `Brand/Blue/300`을 사용하면 Dark 모드에서는 `Brand/Blue Dark/300`을 사용한다. |
| Contrast first | 다크모드에서는 배경이 어두워지므로 텍스트와 아이콘은 `Brand/Gray Dark/600~900`처럼 밝은 쪽 단계를 우선 사용한다. |
| Semantic first | 구현 시 직접 `* Dark` 값을 선택하기보다 theme mode에 따라 Semantic 토큰이 적절한 primitive 값을 바라보도록 구성한다. |
| Custom colors | 커스텀 Main/Sub 컬러가 들어오는 경우에도 Light/Dark 쌍을 함께 입력받는다. Dark 값이 없으면 기본 Dark 토큰을 fallback으로 사용한다. |
| Component coverage | Input, Select, Button, Checkbox, Radio, Textarea, Table, Modal 등 모든 컴포넌트는 Light/Dark 모드를 모두 지원한다. |
| Surface mapping | 컴포넌트 배경, 보더, 구분선, hover, selected, disabled, overlay는 모드별 surface 토큰으로 분리해 관리한다. |
| State color mapping | Good, Weak, Error, Warning, Success, Loading 같은 상태 색상은 Light/Dark 모드에서 동일한 의미를 유지하되, 각 모드의 대비 기준을 만족해야 한다. |

### 1.9 Usage Notes

- Primary CTA는 기본적으로 `Button/Background/Primary`를 사용한다.
- Secondary CTA는 `Button/Background/Secondary`를 사용한다.
- 위험/삭제 액션은 Brand Sub Red 또는 Semantic Red 토큰을 사용한다.
- 경고/주의/하이라이트는 Brand Sub Yellow를 사용한다.
- 일반 본문, 보조 텍스트, 비활성 상태는 Gray 계열 Semantic 토큰을 사용한다.
- 화면 단위에서 색을 추가할 때는 먼저 기존 Semantic 토큰으로 표현 가능한지 확인하고, 반복 사용되는 역할이면 새로운 Semantic 토큰을 정의한다.

## 2. Typography System

본 파트는 디자인시스템에서 사용하는 기본 폰트와 텍스트 크기 토큰을 정의한다.  
기본 폰트는 `Pretendard`를 사용하며, Android, iOS, Web 환경에서 동일한 폰트 체계를 기준으로 한다.

### 2.1 Font Family

| Role | Font Family | Usage |
| --- | --- | --- |
| Default | `Pretendard` | 서비스 전반의 기본 한글/영문/숫자 UI 폰트 |

폰트는 시스템 전반에서 일관되게 적용한다. 별도 브랜드 표현이나 이미지형 그래픽을 제외하고, 본문/버튼/입력/내비게이션/테이블/카드에는 기본 폰트를 사용한다.

### 2.2 Responsive Type Scale

폰트 토큰은 화면 너비에 따라 `xl`, `lg`, `sm` 3가지 크기 체계를 가진다.

| Breakpoint | Width | Description |
| --- | --- | --- |
| `xl` | `1280px ~` | 데스크톱 대형 화면 기준 |
| `lg` | `1024px ~` | 태블릿 또는 작은 데스크톱 기준 |
| `sm` | `~ 640px` | 모바일 화면 기준 |

### 2.3 Line Height

모든 기본 텍스트 토큰은 `line-height: 150%`를 기준으로 한다.  
텍스트가 여러 줄로 흐르는 본문, 카드 설명, 폼 도움말, 테이블 셀에서도 같은 기준을 사용해 읽기 흐름을 유지한다.

### 2.4 Body Text Tokens

| Token | `xl` Size | `lg` Size | `sm` Size | Line Height | Usage |
| --- | --- | --- | --- | --- | --- |
| `text-xs` | `12px / 0.75rem` | `10px / 0.625rem` | `10px / 0.625rem` | `150%` | 보조 라벨, 짧은 메타 정보, 작은 캡션 |
| `text-sm` | `14px / 0.875rem` | `12px / 0.75rem` | `12px / 0.75rem` | `150%` | 보조 본문, 설명 텍스트, 도움말 |
| `text-base` | `16px / 1rem` | `14px / 0.875rem` | `14px / 0.875rem` | `150%` | 기본 본문, 입력값, 일반 UI 텍스트 |
| `text-lg` | `18px / 1.125rem` | `16px / 1rem` | `16px / 1rem` | `150%` | 강조 본문, 카드 제목, 작은 섹션 제목 |
| `text-xl` | `20px / 1.25rem` | `18px / 1.125rem` | `16px / 1rem` | `150%` | 큰 본문 강조, 중요한 요약 텍스트 |

### 2.5 Heading Tokens

| Token | `xl` Size | `lg` Size | `sm` Size | Line Height | Usage |
| --- | --- | --- | --- | --- | --- |
| `H1` | `38px / 2.375rem` | `30px / 1.875rem` | `24px / 1.5rem` | `150%` | 페이지 최상위 제목 |
| `H2` | `30px / 1.875rem` | `24px / 1.5rem` | `20px / 1.25rem` | `150%` | 주요 섹션 제목 |
| `H3` | `24px / 1.5rem` | `20px / 1.25rem` | `18px / 1.125rem` | `150%` | 하위 섹션 제목, 카드 그룹 제목 |

### 2.6 Token Naming

디자인시스템의 텍스트 토큰은 기본 이름과 반응형 suffix를 함께 사용할 수 있다.

| Pattern | Example | Meaning |
| --- | --- | --- |
| Base token | `text-base`, `H1` | 기본 데스크톱 기준 토큰 |
| Large breakpoint token | `text-base-lg`, `H1-lg` | `lg` 구간에서 사용하는 크기 |
| Small breakpoint token | `text-xl-sm`, `H1-sm` | `sm` 구간에서 별도로 조정되는 크기 |

구현 시에는 화면 크기에 따라 토큰이 자동으로 전환되도록 구성한다. 컴포넌트 안에서 임의의 px 값을 직접 지정하기보다, 위에 정의된 토큰을 우선 사용한다.

### 2.7 Usage Notes

- 제목은 정보 구조에 맞게 `H1`, `H2`, `H3` 순서로 사용한다.
- 본문 기본값은 `text-base`를 사용한다.
- 보조 설명이나 캡션은 `text-sm` 또는 `text-xs`를 사용한다.
- 버튼, 입력창, 테이블 셀처럼 반복되는 UI 요소는 컴포넌트별 기본 텍스트 토큰을 지정해 일관성을 유지한다.
- 모바일에서는 제목 크기를 줄여 화면 점유율을 낮추고, 본문은 읽기성을 해치지 않는 범위에서 `lg` 또는 `sm` 토큰을 따른다.
- 특수한 마케팅 문구나 그래픽 표현을 제외하면 임의의 font-size, line-height를 새로 만들지 않는다.

## 3. Spacing System

본 파트는 디자인시스템에서 사용하는 여백 공간의 기준과 적용 방식을 정의한다.  
스페이싱은 `4px` 배수를 기본 단위로 사용하며, 필요 시 짝수 크기를 추가해 유연하게 확장할 수 있다.

### 3.1 Base Unit

| Rule | Description |
| --- | --- |
| Base unit | `4px`를 최소 단위로 사용한다. |
| Scale | `4px` 배수로 여백 값을 확장한다. |
| Extension | 화면 밀도나 컴포넌트 특성상 필요한 경우 짝수 단위 값을 추가할 수 있다. |
| Consistency | 같은 의미의 여백은 화면이 달라도 동일한 토큰을 사용한다. |

### 3.2 Spacing Tokens

| Token | Value | Usage |
| --- | --- | --- |
| `space-1` | `4px` | 아주 작은 요소 간격, 아이콘과 텍스트 사이의 최소 간격 |
| `space-2` | `8px` | 작은 버튼 내부 간격, 작은 UI 요소 사이 간격 |
| `space-3` | `12px` | 입력 필드 주변 간격, 컴팩트한 목록 간격 |
| `space-4` | `16px` | 기본 컴포넌트 간격, 카드 내부 기본 padding |
| `space-5` | `20px` | 섹션 내부의 보조 간격, 폼 그룹 간격 |
| `space-6` | `24px` | 카드와 카드 사이, 주요 콘텐츠 블록 간격 |
| `space-7` | `28px` | 입력 필드 그룹 사이의 넓은 간격, 반복 폼 항목 간격 |
| `space-10` | `40px` | 섹션 상하 여백, 큰 컨테이너 내부 padding |

### 3.3 Form Spacing Guide

폼과 입력 영역은 사용자가 항목의 관계를 빠르게 이해할 수 있도록 라벨, 입력창, 그룹 사이의 간격을 구분해 사용한다.

| Area | Value | Usage |
| --- | --- | --- |
| Container padding | `40px` | 폼 카드 또는 입력 컨테이너의 상단/좌측 주요 안쪽 여백 |
| Field group gap | `28px` | 서로 다른 입력 항목 그룹 사이의 간격 |
| Label to field gap | `10px` | 라벨과 입력 필드 사이의 간격 |

### 3.4 Usage Notes

- 기본 화면 구성은 `4px` 배수 토큰을 우선 사용한다.
- 컴포넌트 내부 여백과 컴포넌트 사이 여백을 같은 값으로 혼용하지 않는다.
- 관련성이 높은 요소는 작은 간격을 사용하고, 서로 다른 정보 그룹은 더 큰 간격을 사용한다.
- 폼에서는 라벨과 입력 필드는 가깝게, 입력 그룹끼리는 충분히 띄워 정보 구조를 명확히 한다.
- 새로운 여백 값이 필요하면 먼저 기존 토큰으로 표현 가능한지 확인하고, 반복적으로 필요할 때만 확장한다.


## 4. Radius System

> 초안(기존 "부드러운 radius / 16~20px" 표현을 값으로 명시). 필요 시 조정.

| Token | Value | Usage |
| --- | --- | --- |
| `radius-xs` | `4px` | 배지, 작은 칩, 태그 |
| `radius-sm` | `8px` | 버튼, 입력 필드 |
| `radius-md` | `12px` | 카드, 컨테이너 박스 |
| `radius-lg` | `16px` | 큰 카드, 패널 |
| `radius-xl` | `20px` | 모달, 히어로 카드 |
| `radius-pill` | `999px` | 라운드(C) 버튼·입력, pill 태그, page-index 칩 |
| `radius-full` | `50%` | 아바타, 원형 아이콘 버튼 |

- 같은 화면 안에서 카드 radius는 한 단계로 통일한다.
- 모달은 `radius-lg`~`radius-xl`(16~20px)를 사용한다.

## 5. Shadow / Elevation System

> 초안(기존 "약한/강한 shadow"를 단계값으로 명시). Light/Dark 분리.

| Token | Light | Dark | Usage |
| --- | --- | --- | --- |
| `shadow-0` | `none` | `none` | 평면, 보더로만 구분 |
| `shadow-1` | `0 1px 2px rgba(16,24,40,.06)` | `0 1px 2px rgba(0,0,0,.4)` | 카드 기본, 입력 영역 |
| `shadow-2` | `0 6px 16px rgba(16,24,40,.10)` | `0 6px 16px rgba(0,0,0,.5)` | hover 카드, 드롭다운, 떠 있는 요소 |
| `shadow-3` | `0 16px 40px rgba(16,24,40,.16)` | `0 16px 40px rgba(0,0,0,.6)` | 모달, 오버레이 레이어 |

- 기본 카드는 `shadow-1` 또는 보더 중 하나만 사용해 과한 그림자를 피한다.
- Dark 모드에서는 그림자 대신 surface 대비/보더로 구분을 보강한다.

## 6. Motion System

> 초안(기존 hover/active/slide 동작에 시간·곡선 기준 부여).

| Token | Value | Usage |
| --- | --- | --- |
| `dur-fast` | `140ms` | hover out, 작은 상태 변화 |
| `dur-base` | `200ms` | hover in, 일반 전환 |
| `dur-slow` | `320ms` | 펼침/접힘, 슬라이드, 모달 등장 |
| `ease-standard` | `cubic-bezier(0.2, 0, 0, 1)` | 일반 진입/이동 |
| `ease-emphasized` | `cubic-bezier(0.23, 1, 0.32, 1)` | 강조 전환, 카드 lift |

- `prefers-reduced-motion` 환경에서는 애니메이션/트랜지션을 제거한다.

## 7. Z-index System

> 초안. 레이어 충돌을 막기 위한 표준 스택.

| Token | Value | Layer |
| --- | --- | --- |
| `z-base` | `0` | 일반 콘텐츠 |
| `z-sticky` | `100` | sticky 헤더/내비, sub_nav |
| `z-dropdown` | `1000` | select/메뉴 드롭다운 |
| `z-overlay` | `1100` | 모달 dim 배경 |
| `z-modal` | `1200` | 모달 컨테이너 |
| `z-toast` | `1300` | 토스트/스낵바 |
| `z-tooltip` | `1400` | 툴팁 |

## 8. Grid & Container System

> 초안. 콘텐츠 폭·거터·열 기준. Breakpoint는 Typography(2.2)의 `xl`/`lg`/`sm`를 공유한다.

| Token | Value | Usage |
| --- | --- | --- |
| `container-max` | `1200px` | 본문 중앙 정렬 컨테이너 기본 최대 폭 |
| `container-wide` | `1400px` | 넓은 메인/갤러리 섹션 |
| `gutter` | `24px` | 데스크톱 좌우 여백·열 간격 |
| `gutter-mobile` | `16px` | 모바일 좌우 여백 |
| `columns` | `12` | 기준 그리드 컬럼 수 |

| Card Grid | xl/lg | sm |
| --- | --- | --- |
| 기본 카드 그리드 | 3열 | 1~2열 |
| 콘텐츠 분할 | 2열 | 1열 |

- 본문 콘텐츠는 `container-max` 중앙 정렬을 기본으로 하고, 한 줄이 과도하게 길어지지 않게 폭을 제한한다.

## 9. CSS Variables (:root)

> 복붙용 코어 토큰. 구현 시 컴포넌트는 raw HEX 대신 아래 변수를 사용한다.
> Dark 모드는 `:root[data-theme="dark"]`(또는 `.dark`)에서 brand/surface/shadow만 재정의한다.
> (전체 팔레트 단계값은 위 1.5~1.6 표 참조 — 변수에는 실제 사용하는 토큰만 둔다.)

```css
:root {
  /* Brand core (Light) */
  --brand-main:        #1EBFFF; /* Brand/Blue/300 — 주요 CTA·활성·강조 */
  --brand-main-strong: #0095EE; /* Brand/Blue/600 — 링크·아이콘 강조 */
  --sub-gray:          #404040; /* Brand/Gray/800 — 고강도 텍스트 */
  --sub-navy:          #1D5CEE; /* Brand/Navy/800 — 보조 브랜드·세컨더리 */
  --sub-yellow:        #FFA200; /* Brand/Yellow/700 — 주의·하이라이트 */
  --sub-red:           #FF2F59; /* Brand/Red/400 — 오류·삭제·위험 */

  /* Semantic surface / text (Light) */
  --surface:     #FFFFFF;
  --bg:          #F1F1F1; /* Brand/Gray/50 */
  --border:      #DBDBDB; /* Brand/Gray/300 */
  --border-soft: #EDEDED; /* Brand/Gray/100 */
  --text:        #202020; /* Brand/Gray/900 */
  --text-sub:    #404040; /* Brand/Gray/800 */
  --text-muted:  #737373; /* Brand/Gray/600 */

  /* State */
  --success: #04BA15;
  --warning: #FF7A00;
  --danger:  #FF2F57;

  /* Spacing (4px scale) */
  --space-1: 4px;  --space-2: 8px;  --space-3: 12px; --space-4: 16px;
  --space-5: 20px; --space-6: 24px; --space-7: 28px; --space-10: 40px;

  /* Radius */
  --radius-xs: 4px; --radius-sm: 8px; --radius-md: 12px;
  --radius-lg: 16px; --radius-xl: 20px; --radius-pill: 999px; --radius-full: 50%;

  /* Shadow */
  --shadow-1: 0 1px 2px rgba(16,24,40,.06);
  --shadow-2: 0 6px 16px rgba(16,24,40,.10);
  --shadow-3: 0 16px 40px rgba(16,24,40,.16);

  /* Motion */
  --dur-fast: 140ms; --dur-base: 200ms; --dur-slow: 320ms;
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.23, 1, 0.32, 1);

  /* Z-index */
  --z-sticky: 100; --z-dropdown: 1000; --z-overlay: 1100;
  --z-modal: 1200; --z-toast: 1300; --z-tooltip: 1400;

  /* Layout */
  --container-max: 1200px; --container-wide: 1400px;
  --gutter: 24px; --gutter-mobile: 16px;

  /* Type scale (xl 기준) */
  --text-xs: 12px; --text-sm: 14px; --text-base: 16px; --text-lg: 18px; --text-xl: 20px;
  --h1: 38px; --h2: 30px; --h3: 24px;
  --leading: 1.5;
  --font-sans: 'Pretendard', -apple-system, 'Apple SD Gothic Neo', sans-serif;
}

:root[data-theme="dark"] {
  /* Brand core (Dark) */
  --brand-main:        #00AEFF; /* Brand/Blue Dark/300 */
  --brand-main-strong: #44C8FF; /* Brand/Blue Dark/600 */
  --sub-gray:          #ECF4FF; /* Brand/Gray Dark/800 */
  --sub-navy:          #BBE0FB; /* Brand/Navy Dark/800 */
  --sub-yellow:        #FFF69B; /* Brand/Yellow Dark/700 */
  --sub-red:           #E23E5F; /* Brand/Red Dark/400 */

  /* Semantic surface / text (Dark) */
  --surface:     #171D25; /* Brand/Gray Dark/50 */
  --bg:          #0F141A;
  --border:      #373E46; /* Brand/Gray Dark/100 */
  --border-soft: #565C66; /* Brand/Gray Dark/200 */
  --text:        #ECF4FF; /* Brand/Gray Dark/800 */
  --text-sub:    #D4DCE7; /* Brand/Gray Dark/600 */
  --text-muted:  #B1B8C3; /* Brand/Gray Dark/500 */

  /* Shadow (Dark) */
  --shadow-1: 0 1px 2px rgba(0,0,0,.4);
  --shadow-2: 0 6px 16px rgba(0,0,0,.5);
  --shadow-3: 0 16px 40px rgba(0,0,0,.6);
}
```
