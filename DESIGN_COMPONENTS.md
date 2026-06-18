# DESIGN_COMPONENTS.md

> 공통 컴포넌트 상세 스펙(상태·사이즈 매트릭스 중심).
> 토큰값(컬러/스페이싱/radius/shadow 등)의 출처는 `DESIGN_TOKENS.md`. 페이지 패턴은 `DESIGN_PAGE_MAIN.md`(메인)·`DESIGN_PAGE_SUB.md`(서브/기능형). 항상 읽는 가이드는 `DESIGN.md`.
> 컴포넌트 1개 작업 시 `DESIGN.md` + 이 문서의 해당 절만 읽으면 된다.

## C0. Common States & Sizes (공통 정의)

아래 상태/사이즈는 **여기서 한 번만** 정의한다. 각 컴포넌트 절에서는 이 정의를 전제로 하고, **다른 점만** 표로 적는다. (컴포넌트마다 같은 설명을 반복하지 않는다.)

### C0.1 Interaction States

| State | Description |
| --- | --- |
| `Default` | 기본 상태 |
| `Hover` | PC에서 마우스를 올린 상태. **모바일/터치 환경에서는 사용하지 않는다.** |
| `Focus` | 키보드/포커스 진입 상태 |
| `Active` | 누르는 중 또는 입력 중 상태 |
| `Completion` | 입력/선택이 완료된 상태 |
| `Disabled` | 비활성(조작 불가) 상태 |
| `Select-Disabled` | 선택된 값이지만 비활성이라 변경 불가한 상태 |

> 모바일에서는 `Hover`를 제외하고 `Focus`/`Active`/`Completion`/`Disabled` + 검증 상태 중심으로 표현한다. 시각 박스 크기와 별개로 충분한 터치 영역을 확보한다.

### C0.2 Validation States

| State | Color Role | Meaning |
| --- | --- | --- |
| `Good` | Success(Green) | 올바른 입력 / 성공 |
| `Weak` | Warning(Yellow·Orange) | 확인 필요 / 주의 |
| `Error` | Danger(Red) | 잘못된 입력 / 실패 |

> 색상은 직접 HEX가 아닌 `DESIGN_TOKENS.md`의 Semantic 토큰으로 연결한다. 검증 메시지는 입력 요소 바로 아래, 안내 문구보다 우선 노출한다.

### C0.3 Standard Sizes

| Size | 기준 높이 | 사용처 |
| --- | --- | --- |
| `small` | 36px | 좁은 필터, 테이블 내부, 보조 |
| `basic` | 46px | 일반 폼/기본 (기본값) |
| `large` | 56px | 강조, 주요 CTA와 결합 |

> 컴포넌트별로 박스 크기가 다른 경우(체크박스 20/24px 등)는 해당 절에서 별도 명시한다.

### C0.4 Theme

모든 컴포넌트는 Light/Dark 두 모드를 지원한다. surface·border·구분선·hover·selected·disabled·overlay는 모드별 토큰으로 분리한다. 상세 규칙은 `DESIGN_TOKENS.md`의 Dark Mode Rules를 따른다.

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

