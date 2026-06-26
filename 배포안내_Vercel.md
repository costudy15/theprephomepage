# 더프렙 홈페이지 — Vercel 배포 안내

theprep.co.kr 에 새 홈페이지를 올리는 방법입니다.
사이트는 정적(HTML)이라 **빌드 과정 없이 그대로** 올라갑니다.

---

## 0. 준비물

- 올릴 파일 (이 폴더 안에 이미 있음)
  - `index.html`
  - `system.html`
  - `images/` 폴더 (사진 12장)
- **Vercel 계정** — 학생관리 앱 만들 때 쓰던 그 계정
- **가비아 로그인 정보** — 도메인 DNS 변경용

> ⚠️ 비밀번호·결제정보·DNS 값 입력은 본인 계정에서 직접 하셔야 합니다.

---

## 1단계 · Vercel에 사이트 올리기 (둘 중 하나)

### 방법 ① GitHub 연동 — 클릭만으로 (권장)
1. **github.com** 에서 새 저장소(repository) 만들기
   - 이름 예: `theprep-home` / Public·Private 무관
2. 저장소 화면에서 **"uploading an existing file"** 클릭
   → `index.html`, `system.html`, `images` 폴더를 **드래그해서 업로드** → Commit
3. **vercel.com** → **Add New → Project** → 방금 만든 GitHub 저장소 **Import**
4. Framework Preset 은 **"Other"** 그대로 → **Deploy**
5. 몇 초 뒤 `xxxx.vercel.app` 주소로 사이트 완성 ✅

> 장점: 앞으로 파일만 다시 업로드(push)하면 자동으로 새로 배포됩니다.

### 방법 ② Vercel CLI — 명령어로 빠르게
> Node.js 가 설치돼 있어야 합니다.
1. 명령 프롬프트(터미널)에서:
   ```
   npm i -g vercel
   cd "C:\Users\USER\Claude\Projects\더프렙 홈페이지 만들기"
   vercel
   ```
2. 브라우저로 로그인 → 이후 질문은 전부 **Enter**(기본값)
3. 테스트 배포가 끝나면 정식 배포:
   ```
   vercel --prod
   ```

---

## 2단계 · 도메인 theprep.co.kr 연결 (Vercel 쪽)

1. Vercel 프로젝트 → **Settings → Domains**
2. `theprep.co.kr` 입력 → **Add**
3. `www.theprep.co.kr` 도 추가 (권장)
4. Vercel이 **연결에 필요한 값**을 화면에 보여줍니다. 보통:
   - `theprep.co.kr` → **A 레코드** → `76.76.21.21`
   - `www` → **CNAME** → `cname.vercel-dns.com`

   👉 반드시 **Vercel 화면에 표시된 실제 값**을 사용하세요. (위는 일반적인 예시)

---

## 3단계 · 가비아에서 DNS 바꾸기

1. **My가비아** 로그인 → **도메인** → `theprep.co.kr` → **DNS 관리(DNS 설정)**
2. 기존 레코드를 Vercel이 알려준 값으로 **수정/추가**
   - 호스트 `@`(또는 빈칸) → 타입 **A** → 값 `76.76.21.21`
   - 호스트 `www` → 타입 **CNAME** → 값 `cname.vercel-dns.com`
3. **저장**
4. 반영까지 보통 몇 분 ~ 몇 시간 (최대 24~48시간)

---

## 4단계 · 확인

- Vercel **Domains** 화면에 **"Valid Configuration"**(초록 체크) 뜨면 연결 완료
- 브라우저에서 **https://theprep.co.kr** 접속 → 새 사이트 + 자물쇠(HTTPS) 확인

---

## 참고

- 기존 사이트가 가비아 웹호스팅에 있었더라도, 도메인이 Vercel을 가리키게 되면 자동으로 새 사이트가 보입니다. 기존 파일은 그대로 둬도 됩니다.
- **앞으로 내용 수정할 때**
  - 방법①(GitHub): 파일 고쳐서 다시 업로드(push) → 자동 재배포
  - 방법②(CLI): `vercel --prod` 다시 실행
- 블로그·전화번호 등은 모두 사이트 안에 이미 반영돼 있습니다.
