# 🖥️ Web Frontend — 번역 결과 시각화

> **반응형 메뉴판 번역 결과 대시보드 (Next.js 14)**

| 기술 스택 | 역할 |
|-----------|------|
| **Next.js 14** | React 서버 컴포넌트 프레임워크 |
| **NextUI** | UI 컴포넌트 라이브러리 |
| **TailwindCSS** | 유틸리티 기반 스타일링 |
| **React Context API** | 전역 상태 관리 (DataContext) |

---

## 📁 프로젝트 구조

```
src/
├── app/
│   ├── api/
│   │   ├── receive/route.jsx      # FastAPI에서 JSON 수신 (POST)
│   │   └── save-images/route.jsx  # 이미지 저장 처리
│   ├── loading/
│   │   └── page.jsx               # 로딩 UI (Progress Bar)
│   ├── result/
│   │   ├── page.jsx               # 번역 결과 그리드 페이지
│   │   └── SearchIcon.jsx         # 검색 아이콘 컴포넌트
│   ├── layout.jsx                 # 루트 레이아웃
│   ├── page.jsx                   # 메인 페이지
│   └── globals.css                # 전역 스타일
├── context/
│   └── DataContext.jsx            # Base64 이미지 + 텍스트 전역 상태
└── hooks/
    └── useWheelSelection.jsx      # 휠 선택 커스텀 훅
```

## 🔄 데이터 흐름

```
FastAPI 서버
    │ POST /api/receive
    │ (Base64 이미지 + 번역 텍스트 JSON)
    ↓
DataContext (전역 상태 저장)
    ↓
/result 페이지
    ├── 원본 메뉴판 이미지
    ├── Bounding Box 검출 시각화 이미지
    └── 크롭 이미지 + 한국어/영어 텍스트 그리드
```

## 📱 반응형 지원

- Flutter 앱 내 `webview_flutter`로 로드되므로 **모바일 최적화**가 핵심입니다.
- NextUI + TailwindCSS의 Breakpoint 시스템으로 모바일/태블릿/데스크톱 모두 대응합니다.

## 🚀 실행

```bash
npm install
npm run dev    # http://localhost:3000
```
