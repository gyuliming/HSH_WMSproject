🔹 운영 방식 (프로세스)

기능 시작

각자 맡은 기능별 feature/* 브랜치에서 작업 시작

예: A → feature/warehouse

작업 진행

작업 전 항상 develop 최신화

git checkout develop
git pull origin develop
git checkout feature/warehouse
git merge develop


기능 개발 및 commit

작업 완료 → Pull Request

feature/* → develop 으로 PR 생성

팀원 코드리뷰 후 머지

통합 테스트

develop에서 통합 확인 후 안정화

배포

릴리즈 시점에 develop → main 머지

필요 시 태그(v1.0.0) 달아서 관리

🔹 팁 (4명 협업시 유용한 규칙)

브랜치 네이밍 규칙 통일 : feature/{기능명}

commit 규칙 :

feat: 기능 추가

fix: 버그 수정

refactor: 리팩토링

docs: 문서 수정

PR 규칙 : 최소 1명 이상 리뷰 → 승인 후 머지
