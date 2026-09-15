# 씬별 프롬프트 — Lumin 광고

## 사용 방법 (일관성 유지 절차)
1. **같은 Gemini 대화(채팅) 세션**에서 씬1 → 씬5 순서대로 이미지를 생성한다 (세션을 바꾸지 않는다).
2. 씬2부터는 프롬프트 앞에 "이전 이미지와 동일한 조명/색감/카메라 톤을 유지해서"를 붙이고, 가능하면 씬1 결과 이미지를 참고 이미지로 함께 첨부한다.
3. 모든 프롬프트에 고정 스타일 키워드를 포함한다: `warm amber tone, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, no visible face / silhouette or back view only`
4. 이미지가 확정되면(재생성 최소화) 그 이미지를 입력으로 Veo에서 이미지→영상 변환을 진행한다.
5. 파일명 규칙: `scene0{N}_key.png`(이미지), `scene0{N}_motion.mp4`(영상)

---

## 씬 1 — Intro (문제 제시) / 8초
- **사용 도구**: Gemini(Imagen) — 키비주얼 생성 / Gemini(Veo) — 미세한 정지 상태에 가까운 느린 무빙 부여
- **입력 프롬프트(이미지)**:
  > A tired person's silhouette walking into a cluttered living room after work, cold white fluorescent light, messy coat and bag on the floor, evening blue-toned atmosphere, warm amber tone, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, no visible face / silhouette or back view only, wide shot
- **입력 프롬프트(영상, Veo / image-to-video)**:
  > Slow subtle push-in camera movement, person's silhouette remains still, very slight ambient dust particles in the cold light, 8 seconds, no camera shake
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene01_key.png` / `scene01_motion.mp4`

## 씬 2 — 전환의 시작 / 6초
- **사용 도구**: Gemini(Imagen) — 제품 클로즈업 / Gemini(Veo) — 다이얼 회전 모션
- **입력 프롬프트(이미지)**:
  > Close-up of a hand slowly turning a minimalist dial on a smart mood-light and scent diffuser device, product name "Lumin" subtly visible on device, warm amber tone starting to glow, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, keep same lighting mood as previous image
- **입력 프롬프트(영상, Veo)**:
  > Hand turns the dial slowly and deliberately, macro lens feel, light on the device gradually brightens as the dial turns, 6 seconds
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene02_key.png` / `scene02_motion.mp4`

## 씬 3 — 변화(라이트 & 스캔트) / 10초
- **사용 도구**: Gemini(Imagen) — 조명 전환 장면 / Gemini(Veo) — 색온도 전환 + 연기 확산 모션
- **입력 프롬프트(이미지)**:
  > Wide shot of a living room where cold white light is transforming into warm amber light, soft scent smoke/particles diffusing gently in the air, visible light gradient across the room, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone, keep same style as previous images, no visible face
- **입력 프롬프트(영상, Veo)**:
  > Smooth transition of light color temperature from cool white to warm amber across 10 seconds, scent particles slowly drifting and diffusing in the light beam, gentle camera drift
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene03_key.png` / `scene03_motion.mp4`

## 씬 4 — 체감(휴식) / 12초
- **사용 도구**: Gemini(Imagen) — 인물 휴식 장면 / Gemini(Veo) — 미세한 호흡/움직임 느낌의 정적 모션
- **입력 프롬프트(이미지)**:
  > A person relaxing comfortably on a sofa under warm amber light, eyes closed or holding a warm cup, peaceful posture, back view or silhouette only (no visible face), cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone, consistent with previous scenes
- **입력 프롬프트(영상, Veo)**:
  > Very subtle breathing motion, soft ambient light flicker from the diffuser, slow gentle zoom out, calm and still overall, 12 seconds
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene04_key.png` / `scene04_motion.mp4`

## 씬 5 — 아웃트로(브랜드/CTA) / 8초
- **사용 도구**: Gemini(Imagen) — 로고/제품 실루엣 구도 / Gemini(Veo) — 페이드인 모션
- **텍스트 유무**: 있음 — "Lumin" 워드마크 + 슬로건 "당신의 저녁에, 쉼표를 켜다." (편집 단계에서 자막 오버레이로 추가, 이미지 자체에는 텍스트 생성 요청하지 않음 — AI 생성 텍스트 왜곡 방지)
- **입력 프롬프트(이미지)**:
  > Dark minimal background with the Lumin device silhouette glowing warm amber light in the center, soft bokeh light particles, cinematic product photography style, 35mm lens, shallow depth of field, warm amber tone, consistent with previous scenes, empty negative space on the right side for text overlay
- **입력 프롬프트(영상, Veo)**:
  > Slow fade-in of the glowing device from darkness, gentle light pulse, 8 seconds, static camera
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `scene05_key.png` / `scene05_motion.mp4`

---

## 오디오 프롬프트

### BGM (Suno, 44초 단일 트랙)
> Lo-fi ambient track, warm and calming, soft piano and gentle synth pad, slow tempo (around 70 BPM), evening relaxation mood, minimal percussion, no vocals, 44 seconds

### 내레이션 스크립트 (ElevenLabs, 한국어, 차분한 톤)
1. (씬1) "오늘 하루도, 켜둔 채 잊고 있던 마음."
2. (씬2) "다이얼 하나, 그것으로 충분합니다."
3. (씬3) "빛이 바뀌고, 향이 스며듭니다."
4. (씬4) "이제야, 하루가 끝난 것 같습니다."
5. (씬5, 자막과 동시) "Lumin — 당신의 저녁에, 쉼표를 켜다."

- **결과 파일명**: `bgm_track.wav`, `narration_scene01.wav` ~ `narration_scene05.wav`

---

## 프롬프트 수정 전/후 기록 (생성 후 실제 결과 기반으로 작성 예정)
- 대상 씬: (생성 완료 후 결정)
- 수정 전 의도 / 문제점 / 수정 후 변경 / 결과 변화: TBD
