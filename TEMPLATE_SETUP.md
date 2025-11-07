# Project Setup Template - Usage Guide

이 템플릿을 사용하여 새로운 프로젝트를 빠르게 시작하는 방법입니다.

---

## 🚀 Step 1: Clone the Template

```bash
git clone <this-template-repo> <your-project-name>
cd <your-project-name>
```

---

## 📝 Step 2: Configure Project Metadata

### Edit `.project-info`

이 파일에서 다음 항목들을 수정하세요:

```bash
nano .project-info
```

**필수 항목 (Required)**:

- `PROJECT_NAME`: 프로젝트 이름 (예: "my-awesome-app")
- `PROJECT_DESCRIPTION`: 프로젝트 설명
- `PROJECT_VERSION`: 시작 버전 (일반적으로 "0.1.0")
- `DEVELOPER_NAME`: 당신의 이름

**선택 항목 (Optional)**:

- `BACKEND_FRAMEWORK`: FastAPI, Django, Flask 등
- `PYTHON_VERSION`: 3.11 (또는 원하는 버전)
- `DATABASE_TYPE`: PostgreSQL, MySQL, SQLite 등

**예시**:

```bash
PROJECT_NAME="my-learning-app"
PROJECT_DESCRIPTION="AI-powered learning assistant"
PROJECT_VERSION="0.1.0"
DEVELOPER_NAME="john-doe"
DATABASE_TYPE="PostgreSQL"
```

---

## 📚 Step 3: Write Feature Requirements

### Edit `docs/FEATURE_REQUIREMENTS.md`

프로젝트의 모든 기능을 REQ ID와 함께 정의하세요:

```bash
nano docs/FEATURE_REQUIREMENTS.md
```

**예시 구조**:

```markdown
### REQ-A1-Authentication

**Description**: User login with email and password

**Priority**: High

**Acceptance Criteria**:
- [ ] User can submit email/password
- [ ] System validates credentials
- [ ] System returns auth token
- [ ] System rejects invalid credentials

**Implementation Details**:
- Location: `src/backend/auth/`
- Input: username (str), password (str)
- Output: token (str)
```

---

## 🏗️ Step 4: Define Architecture

### Edit `docs/ARCHITECTURE.md`

프로젝트의 전체 시스템 아키텍처를 정의하세요:

```bash
nano docs/ARCHITECTURE.md
```

**포함할 내용**:

- 시스템 다이어그램
- 주요 컴포넌트 설명
- 데이터 모델 (SQL/NoSQL)
- 핵심 워크플로우
- 보안 및 성능 요구사항

---

## 👥 Step 5: Update README

### Edit `README.md`

프로젝트에 대한 사용자 친화적 가이드를 작성하세요:

```bash
nano README.md
```

**수정 항목**:

- 프로젝트 이름 및 설명
- 주요 기능 (Features 섹션)
- 빠른 시작 가이드 (필요시)

---

## 🔧 Step 6: Start Development

### 의존성 설치 및 개발 환경 설정

```bash
./tools/dev.sh up              # 개발 서버 시작
```

다른 터미널에서:

```bash
./tools/dev.sh test            # 테스트 실행
./tools/dev.sh format          # 코드 포맷
```

---

## 💡 Step 7: Begin REQ-Based Development

### Claude Code로 기능 구현하기

```bash
claude
```

프롬프트에서:

```
REQ-A1-Authentication 기능 구현해
```

**자동 워크플로우**:

1. **Phase 1**: Specification - 명세 검토
2. **Phase 2**: Test Design - 테스트 설계 검토
3. **Phase 3**: Implementation - 코드 작성 및 검증
4. **Phase 4**: Summary - 결과 보고 및 commit

자세한 내용은 `CLAUDE.md` → "REQ-Based Development Workflow" 참고

---

## 📋 Development Checklist

```
프로젝트 초기 설정 체크리스트:

[ ] .project-info 파일 수정
[ ] docs/FEATURE_REQUIREMENTS.md 작성
[ ] docs/ARCHITECTURE.md 작성
[ ] README.md 업데이트
[ ] ./tools/dev.sh up 실행 (의존성 설치)
[ ] 첫 번째 REQ 구현 시작
```

---

## 🎯 Key Commands

| Command | Purpose |
|---------|---------|
| `./tools/dev.sh up` | Start dev server |
| `./tools/dev.sh test` | Run tests |
| `./tools/dev.sh format` | Format + lint code |
| `./tools/dev.sh shell` | Enter project shell |
| `./tools/commit.sh` | Create conventional commit |
| `tox -e style` | Full code quality checks |

---

## ❓ Troubleshooting

### Issue: "Module not found" errors

**Solution**: Run `./tools/dev.sh up` to install dependencies

### Issue: Type checking fails

**Solution**: Run `tox -e mypy` to see strict type errors

### Issue: Import errors after changes

**Solution**: Run `./tools/dev.sh format` to fix imports

---

## 📚 Further Reading

- **CLAUDE.md**: Development conventions and REQ workflow
- **docs/FEATURE_REQUIREMENTS.md**: Your project's requirements
- **docs/ARCHITECTURE.md**: Your system design
- **README.md**: Public project documentation

---

**Ready to start?** Begin with Step 1 above or run:

```bash
# Quick setup walkthrough
echo "✓ Clone template"
echo "✓ Edit .project-info"
echo "✓ Edit docs/FEATURE_REQUIREMENTS.md"
echo "✓ Run ./tools/dev.sh up"
echo "✓ Start first REQ with: claude"
```
