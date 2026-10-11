# 스마트스토어 AI 운영팀의 하루 — 1차시

현재 완성된 수업 UI, 상품별 프롬프트 작성, 검토, 패들렛 복사·제출 확인, 사원→대리 승진을 포함합니다.

## GitHub Pages용 파일
- `index.html`: 바로 배포할 수 있는 전체 HTML/CSS/JavaScript
- `.nojekyll`: 정적 파일 배포용

압축을 풀고 위 두 파일을 GitHub 저장소의 최상위에 올립니다. 저장소 Settings → Pages에서 배포할 브랜치와 루트 폴더를 선택합니다. 설정 화면이나 사용 가능한 기능은 계정·저장소에 따라 다를 수 있습니다.

이 버전은 진행 내용을 localStorage에 저장합니다. 같은 기기·같은 브라우저·같은 사이트 주소에서 이어서 사용합니다. 브라우저 저장소 삭제, 시크릿 창 종료, 다른 기기로 변경 시 기록을 복구할 수 없습니다. 사원증 사진도 해당 기기에만 저장됩니다. 기존 Sites 주소의 기록은 새 GitHub Pages 주소로 자동 이전되지 않습니다.

KoPub 돋움체는 외부 CDN에서 불러오므로 온라인 연결이 필요합니다. 패들렛 게시 여부는 자동 확인하지 않으며 학생이 화면의 제출 확인 버튼을 누릅니다.

## DB 기능을 포함한 원본
`server-source/`에 현재 사이트의 원본을 포함했습니다.
- `build_app.py`: 수업 화면 전체 HTML/CSS/JS와 Worker를 생성하는 원본
- `worker/index.js`: Cloudflare Worker 서버와 화면
- `migrations/`: D1 테이블 생성 SQL
- `scripts/`, `drizzle/`, `package.json`: 원본 빌드·검증 파일

DB가 필요한 경우 GitHub는 소스 저장소로 사용하고, Worker를 지원하는 호스팅에서 배포해야 합니다. DB 바인딩 이름은 `DB`이며 migrations SQL을 적용해야 합니다. 원본의 Sites 전용 프로젝트 식별자와 호스팅 설정은 포함하지 않았으므로 별도 환경에 맞춰 설정하세요. 인증 토큰, 학생 기록, 사원증 사진, Git 이력은 포함하지 않았습니다.

루트 index.html은 원본에서 API 저장을 제거해 만든 정적 배포본입니다. 원본 build_app.py를 수정·실행하면 Worker 소스가 생성되며 루트 정적 HTML은 별도로 다시 내보내야 합니다.
