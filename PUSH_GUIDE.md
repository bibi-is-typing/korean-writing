# GitHub 푸시 가이드 (v0.2.0 업데이트)

기존 `korean-writing` 저장소가 있다면 업데이트, 없다면 새로 생성.

---

## 시나리오 A. 기존 저장소가 있는 경우 (업데이트)

v0.1.0을 이미 푸시한 상태에서 v0.2.0으로 업데이트.

```bash
# 다운로드 받은 v2 폴더로 이동
cd ~/Downloads/korean-writing-v2

# 기존 .git 폴더 가져오기 (히스토리 유지하려면)
# 또는 v1 폴더의 기존 git 설정을 v2 폴더로 복사
# 가장 깔끔한 방법: v1 폴더에서 v2 내용으로 교체하고 커밋

# v1 폴더의 git 정보 가져오기
cp -r ~/Downloads/korean-writing-public/.git ./
# 또는 새로 init
# git init
# git remote add origin https://github.com/YOUR_USERNAME/korean-writing.git

# 기존 파일 삭제 후 새 파일 적용
git rm -rf korean-writing/
cp -r ../korean-writing-v2/korean-writing ./
git add .

# 커밋
git commit -m "v0.2.0: 7개 장르 분기 시스템 추가"

# 푸시
git push origin main
```

**히스토리 지우고 깔끔하게 다시 올리고 싶다면**:

```bash
cd ~/Downloads/korean-writing-v2

# .git 새로 만들기 (히스토리 X)
git init
git add .
git commit -m "v0.2.0: 7개 장르 분기 시스템"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/korean-writing.git
git push -u origin main --force
```

---

## 시나리오 B. 저장소가 없는 경우 (신규)

### STEP 1. GitHub에서 빈 저장소 만들기

1. [github.com/new](https://github.com/new) 접속.
2. **Repository name**: `korean-writing`.
3. **Description**: `AI 티 나는 한국어를 자연스러운 한국어로 다시 쓰는 Claude 스킬 (7개 장르 분기)`.
4. **Public** 선택.
5. **모든 옵션 체크 해제**.
6. **"Create repository"** 클릭.

### STEP 2. 로컬에서 푸시

```bash
cd ~/Downloads/korean-writing-v2

git init
git add .
git commit -m "Initial commit: v0.2.0"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/korean-writing.git
git push -u origin main
```

`YOUR_USERNAME` 은 본인 GitHub 사용자명으로 변경.

---

## STEP 3. (선택) Release 만들기

1. 저장소 페이지에서 **"Releases"** 클릭.
2. **"Create a new release"** 클릭.
3. **Tag**: `v0.2.0`.
4. **Title**: `v0.2.0 - 7개 장르 분기 시스템`.
5. **Description**:
   ```
   ## What's new in v0.2.0
   
   - 7개 글쓰기 장르 분기 처리 (blog, linkedin, business-comm, gov-doc, announcement, feedback, report)
   - business-writer 스킬 통합 (gov-doc, business-comm에 흡수)
   - 장르별 references 파일 추가 (7개)
   - 장르별 체크리스트 추가
   - 워크플로우 6단계 → 7단계로 확장
   ```
6. **Attach binaries**: `releases/korean-writing.skill` 첨부.
7. **"Publish release"**.

---

## 푸시 후 확인

- [ ] GitHub 페이지에서 7개 genre 파일 확인
- [ ] README 클론 URL의 `[사용자]` 부분 수정 후 재푸시
- [ ] About 섹션에 한 줄 설명 업데이트
- [ ] Topics 추가 (`claude`, `claude-skills`, `korean`, `writing`, `rewriting`, `multi-genre`)
