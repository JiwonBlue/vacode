# 카페24 변환 및 8번 갤러리 게시판 배포 가이드

기존 정적 웹사이트를 **카페24 스마트디자인 템플릿(갤러리 게시판 ID 8번)** 연동 구조로 변환한 후, 카페24 시스템 CSS 간섭 및 8번 갤러리 게시판(목록/글쓰기/글수정/글보기) 전용 디자인 커스텀을 완료한 버전입니다. 모든 파일은 **[cafe24_skin](file:///c:/Users/softchain/Desktop/카페24%20(2)/cafe24_skin)** 폴더에 정돈되어 있습니다.

---

## 1. 최근 주요 변경 내역

1. **8번 갤러리 게시판 목록/글쓰기/글수정/글보기 UI 완성**:
   * `board/gallery/list.html`, `write.html`, `modify.html`, `read.html` 템플릿을 서브 레이아웃(`sub_layout.html`) 및 좌측 420px 사이드바와 결합하여 VACODE 통일감 유지.
   * 브라우저 기본 fieldset 박스 제거, 브레드크럼 리셋, 포트폴리오 폼 입력창, 썸네일 파일 업로드, [글쓰기]/[등록]/[취소] 버튼 디자인 커스텀 적용.
2. **ABOUT / CONTACT 페이지 개별 스타일 규격 복원**:
   * 원본 `about.html` 730px 회색 박스, 700px Sign 이미지, 30px 제목 폰트 및 `contact.html` 60px 입력창 등의 고유 `<style>` 완전 복원.
3. **SUITE 웹폰트 및 카페24 기본 폰트(돋움/굴림) 덮어쓰기 방어**:
   * `VACODE_style.css` 최상단 `@import` 주입 및 전역 폰트 우선 순위 지정.

---

## 2. 카페24 FTP 업로드 안내

FTP 프로그램(FileZilla 등)을 통해 `cafe24_skin` 폴더의 파일들을 카페24 스킨 목적지 폴더(예: `/sde_design/skin1/`)로 덮어쓰기 업로드하시면 적용됩니다.

| 로컬 파일 (`cafe24_skin/` 기준) | 서버 목적지 폴더 (`/sde_design/skin1/` 기준) |
| :--- | :--- |
| `index.html` | `/index.html` |
| `layout/basic/layout.html` | `/layout/basic/layout.html` |
| `layout/basic/sub_layout.html` | `/layout/basic/sub_layout.html` |
| `css/VACODE_style.css` | `/css/VACODE_style.css` |
| `layout/basic/css/VACODE_style.css` | `/layout/basic/css/VACODE_style.css` |
| `board/gallery/list.html` | `/board/gallery/list.html` |
| `board/gallery/write.html` | `/board/gallery/write.html` |
| `board/gallery/modify.html` | `/board/gallery/modify.html` |
| `board/gallery/read.html` | `/board/gallery/read.html` |
| `VACODE/about.html` | `/VACODE/about.html` |
| `VACODE/portfolio.html` | `/VACODE/portfolio.html` |
| `VACODE/portfolio_detail.html` | `/VACODE/portfolio_detail.html` |
| `VACODE/contact.html` | `/VACODE/contact.html` |
