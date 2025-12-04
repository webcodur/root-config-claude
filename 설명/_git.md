# .git/ 디렉토리

## 개요

`.git/` 디렉토리는 Git 버전 관리 시스템의 저장소 데이터를 담고 있다. Claude Code 설정을 버전 관리하고 원격 저장소와 동기화하는 데 사용된다.

---

## 용도

- 설정 파일 변경 이력 추적
- 원격 저장소(GitHub 등)와 동기화
- 여러 기기에서 동일 설정 공유
- 설정 변경 시 롤백 가능

---

## 주요 파일/폴더

```
.git/
├── config          # 저장소 설정 (원격 URL, 브랜치 등)
├── HEAD            # 현재 브랜치 참조
├── index           # 스테이징 영역
├── objects/        # Git 객체 (커밋, 트리, 블롭)
├── refs/           # 브랜치, 태그 참조
└── hooks/          # Git 훅 스크립트
```

---

## 설정 동기화 워크플로우

### 초기 설정 (새 기기)

```bash
# 저장소 클론
git clone https://github.com/your-username/claude-config.git ~/.claude
```

### 설정 변경 후 동기화

```bash
cd ~/.claude

# 변경 사항 확인
git status
git diff

# 커밋 및 푸시
git add .
git commit -m "설정 업데이트"
git push
```

### 다른 기기에서 최신 설정 가져오기

```bash
cd ~/.claude
git pull
```

---

## 브랜치 활용

여러 설정 프로필을 브랜치로 관리할 수 있다.

```bash
# 프로필 브랜치 생성
git checkout -b work-profile
git checkout -b personal-profile

# 프로필 전환
git checkout work-profile
git checkout personal-profile
```

---

## 주의사항

- `.git/` 폴더는 직접 수정하지 않는다
- `.credentials.json`은 `.gitignore`에 포함되어 Git에 추적되지 않는다
- 민감한 정보가 포함된 파일은 커밋하지 않는다
- `git push --force`는 다른 기기의 변경사항을 덮어쓸 수 있으므로 주의

---

## 원격 저장소 설정

### 새 저장소 연결

```bash
cd ~/.claude
git remote add origin https://github.com/your-username/claude-config.git
git push -u origin master
```

### 원격 URL 변경

```bash
git remote set-url origin https://github.com/new-username/claude-config.git
```

### 원격 저장소 확인

```bash
git remote -v
```
