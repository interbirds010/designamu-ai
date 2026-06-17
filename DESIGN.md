# DESIGN.md

## 0. Design System Principle

본 문서는 화면 작업에서 반복적으로 사용하는 기본 디자인 시스템과 컴포넌트 기준을 정의한다.  
버튼, 모달, 게시판, 입력 요소, 테이블, 카드 등 공통 UI는 화면 간 통일성을 유지하기 위해 본 문서의 기준을 우선 사용한다.

### 0.1 Default Usage

| Rule | Description |
| --- | --- |
| System first | 공통 UI는 본 문서에 정의된 컬러, 폰트, 스페이싱, 컴포넌트 규칙을 우선 사용한다. |
| Consistency | 같은 의미와 같은 기능을 가진 요소는 화면이 달라도 동일한 스타일과 동작을 유지한다. |
| Reuse | 버튼, 입력, 선택, 테이블, 카드, 모달 등 반복되는 UI는 새로 만들기보다 기존 컴포넌트 패턴을 재사용한다. |
| Theme support | 새로 추가되는 UI도 Light/Dark 모드를 함께 고려한다. |

### 0.2 Extension Policy

더 나은 사용자 경험이나 화면 목적에 맞는 디자인이 필요한 경우, 새로운 디자인 패턴이나 컴포넌트를 추가할 수 있다.  
단, 새로운 디자인을 추가할 때는 이후 이어지는 페이지 작업과 연계되는 부분을 함께 고려해야 한다.

| Rule | Description |
| --- | --- |
| Reason | 기존 컴포넌트로 해결하기 어렵거나, 사용성/가독성/브랜드 표현이 명확히 개선되는 경우에 추가한다. |
| Relationship | 새 디자인이 기존 컴포넌트와 어떤 관계인지 명시한다. 예: Button의 변형, Card의 확장, Table의 대체 패턴. |
| Reusability | 한 화면 전용 장식이 아니라, 이후 페이지에서도 재사용 가능한 구조인지 검토한다. |
| Continuity | 이어지는 페이지, 상세 화면, 목록 화면, 모달, 모바일 화면에서 같은 패턴이 어떻게 연결될지 함께 정의한다. |
| Token alignment | 새 디자인도 컬러, 폰트, 스페이싱, 다크모드 토큰 체계를 벗어나지 않는다. |
| Documentation | 새 패턴이 반복 사용될 가능성이 있으면 DESIGN.md에 섹션을 추가하거나 기존 섹션에 변형으로 기록한다. |

### 0.3 Current Scope

현재 문서는 기본 디자인 시스템과 공통 컴포넌트의 사용 기준을 먼저 정리한 것이다.  
실제 서비스의 화면 분위기, 브랜드 톤, 레이아웃 성격, 주요 페이지별 스타일은 별도 화면 스냅샷과 함께 추가 정의한다.

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

## 4. Input Box

본 파트는 디자인시스템에서 사용하는 입력 필드의 형태, 크기, 상태, 내부 여백 기준을 정의한다.  
Input Box는 상태에 따라 색상과 보더를 구분해 사용하며, 모바일에서는 `hover` 상태를 적용하지 않고 PC 버전과 동일한 높이 및 좌우 여백 규칙을 사용한다.

### 4.1 Input Types

| Type | Name | Description |
| --- | --- | --- |
| `A` | 일반 형태 | 외곽선이 있는 기본 입력 박스. 가장 일반적인 입력 UI에 사용한다. |
| `B` | 라인 형태 | 하단 라인만 사용하는 입력 박스. 화면 밀도가 높거나 간결한 폼에 사용한다. |
| `C` | 라운드 형태 | 둥근 pill 형태의 입력 박스. 검색, 필터, 부드러운 인상의 입력 UI에 사용한다. |

### 4.2 Input States

| State | Description |
| --- | --- |
| `Default` | 입력 전 기본 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Focus` | 입력 필드가 포커스된 상태 |
| `Active` | 사용자가 입력 중인 상태 |
| `Completion` | 입력이 완료된 상태 |
| `Disabled` | 입력할 수 없는 비활성 상태 |

모바일에서는 `hover` 상호작용을 사용하지 않는다. 터치 환경에서는 `focus`, `active`, `completion`, `disabled` 상태를 중심으로 표현한다.

### 4.3 Input Sizes

Input Box는 `small`, `basic`, `large` 3가지 크기를 사용한다.

| Size | Height | Usage |
| --- | --- | --- |
| `small` | `36px` | 좁은 필터, 테이블 내부 입력, 보조 입력 |
| `basic` | `46px` | 일반 폼 입력, 기본 검색창 |
| `large` | `56px` | 강조된 입력, 주요 CTA와 함께 쓰는 입력 |

### 4.4 Horizontal Padding

입력 필드의 좌우 여백은 형태와 크기에 따라 다르게 적용한다.

| Type | Small | Basic | Large |
| --- | --- | --- | --- |
| `A` 일반 형태 | `12px` | `16px` | `16px` |
| `B` 라인 형태 | `12px` | `16px` | `16px` |
| `C` 라운드 형태 | `16px` | `20px` | `20px` |

### 4.5 Input With Right Button

입력 필드 우측에 버튼이 들어가는 경우, 텍스트 입력 영역과 버튼 사이의 간격은 스페이싱 토큰의 `space-2`를 사용한다.

| Area | Value | Token |
| --- | --- | --- |
| Text area to right button gap | `8px` | `space-2` |

버튼이 포함된 입력 필드는 텍스트가 버튼 영역과 겹치지 않도록 입력 영역의 오른쪽 padding 또는 button slot 영역을 별도로 확보한다.

### 4.6 Input With Icon

아이콘이 들어가는 경우 다음 기준을 따른다.

| Rule | Description |
| --- | --- |
| Icon position | 아이콘은 기본적으로 입력 필드의 우측에 배치한다. |
| Delete icon | 지우기 아이콘은 `Active` 상태에서만 노출한다. |
| Icon spacing | 텍스트 입력 영역과 아이콘 영역이 겹치지 않도록 우측 여백을 확보한다. |
| Icon interaction | 지우기, 비밀번호 보기/숨기기처럼 명확한 기능이 있는 아이콘만 클릭 가능하게 처리한다. |

아이콘과 버튼이 동시에 들어가는 복합 입력 필드는 우측 요소 간 간격을 `space-2` 기준으로 정리한다.

### 4.7 Password Strength Guide

비밀번호 상태 값은 아래 3가지 기준으로 사용한다.

| State | Color | HEX | Usage |
| --- | --- | --- | --- |
| `Good` | Green | `#04BA15` | 성공, 진행, 안전 등 긍정 상태 |
| `Weak` | Yellow | `#FF7A00` | 보통, 주의, 경고 등 보완이 필요한 상태 |
| `Error` | Red | `#FF2F57` | 금지, 실패, 위험 등 오류 상태 |

비밀번호 입력 필드는 상태에 따라 보더, 안내 문구, 보조 메시지 색상을 함께 변경한다. 상태 메시지는 짧고 직접적인 문장으로 작성한다.

### 4.8 Usage Notes

- 기본 입력은 `A` 타입과 `basic` 크기를 우선 사용한다.
- 검색, 필터처럼 부드러운 인상이 필요한 입력에는 `C` 타입을 사용할 수 있다.
- 화면 밀도가 높은 관리 도구나 테이블 내부 입력에는 `small` 크기를 사용한다.
- 주요 액션과 결합된 입력에는 `large` 크기를 사용할 수 있다.
- 입력 필드 내부의 임의 padding 값은 새로 만들지 않고, 이 파트에 정의된 좌우 여백을 우선 사용한다.
- 상태 색상은 직접 HEX를 반복 사용하기보다 Semantic 토큰으로 연결해 관리한다.

## 5. Input Component

본 파트는 `Input Box`를 실제 화면에서 사용하는 컴포넌트 단위로 조합하는 기준을 정의한다.  
`Input Box`가 입력 필드의 형태, 크기, 상태, 내부 여백을 정의한다면, `Input Component`는 라벨, 보조 설명, 상태 메시지, 아이콘, 버튼이 함께 배치되는 사용 패턴을 정의한다.

### 5.1 Component Structure

| Element | Required | Description |
| --- | --- | --- |
| Label | Optional | 입력 항목의 이름을 표시한다. |
| Input Box | Required | `A`, `B`, `C` 타입 중 하나를 사용한다. |
| Helper text | Optional | 입력 전 안내 또는 입력 규칙을 설명한다. |
| Status message | Optional | Good, Weak, Error 등 검증 결과를 표시한다. |
| Icon | Optional | 검색, 사용자, 파일, 삭제, 보기/숨기기 같은 보조 기능을 제공한다. |
| Button | Optional | 검색, 첨부, 확인처럼 입력값과 직접 연결된 액션을 제공한다. |

### 5.2 Component Font Size

Input Component의 기본 텍스트는 `14px`를 사용하며, `large` 크기에서는 `16px`를 사용한다.

| Size | Font Size | Usage |
| --- | --- | --- |
| `small` | `14px` | 작은 입력 컴포넌트, 보조 입력 |
| `basic` | `14px` | 기본 입력 컴포넌트 |
| `large` | `16px` | 강조 입력, 주요 액션과 결합된 입력 |

Helper text와 status message는 입력 텍스트보다 시각적 우선순위가 낮아야 한다. 단, 오류 메시지는 사용자가 즉시 인지할 수 있도록 상태 색상을 함께 사용한다.

### 5.3 Component Matrix

Input Component는 `Input Box`의 타입과 크기, 상태를 조합해 사용한다.

| Axis | Values |
| --- | --- |
| Type | `A` 일반, `B` 라인, `C` 라운드 |
| Size | `small`, `basic`, `large` |
| Interaction state | `Default`, `Hover`, `Focus`, `Active`, `Completion`, `Disabled` |
| Validation state | `Good`, `Weak`, `Error` |

`Hover`는 PC 환경에서만 사용한다. 모바일에서는 `Focus`, `Active`, `Completion`, `Disabled`, `Good`, `Weak`, `Error` 상태를 중심으로 표현한다.

### 5.4 Validation States

검증 상태는 입력 필드의 보더 또는 라인, 상태 메시지, 필요 시 아이콘 색상에 함께 반영한다.

| State | Meaning | Visual Rule | Message Example |
| --- | --- | --- | --- |
| `Good` | 올바른 입력 | Green 계열 보더/라인과 성공 메시지 | 정확한 정보입니다. |
| `Weak` | 확인이 필요한 입력 | Yellow/Orange 계열 보더/라인과 주의 메시지 | 동일한 정보입니다. |
| `Error` | 잘못된 입력 | Red 계열 보더/라인과 오류 메시지 | 잘못된 정보입니다. |

검증 메시지는 입력 필드 하단에 배치한다. 입력 전 안내 문구와 검증 메시지가 동시에 필요한 경우, 검증 메시지를 우선 노출한다.

### 5.5 Input Component With Icon

아이콘이 포함된 Input Component는 입력 목적을 빠르게 인지시키거나, 입력값을 보조 조작하기 위해 사용한다.

| Icon Type | Position | Usage |
| --- | --- | --- |
| Leading icon | Left | 사용자, 검색, 파일 등 입력 목적을 보조한다. |
| Trailing icon | Right | 지우기, 보기/숨기기, 첨부 등 입력값 조작 액션에 사용한다. |
| Delete icon | Right | `Active` 상태에서 입력값이 있을 때만 노출한다. |

아이콘이 있는 경우 텍스트 영역이 아이콘과 겹치지 않도록 좌우 padding을 확장하거나 icon slot을 별도로 확보한다. 아이콘과 텍스트 사이의 최소 간격은 `space-2`인 `8px`를 기준으로 한다.

### 5.6 Input Component With Button

입력 필드 안에 버튼이 들어가는 경우 검색, 첨부, 확인처럼 입력값과 직접 연결된 액션에만 사용한다.

| Button Pattern | Description | Example |
| --- | --- | --- |
| Icon button | 우측에 아이콘만 배치한다. | 검색 아이콘, 첨부 아이콘 |
| Filled icon button | 우측에 배경색이 있는 아이콘 버튼을 배치한다. | 강조 검색 버튼 |
| Text button | 우측에 텍스트 버튼을 배치한다. | `Search`, `File` |

입력 영역과 우측 버튼 사이의 간격은 `space-2`인 `8px`를 사용한다. 버튼이 포함된 경우 버튼 영역을 제외한 나머지 영역만 텍스트 입력 영역으로 계산한다.

### 5.7 Composition Rules

- 컴포넌트의 높이, 형태, 좌우 여백은 `Input Box` 규칙을 따른다.
- Input Component는 화면에서 재사용되는 조합 단위이며, 단순 입력 필드의 세부 수치는 `Input Box`를 기준으로 관리한다.
- 라벨, helper text, status message는 입력 필드와 명확한 관계를 갖도록 가까운 위치에 배치한다.
- 상태 메시지는 입력 필드 바로 아래에 배치하며, 여러 줄이 되더라도 다음 입력 컴포넌트와 겹치지 않도록 간격을 확보한다.
- 아이콘과 버튼은 입력 목적 또는 입력값 조작과 직접 관련이 있을 때만 사용한다.
- 하나의 입력 필드에 너무 많은 우측 요소를 넣지 않는다. 아이콘과 버튼이 동시에 필요한 경우 우선순위를 정해 하나의 주요 액션만 강조한다.

## 6. Check Box Component

본 파트는 디자인시스템에서 사용하는 체크박스 컴포넌트의 크기, 방향, 상태 기준을 정의한다.  
체크박스는 `basic`, `large` 2가지 크기를 기본으로 하며, 가로형과 세로형 레이아웃을 지원한다.

### 6.1 Component Sizes

| Size | Box Size | Usage |
| --- | --- | --- |
| `basic` | `20px × 20px` | 일반 폼, 설정 항목, 목록 선택 |
| `large` | `24px × 24px` | 터치 영역이 더 필요한 화면, 강조 선택 항목 |

컴포넌트 속성에서 크기를 변경할 수 있다. 기본값은 `basic`이며, 모바일이나 터치 환경에서는 `large` 사용을 우선 검토한다.

### 6.2 Layout Types

| Layout | Type | Description |
| --- | --- | --- |
| 가로형 A | `horizontal-a` | 체크박스가 왼쪽, 텍스트가 오른쪽에 배치되는 기본 가로형 |
| 가로형 B | `horizontal-b` | 가로형 A와 동일한 구조에서 선택 상태의 채움 표현을 더 강조하는 형태 |
| 세로형 A | `vertical-a` | 체크박스가 위, 텍스트가 아래에 배치되는 기본 세로형 |
| 세로형 B | `vertical-b` | 세로형 A와 동일한 구조에서 선택 상태의 채움 표현을 더 강조하는 형태 |

가로형은 폼, 약관, 목록형 선택 UI에 사용한다. 세로형은 옵션 카드, 아이콘형 선택, 좁은 영역에서 라벨을 아래에 배치해야 하는 경우 사용한다.

### 6.3 States

| State | Description |
| --- | --- |
| `Default` | 선택되지 않은 기본 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Selected` | 사용자가 선택한 상태 |
| `Disabled` | 선택할 수 없는 비활성 상태 |
| `Select-Disabled` | 선택된 값이지만 비활성화되어 변경할 수 없는 상태 |

`Hover`는 PC 환경에서만 사용한다. 모바일에서는 터치 후 `Selected`, `Disabled`, `Select-Disabled` 상태 중심으로 표현한다.

### 6.4 Visual Rules

| State | Box | Check Icon | Label |
| --- | --- | --- | --- |
| `Default` | Gray 계열 보더, 흰 배경 | 없음 | 기본 텍스트 색상 |
| `Hover` | Primary 계열 보더 | 없음 | 기본 텍스트 색상 |
| `Selected` | Primary 계열 보더 또는 채움 | Primary 또는 White 체크 | 기본 텍스트 색상 |
| `Disabled` | Disabled 배경과 보더 | 없음 | 비활성 텍스트 색상 |
| `Select-Disabled` | Disabled 배경과 보더 | 비활성 체크 | 비활성 텍스트 색상 |

가로형 B와 세로형 B는 선택 상태에서 체크박스 내부를 Primary 컬러로 채우고, 체크 아이콘은 White로 표시한다.

### 6.5 Label Rules

| Layout | Label Position | Usage |
| --- | --- | --- |
| 가로형 | 체크박스 오른쪽 | 일반 설명형 체크박스 |
| 세로형 | 체크박스 아래 | 옵션 선택형 UI, 좁은 카드형 UI |

라벨은 체크박스와 함께 하나의 클릭 영역으로 동작해야 한다. 라벨이 길어지는 경우 줄바꿈을 허용하되, 체크박스와 첫 줄의 정렬이 어색해지지 않도록 한다.

### 6.6 Usage Notes

- 단일 동의나 설정 항목에는 가로형 A를 우선 사용한다.
- 선택 상태를 더 강하게 보여야 하는 목록이나 옵션에는 가로형 B 또는 세로형 B를 사용할 수 있다.
- 여러 개의 체크박스를 세로로 나열할 때는 항목 간 간격을 스페이싱 토큰으로 통일한다.
- 체크박스는 복수 선택에 사용한다. 하나만 선택해야 하는 경우 라디오 컴포넌트를 사용한다.
- Disabled 상태에서도 현재 선택 여부가 필요한 경우 `Select-Disabled` 상태를 사용한다.
- 터치 환경에서는 시각적 박스 크기와 별개로 충분한 클릭 영역을 확보한다.

## 7. Radio Button Component

본 파트는 디자인시스템에서 사용하는 라디오 버튼 컴포넌트의 크기, 방향, 상태 기준을 정의한다.  
라디오 버튼은 체크박스와 동일하게 `basic`, `large` 2가지 크기를 사용하며, 여러 선택지 중 하나만 선택해야 하는 경우에 사용한다.

### 7.1 Component Sizes

| Size | Button Size | Usage |
| --- | --- | --- |
| `basic` | `20px × 20px` | 일반 폼, 설정 항목, 단일 선택 목록 |
| `large` | `24px × 24px` | 터치 영역이 더 필요한 화면, 강조 선택 항목 |

라디오 버튼의 크기 체계는 체크박스와 동일하게 유지한다.

### 7.2 Layout Types

| Layout | Type | Description |
| --- | --- | --- |
| 가로형 A | `horizontal-a` | 라디오 버튼이 왼쪽, 텍스트가 오른쪽에 배치되는 기본 가로형 |
| 가로형 B | `horizontal-b` | 가로형 A와 동일한 구조에서 선택 상태의 채움 표현을 더 강조하는 형태 |
| 세로형 A | `vertical-a` | 라디오 버튼이 위, 텍스트가 아래에 배치되는 기본 세로형 |
| 세로형 B | `vertical-b` | 세로형 A와 동일한 구조에서 선택 상태의 채움 표현을 더 강조하는 형태 |

가로형은 폼, 설정, 목록형 단일 선택 UI에 사용한다. 세로형은 옵션 카드나 좁은 영역에서 라벨을 아래에 배치해야 하는 경우 사용한다.

### 7.3 States

| State | Description |
| --- | --- |
| `Default` | 선택되지 않은 기본 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Selected` | 사용자가 선택한 상태 |
| `Disabled` | 선택할 수 없는 비활성 상태 |
| `Select-Disabled` | 선택된 값이지만 비활성화되어 변경할 수 없는 상태 |

`Hover`는 PC 환경에서만 사용한다. 모바일에서는 터치 후 `Selected`, `Disabled`, `Select-Disabled` 상태 중심으로 표현한다.

### 7.4 Visual Rules

| State | Button | Inner Dot | Label |
| --- | --- | --- | --- |
| `Default` | Gray 계열 원형 보더, 흰 배경 | 없음 | 기본 텍스트 색상 |
| `Hover` | Primary 계열 원형 보더 | 없음 | 기본 텍스트 색상 |
| `Selected` | Primary 계열 보더 또는 채움 | Primary 또는 White 점 | 기본 텍스트 색상 |
| `Disabled` | Disabled 배경과 보더 | 없음 | 비활성 텍스트 색상 |
| `Select-Disabled` | Disabled 배경과 보더 | 비활성 점 | 비활성 텍스트 색상 |

가로형 B와 세로형 B는 선택 상태에서 라디오 내부를 Primary 컬러로 채우고, 내부 점은 White로 표시한다.

### 7.5 Usage Notes

- 라디오 버튼은 하나의 그룹에서 하나만 선택할 수 있는 경우 사용한다.
- 복수 선택이 필요한 경우 체크박스 컴포넌트를 사용한다.
- 라디오 그룹에는 선택지의 의미를 설명하는 그룹 라벨을 제공한다.
- 라벨은 라디오 버튼과 함께 하나의 클릭 영역으로 동작해야 한다.
- Disabled 상태에서도 현재 선택 여부가 필요한 경우 `Select-Disabled` 상태를 사용한다.
- 터치 환경에서는 시각적 버튼 크기와 별개로 충분한 클릭 영역을 확보한다.

## 8. Textarea Component

본 파트는 디자인시스템에서 사용하는 여러 줄 입력 컴포넌트의 상태와 사용 기준을 정의한다.  
Textarea는 긴 문장이나 설명을 입력하는 영역에 사용하며, 글자 수 제한이 있는 경우 count 값을 함께 표시할 수 있다.

### 8.1 Component Sizes

| Size | Usage |
| --- | --- |
| `small` | 짧은 메모, 보조 설명 입력 |
| `basic` | 일반적인 여러 줄 입력 |
| `large` | 긴 설명, 상세 내용, 문의 내용 입력 |

Textarea의 폭은 배치되는 컨테이너에 맞춰 확장할 수 있으며, 높이는 입력 목적과 예상 문장 길이에 따라 선택한다.

### 8.2 States

| State | Description |
| --- | --- |
| `Default` | 입력 전 기본 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Focus` | 입력 영역이 포커스된 상태 |
| `Active` | 사용자가 입력 중인 상태 |
| `Completion` | 입력이 완료된 상태 |
| `Disabled` | 입력할 수 없는 비활성 상태 |
| `Good` | 올바른 입력 또는 검증 성공 상태 |
| `Weak` | 확인이 필요한 입력 상태 |
| `Error` | 잘못된 입력 또는 검증 실패 상태 |

`Hover`는 PC 환경에서만 사용한다. 모바일에서는 `Focus`, `Active`, `Completion`, `Disabled`, 검증 상태 중심으로 표현한다.

### 8.3 Count Guide

| Element | Description |
| --- | --- |
| Current count | 현재 입력된 글자 수 |
| Max count | 입력 가능한 최대 글자 수 |
| Format | `0 / 100`처럼 현재값과 최대값을 함께 표시한다. |

글자 수 제한이 있는 Textarea는 우측 하단에 count를 표시한다. 오류 상태에서는 상태 메시지를 우선적으로 인지할 수 있도록 배치하고, count는 입력 제한 확인용 보조 정보로 유지한다.

### 8.4 Usage Notes

- 한 줄 입력에는 Input Component를 사용하고, 여러 줄 입력에는 Textarea를 사용한다.
- 긴 설명 입력에는 `basic` 또는 `large` 크기를 우선 사용한다.
- 검증 상태는 보더 색상과 상태 메시지에 함께 반영한다.
- Disabled 상태에서는 입력값을 수정할 수 없으며, 필요 시 기존 내용을 읽을 수 있도록 충분한 대비를 유지한다.
- Textarea의 크기 변경이 필요한 경우 화면 레이아웃이 깨지지 않도록 최소 높이와 최대 높이를 함께 정의한다.

## 9. Quantity Button

본 파트는 디자인시스템에서 사용하는 숫자 증감 컴포넌트의 타입, 크기, 상태 기준을 정의한다.  
Quantity Button은 수량, 횟수, 인원수처럼 정해진 단위의 숫자를 증가 또는 감소시킬 때 사용한다.

### 9.1 Component Types

| Type | Description | Usage |
| --- | --- | --- |
| `A` | 숫자 양쪽에 원형 `-`, `+` 버튼을 배치하는 형태 | 간단한 수량 조절, 쇼핑/예약 수량 |
| `B` | `-`, 숫자, `+`를 하나의 작은 그룹으로 묶는 형태 | 좁은 영역의 수량 조절 |
| `C` | 숫자 입력 필드와 위/아래 스테퍼를 함께 사용하는 형태 | 직접 입력과 단계 조절이 모두 필요한 경우 |

### 9.2 Component Sizes

| Size | Usage |
| --- | --- |
| `small` | 좁은 목록, 테이블 내부, 보조 수량 조절 |
| `basic` | 기본 수량 조절 |
| `large` | 터치 영역이 더 필요한 화면, 강조 수량 조절 |

### 9.3 States

| State | Description |
| --- | --- |
| `Default` | 기본 조작 가능 상태 |
| `Active` | 현재 값이 활성화되어 조작 중인 상태 |
| `Disabled` | 값을 변경할 수 없는 상태 |

감소 또는 증가가 불가능한 경계값에서는 해당 방향의 버튼만 Disabled 처리할 수 있다. 예를 들어 최소값에 도달하면 `-` 버튼을 비활성화한다.

### 9.4 Usage Notes

- 수량을 빠르게 조절해야 하는 경우 `A` 타입을 우선 사용한다.
- 공간이 좁은 테이블, 리스트, 카드 내부에서는 `B` 타입을 사용할 수 있다.
- 사용자가 숫자를 직접 입력해야 하는 경우 `C` 타입을 사용한다.
- 최소값, 최대값, 증가 단위를 컴포넌트 속성으로 정의한다.
- 숫자 값은 항상 중앙 정렬하고, 버튼 영역과 숫자 영역이 명확히 구분되도록 한다.
- Disabled 상태에서도 현재 값을 읽을 수 있어야 한다.

## 10. Toggle Component

본 파트는 디자인시스템에서 사용하는 토글 스위치의 타입, 크기, 상태 기준을 정의한다.  
Toggle은 켜짐/꺼짐처럼 즉시 전환되는 이진 설정에 사용한다.

### 10.1 Component Types

| Type | Description | Usage |
| --- | --- | --- |
| `A` | pill 형태의 기본 스위치 | 일반 설정 on/off |
| `B` | 라인 위의 원형 핸들을 이동시키는 형태 | 슬라이더에 가까운 설정 표현 |
| `C` | 작은 트랙과 핸들을 조합한 컴팩트 형태 | 좁은 영역의 on/off 설정 |

### 10.2 Component Sizes

| Size | Usage |
| --- | --- |
| `small` | 좁은 설정 목록, 테이블 내부 |
| `basic` | 기본 토글 스위치 |
| `large` | 터치 영역이 더 필요한 화면, 강조 설정 |

### 10.3 States

| State | Description |
| --- | --- |
| `Default` | 꺼짐 상태 |
| `Active` | 켜짐 상태 |
| `Disabled` | 조작할 수 없는 비활성 상태 |

Active 상태는 Primary 컬러를 사용해 켜짐 여부를 명확하게 보여준다. Disabled 상태는 조작 불가 상태가 드러나도록 Gray 계열 배경과 낮은 대비를 사용한다.

### 10.4 Usage Notes

- 즉시 적용되는 on/off 설정에는 Toggle을 사용한다.
- 여러 선택지 중 하나를 고르는 경우에는 Radio Button을 사용한다.
- 여러 항목을 복수 선택하는 경우에는 Check Box를 사용한다.
- Toggle은 상태 변경 결과가 즉시 이해되는 항목에만 사용한다.
- 중요한 설정을 변경하는 경우에는 상태 변경 후 안내 메시지나 확인 피드백을 제공한다.
- 라벨은 토글의 의미를 명확하게 설명해야 하며, `켜기/끄기`처럼 상태만 반복하는 문구는 피한다.

## 11. Select Box

본 파트는 디자인시스템에서 사용하는 Select Box의 형태, 크기, 상태, 옵션 목록 기준을 정의한다.  
Select Box는 사용자가 정해진 선택지 중 하나를 고르는 입력 컴포넌트이며, 크기와 좌우 여백은 Input Box와 동일한 기준을 따른다.

### 11.1 Select Types

| Type | Name | Description |
| --- | --- | --- |
| `A` | 일반 형태 | 외곽선이 있는 기본 Select Box. 가장 일반적인 선택 UI에 사용한다. |
| `B` | 라인 형태 | 하단 라인만 사용하는 Select Box. 화면 밀도가 높거나 간결한 폼에 사용한다. |
| `C` | 라운드 형태 | 둥근 pill 형태의 Select Box. 검색 필터, 태그형 필터, 부드러운 인상의 선택 UI에 사용한다. |

### 11.2 Select Sizes

Select Box는 Input Box와 동일하게 `small`, `basic`, `large` 3가지 크기를 사용한다.

| Size | Height | Usage |
| --- | --- | --- |
| `small` | `36px` | 좁은 필터, 테이블 내부 선택, 보조 선택 |
| `basic` | `46px` | 일반 폼 선택, 기본 필터 |
| `large` | `56px` | 강조 선택, 주요 검색 조건 |

### 11.3 Horizontal Padding

Select Box의 좌우 여백은 Input Box와 동일한 기준을 따른다.

| Type | Small | Basic | Large |
| --- | --- | --- | --- |
| `A` 일반 형태 | `12px` | `16px` | `16px` |
| `B` 라인 형태 | `12px` | `16px` | `16px` |
| `C` 라운드 형태 | `16px` | `20px` | `20px` |

우측에는 드롭다운 화살표 영역이 필요하므로, 선택된 텍스트가 아이콘과 겹치지 않도록 별도 icon slot 또는 오른쪽 여백을 확보한다.

### 11.4 States

| State | Description |
| --- | --- |
| `Default` | 선택 전 기본 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Focus` | Select Box가 포커스된 상태 |
| `Active` | 드롭다운 목록이 열린 상태 |
| `Completion` | 선택이 완료된 상태 |
| `Disabled` | 선택할 수 없는 비활성 상태 |

모바일에서는 `hover` 상호작용을 사용하지 않는다. 터치 환경에서는 `focus`, `active`, `completion`, `disabled` 상태를 중심으로 표현한다.

### 11.5 Dropdown List

| Element | Description |
| --- | --- |
| Trigger | 현재 선택값 또는 placeholder와 드롭다운 화살표를 표시한다. |
| Option list | 선택 가능한 옵션을 세로 목록으로 표시한다. |
| Option hover | PC 환경에서 옵션에 마우스를 올렸을 때 배경색으로 강조한다. |
| Selected option | 현재 선택된 옵션을 목록 안에서 구분해 표시한다. |

드롭다운이 열린 `Active` 상태에서는 화살표 방향을 위로 변경한다. 옵션 목록은 Select Box의 너비를 기준으로 정렬하며, 너무 긴 옵션은 줄바꿈 또는 말줄임 기준을 별도로 정한다.

### 11.6 Select With Icon

아이콘이 포함된 Select Box는 선택지의 성격을 빠르게 구분해야 할 때 사용한다.

| Area | Small | Basic | Large | Description |
| --- | --- | --- | --- | --- |
| Text to arrow gap | `10px` | `10px` | `10px` | 선택 텍스트와 우측 화살표 사이의 최소 간격 |
| A/B icon slot | `20px` | `24px` | `24px` | 일반/라인 형태에서 좌측 아이콘 영역 |
| C icon slot | `20px` | `20px` | `24px` | 라운드 형태에서 좌측 아이콘 영역 |

아이콘 이미지는 정사각형으로 제작해 사용한다. 옵션 목록 안에서도 동일한 아이콘 크기와 정렬 기준을 유지한다.

### 11.7 Usage Notes

- 사용자가 직접 입력해야 하는 경우에는 Input Component를 사용하고, 정해진 목록에서 선택하는 경우 Select Box를 사용한다.
- Select Box의 크기, 형태, 좌우 여백은 Input Box와 동일한 기준으로 관리한다.
- 선택지가 5개 이하이고 한눈에 비교해야 하는 경우 Radio Button 사용을 검토한다.
- 선택지가 많거나 공간을 절약해야 하는 경우 Select Box를 사용한다.
- Disabled 상태에서도 현재 선택값은 읽을 수 있어야 한다.
- 옵션 목록은 trigger와 시각적으로 연결되어야 하며, 열린 상태에서 다른 입력 컴포넌트와 겹치지 않도록 z-index와 배치 기준을 정한다.

## 12. Button Component

본 파트는 디자인시스템에서 사용하는 버튼의 크기, 여백, 상태, 아이콘 조합, 스타일 패밀리 기준을 정의한다.  
모든 버튼은 Hover, Completion 등 상태 변화에 대응할 수 있도록 border 기준을 포함하며, 좌측 아이콘과 우측 아이콘은 컴포넌트 속성에서 서로 교체하거나 숨길 수 있다.

### 12.1 Button Sizes

버튼은 `large`, `basic`, `small`, `x-small` 4가지 크기를 제공하며, 기본 크기는 `basic`이다.

| Size | Height | Horizontal Padding | Usage |
| --- | --- | --- | --- |
| `large` | `56px` | `28px` | 주요 CTA, 넓은 화면의 강조 버튼 |
| `basic` | `46px` | `24px` | 기본 버튼 |
| `small` | `36px` | `20px` | 보조 버튼, 테이블/카드 내부 액션 |
| `x-small` | `26px` | `12px` | 좁은 영역의 보조 액션, 태그형 액션 |

### 12.2 Icon Spacing

| Rule | Value |
| --- | --- |
| Text to icon gap | `4px` |

아이콘이 포함된 버튼은 아이콘과 텍스트 사이 간격을 `4px`로 통일한다. 좌측 아이콘과 우측 아이콘은 동일한 간격 규칙을 사용한다.

### 12.3 Button States

| State | Description |
| --- | --- |
| `Default` | 기본 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Completion` | 클릭 또는 처리 완료 상태 |
| `Disabled` | 클릭할 수 없는 비활성 상태 |
| `Progress` | 작업이 진행 중인 로딩 상태 |
| `Left Icon` | 왼쪽 아이콘이 포함된 상태 |
| `Right Icon` | 오른쪽 아이콘이 포함된 상태 |

`Progress` 상태에서는 텍스트 대신 로딩 인디케이터를 표시할 수 있다. 이때 버튼의 높이와 최소 너비는 유지해 레이아웃이 흔들리지 않도록 한다.

### 12.4 Shape And Style Families

| Family | Variants | Shape | Description |
| --- | --- | --- | --- |
| Basic | `button_basic_a`, `button_basic_b`, `button_basic_c` | Rect | 사각형에 가까운 기본 버튼 패밀리 |
| Line | `button_line_a`, `button_line_b` | Rect outline | 외곽선 중심의 버튼 패밀리 |
| Round | `button_round_a`, `button_round_b`, `button_round_c` | Pill | 완전 라운드 형태의 버튼 패밀리 |
| Round Line | `button_round_line_a`, `button_round_line_b` | Pill outline | 라운드 외곽선 버튼 패밀리 |
| Text | `button_text` | Text only | 배경 없이 텍스트 중심의 버튼 |

### 12.5 Basic Button Variants

| Variant | Default | Hover | Completion | Disabled |
| --- | --- | --- | --- | --- |
| `button_basic_a` | Primary filled | Lighter primary filled | Primary filled | Disabled background |
| `button_basic_b` | Light primary background with primary border/text | Primary filled | Primary filled | Disabled background |
| `button_basic_c` | Gray filled | Primary filled | Primary filled | Disabled background |

Basic 버튼은 일반적인 CTA와 주요 액션에 사용한다. `button_basic_a`는 가장 강한 강조 버튼이며, `button_basic_b`는 기본 상태에서 부담이 낮은 강조 버튼으로 사용한다. `button_basic_c`는 기본 상태에서는 중립적이고 hover 또는 completion에서 강조되는 액션에 사용한다.

### 12.6 Line Button Variants

| Variant | Default | Hover | Completion | Disabled |
| --- | --- | --- | --- | --- |
| `button_line_a` | Neutral outline | Primary outline | Primary outline | Disabled background |
| `button_line_b` | Neutral outline | Primary filled | Primary outline | Disabled background |

Line 버튼은 보조 액션, 취소, 필터, 서브 액션처럼 Primary filled 버튼보다 낮은 우선순위의 액션에 사용한다.

### 12.7 Round Button Variants

| Variant | Default | Hover | Completion | Disabled |
| --- | --- | --- | --- | --- |
| `button_round_a` | Primary filled | Lighter primary filled | Primary filled | Disabled background |
| `button_round_b` | Light primary background with primary border/text | Primary filled | Primary filled | Disabled background |
| `button_round_c` | Gray filled | Primary filled | Primary filled | Disabled background |

Round 버튼은 검색, 필터, 태그형 액션, 모바일 하단 액션처럼 부드러운 형태가 필요한 곳에 사용한다.

### 12.8 Round Line Button Variants

| Variant | Default | Hover | Completion | Disabled |
| --- | --- | --- | --- | --- |
| `button_round_line_a` | Neutral round outline | Primary round outline | Primary round outline | Disabled background |
| `button_round_line_b` | Neutral round outline | Primary filled | Primary round outline | Disabled background |

Round Line 버튼은 라운드 형태는 유지하되 시각적 강조를 낮춰야 하는 보조 액션에 사용한다.

### 12.9 Text Button

| Size | States | Usage |
| --- | --- | --- |
| `basic` | `Default`, `Hover`, `Completion`, `Disabled`, `Progress`, `Left Icon`, `Right Icon` | 일반 텍스트 액션 |
| `small` | `Default`, `Hover`, `Completion`, `Disabled`, `Progress`, `Left Icon`, `Right Icon` | 작은 영역의 텍스트 액션 |

Text 버튼은 배경 없이 텍스트와 underline 중심으로 표현한다. 중요도가 낮은 액션, 문장 안의 링크형 액션, 보조 이동에 사용한다.

### 12.10 Icon Rules

| Pattern | Description |
| --- | --- |
| Left Icon | 아이콘을 텍스트 왼쪽에 배치한다. |
| Right Icon | 아이콘을 텍스트 오른쪽에 배치한다. |
| Icon only progress | Progress 상태에서는 로딩 인디케이터만 표시할 수 있다. |

아이콘은 버튼 의미를 보조할 때만 사용한다. 아이콘과 텍스트가 같은 의미를 반복하지 않도록 하고, 검색, 이동, 다운로드처럼 행동을 빠르게 인지시키는 경우에 우선 사용한다.

### 12.11 Usage Notes

- 기본 버튼 크기는 `basic`을 사용한다.
- 가장 중요한 액션은 `button_basic_a` 또는 `button_round_a`를 사용한다.
- 보조 액션은 Line 또는 Round Line 패밀리를 우선 검토한다.
- 텍스트 버튼은 시각적 강조가 낮은 링크형 액션에 사용한다.
- 한 화면에서 Primary filled 버튼을 과도하게 반복하지 않는다.
- Disabled 상태에서는 클릭 이벤트를 제거하고, 시각적으로 비활성 상태가 명확해야 한다.
- 버튼 안의 텍스트는 한 줄을 기본으로 하며, 줄바꿈이 필요한 긴 문구는 버튼 라벨을 짧게 다시 작성한다.

## 13. Badge Icon

본 파트는 디자인시스템에서 사용하는 Badge Icon의 타입, 색상 의미, 사용 기준을 정의한다.  
Badge Icon은 프로모션, 상품 상태, 짧은 상태값을 알리는 수단으로 사용하며, 작은 버튼처럼 보일 수 있지만 기본적으로 정보 표시 목적을 가진다.

### 13.1 Badge Types

| Type | Name | Description |
| --- | --- | --- |
| `A` | Line | 배경 없이 보더와 텍스트 컬러로 상태를 표현한다. |
| `B` | Fill | 배경색과 흰색 텍스트로 상태를 더 강하게 표현한다. |

### 13.2 Badge Padding

| Rule | Value |
| --- | --- |
| Horizontal padding | `12px` |

좌우 여백은 `12px`를 기본으로 하며, 사용 공간이나 텍스트 길이에 따라 조정할 수 있다. 높이는 텍스트 크기와 내부 padding에 맞춰 컴팩트하게 유지한다.

### 13.3 Badge Color Roles

| Role | Meaning | Example |
| --- | --- | --- |
| Gray | 일반 상태, 셀링 아이콘 | 셀링아이콘 |
| Blue | 추천, 베스트, 주요 강조 | 베스트 |
| Red | 핫딜, 긴급성, 강한 주목 | 핫세일 |
| Green | 상품 상태, 안정적 긍정 정보 | 사은품 |
| Purple | 특별 혜택, 이벤트성 강조 | 특가세일 |
| Orange | 구매 유도, 재구매, 전환 강조 | 재구매 |

Line 타입은 색상 보더와 텍스트를 사용하고, Fill 타입은 같은 의미의 배경색과 대비되는 텍스트를 사용한다.

### 13.4 Usage Notes

- Badge Icon은 짧은 단어 또는 매우 짧은 문구로 작성한다.
- 클릭 액션이 필요한 경우 Button 또는 Tag의 액션형 패턴을 사용한다.
- 한 화면에서 너무 많은 색상의 Badge를 동시에 사용하지 않는다.
- Badge가 상품 상태를 나타내는 경우 같은 상태에는 항상 같은 색상 역할을 사용한다.
- 프로모션 강조가 필요한 경우 Fill 타입을 사용하고, 일반 정보 표시는 Line 타입을 우선 사용한다.

## 14. Tag

본 파트는 디자인시스템에서 사용하는 Tag의 형태와 사용 기준을 정의한다.  
Tag는 사용자에게 한 단어 또는 짧은 키워드로 의미를 전달할 때 사용하며, 분류, 필터, 위치, 키워드, 선택된 조건을 간단히 표시한다.

### 14.1 Tag Types

| Type | Description | Usage |
| --- | --- | --- |
| Text tag | 텍스트만 포함하는 기본 태그 | 키워드, 분류 표시 |
| Icon tag | 아이콘과 텍스트를 함께 표시하는 태그 | 위치, 상태, 속성 표시 |
| Removable tag | 텍스트와 삭제 아이콘을 함께 표시하는 태그 | 선택된 필터, 제거 가능한 조건 |
| Elevated tag | 그림자를 사용해 떠 있는 형태로 표현하는 태그 | 지도, 카드 위의 강조 태그 |

### 14.2 Tag Elements

| Element | Required | Description |
| --- | --- | --- |
| Label | Required | 태그의 의미를 전달하는 짧은 텍스트 |
| Prefix icon | Optional | 위치, 상태, 카테고리 등 의미를 보조하는 아이콘 |
| Remove icon | Optional | 선택된 태그를 제거하는 아이콘 |
| Border | Optional | 태그의 범위를 구분하는 외곽선 |
| Shadow | Optional | 태그를 배경에서 띄워 보여야 할 때 사용 |

### 14.3 Visual Rules

| Pattern | Visual Rule |
| --- | --- |
| Default | 흰 배경, Gray 계열 보더, 중립 텍스트 |
| Active | Primary 계열 보더와 텍스트 |
| Icon | 아이콘과 텍스트 사이 간격을 일정하게 유지 |
| Removable | 삭제 아이콘을 우측에 배치 |
| Elevated | 작은 그림자를 사용해 배경과 분리 |

Tag는 버튼처럼 보일 수 있지만 기본 목적은 정보 표시다. 삭제 아이콘이 있는 경우에만 제거 액션을 제공하고, 그 외에는 클릭 가능한 버튼처럼 사용하지 않는다.

### 14.4 Usage Notes

- Tag 라벨은 한 단어 또는 짧은 구문을 사용한다.
- 여러 태그를 나열할 때는 줄바꿈이 가능하도록 구성한다.
- 선택된 필터를 표시할 때는 Removable tag를 사용한다.
- 위치나 속성처럼 의미 보조가 필요한 경우 Prefix icon을 사용한다.
- Elevated tag는 지도, 이미지, 카드 위처럼 배경과 분리해야 하는 상황에만 사용한다.
- 삭제 아이콘은 충분한 클릭 영역을 확보하고, 라벨 텍스트와 겹치지 않게 배치한다.

## 15. Alert / Result / Confirm

본 파트는 디자인시스템에서 사용하는 알림, 경고, 완료, 확인 모달의 구조와 상태 기준을 정의한다.  
Alert / Result / Confirm은 사용자에게 중요한 정보를 전달하거나, 작업 결과를 보여주거나, 사용자의 최종 확인을 받아야 할 때 사용한다.

### 15.1 Modal Types

| Type | Description | Usage |
| --- | --- | --- |
| `Alert` | 정보, 경고, 진행 상태를 알리는 모달 | 안내, 경고, 로딩 |
| `Result` | 작업 결과를 강조해서 보여주는 모달 | 성공, 실패, 완료, 결과 안내 |
| `Confirm` | 사용자의 선택 또는 확인을 요구하는 모달 | 삭제 확인, 저장 확인, 이동 확인 |

### 15.2 Theme Modes

| Mode | Description |
| --- | --- |
| `Light` | 밝은 배경 위에서 사용하는 기본 모달 |
| `Dark` | 어두운 배경 또는 다크모드에서 사용하는 모달 |

Light와 Dark 모드는 동일한 정보 구조를 유지하되, 배경/텍스트/버튼/아이콘의 대비를 각 모드에 맞게 조정한다.

### 15.3 Content Layouts

| Layout | Description | Usage |
| --- | --- | --- |
| Basic | 아이콘 없이 제목, 설명, 버튼으로 구성 | 일반 알림, 기본 확인 |
| Inline icon | 제목 왼쪽에 작은 상태 아이콘을 배치 | 정보, 경고, 성공, 로딩 상태를 빠르게 표시 |
| Center result | 상단 중앙에 큰 상태 아이콘을 배치하고 내용을 중앙 정렬 | 결과 안내, 성공/실패 완료 화면 |

Basic과 Inline icon 레이아웃은 본문을 왼쪽 정렬한다. Center result 레이아웃은 아이콘, 제목, 설명, 버튼 그룹을 중앙 정렬한다.

### 15.4 Status Types

| Status | Meaning | Visual Role |
| --- | --- | --- |
| `Info` | 일반 안내 | Blue 계열 아이콘과 확인 버튼 |
| `Warning` | 주의, 위험, 실패 가능성 | Red 계열 배경/아이콘/확인 버튼 |
| `Loading` | 처리 중 | Loading indicator와 Blue 계열 확인 버튼 |
| `Success` | 성공, 완료 | Green 계열 아이콘과 확인 버튼 |
| `Error` | 실패, 삭제, 위험 결과 | Red 계열 아이콘과 확인 버튼 |

상태 색상은 아이콘, 강조 배경, 확인 버튼에 일관되게 반영한다. Cancel 버튼은 보조 액션으로 유지하고, 주요 확인 버튼만 상태 색상으로 강조한다.

### 15.5 Modal Structure

| Element | Required | Description |
| --- | --- | --- |
| Container | Required | 모달 콘텐츠를 감싸는 영역 |
| Close button | Optional | 우측 상단 닫기 버튼 |
| Status icon | Optional | 상태를 시각적으로 전달하는 아이콘 |
| Title | Required | 알림 또는 결과의 핵심 메시지 |
| Description | Optional | 사용자가 이해해야 할 상세 설명 |
| Button group | Optional | Cancel, Ok 등 사용자 액션 |

확인 또는 취소가 필요한 Confirm 모달은 버튼 그룹을 포함한다. 단순 정보성 Alert는 닫기 버튼 또는 Ok 버튼 중 하나만 사용할 수 있다.

### 15.6 Button Rules

| Button | Role | Usage |
| --- | --- | --- |
| `Cancel` | Secondary | 취소, 닫기, 이전으로 돌아가기 |
| `Ok` | Primary | 확인, 진행, 완료 |

버튼은 우측 하단에 배치하는 것을 기본으로 한다. Center result 레이아웃에서는 버튼 그룹을 중앙 하단에 배치한다. 위험하거나 실패와 관련된 확인 버튼은 Red 계열을 사용한다.

### 15.7 Usage Notes

- Alert는 정보를 알려주는 목적, Confirm은 사용자의 결정을 받는 목적, Result는 작업 결과를 보여주는 목적으로 구분한다.
- 중요한 경고나 실패 상황에서는 상태 아이콘을 함께 사용한다.
- Loading 상태에서는 진행 중임을 명확하게 보여주고, 중복 클릭이 발생하지 않도록 주요 액션을 제어한다.
- 모달 제목은 짧고 명확하게 작성한다.
- 설명 문구는 사용자가 다음 행동을 결정할 수 있을 만큼만 제공한다.
- 닫기 버튼, Cancel, Ok가 동시에 있을 경우 각 액션의 의미가 겹치지 않게 한다.
- Dark 모드에서는 텍스트 대비와 버튼 대비가 충분히 확보되어야 한다.

## 16. Modal

본 파트는 디자인시스템에서 사용하는 Modal 컨테이너의 구조, 반응형 동작, Light/Dark 모드 기준을 정의한다.  
Modal은 화면 위에 별도 레이어를 띄워 사용자의 집중이 필요한 콘텐츠, 입력, 목록, 확인 작업을 제공할 때 사용한다.

### 16.1 Modal Relationship

| Component | Role |
| --- | --- |
| `Modal` | 콘텐츠를 담는 공통 컨테이너 |
| `Alert / Result / Confirm` | Modal을 기반으로 한 메시지/결과/확인 패턴 |

Alert / Result / Confirm은 Modal의 특수한 사용 예시다. 일반 Modal은 표, 검색, 폼, 상세 정보처럼 더 복합적인 콘텐츠를 포함할 수 있다.

### 16.2 Responsive Rules

| Environment | Rule |
| --- | --- |
| PC | PC 버전은 Mobile과 같은 구조를 사용하되, 화면 크기에 맞춰 더 넓은 컨테이너를 사용할 수 있다. |
| Mobile | Mobile Modal은 모바일 화면에서만 사용한다. |
| Responsive | PC 팝업도 화면이 줄어들면 Mobile Modal과 같은 화면 구조로 전환한다. |

반응형으로 크기가 줄어들 때는 Modal 내부 콘텐츠가 잘리지 않도록 스크롤 영역과 버튼 영역을 분리한다.

### 16.3 Modal Sizes

| Size | Description | Usage |
| --- | --- | --- |
| `large` | 넓은 콘텐츠를 담는 큰 모달 | 표, 검색 결과, 복합 폼 |
| `basic` | 일반적인 확인 또는 입력 모달 | 기본 폼, 간단한 상세 정보 |
| `mobile` | 모바일 화면 전용 모달 | 모바일 하단 또는 중앙 모달 |

Modal 크기는 콘텐츠의 복잡도에 따라 선택한다. 단순 메시지는 Alert / Result / Confirm 패턴을 우선 사용하고, 목록이나 폼이 포함되면 일반 Modal을 사용한다.

### 16.4 Theme Modes

| Mode | Description |
| --- | --- |
| `Light` | 밝은 배경과 어두운 텍스트를 사용하는 기본 모드 |
| `Dark` | 어두운 배경과 밝은 텍스트를 사용하는 다크 모드 |

Light와 Dark 모드는 동일한 레이아웃을 유지한다. 배경, 보더, 테이블, 입력, 버튼, 페이지네이션 등 내부 컴포넌트도 각 모드에 맞는 토큰을 사용한다.

### 16.5 Modal Structure

| Element | Required | Description |
| --- | --- | --- |
| Overlay | Required | 배경 콘텐츠와 Modal을 분리하는 반투명 레이어 |
| Container | Required | Modal 전체를 감싸는 영역 |
| Header | Optional | 제목과 닫기 버튼을 포함하는 상단 영역 |
| Drag handle | Mobile only | 모바일 모달 상단의 핸들 |
| Body | Required | 표, 폼, 메시지, 검색 등 주요 콘텐츠 영역 |
| Footer | Optional | 주요 액션 버튼을 배치하는 하단 영역 |
| Close button | Optional | Modal을 닫는 우측 상단 버튼 |

Header와 Footer는 콘텐츠와 시각적으로 분리한다. Body가 길어질 경우 Body만 스크롤되도록 하고, Header와 Footer는 고정할 수 있다.

### 16.6 Footer Button Layout

| Layout | Description | Usage |
| --- | --- | --- |
| Right aligned | 버튼을 우측 하단에 배치 | PC Modal의 기본 액션 영역 |
| Full width stacked | 버튼을 세로로 전체 너비 배치 | Mobile Modal 또는 강한 선택 유도 |
| Inline pair | 취소/확인 버튼을 가로로 배치 | 기본 확인 액션 |

PC Modal은 우측 하단 버튼 배치를 기본으로 한다. Mobile Modal은 화면 폭이 좁기 때문에 버튼을 전체 너비로 쌓아 배치할 수 있다.

### 16.7 Content Patterns

| Pattern | Description |
| --- | --- |
| Search + table | 검색 입력, 정렬/필터, 테이블, 페이지네이션을 포함하는 목록형 Modal |
| Result content | 상태 아이콘, 제목, 설명, 버튼을 포함하는 결과형 Modal |
| Form content | 입력 컴포넌트와 저장/취소 버튼을 포함하는 입력형 Modal |

검색과 테이블이 포함된 Modal은 입력, Select Box, Check Box, Pagination, Button 등 기존 컴포넌트 규칙을 그대로 따른다.

### 16.8 Usage Notes

- Modal은 사용자의 현재 흐름을 잠시 멈추게 하므로 중요한 작업에만 사용한다.
- 단순 안내는 Alert, 작업 결과는 Result, 사용자 확인은 Confirm 패턴을 우선 사용한다.
- Modal이 열린 동안 배경 콘텐츠는 조작되지 않아야 한다.
- 닫기 버튼, Cancel, ESC, overlay click 등의 닫기 정책은 작업 위험도에 따라 정한다.
- 삭제, 결제, 저장 취소처럼 위험한 작업은 overlay click으로 닫히지 않게 할 수 있다.
- Mobile Modal에서는 콘텐츠가 화면 밖으로 밀리지 않도록 Body 스크롤과 Footer 고정을 우선 고려한다.
- Dark 모드에서는 Overlay와 Modal Container의 대비를 충분히 확보한다.

## 17. Table / List

본 파트는 디자인시스템에서 사용하는 Table과 List 형태의 데이터 표시 기준을 정의한다.  
Table / List는 Light와 Dark 모드를 모두 지원하며, 행 선택, 정렬, 파일, 멤버, 액션, 이미지 썸네일 등 다양한 정보를 구조적으로 표시할 때 사용한다.

### 17.1 Table Types

| Type | Description | Usage |
| --- | --- | --- |
| Basic table | 헤더와 셀 구분선이 있는 기본 테이블 | 관리자 목록, 데이터 관리 화면 |
| Member table | 멤버 아바타 또는 담당자 정보를 포함하는 테이블 | 담당자 목록, 협업 데이터 |
| Media table | 썸네일 이미지와 제목/날짜 정보를 함께 표시하는 테이블 | 콘텐츠 목록, 게시물 관리 |
| Card list | 각 행을 카드처럼 분리한 리스트 | 사용자 목록, 메시지 목록, 모바일 친화 목록 |
| Notice list | 날짜, 제목, 썸네일을 강조하는 게시판형 리스트 | 공지사항, 뉴스, 이벤트 목록 |

### 17.2 Theme Modes

| Mode | Description |
| --- | --- |
| `Light` | 밝은 배경, Gray 계열 헤더, 밝은 구분선, 어두운 텍스트를 사용한다. |
| `Dark` | 어두운 배경, Dark surface 헤더, 낮은 대비 구분선, 밝은 텍스트를 사용한다. |

Light와 Dark는 동일한 컬럼 구조와 인터랙션을 유지한다. 배경, 보더, 텍스트, hover, selected, checkbox, icon, badge, button은 각 모드에 맞는 Semantic 토큰을 사용한다.

### 17.3 Table Structure

| Element | Required | Description |
| --- | --- | --- |
| Header row | Optional | 컬럼명, 전체 선택, 정렬 상태를 표시한다. |
| Body row | Required | 실제 데이터 행을 표시한다. |
| Checkbox cell | Optional | 행 선택 또는 전체 선택을 제공한다. |
| Number cell | Optional | 순번 또는 식별 번호를 표시한다. |
| Title cell | Required | 주요 텍스트, 보조 텍스트, 뱃지, 첨부 아이콘을 표시한다. |
| File cell | Optional | 파일 종류 아이콘 또는 첨부 상태를 표시한다. |
| Date cell | Optional | 날짜와 시간을 표시한다. |
| Member cell | Optional | 아바타, 이니셜, 멤버 그룹을 표시한다. |
| Action cell | Optional | 보기, 수정, 삭제 등 행 단위 액션을 제공한다. |

### 17.4 Row States

| State | Description |
| --- | --- |
| `Default` | 기본 행 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 행 강조 상태 |
| `Selected` | 체크박스 선택 또는 현재 선택된 행 상태 |
| `Disabled` | 조작할 수 없는 행 상태 |
| `Empty` | 데이터가 없을 때의 빈 상태 |

선택된 행은 Light 모드에서 연한 Blue 계열 배경을 사용하고, Dark 모드에서는 Dark surface 위에서 구분 가능한 selected surface를 사용한다.

### 17.5 Cell Content Rules

| Content | Rule |
| --- | --- |
| Title | 한 줄 표시를 기본으로 하며, 길면 말줄임 처리한다. 필요 시 보조 텍스트를 아래 줄에 배치한다. |
| Badge | 제목 옆에 상태를 보조하는 짧은 Badge를 배치할 수 있다. |
| File icon | 파일 종류를 아이콘으로 표시하되, 너무 많은 아이콘은 요약 표시를 검토한다. |
| Attachment | 첨부가 있는 경우 paperclip 아이콘으로 표시할 수 있다. |
| Member | 아바타는 겹쳐 배치할 수 있으며, 이니셜 아바타를 fallback으로 사용한다. |
| Action | 행 단위 액션은 아이콘 버튼 또는 small 버튼으로 제공한다. |
| Date | `yyyy-00-00 / 00:00`처럼 날짜와 시간을 일관된 포맷으로 표시한다. |

### 17.6 Media And Avatar Rules

| Pattern | Description |
| --- | --- |
| Circle thumbnail | 사용자, 프로필, 아바타에 사용한다. |
| Square thumbnail | 콘텐츠 썸네일, 이미지 파일, 게시물 대표 이미지에 사용한다. |
| Placeholder thumbnail | 이미지가 없을 때 기본 placeholder를 사용한다. |
| Initial avatar | 이미지가 없는 멤버를 이니셜로 표시한다. |

썸네일과 아바타는 테이블 행 높이를 과도하게 늘리지 않도록 크기를 제한한다. Dark 모드에서는 placeholder, avatar border, shadow가 배경과 구분되도록 조정한다.

### 17.7 Card List Rules

Card list는 행 전체를 하나의 카드처럼 보여주는 목록형 패턴이다.

| Element | Description |
| --- | --- |
| Selection | 좌측 체크박스로 행 선택을 제공한다. |
| Favorite | 별 아이콘 등 보조 상태를 표시할 수 있다. |
| Avatar | 사용자 또는 항목 대표 이미지를 표시한다. |
| Main text | 사용자명, 제목 등 핵심 정보를 표시한다. |
| Sub text | 이메일, 날짜, 설명 등 보조 정보를 표시한다. |
| Meta | 우측에 날짜, 첨부, 상태 정보를 표시한다. |

Card list는 일반 table보다 행 간 여백과 radius를 더 크게 사용한다. 모바일 또는 좁은 화면에서 테이블 대체 패턴으로 사용할 수 있다.

### 17.8 Notice List Rules

Notice list는 게시글, 공지, 이벤트처럼 날짜와 제목을 강조하는 목록에 사용한다.

| Element | Description |
| --- | --- |
| Date block | 월/일 또는 연/월/일 정보를 강조한다. |
| Title | 게시글 제목을 크게 표시한다. |
| Thumbnail | 선택적으로 우측에 대표 이미지를 표시한다. |
| Search area | Select Box, Input Component, Button을 조합해 검색 조건을 제공한다. |
| Pagination | 목록 하단에 페이지 이동을 제공한다. |

Notice list는 일반 데이터 테이블보다 콘텐츠 탐색과 읽기 흐름을 우선한다. 썸네일이 없는 경우에도 제목과 날짜 정렬이 흐트러지지 않아야 한다.

### 17.9 Usage Notes

- 단순 데이터 관리는 Basic table을 우선 사용한다.
- 이미지나 멤버 정보가 중요한 경우 Media table 또는 Member table을 사용한다.
- 모바일 또는 카드형 탐색이 필요한 경우 Card list를 사용한다.
- 공지사항, 뉴스, 이벤트처럼 읽기 중심 콘텐츠는 Notice list를 사용한다.
- 컬럼이 많아지는 경우 중요도가 낮은 컬럼은 숨기거나 상세 화면으로 이동한다.
- 정렬 가능한 컬럼은 sort icon을 표시하고, 현재 정렬 방향을 명확히 보여준다.
- Light/Dark 모드 모두에서 헤더, 행, 선택 상태, hover 상태, 구분선, 액션 아이콘의 대비를 확인한다.

## 18. Gallery Table

본 파트는 디자인시스템에서 사용하는 갤러리 형태의 데이터 목록 기준을 정의한다.  
Gallery Table은 이미지 썸네일이 중요한 콘텐츠를 카드 그리드로 보여주는 패턴이며, Light와 Dark 모드를 모두 지원한다.

### 18.1 Gallery Types

| Type | Description | Usage |
| --- | --- | --- |
| Content card | 썸네일, 배지, 제목, 설명, 메타 정보를 포함하는 카드 | 콘텐츠 목록, 갤러리, 포트폴리오 |
| Simple gallery card | 썸네일, 제목, 날짜 중심의 간단한 카드 | 이미지 목록, 앨범, 게시물 |
| Dark gallery card | Dark surface 위에 콘텐츠를 표시하는 카드 | 다크모드 갤러리, 미디어 중심 화면 |

### 18.2 Card Structure

| Element | Required | Description |
| --- | --- | --- |
| Thumbnail | Required | 카드 상단의 대표 이미지 |
| Avatar | Optional | 작성자 또는 소유자를 나타내는 원형 이미지 |
| Badge | Optional | 카테고리, 상태, 프로모션 정보를 표시 |
| Title | Required | 콘텐츠의 핵심 제목 |
| Description | Optional | 콘텐츠 요약 설명 |
| Date | Optional | 작성일 또는 이벤트 날짜 |
| Meta | Optional | 조회수, 댓글 수 등 보조 정보 |

### 18.3 Layout Rules

| Rule | Description |
| --- | --- |
| Grid | 화면 폭에 따라 2~3열 이상의 카드 그리드를 사용할 수 있다. |
| Card width | 같은 행의 카드는 동일한 너비를 유지한다. |
| Thumbnail ratio | 썸네일은 동일한 비율로 크롭해 카드 정렬을 유지한다. |
| Content padding | 카드 본문은 일관된 padding을 사용한다. |
| Gap | 카드 사이 간격은 Spacing System 토큰을 사용한다. |

카드 높이는 콘텐츠 양에 따라 달라질 수 있지만, 같은 목록 안에서는 제목과 메타 정보의 위치가 지나치게 흔들리지 않도록 텍스트 줄 수를 제한한다.

### 18.4 Theme Modes

| Mode | Card Surface | Text | Border / Shadow |
| --- | --- | --- | --- |
| `Light` | 밝은 surface | 어두운 본문 텍스트 | 약한 shadow 또는 Gray 보더 |
| `Dark` | Dark surface | 밝은 본문 텍스트 | Dark surface와 구분되는 보더 또는 shadow |

Light와 Dark 모드는 동일한 정보 구조를 유지한다. Badge, avatar, meta icon, hover, selected 상태는 각 모드에서 충분한 대비를 확보해야 한다.

### 18.5 Content Rules

| Content | Rule |
| --- | --- |
| Thumbnail | 이미지가 없으면 placeholder를 사용한다. |
| Avatar | 썸네일과 본문 경계에 걸쳐 배치할 수 있다. |
| Badge | 카드 본문 상단에 배치하며, Badge Icon 규칙을 따른다. |
| Title | 한 줄 또는 두 줄까지 허용하고, 초과 시 말줄임 처리한다. |
| Description | 두세 줄 내로 제한하고, 긴 텍스트는 말줄임 처리한다. |
| Meta icon | 조회수, 댓글 수 등은 아이콘과 숫자를 함께 표시한다. |

### 18.6 Usage Notes

- 이미지가 콘텐츠 선택의 핵심 기준일 때 Gallery Table을 사용한다.
- 텍스트 비교가 더 중요한 경우 Basic table 또는 Notice list를 사용한다.
- 카드 전체가 클릭 가능한 경우 내부 버튼과 클릭 영역이 충돌하지 않도록 한다.
- Badge 색상은 콘텐츠 카테고리 또는 상태 의미와 일관되게 연결한다.
- Dark 모드에서는 썸네일 아래 본문 영역과 배경이 구분되도록 surface 대비를 확보한다.
- 모바일에서는 1열 또는 2열 카드 그리드로 전환하고, 텍스트 줄 수를 더 엄격히 제한한다.

## 19. Card Style

본 파트는 디자인시스템에서 사용하는 Card 컴포넌트의 구조, 유형, 액션, Light/Dark 모드 기준을 정의한다.  
Card는 서로 연관된 정보와 액션을 하나의 독립된 묶음으로 보여줄 때 사용한다.

### 19.1 Card Types

| Type | Description | Usage |
| --- | --- | --- |
| Basic content card | 배지, 제목, 설명, 날짜, 팀 정보를 포함하는 기본 카드 | 게시물 요약, 프로젝트 요약 |
| Media action card | 이미지, 제목, 설명, 하단 액션을 포함하는 카드 | 콘텐츠 카드, 피드형 카드 |
| Profile card | 아바타, 이름, 직책, 연락처, 위치, 버튼을 포함하는 카드 | 사용자 카드, 담당자 카드 |
| Product / menu card | 이미지, 본문, 메뉴 리스트, 링크 액션을 포함하는 카드 | 상품, 서비스, 메뉴형 콘텐츠 |
| Horizontal media card | 제목/보조정보와 이미지를 조합한 카드 | 상세 카드, 추천 카드 |

### 19.2 Theme Modes

| Mode | Surface | Text | Divider / Border |
| --- | --- | --- | --- |
| `Light` | 밝은 card surface | 어두운 제목, Gray 계열 본문 | Gray 계열 보더와 약한 shadow |
| `Dark` | Dark card surface | 밝은 제목, Gray Dark 계열 본문 | Dark surface에서 구분되는 보더와 divider |

Light와 Dark 모드는 동일한 카드 구조를 유지한다. Card 내부의 Badge, Button, Icon, Avatar, Divider는 각 모드에 맞는 Semantic 토큰을 사용한다.

### 19.3 Card Structure

| Element | Required | Description |
| --- | --- | --- |
| Container | Required | 카드 전체를 감싸는 surface 영역 |
| Thumbnail | Optional | 상단 또는 중간에 배치되는 대표 이미지 |
| Badge | Optional | 카테고리, 상태, 프로모션 정보를 표시 |
| More button | Optional | 우측 상단 더보기 액션 |
| Avatar | Optional | 작성자 또는 멤버를 표시 |
| Title | Required | 카드의 핵심 제목 |
| Description | Optional | 카드 내용을 요약하는 본문 |
| Date / Meta | Optional | 날짜, 조회수, 댓글 수 등 보조 정보 |
| Divider | Optional | 본문과 하단 영역을 분리 |
| Action area | Optional | 버튼, 링크, 아이콘 액션을 배치 |

### 19.4 Layout Patterns

| Pattern | Description |
| --- | --- |
| Text only | 제목, 설명, 메타 정보만 포함한다. |
| Image top | 썸네일을 상단에 두고 본문을 아래에 배치한다. |
| Avatar leading | 아바타를 제목 왼쪽에 배치한다. |
| Footer action | 하단에 좋아요, 편집, 더보기 같은 아이콘 액션을 배치한다. |
| Button group | 하단에 1~2개의 버튼을 배치한다. |
| Menu list | 카드 내부에 메뉴 행을 나열한다. |

카드 안에 여러 액션을 넣는 경우 주 액션과 보조 액션을 시각적으로 구분한다. 액션이 너무 많아지면 더보기 메뉴로 정리한다.

### 19.5 Card Actions

| Action | Usage |
| --- | --- |
| More | 카드 우측 상단의 추가 메뉴 |
| Like | 하단 아이콘 액션 |
| Edit | 하단 아이콘 액션 또는 관리 액션 |
| Link | 외부 이동 또는 상세 이동 |
| Primary button | 주요 CTA |
| Secondary button | 보조 CTA |

카드 전체가 클릭 가능한 경우 내부 버튼, 링크, 더보기 메뉴의 클릭 영역과 충돌하지 않도록 한다.

### 19.6 Content Rules

| Content | Rule |
| --- | --- |
| Title | 한 줄을 기본으로 하며, 긴 제목은 최대 두 줄까지 허용한다. |
| Description | 두세 줄 내로 제한하고 초과 시 말줄임 처리한다. |
| Thumbnail | 동일 목록 안에서는 동일한 비율을 유지한다. |
| Avatar | 원형을 기본으로 하며 이미지가 없으면 이니셜 또는 placeholder를 사용한다. |
| Badge | 제목보다 먼저 카테고리를 알려야 할 때 상단에 배치한다. |
| Divider | 콘텐츠 그룹을 분리해야 할 때만 사용한다. |

### 19.7 Usage Notes

- 독립된 정보 묶음에는 Card를 사용한다.
- 데이터 비교가 중요한 경우 Card보다 Table을 우선 사용한다.
- 이미지가 선택 기준인 경우 Gallery Table 또는 Image top Card를 사용한다.
- 다크모드에서는 카드 배경과 페이지 배경의 대비를 충분히 확보한다.
- 카드 안에 카드처럼 보이는 중첩 구조를 만들지 않는다.
- 카드 radius, shadow, border는 같은 화면 안에서 일관되게 사용한다.
- 모바일에서는 카드 폭을 화면에 맞추고, 액션 영역이 너무 좁아지지 않도록 한다.

## 20. Pagination

본 파트는 디자인시스템에서 사용하는 페이지 이동 컴포넌트의 타입, 크기, 상태 기준을 정의한다.  
Pagination은 Table, List, Gallery Table처럼 여러 페이지로 나뉘는 데이터 목록 하단에 배치한다.

### 20.1 Pagination Types

| Type | Description | Usage |
| --- | --- | --- |
| `A` | 숫자와 단순 chevron 아이콘을 사용하는 기본형 | 기본 테이블, 간결한 목록 |
| `B` | 원형 버튼 형태의 이전/다음 컨트롤을 사용하는 강조형 | 클릭 영역이 더 필요한 목록 |
| `C` | `Previous`, `Next`, `First`, `Last` 텍스트를 함께 사용하는 텍스트형 | 페이지 이동 의미를 명확히 보여야 하는 화면 |

### 20.2 Component Sizes

| Size | Description |
| --- | --- |
| `basic` | 기본 페이지네이션 크기 |
| `large` | 더 큰 클릭 영역이 필요한 크기 |

라지 크기는 추후 상세 수치가 확정되면 보완한다. 현재는 basic과 large 두 가지 크기 체계를 지원하는 것으로 정의한다.

### 20.3 States

| State | Description |
| --- | --- |
| `Default` | 기본 페이지 이동 상태 |
| `Hover` | PC 환경에서 마우스를 올렸을 때의 상태 |
| `Select` | 현재 선택된 페이지 |
| `Disabled` | 이동할 수 없는 페이지 이동 버튼 |
| `First / Last` | 첫 페이지 또는 마지막 페이지로 이동하는 컨트롤 |

현재 페이지는 Primary 계열 컬러 또는 보더로 명확히 표시한다. 이동할 수 없는 Previous, Next, First, Last는 Disabled 상태로 표시한다.

### 20.4 Control Rules

| Control | Usage |
| --- | --- |
| Previous | 이전 페이지로 이동 |
| Next | 다음 페이지로 이동 |
| First | 첫 페이지로 이동, 필요한 상황에서만 사용 |
| Last | 마지막 페이지로 이동, 필요한 상황에서만 사용 |
| Page number | 특정 페이지로 직접 이동 |

First / Last는 페이지 수가 많거나 빠른 이동이 필요한 경우에만 사용한다. 페이지 수가 적은 목록에서는 Previous / Next와 페이지 번호만 사용한다.

### 20.5 Placement Rules

| Parent | Placement |
| --- | --- |
| Table | 테이블 하단 중앙 또는 우측 |
| Gallery Table | 카드 그리드 하단 중앙 |
| Notice List | 목록 하단 중앙 |
| Modal | Modal Body 하단 또는 Footer 위 |

Pagination은 목록과 시각적으로 연결되어야 하며, 검색/필터 조건이 변경되면 첫 페이지로 초기화할 수 있다.

### 20.6 Theme Modes

| Mode | Rule |
| --- | --- |
| `Light` | 선택 페이지는 Primary 계열, 비활성 컨트롤은 Gray 계열로 표시한다. |
| `Dark` | 선택 페이지는 Primary 계열을 유지하되, 숫자/아이콘/보더가 Dark surface 위에서 충분히 보이도록 한다. |

Light와 Dark 모드 모두에서 현재 페이지, hover 상태, disabled 상태의 구분이 명확해야 한다.

### 20.7 Usage Notes

- 기본적으로 `Default`와 `Hover` 상태를 사용한다.
- 현재 페이지는 `Select` 상태로 표시한다.
- First / Last는 목록 규모와 사용자 이동 패턴에 따라 선택적으로 사용한다.
- 페이지 번호가 많아지는 경우 중간 페이지는 생략 표시를 사용할 수 있다.
- 페이지 이동 후 스크롤 위치와 포커스 위치가 사용자의 흐름을 방해하지 않도록 한다.

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

## 22. Sub Page Visual Direction

본 파트는 서브페이지의 화면 스타일 방향을 정의한다.  
서브페이지는 메인페이지의 분위기를 이어가되, 사용자가 원하는 정보를 안정적으로 읽고 행동할 수 있도록 정보 구조, 여백, 타이포 위계를 더 명확하게 설계한다.

### 22.1 Sub Page Design Tone

| Principle | Description |
| --- | --- |
| Calm continuation | 메인페이지의 브랜드 톤을 이어가되, 서브페이지에서는 장면감보다 정보 전달력을 우선한다. |
| Clear hierarchy | 페이지 제목, 현재 위치, 본문 제목, 설명, CTA의 위계를 명확히 나눈다. |
| Wide breathing space | 콘텐츠 폭을 제한하고 섹션 사이 여백을 충분히 두어 긴 글과 표도 답답하지 않게 만든다. |
| Image as context | 상단 비주얼이나 본문 이미지는 장식이 아니라 페이지 주제와 맥락을 설명하는 역할로 사용한다. |
| Structured content | 소개, 서비스, 절차, 문의, 표, 목록 등 정보 유형에 맞는 구조를 선택한다. |

### 22.2 Sub Visual / Page Header

서브페이지 상단은 현재 페이지의 성격을 빠르게 알려주는 영역이다.

| Type | Rule |
| --- | --- |
| Image hero | 회사소개, 서비스 소개, 브랜드/기관 소개처럼 분위기가 중요한 페이지에 사용한다. 이미지 위에는 짧은 제목과 breadcrumb 또는 location bar를 배치한다. |
| Minimal title | 제품 상세, 기능 안내, 정책 안내처럼 정보 중심 페이지에 사용한다. 흰 배경과 넓은 여백으로 제목을 강조한다. |
| Color band | 교육, 캠페인, 프로그램처럼 카테고리 성격이 강한 페이지에 사용한다. 브랜드 컬러를 넓게 쓰되 본문과 대비를 명확히 한다. |
| Tab header | 동일 레벨의 하위 콘텐츠가 여러 개 있을 때 사용한다. 현재 위치와 선택 상태가 분명해야 한다. |

### 22.3 Preferred Sub Page Patterns

| Pattern | Description | Use Case |
| --- | --- | --- |
| Greeting / Message | 큰 대표 이미지 아래 인사말, 본문, 서명 정보를 여백 있게 배치한다. | 인사말, 대표 메시지, 회사/기관 소개 |
| Service detail | 이미지와 텍스트를 좌우로 교차 배치하고, 하단에 프로세스 또는 관련 서비스를 카드로 정리한다. | 서비스 소개, 컨설팅, 업무 영역 |
| Inquiry form | 큰 서브 비주얼 이후 넓은 폼 영역을 제공한다. 입력 항목은 줄과 여백으로 정돈하고, 버튼은 하단 우측에 배치한다. | 문의, 상담, 견적 요청 |
| Vision / Values | 큰 개념 도식, 이미지+텍스트 조합, 항목별 설명으로 철학과 가치를 전달한다. | 비전, 미션, 핵심가치, ESG |
| Process / Step | 번호, 선, 카드, 아이콘을 사용해 절차를 순서대로 보여준다. | 처리 절차, 학습 시스템, 신청 절차 |
| Timeline | 중앙 라인과 연도/이미지를 조합해 연혁을 시각적으로 보여준다. | 회사 연혁, 서비스 발전 과정 |
| Feature detail | 기능 설명, 아이콘 리스트, 적용 사례, CTA를 조합해 제품/기능 정보를 제공한다. | 제품 상세, SDK, 솔루션 상세 |
| Table guide | 표와 안내 카드, 주의 사항을 중심으로 정확한 정보를 제공한다. | 포인트 안내, 요금, 정책, 기준표 |

### 22.4 Sub Page Layout Rules

| Area | Rule |
| --- | --- |
| Container | 본문은 중앙 정렬된 고정 폭 컨테이너를 기본으로 하며, 너무 넓게 펼치지 않는다. |
| Section | 서브페이지 섹션은 메인보다 차분하게 구성하되, 제목과 본문 사이 여백을 충분히 둔다. |
| Content width | 긴 문장은 한 줄이 과도하게 길어지지 않도록 폭을 제한한다. |
| Image block | 이미지는 텍스트와 동일한 무게를 가지도록 크기와 위치를 정리한다. |
| Card grid | 서비스, 기능, 혜택 카드는 동일 높이와 동일 간격을 우선한다. |
| CTA | 서브페이지 CTA는 과하게 많지 않게 배치하고, 주요 행동 1개를 먼저 보이게 한다. |
| Footer link | 서브페이지에서도 하단 정보와 관련 링크는 메인과 같은 톤으로 유지한다. |

### 22.5 Typography Direction

| Usage | Rule |
| --- | --- |
| Page title | 페이지의 가장 큰 정보로 처리한다. 이미지 위에 올릴 경우 대비를 충분히 확보한다. |
| Section title | 본문 흐름을 나누는 기준이므로 짧고 명확하게 작성한다. |
| Body text | line-height를 넉넉하게 두고 문단 사이 간격을 확보한다. 긴 설명은 여러 문단으로 나눈다. |
| Label / Eyebrow | 작은 라벨은 포인트 컬러로 사용할 수 있지만, 너무 장식적으로 보이지 않게 한다. |
| Data / Number | 절차 번호, 연도, 수치 정보는 색상이나 굵기로 구분해 빠르게 인식되게 한다. |

### 22.6 Form Page Rules

문의, 상담, 신청처럼 입력이 필요한 서브페이지는 아래 기준을 따른다.

| Rule | Description |
| --- | --- |
| Form width | 입력 영역은 너무 넓게 펼치지 않고, 사용자가 한눈에 항목을 따라갈 수 있는 폭으로 제한한다. |
| Grouping | 동의, 분류, 기본 정보, 상세 내용, 첨부파일, 보안 입력을 구역별로 나눈다. |
| Input alignment | 라벨과 입력 영역의 정렬을 일정하게 유지한다. |
| Editor area | 에디터나 textarea는 충분한 높이를 제공하되, 주변 여백을 확보해 무겁게 보이지 않게 한다. |
| Attachment | 파일 목록은 카드 형태로 정리하고, 삭제/추가 버튼은 작지만 명확하게 제공한다. |
| Button placement | 취소/목록 버튼은 보조, 문의/등록 버튼은 주요 액션으로 구분한다. |

### 22.7 Information Page Rules

표, 정책, 포인트, 기준 안내처럼 정확성이 중요한 페이지는 아래 기준을 따른다.

| Rule | Description |
| --- | --- |
| Summary first | 상단에서 이 페이지가 무엇을 설명하는지 짧게 요약한다. |
| Visual anchor | 필요한 경우 상단에 큰 안내 이미지나 일러스트를 배치해 주제를 쉽게 인식하게 한다. |
| Table clarity | 표는 헤더, 구분 열, 기준 값이 명확히 읽히도록 배경색과 선을 정리한다. |
| Help card | 관련 행동이 필요한 경우 하단에 안내 카드 또는 CTA 카드를 배치한다. |
| Notice box | 예외, 유의사항, 변경 가능성은 별도 박스로 분리한다. |

### 22.8 Preferred Sub Page Do / Don't

| Do | Don't |
| --- | --- |
| 메인페이지의 톤을 이어가되 서브페이지에서는 정보 전달을 우선한다. | 메인처럼 모든 서브페이지를 강한 비주얼 중심으로 만들지 않는다. |
| 긴 본문은 문단, 이미지, 카드, 표로 나누어 읽기 쉽게 만든다. | 긴 텍스트를 한 덩어리로 배치하지 않는다. |
| 이미지와 텍스트의 크기 관계를 안정적으로 맞춘다. | 이미지는 큰데 설명이 너무 작거나, 반대로 텍스트만 과하게 커지지 않게 한다. |
| 절차와 기능은 번호, 선, 아이콘, 카드로 시각화한다. | 설명 문장만으로 복잡한 구조를 이해시키려 하지 않는다. |
| 폼 화면은 실용성을 우선하되 여백과 정렬로 깔끔하게 만든다. | 입력 요소를 촘촘히 붙여 관리 화면처럼 보이게 하지 않는다. |
| 표 중심 페이지는 상단 요약과 하단 CTA로 흐름을 만든다. | 표만 나열해 페이지가 딱딱하게 끝나지 않게 한다. |

### 22.9 Sub Page Review Checklist

| Check | Question |
| --- | --- |
| Continuity | 메인페이지와 같은 브랜드 톤을 유지하고 있는가? |
| Readability | 제목, 본문, 표, 카드가 편하게 읽히는가? |
| Spacing | 섹션 사이와 콘텐츠 내부 여백이 충분한가? |
| Purpose | 이 페이지에서 사용자가 얻어야 할 정보와 행동이 명확한가? |
| Image fit | 이미지가 페이지 주제와 실제로 연결되는가? |
| Component consistency | 버튼, 카드, 폼, 표가 앞서 정의한 공통 컴포넌트 기준을 따르는가? |
| Mobile flow | 모바일에서 제목, 이미지, 표, 폼이 무리 없이 세로 흐름으로 전환되는가? |

## 23. Utility / Functional Page Direction

본 파트는 FAQ, 로그인, 회원가입, 문의, 게시판, 모달처럼 사용자가 특정 작업을 완료해야 하는 기능형 화면의 방향을 정의한다.

기능형 화면은 장식보다 명확한 흐름을 우선한다. 다만 단순하고 건조하게만 만들지 않고, 여백, 정렬, 버튼, 상태 표현을 정돈해 디자인시스템의 깔끔한 인상을 유지한다.

### 23.1 Functional Page Tone

| Principle | Guide |
| --- | --- |
| Task first | 사용자가 해야 할 행동을 첫 화면에서 바로 이해할 수 있게 한다. |
| Calm structure | 기능 화면에서는 과한 장식보다 제목, 설명, 입력, 버튼의 계층을 명확히 둔다. |
| Polished utility | 단순한 화면이라도 여백, 라인, 버튼 상태, 아이콘 정렬을 정돈해 완성도를 만든다. |
| Same system | 버튼, 입력, 체크박스, 라디오, 셀렉트, 모달은 앞서 정의한 컴포넌트를 우선 사용한다. |
| Controlled accent | 핵심 CTA, 선택 상태, 진행 단계에만 브랜드 컬러를 사용한다. |
| Stable footer | 로그인, 가입, FAQ처럼 콘텐츠가 짧은 페이지도 하단 정보 영역이 어색하게 뜨지 않게 한다. |

### 23.2 FAQ / Help Center

FAQ와 도움말 화면은 사용자가 빠르게 범주를 찾고 질문을 펼쳐볼 수 있어야 한다.

| Element | Guide |
| --- | --- |
| Page title | 중앙 정렬 또는 넓은 상단 여백을 사용해 페이지 성격을 명확히 보여준다. |
| Category card | 아이콘과 짧은 라벨을 함께 사용하며, 선택 상태는 border 또는 fill로 분명하게 표시한다. |
| Accordion list | 질문 행은 1줄 기준으로 정리하고, 펼침 아이콘은 우측 끝에 고정한다. |
| Category label | 질문의 분류는 작은 칩 또는 라인 태그로 제공한다. |
| Pagination | FAQ 항목이 많을 경우 하단 중앙에 배치한다. |
| Utility button | 챗봇, TOP, 고객센터 버튼은 화면을 가리지 않는 위치에 배치한다. |

FAQ 화면은 친절해야 하지만 장식이 많으면 탐색성이 떨어진다. 아이콘은 범주를 구분하는 정도로 사용하고, 본문 영역은 충분한 행간과 라인으로 정리한다.

### 23.3 Member / Login / Auth

로그인, 회원가입, 인증 화면은 집중도가 가장 중요하다. 사용자가 입력해야 할 정보와 다음 행동만 보이도록 구성한다.

| Pattern | Guide |
| --- | --- |
| Member select | 개인, 기업, 기관 등 선택지는 카드형으로 제공하고, 아이콘과 CTA를 함께 배치한다. |
| Login page | 중앙 컨테이너를 기본으로 하며, 로고, 제목, 입력, 보조 링크, CTA 순서로 구성한다. |
| Auth step | 약관 동의, 휴대폰 인증, 정보 입력처럼 단계가 있는 화면은 `STEP 01` 형태의 보조 라벨을 사용한다. |
| Disabled state | 입력 미완료 상태의 버튼은 낮은 대비로 표시하되 클릭 불가 상태가 분명해야 한다. |
| Social login | 일반 로그인과 소셜 로그인은 시각적으로 분리한다. |
| Footer | 화면 콘텐츠가 짧아도 푸터가 너무 가까이 붙거나 떠 보이지 않도록 수직 여백을 확보한다. |

회원 흐름에서는 CTA를 여러 개 강조하지 않는다. 기본 행동은 1개만 강하게 보여주고, 보조 링크는 작은 텍스트 버튼으로 정리한다.

### 23.4 Inquiry / Contact Form

문의 화면은 사용자가 긴 입력을 부담 없이 완료할 수 있도록 폼을 그룹화한다.

| Group | Guide |
| --- | --- |
| Intro | 페이지 제목 아래에 문의 목적과 처리 안내를 짧게 제공한다. |
| Basic info | 이름, 이메일, 연락처, 회사명 등 기본 정보는 2열 배치를 사용할 수 있다. |
| Category | 문의 유형은 체크박스, 라디오, 셀렉트 중 성격에 맞게 사용한다. |
| Content | 제목과 내용은 넓은 입력 영역으로 제공하고, 긴 텍스트 입력은 textarea 기준을 따른다. |
| Agreement | 개인정보 동의는 제출 버튼 이전에 배치하고 필수 여부를 명확히 표시한다. |
| Attachment | 파일 첨부는 파일명, 용량, 삭제/추가 액션을 같은 줄에서 확인할 수 있게 한다. |
| Submit | 제출 버튼은 하단 우측 또는 중앙에 배치하되, 페이지 전체 정렬 기준과 맞춘다. |

폼 화면에서는 입력칸을 촘촘히 붙이지 않는다. 행 간격은 기본 spacing보다 넉넉하게 잡고, 라벨과 placeholder가 서로 역할을 침범하지 않게 한다.

### 23.5 Board / Notice / PR

게시판과 공지 화면은 목록 탐색이 중심이다. 목록형, 카드형, 갤러리형 중 콘텐츠 성격에 맞는 패턴을 선택한다.

| Type | Guide |
| --- | --- |
| Notice list | 텍스트 중심 공지는 날짜, 상태, 제목의 정렬을 명확히 한다. |
| PR grid | 이미지가 중요한 보도자료나 뉴스는 카드형 그리드를 사용할 수 있다. |
| Search | 검색은 목록 상단 우측에 배치하는 것을 기본으로 한다. |
| Filter | 탭, 칩, 셀렉트 등은 목록 위에 배치하며 선택 상태를 분명히 한다. |
| Status | 마감, 공지, 신규 등 상태는 작은 태그로 제공한다. |
| Empty state | 결과가 없을 경우 빈 영역만 남기지 말고 짧은 안내와 복귀 액션을 제공한다. |
| Pagination | 목록 하단 중앙 배치를 기본으로 한다. |

게시판은 정보 밀도가 높지만 답답해 보이면 안 된다. 행 높이, 구분선, 날짜 컬럼, 태그 크기를 정돈해 스캔이 편하게 만든다.

### 23.6 Modal / Layer Utility

모달은 사용자의 현재 흐름을 잠시 멈추고 중요한 작업을 처리하게 하는 레이어다.

| Element | Guide |
| --- | --- |
| Overlay | 배경은 충분히 어둡게 dim 처리해 모달에 집중하게 한다. |
| Container | 기본 모달은 white 배경과 16-20px radius를 사용한다. |
| Close | 닫기 버튼은 우측 상단에 고정한다. |
| Title | 로그인, 약관, 정보 입력 등 모달 목적을 큰 제목으로 표시한다. |
| Step label | 단계형 모달은 `STEP 01`, `STEP 02`처럼 현재 위치를 알려준다. |
| Primary CTA | 주요 버튼은 1개만 강하게 표현한다. |
| Secondary CTA | 취소, 이전, 보조 링크는 line 또는 text button을 사용한다. |

모달 안에서도 공통 input, button, checkbox 기준을 따른다. 단, 모달은 독립된 작은 화면처럼 보이므로 내부 여백과 버튼 크기를 더 엄격히 맞춘다.

### 23.7 Campaign / Event Page

이벤트와 캠페인 페이지는 일반 기능 화면보다 표현의 폭을 넓게 가져갈 수 있다.

| Element | Guide |
| --- | --- |
| Visual theme | 일러스트, 캐릭터, 강한 컬러, 게임형 그래픽을 사용할 수 있다. |
| Section rhythm | 큰 비주얼 섹션과 정보 섹션을 번갈아 배치해 지루함을 줄인다. |
| Rule box | 참여 방법, 기간, 경품, 유의사항은 별도 박스로 명확히 분리한다. |
| CTA | 시작하기, 참여하기, 신청하기 등 행동 버튼은 가장 눈에 띄게 배치한다. |
| Reward | 경품이나 혜택 이미지는 시각적으로 충분히 크게 보여준다. |
| Mobile | 이벤트 페이지는 모바일에서 이미지 안의 작은 글자가 읽히는지 반드시 확인한다. |

캠페인 화면은 개성이 있어도 된다. 다만 정보 전달이 흐려지면 안 되며, 참여 조건과 CTA는 언제나 쉽게 찾을 수 있어야 한다.

### 23.8 Medical / Expert Profile

의료, 전문가, 연구, 기관 소개 화면은 신뢰감과 전문성을 우선한다.

| Element | Guide |
| --- | --- |
| Hero | 절제된 이미지와 간결한 카피로 전문성을 보여준다. |
| Profile card | 인물 사진, 이름, 직책, 전문 분야, 약력을 일정한 구조로 반복한다. |
| Long list | 의료진처럼 항목이 많을 경우 카드 높이와 내부 정보 순서를 고정한다. |
| Trust color | blue, navy, green 계열을 사용할 수 있으나 한 화면에 과하게 섞지 않는다. |
| Detail text | 전문 정보는 작은 글자로 밀어 넣지 않고, 문단과 표로 나누어 읽게 한다. |
| CTA | 상담, 예약, 문의 등 행동은 페이지 하단 또는 우측 고정 영역에서 제공할 수 있다. |

전문가 페이지는 신뢰가 핵심이다. 사진 품질, 여백, 텍스트 정렬이 흐트러지면 화면 전체가 가볍거나 투박해 보이므로 반복 요소의 기준을 엄격히 맞춘다.

### 23.9 Footer / Floating Utility

하단과 플로팅 영역은 사이트 전체의 안정감을 결정한다.

| Element | Guide |
| --- | --- |
| Footer | 기본적으로 dark footer를 사용해 페이지를 안정적으로 마감한다. |
| Footer info | 회사 정보, 연락처, 정책 링크, 패밀리 사이트를 그룹화한다. |
| Quick menu | 상담, 신청, 자료실, TOP 같은 플로팅 메뉴는 화면 우측에 둘 수 있다. |
| Visual weight | 플로팅 메뉴는 유용해야 하며 본문을 가리거나 시선을 과하게 빼앗지 않게 한다. |
| Sticky CTA | 상담이나 신청이 핵심인 사이트는 하단 또는 우측 CTA를 사용할 수 있다. |

### 23.10 Functional Page Do / Don't

| Do | Don't |
| --- | --- |
| 기능 화면에서도 여백과 정렬로 고급스러운 인상을 유지한다. | 기능 화면이라는 이유로 입력 요소와 텍스트를 촘촘히 붙이지 않는다. |
| 사용자의 다음 행동을 한눈에 보이게 한다. | CTA가 여러 개라 무엇을 눌러야 할지 헷갈리게 하지 않는다. |
| 상태, 단계, 선택값을 명확히 표시한다. | 선택 상태와 비활성 상태를 색만 약하게 바꿔 애매하게 만들지 않는다. |
| 목록과 폼은 반복 규칙을 고정한다. | 같은 페이지 안에서 행 높이, 라벨 위치, 버튼 크기를 제각각 쓰지 않는다. |
| 모달은 현재 작업에 필요한 정보만 담는다. | 모달 안에 긴 설명, 여러 그룹, 많은 CTA를 한꺼번에 넣지 않는다. |
| 이벤트 페이지는 과감한 표현을 허용하되 정보 구조를 지킨다. | 재미있는 그래픽 때문에 참여 방법과 CTA가 묻히게 하지 않는다. |
| 전문성 페이지는 사진, 표, 약력 구조를 깨끗하게 반복한다. | 인물 정보나 전문 정보를 작은 글자로 빽빽하게 밀어 넣지 않는다. |

### 23.11 Functional Page Review Checklist

| Check | Question |
| --- | --- |
| Goal | 이 화면에서 사용자가 해야 할 일이 3초 안에 보이는가? |
| Hierarchy | 제목, 설명, 입력, 버튼, 보조 링크의 우선순위가 명확한가? |
| Spacing | 여백이 충분하지만 요소가 흩어져 보이지 않는가? |
| State | 선택, 비활성, 오류, 완료, 진행 상태가 명확한가? |
| Reuse | 공통 컴포넌트 기준을 우선 사용하고 있는가? |
| Density | 목록, 폼, 카드가 답답하거나 투박해 보이지 않는가? |
| Modal focus | 모달이 배경과 분리되고 한 가지 작업에 집중하는가? |
| Mobile | 모바일에서 입력, 버튼, 리스트, 모달이 손가락 조작에 충분한가? |
| Brand fit | 기능 화면도 전체 브랜드 톤과 같은 결을 유지하는가? |
