# 카페24 변환 및 버그 수정 완료 배포 가이드

기존 정적 웹사이트를 **카페24 스마트디자인 템플릿(갤러리 게시판 ID 8번)** 연동 구조로 변환한 후, 카페24 시스템 CSS 간섭 및 누락된 개별 페이지 스타일 규격을 전수 복원하여 완벽하게 보완한 버전입니다. 모든 수정사항은 **[cafe24_skin](file:///c:/Users/softchain/Desktop/카페24%20(2)/cafe24_skin)** 폴더 안에 적용되었습니다.

---

## 1. 최근 주요 원인 파악 및 수정 내역

1. **ABOUT / CONTACT 페이지 개별 스타일 규격 복원 (원형 대형 박스/폰트 복구)**:
   * **원인**: 원본 `about.html`의 730px 회색 메인 박스(`about_visual_box`), 700px 대형 sign 이미지(`visual_img`), 30px 제목 폰트(`visual_txt h2`), `process_list` 3열 및 `partner_card` 480px 규격과 `contact.html` 60px 입력창 등의 개별 `<style>` 규격이 Cafe24 변환 과정에서 누락되어 서브 화면이 작게 나오고 깨지던 문제 원천 해결.
   * **수정**: [about.html](file:///c:/Users/softchain/Desktop/카페24%20(2)/cafe24_skin/VACODE/about.html#L3-L228) 및 [contact.html](file:///c:/Users/softchain/Desktop/카페24%20(2)/cafe24_skin/VACODE/contact.html#L3-L62) 상단에 원본 고유 `<style>` 블록을 완전 복원.
2. **SUITE 웹폰트 및 카페24 기본 폰트(돋움/굴림) 강제 덮어쓰기 방어**:
   * CSS 최상단에 SUITE 폰트 `@import` 및 `body, h1~h6, p, a, div, span, input, textarea, button { font-family: var(--vc-font-suite) !important; }`를 추가하여 카페24 어드민/기본 CSS 폰트 강제 덮어쓰기 방어.
3. **헤더 로고 치우침 방지**:
   * 카페24 기본 CSS의 `position: absolute; float: left;` 간섭을 완벽히 방어(`position: static !important; float: none !important; margin-right: 254px !important;`)하여 헤더 수직 정중앙 위치 보정.
4. **포트폴리오 예외 문구 오류 해결**:
   * `module="board_empty_8"`를 `module="board_listpackage_8"` 내부에 올바르게 배치하여 게시글이 1개 이상 존재할 때 '등록된 포트폴리오가 없습니다'가 정상적으로 자동 숨김 처리됨.
5. **메인 Swiper 모듈 구조 교정**:
   * `index.html`에서 `module="board_list_8"`을 `.swiper-slide` 슬라이드 단위로 지정하고 Swiper 슬라이더 동작과 `board_empty_8` 모듈이 충돌하지 않도록 정돈.
6. **포트폴리오 상세 Masonry 그리드 복원**:
   * `portfolio_detail.html` 및 `VACODE_style.css`에 핀터레스트 스타일 다단 그리드(`column-count: 3; column-gap: 25px;` 및 반응형 미디어쿼리)를 탑재하여 본문 시공 이미지 자동 3열/2열/1열 배치 완성.
7. **미사용 `board` 폴더 제거**:
   * `board/gallery/list.html` 및 `read.html` 폴더 삭제 완료.

---

## 2. 카페24 FTP 업로드 방법

FTP 프로그램(FileZilla 등)을 통해 `cafe24_skin` 폴더의 파일들을 카페24 스킨 목적지 폴더(예: `/sde_design/skin1/`)로 덮어쓰기하여 업로드하시면 적용됩니다.

| 로컬 파일 (`cafe24_skin/` 기준) | 서버 목적지 폴더 (`/sde_design/skin1/` 기준) |
| :--- | :--- |
| `index.html` | `/index.html` |
| `layout/basic/layout.html` | `/layout/basic/layout.html` |
| `layout/basic/sub_layout.html` | `/layout/basic/sub_layout.html` |
| `css/VACODE_style.css` | `/css/VACODE_style.css` |
| `layout/basic/css/VACODE_style.css` | `/layout/basic/css/VACODE_style.css` |
| `VACODE/about.html` | `/VACODE/about.html` |
| `VACODE/portfolio.html` | `/VACODE/portfolio.html` |
| `VACODE/portfolio_detail.html` | `/VACODE/portfolio_detail.html` |
| `VACODE/contact.html` | `/VACODE/contact.html` |
