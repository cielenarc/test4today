# KAIST Sleek CV — Portfolio Template (KR)

이 레포는 정적 HTML/CSS/JS로 만든 개인 포트폴리오/이력서 템플릿입니다. 본 README는 `kaist-sleek-CV-master/` 디렉터리의 코드(`index.html`, `style.css`, `script.js`)를 기준으로 작성되었습니다.

## 미리보기 / 실행
- 방법 1: 파일 더블클릭 → `kaist-sleek-CV-master/index.html`을 브라우저로 열기
- 방법 2: 간단 서버 실행 후 접속
  - Python 3: `python3 -m http.server 8000` 후 `http://localhost:8000/kaist-sleek-CV-master/`

## 기술 스택
- HTML5, CSS3 (순수 스타일시트), 바닐라 JavaScript
- 빌드/의존성 없음 (npm, 프레임워크 미사용)

## 주요 기능
- 반응형 헤더/내비게이션
  - 햄버거 메뉴(모바일), 현재 섹션 하이라이트, 고정 헤더 스크롤 스타일 변경
- 부드러운 스크롤 및 고정 헤더 오프셋 처리
- 히어로 영역 타이핑 효과
  - 단일 타이핑(`typeWriter`), 다중 텍스트 순환(`multiTypeWriter` + blinking cursor)
- 스킬 바 인터섹션 애니메이션
  - `IntersectionObserver`로 뷰포트 진입 시 진행바 채움
- 스크롤 인(페이드/트랜지션) 애니메이션
  - 타임라인/프로젝트/스킬 블록에 AOS 유사 효과
- 연락처 폼 프런트엔드 유효성 검사 (데모용 알림)
- 유틸리티: 디바운스/스로틀, 페이드인 로딩

## 디렉터리 구조


## 파일별 개요
- `index.html`
  - 섹션: `#home`(Hero), `#about`, `#skills`, `#experience`, `#projects`, `#contact`
  - 히어로: 이름/타이핑 텍스트(`.typing-text`의 `data-texts`에 배열), 액션 버튼
  - 스킬: `.skill-progress`에 `data-width`(예: `90%`)로 목표 폭 설정
  - 경력: 수평 카드들의 교차 정렬 + 타임라인 마커
  - 프로젝트: 카드형 목록(기술 태그/링크)
  - 연락처: 정보 + 폼(이름/이메일/제목/메시지)

- `style.css`
  - 고정 헤더, 그라디언트 히어로, 타이핑 텍스트 하이라이트/섬광(`shimmer`), 버튼 스타일
  - 스킬 바 진행 애니메이션(`fillBar`) 및 `.skill-progress.animate`
  - 타임라인 수직선/마커, 홀짝 레이아웃, 그림자/모서리 라운딩
  - 프로젝트 카드 호버 상승, 반응형 레이아웃(768px/480px)
  - `section { scroll-margin-top: 80px; }`으로 고정 헤더 보정

- `script.js`
  - 모바일 메뉴 토글, 내비게이션 클릭 시 스무스 스크롤(헤더 높이 보정)
  - 스크롤 시 헤더 스타일 업데이트, 현재 섹션에 맞춘 `.nav-link.active`
  - 스킬 바: `IntersectionObserver`로 `data-width`만큼 확장 후 `animate` 클래스 부여
  - 타이핑 효과: `typeWriter`(단일), `multiTypeWriter`(배열 순환 + 삭제/입력)
  - 스크롤 인 애니메이션: 초기 opacity/translate 지정 후 뷰포트 진입 시 원복
  - 폼 제출 유효성 검사(필수값 + 이메일 정규식) → 성공 알림/리셋
  - 접근성/사용성: ESC/외부클릭/리사이즈 시 모바일 메뉴 닫기, 60fps 목표 스크롤 스로틀러 예시

## 커스터마이징 가이드
- 텍스트/프로필
  - `index.html`의 히어로 이름/소개 문구, About/Experience/Projects/Contact 섹션 텍스트 수정
  - 히어로 멀티 타이핑: `.typing-text`의 `data-texts` JSON 배열 편집
- 스킬 바
  - `Skills` 섹션의 각 `.skill-progress`에 있는 `data-width`를 원하는 수치(%)로 변경
- 색상/테마
  - `style.css`의 그라디언트/포인트 컬러(`#3498db`, `#2ecc71` 등), 히어로 배경 조정
- 애니메이션 속도
  - 타이핑: `multiTypeWriter(element, texts, typeSpeed, deleteSpeed, pauseTime)` 인자 변경
  - 스크롤 인: `transition` 지속시간/이징, `elementVisible`(노출 임계) 조정
- 링크/연락처
  - 프로젝트 카드의 `Live Demo/GitHub` 링크, `Contact` 섹션 이메일/전화/소셜 수정
- 배포
  - 정적 호스팅(Netlify, GitHub Pages, Vercel)에 그대로 업로드하면 동작

## 접근성/SEO 팁
- 이미지 대체텍스트 추가(현재 이모지 플레이스홀더)
- `lang="ko"` 및 의미적 태그 유지, 메타 태그(설명/OG) 보강 권장
- 대비/포커스 스타일, 키보드 트랩 방지 확인

## 브라우저 호환성
- 최신 크롬/파이어폭스/사파리/엣지에서 동작 가정
- `IntersectionObserver` 미지원 구형 브라우저에서는 스킬 바 애니메이션이 동작하지 않을 수 있음

## 한계/주의
- 연락처 폼은 데모용(백엔드 전송 없음). 실제 전송은 서버/서비스(API) 연동 필요
- 워크스페이스 루트의 `index.html`(별도 217줄)은 이 템플릿과 별개일 수 있습니다. 본 README는 `kaist-sleek-CV-master/`를 기준으로 합니다.

## 라이선스
- 레포에 명시된 라이선스가 없습니다. 사용 목적에 맞는 라이선스를 추가하시길 권장합니다.

## 크레딧
- 폰트: Google Fonts — Noto Sans KR
- 아이콘: 이모지 플레이스홀더 사용
