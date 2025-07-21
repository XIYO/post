# Claude Code macOS 설치 가이드

## 시스템 요구사항

- macOS 10.15 (Catalina) 이상
- Apple Silicon (M1/M2/M3) 또는 Intel 프로세서
- 인터넷 연결 필요

## 설치 방법

### 방법 1: Homebrew를 통한 설치 (권장)

```bash
brew install claude
```

설치 확인:
```bash
claude --version
```

### 방법 2: 직접 다운로드

1. [Claude Code 다운로드 페이지](https://claude.ai/download) 방문
2. macOS 버전 다운로드
3. 다운로드한 `.pkg` 파일 실행
4. 설치 마법사 지시에 따라 설치

## 초기 설정

### 1. Claude Code 로그인

```bash
claude login
```

브라우저가 열리면 Anthropic 계정으로 로그인합니다.

### 2. 기본 모델 설정

```bash
# Opus 모델로 설정 (가장 강력함)
claude config set -g model opus

# Sonnet 모델로 설정 (빠른 응답)
claude config set -g model sonnet
```

### 3. 테마 설정

```bash
# 다크 테마
claude config set -g theme dark

# 라이트 테마
claude config set -g theme light
```

## 전역 설정 관리

### 설정 파일 위치

- 전역 설정: `~/.claude/settings.json`
- 프로젝트 설정: `.claude/settings.json`
- 로컬 설정: `.claude/settings.local.json`

### 주요 설정 옵션

```bash
# 자동 업데이트 활성화/비활성화
claude config set -g autoUpdates true

# 상세 출력 모드
claude config set -g verbose true

# 병렬 작업 수 설정
claude config set -g parallelTasksCount 2

# Todo 기능 활성화
claude config set -g todoFeatureEnabled true
```

### 설정 확인

```bash
# 모든 전역 설정 보기
claude config list -g

# 특정 설정 값 확인
claude config get model
```

## IDE 통합

### VS Code 확장 설치

```bash
# VS Code가 설치되어 있다면 자동으로 확장 설치
claude
```

VS Code에서 수동 설치:
1. Extensions 탭 열기 (⌘+Shift+X)
2. "Claude" 검색
3. "Install" 클릭

### JetBrains IDE 플러그인

1. Settings/Preferences 열기 (⌘+,)
2. Plugins 섹션으로 이동
3. Marketplace에서 "Claude" 검색
4. Install 클릭

## 프로젝트별 설정

### 프로젝트 초기화

```bash
# 현재 디렉토리를 Claude 프로젝트로 초기화
claude init
```

### 프로젝트 설정 예시

`.claude/settings.json`:
```json
{
  "model": "opus",
  "parallelTasksCount": 3,
  "env": {
    "NODE_ENV": "development"
  }
}
```

### 로컬 설정 (개인용)

`.claude/settings.local.json`:
```json
{
  "verbose": true,
  "theme": "dark"
}
```

## 유용한 명령어

```bash
# 도움말 보기
claude --help

# 현재 설정 확인
claude config list

# 캐시 정리
claude cache clear

# 업데이트 확인
claude update
```

## 문제 해결

### 권한 문제

```bash
# Claude가 파일에 접근할 수 없을 때
sudo claude auth refresh
```

### 설정 초기화

```bash
# 모든 설정을 기본값으로 되돌리기
rm -rf ~/.claude/settings.json
claude config reset
```

### 로그 확인

```bash
# 디버그 로그 보기
claude logs --tail 50
```

## 업데이트

### 자동 업데이트

기본적으로 활성화되어 있으며, Claude Code가 백그라운드에서 자동으로 업데이트됩니다.

### 수동 업데이트

```bash
# Homebrew로 설치한 경우
brew upgrade claude

# 직접 설치한 경우
claude update
```

## 제거

```bash
# Homebrew로 설치한 경우
brew uninstall claude

# 설정 파일도 함께 제거
rm -rf ~/.claude
```

## 추가 리소스

- [공식 문서](https://docs.anthropic.com/claude-code)
- [GitHub 이슈](https://github.com/anthropics/claude-code/issues)
- [커뮤니티 포럼](https://community.anthropic.com)