# 🥗 BobFit - AI 맞춤 식단 및 운동 코칭 앱

> **Google Gemini API**를 활용하여 개인의 신체 정보, 목표 체중, 선호 운동을 바탕으로 하루 식단을 분석하고 맞춤형 권장 식단 및 운동 루틴을 코칭해 주는 모바일 최적화 웹 앱(PWA)입니다.

---

## ✨ 바로가기 : https://jydarkblue.github.io/BobFit/

---
## 🛠️ ScreenShot
<img width="874" height="783" alt="image" src="https://github.com/user-attachments/assets/92d70b5f-699f-45cc-9ecb-f6dc260d7ad7" />

---

## 🌟 주요 특징

1. **Gemini AI 연동**: 최신 Gemini Flash 모델을 활용하여 빠르고 정확한 일일 영양 평가, 칼로리 계산, 맞춤형 권장 식단 및 운동 가이드를 제공합니다.
2. **개인 맞춤형 코칭**: 성별, 나이, 키, 현재 몸무게뿐만 아니라 **목표 체중**과 **선호 운동(예: 수영, 홈트 등)**을 반영하여 사용자 최적화 코칭을 수행합니다.
3. **날짜별 기록 및 시각화 (Chart.js)**: 날짜별 식단과 체중 변화를 기록하고, 꺾은선 그래프를 통해 섭취 칼로리와 몸무게 추이를 한눈에 파악할 수 있습니다.
4. **오프라인/로컬 데이터 관리 (`localStorage`)**: 별도의 백엔드 서버나 데이터베이스 없이, 브라우저의 `localStorage`를 통해 사용자의 프로필, API Key, 날짜별 식단 기록을 안전하게 기기 내부에 보관합니다.
5. **보안성 강화 (API Key 분리)**: 소스 코드 노출 시 API Key가 유출되는 것을 방지하기 위해, 사용자가 직접 프로필 설정 화면에서 자신의 Gemini API Key를 입력하고 관리하도록 설계되었습니다.
6. **PWA (Progressive Web App) 지원**: 모바일 브라우저(Chrome, Safari)에서 접속 후 **[홈 화면에 추가]**를 통해 앱스토어 설치 없이 스마트폰 전용 앱처럼 간편하게 사용할 수 있습니다.

---

## 🛠️ 기술 스택 (Tech Stack)

* **Frontend**: HTML5, Vanilla JavaScript, Tailwind CSS (Responsive UI)
* **AI Integration**: Google Gemini API (`gemini-3.8-flash`)
* **Visualization**: Chart.js (체중 및 칼로리 변화 추이 그래프)
* **Storage**: Browser LocalStorage (프로필, 식단 로그, API Key 저장)
* **Deployment**: GitHub Pages (HTTPS 정적 웹 호스팅)

---

## 📐 코드 구현 방식 및 구조

* **단일 파일 구조 (`index.html`)**: 별도의 빌드 도구(Webpack, Vite 등)나 복잡한 설정 없이, 순수 HTML/JS 파일 하나로 동작하여 GitHub Pages 등을 통해 즉시 배포 및 실행이 가능합니다.
* **상태 관리 및 영속성 (`localStorage`)**:
  * `bobfit_user_profile`: 사용자 신체 스펙, 목표, 선호 운동 및 Gemini API Key를 JSON 형태로 저장합니다.
  * `bobfit_daily_logs`: 날짜별(`YYYY-MM-DD`) 아침, 점심, 저녁, 간식 기록 및 AI 분석 결과(`resultObj`)를 매핑하여 관리합니다.
* **AI 프롬프트 엔지니어링**: 사용자의 프로필과 식단 데이터를 조합하여 구조화된 프롬프트를 생성하고, Gemini API로부터 **순수 JSON 포맷**(`profile_summary`, `foods_summary`, `total_calories`, `diet_feedback`, `recommended_diet`, `exercise_recommendation`)으로 응답을 받아 안전하게 파싱 및 렌더링합니다.

---

## 🚀 사용 방법 (Getting Started)

### 1. 사전 준비
* Google AI Studio에서 **Gemini API Key**를 발급받습니다.

### 2. 실행 방법 (로컬)
1. 본 저장소의 코드를 다운로드(`index.html`)합니다.
2. `index.html` 파일을 더블클릭하여 웹 브라우저(Chrome 등)로 엽니다.

### 3. 앱 사용 순서
1. **프로필 설정**: 좌측 사이드바에서 성별, 나이, 키, 현재 몸무게, **목표 몸무게**, **선호 운동**을 입력하고, 발급받은 **Gemini API Key**를 입력합니다. (데이터는 자동으로 저장됩니다.)
2. **식단 기록**: 메인 화면에서 기록할 날짜를 선택(또는 '오늘' 버튼 활용)하고 아침, 점심, 저녁, 간식 내용을 입력합니다.
3. **AI 분석**: **[하루 전체 식단 분석 및 칼로리 계산하기]** 버튼을 누르면 AI가 영양 평가, 권장 식단, 맞춤 운동 루틴을 리포트로 제공합니다.
4. **기록 확인 및 관리**: 하단의 날짜 이동 버튼(`<<`, `>>`)이나 저장된 식단 히스토리 태그를 통해 과거 기록을 쉽게 넘겨볼 수 있으며, 그래프 보기 모드로 체중 및 칼로리 변화 추이를 확인할 수 있습니다.

---

## 📱 스마트폰에 앱으로 설치하기 (PWA)
1. GitHub Pages 등을 통해 배포된 웹 앱 주소로 스마트폰 브라우저(Chrome 또는 Safari)에 접속합니다.
2. 브라우저 메뉴에서 **[홈 화면에 추가]** 또는 **[앱 설치]**를 선택합니다.
3. 스마트폰 홈 화면에 생성된 **BobFit** 아이콘을 눌러 일반 모바일 앱처럼 편리하게 사용하세요!

---

## 📄 License
This project is licensed under the MIT License.
