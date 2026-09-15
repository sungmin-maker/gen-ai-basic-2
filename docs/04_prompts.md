# 씬별 프롬프트 — Lumin 광고

## 사용 방법 (일관성 유지 절차)
1. **같은 Gemini 대화(채팅) 세션**에서 씬1 → 씬5 순서대로 이미지를 생성한다 (세션을 바꾸지 않는다).
2. 씬2부터는 프롬프트 앞에 "이전 이미지와 동일한 조명/색감/카메라 톤을 유지해서"를 붙이고, 가능하면 씬1 결과 이미지를 참고 이미지로 함께 첨부한다.
3. 모든 프롬프트에 고정 스타일 키워드를 포함한다: `warm amber tone, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, no visible face / silhouette or back view only`
4. 이미지가 확정되면(재생성 최소화) 그 이미지를 입력으로 **Kling AI**에서 이미지→영상 변환을 진행한다. (당초 Gemini/Veo 예정이었으나 접근 이슈로 전환 — `docs/03_tools.md`의 "도구 전환 기록" 참고)
5. 파일명 규칙: `scene0{N}_key.png`(이미지), `scene0{N}_motion.mp4`(영상)

---

## 씬 1 — Intro (문제 제시) / 8초
- **사용 도구**: Gemini(Imagen) — 키비주얼 생성 / Kling AI — 미세한 정지 상태에 가까운 느린 무빙 부여
- **입력 프롬프트(이미지, 최종본)**:
  > A cluttered living room right after someone came home from work, a coat and bag left near the door, shoes kicked off, cold white fluorescent light, evening blue-toned atmosphere outside the window, warm amber tone accent, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, empty room, no people
- **입력 프롬프트(영상, Kling / image-to-video)**:
  > Slow subtle push-in camera movement across a cluttered living room, cold white fluorescent light, a coat and bag left near the door, dust particles gently floating in the cold light, empty space, 8 seconds, no camera shake
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene01_key.png` / `scene01_motion.mp4`

## 씬 2 — 전환의 시작 / 6초
- **사용 도구**: Gemini(Imagen) — 제품 클로즈업 / Kling AI — 다이얼 회전 모션
- **입력 프롬프트(이미지)**:
  > Close-up of a hand slowly turning a minimalist dial on a smart mood-light and scent diffuser device, product name "Lumin" subtly visible on device, warm amber tone starting to glow, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, keep same lighting mood as previous image
- **입력 프롬프트(영상, Kling)**:
  > Hand turns the dial slowly and deliberately, macro lens feel, light on the device gradually brightens as the dial turns, 6 seconds
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene02_key.png` / `scene02_motion.mp4`

## 씬 3 — 변화(라이트 & 스캔트) / 10초
- **사용 도구**: Gemini(Imagen) — 조명 전환 장면 / Kling AI — 색온도 전환 + 연기 확산 모션
- **입력 프롬프트(이미지)**:
  > Wide shot of a living room where cold white light is transforming into warm amber light, soft scent smoke/particles diffusing gently in the air, visible light gradient across the room, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone, keep same style as previous images, no visible face
- **입력 프롬프트(영상, Kling)**:
  > Smooth transition of light color temperature from cool white to warm amber across 10 seconds, scent particles slowly drifting and diffusing in the light beam, gentle camera drift
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene03_key.png` / `scene03_motion.mp4`

## 씬 4 — 체감(휴식) / 10초 *(기존 12초 → Kling 클립 상한 10초에 맞춰 조정)*
- **사용 도구**: Gemini(Imagen) — 인물 휴식 장면 / Kling AI — 미세한 호흡/움직임 느낌의 정적 모션 (인물 표현 강점 있는 도구로 배정)
- **입력 프롬프트(이미지)**:
  > A person relaxing comfortably on a sofa under warm amber light, eyes closed or holding a warm cup, peaceful posture, back view or silhouette only (no visible face), cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone, consistent with previous scenes
- **입력 프롬프트(영상, Kling)**:
  > Very subtle breathing motion, soft ambient light flicker from the diffuser, slow gentle zoom out, calm and still overall, 10 seconds
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene04_key.png` / `scene04_motion.mp4`

## 씬 5 — 아웃트로(브랜드/CTA) / 8초
- **사용 도구**: Gemini(Imagen) — 로고/제품 실루엣 구도 / Kling AI — 페이드인 모션
- **텍스트 유무**: 있음 — "Lumin" 워드마크 + 슬로건 "당신의 저녁에, 쉼표를 켜다." (편집 단계에서 자막 오버레이로 추가, 이미지 자체에는 텍스트 생성 요청하지 않음 — AI 생성 텍스트 왜곡 방지)
- **입력 프롬프트(이미지)**:
  > Dark minimal background with the Lumin device silhouette glowing warm amber light in the center, soft bokeh light particles, cinematic product photography style, 35mm lens, shallow depth of field, warm amber tone, consistent with previous scenes, empty negative space on the right side for text overlay
- **입력 프롬프트(영상, Kling)**:
  > Slow fade-in of the glowing device from darkness, gentle light pulse, 8 seconds, static camera
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene05_key.png` / `scene05_motion.mp4`

---

## 오디오 프롬프트

### BGM (Suno, 42초 단일 트랙)
> Lo-fi ambient track, warm and calming, soft piano and gentle synth pad, slow tempo (around 70 BPM), evening relaxation mood, minimal percussion, no vocals, 42 seconds

### 내레이션 스크립트 (ElevenLabs, 한국어, 차분한 톤)
1. (씬1) "오늘 하루도, 켜둔 채 잊고 있던 마음."
2. (씬2) "다이얼 하나, 그것으로 충분합니다."
3. (씬3) "빛이 바뀌고, 향이 스며듭니다."
4. (씬4) "이제야, 하루가 끝난 것 같습니다."
5. (씬5, 자막과 동시) "Lumin — 당신의 저녁에, 쉼표를 켜다."

- **결과 파일명**: `bgm_track.wav`, `narration_scene01.wav` ~ `narration_scene05.wav`

---

## 프롬프트 수정 전/후 기록 (실제 제작 중 발생한 사례)

### 사례 1 — 씬1 이미지/영상 프롬프트 수정 (인물 → 무인물)
- **대상 씬**: 씬 1 (Intro)
- **수정 전**: "A tired person's silhouette walking into a cluttered living room after work..." — 인물 실루엣이 직접 등장하는 구도
- **문제**: Kling 전환 전 Gemini(Veo)에서 해당 이미지를 영상으로 변환 시도 시 "I can't generate that video" 오류 발생. 처음에는 인물 묘사(실루엣이라도)가 콘텐츠 정책에 걸린 것으로 추정
- **수정 후**: 인물을 완전히 제거하고 "코트와 가방만 문 앞에 놓인" 구도로 변경, 프롬프트 끝에 `no people`을 명시적으로 추가
- **결과 변화**: 이미지 자체는 의도대로 생성됐으나(무인물 버전), 이 프롬프트로도 Veo 영상 변환은 동일하게 실패 → 아래 사례 2로 이어짐

### 사례 2 — 비디오 생성 도구 전환 (Gemini/Veo → Kling AI)
- **대상**: 전체 비디오 생성 파이프라인 (`docs/03_tools.md` "도구 전환 기록" 참고)
- **진단 과정**: 인물을 제거한 프롬프트로도 동일한 오류가 반복 → 콘텐츠 정책이 아니라 팀 계정에 Veo 영상 생성 권한/크레딧이 없는 문제로 재진단
- **결정**: Veo 재시도를 중단하고, 무료 크레딧이 일일 리셋되는 **Kling AI**로 비디오 생성 도구를 전환. 이미지 생성(Gemini/Imagen)은 문제가 없었으므로 그대로 유지
- **부가 조정**: Kling의 클립 길이 상한(10초)에 맞춰 씬4 길이를 12초 → 10초로 축소 (전체 영상 길이 44초 → 42초, 요구사항 범위 내 유지)
- **배운 점**: 동일한 오류가 프롬프트 수정 후에도 반복되면 콘텐츠 문제보다 도구 접근성/권한 문제를 먼저 의심하고, 검증된 무료 대안으로 빠르게 전환하는 것이 효율적
