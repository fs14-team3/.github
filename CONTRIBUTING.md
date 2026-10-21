# 협업 규칙

fs14-team3의 모든 저장소(moving-fe, moving-be)에 적용됩니다.

## 브랜치

| 브랜치      | 용도                                  |
| ----------- | ------------------------------------- |
| `main`      | 배포 (FE: Vercel, BE: EC2)            |
| `develop`   | 통합 브랜치, PR의 기본 대상           |
| 작업 브랜치 | 최신 `develop`에서 생성, 머지 후 삭제 |

작업 브랜치 이름은 `타입/설명` 형식입니다. 예: `feat/mover-search`, `fix/refresh-cookie`

`main`과 `develop`에는 직접 push하지 않습니다.

## 커밋 메시지

[Conventional Commits](https://www.conventionalcommits.org/ko/v1.0.0/) 형식을 사용하며, commitlint가 커밋할 때 검사합니다.

```text
타입(스코프): 설명
```

- 타입: `feat` `fix` `refactor` `test` `docs` `style` `chore` `ci` `perf`
- 스코프는 선택이며 소문자로 씁니다. 예: `auth`, `quote`, `review`

```text
feat(auth): 카카오 로그인 추가
fix(quote): 견적 5개 초과 시 409 반환
docs: README 실행 방법 수정
```

## Pull Request

- 대상은 `develop`입니다. PR 제목도 커밋 메시지 형식을 따릅니다 (CI가 검사).
- **Squash merge**로 머지합니다. PR 제목이 그대로 `develop`의 커밋 메시지가 됩니다.
- 배포는 `develop` → `main` PR로 하고, 이 PR만 **Merge commit**으로 머지합니다. squash하면 두 브랜치의 이력이 어긋납니다.
- 본문에 `Closes #이슈번호`를 적어 이슈를 자동으로 닫습니다.
- 리뷰 승인 1명 이상, CI 통과 후 머지합니다.
- PR은 작게 유지합니다. 하나의 PR은 하나의 이슈를 다룹니다.
- **API 변경**: `moving-be`의 `docs/api/openapi.yaml`을 같은 PR에서 수정합니다. FE 팀 리뷰가 필요합니다 (CODEOWNERS).
- **환경 변수 추가**: `.env.example`과 README의 환경 변수 표를 같은 PR에서 수정합니다.

## 이슈

- 마일스톤 담당자가 마일스톤 설명의 작업 목록을 보고 직접 작성합니다.
- 템플릿(기능 / 버그)으로 작성하고, 담당자, 라벨, 마일스톤(M1–M8)을 지정합니다.
- 라벨: `feat` `bug` `refactor` `docs` `test` `chore`
- 선행 작업이 있으면 이슈의 Relationships에서 "blocked by"로 연결합니다.
