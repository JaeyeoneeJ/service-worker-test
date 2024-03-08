# service-worker-test

## 0. 개요

- 이 프로젝트는 React App에서 service-worker를 테스트하고 PWA를 연구하기 위해 제작되었습니다.
- 이 프로젝트는 CRA 4.0+ 이후 CRA(create-react-app)의 PWA template을 활용하여 제작되었습니다.

```bash
npx create-react-app my-app --template cra-template-pwa

# typescript로 설치 시
npx create-react-app my-app --template cra-template-pwa-typescript
```

## 1. 개발 환경

이 프로젝트는 다음과 같은 환경에서 개발되었습니다.

- npm: 10.2.4
- node: v20.11.0
- dependencies

  - "@testing-library/jest-dom": "^5.17.0",
  - "@testing-library/react": "^13.4.0",
  - "@testing-library/user-event": "^13.5.0",
  - "react": "^18.2.0",
  - "react-dom": "^18.2.0",
  - "react-scripts": "5.0.1",
  - "web-vitals": "^2.1.4",
  - "workbox-background-sync": "^6.6.0",
  - "workbox-broadcast-update": "^6.6.0",
  - "workbox-cacheable-response": "^6.6.0",
  - "workbox-core": "^6.6.0",
  - "workbox-expiration": "^6.6.0",
  - "workbox-google-analytics": "^6.6.1",
  - "workbox-navigation-preload": "^6.6.0",
  - "workbox-precaching": "^6.6.0",
  - "workbox-range-requests": "^6.6.0",
  - "workbox-routing": "^6.6.0",
  - "workbox-strategies": "^6.6.0",
  - "workbox-streams": "^6.6.0"

> 위의 dependencies는 `npx create-react-app my-app --template cra-template-pwa`로 생성 시 자동으로 설치되는 dependencies입니다.

- 이 프로젝트의 구조는 다음과 같습니다.

```
.
├── README.md
├── package-lock.json
├── package.json
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── reportWebVitals.js
    ├── service-worker.js
    ├── serviceWorkerRegistration.js
    └── setupTests.js
```

## 2. 프로젝트 실행

### 1) `npm start` || `npm run start`

- 위 명령어를 통해 개발 모드의 앱을 실행할 수 있으며, [http://localhost:3000](http://localhost:3000)의 기본 포트의 브라우저에서 확인할 수 있습니다.

### 2) `npm run build`

- 위 명령어를 통해 개발 모드의 앱을 빌드할 수 있습니다.
- 만일 당신의 글로벌 환경에 http-server가 설치되어 있는 경우, 빌드 후, `npx http-server ./build`로 빌드된 앱을 확인할 수 있습니다.

## 3. 프로젝트 확인

- `npm start`와 같은 명령어로는 service-worker를 정상적으로 활용하는지 테스트할 수 없습니다.
- 이 프로젝트에서 service-worker가 정상 동작하는지 확인하기 위해서는 정적 파일을 간단한 웹 서버를 통해 제공하여야 합니다.
- 따라서 아래 중 원하는 지침을 사용하시기 바랍니다.

### 1) `http-server` 활용

```bash
# 아래 방법 중 원하는 방법으로 설치
npm install -g http-server

# 빌드 파일 생성
npm run build

# http-server로 빌드 파일 실행
npx http-server ./build # 기본 8080번 포트
# 또는
npx http-server ./build -p 3000
```

### 2) `serve` 활용

```bash
# serve 패키지를 전역으로 설치
npm install -g serve

# serve로 빌드 파일 실행
serve -s ./build # 기본 3000번 포트
# 또는
serve -s ./build -p 8080
```

### 3) 브라우저에서 확인

- Chrome Development Tools 실행
- `Application` Tab에서 `Service workers` 클릭

<img src="https://github.com/JaeyeoneeJ/service-worker-test/assets/77138259/0aa4ad72-f46c-49de-a7c0-113978f9a0e7" alt="applicationTab" />
