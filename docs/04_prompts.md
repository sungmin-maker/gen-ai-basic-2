# 씬별 프롬프트 — Lumin 광고

## 제작 진행 상황
*(본 프로젝트는 실제 제출용이 아닌 강의용 시연 제작이며, Veo 일일 생성 횟수 제한(추정 약 5회/일)으로 며칠에 걸쳐 순차 진행 중)*

| 씬 | 이미지 | 영상 | 비고 |
|---|---|---|---|
| 1 | ✅ 완료 | ✅ 완료 (텍스트 전용 프롬프트로 성공) | 트러블슈팅 사례 확보 |
| 2 | ⏳ 대기 | ⏳ 대기 | 프롬프트 확정, 생성 예정 |
| 3 | ✅ 완료 | ✅ 완료 | 프롬프트 수정 없이 1회 성공 |
| 4 | ⏳ 대기 | ⏳ 대기 | 프롬프트 확정, 생성 예정 |
| 5 | ✅ 완료 | ✅ 완료 | 프롬프트 수정 없이 1회 성공 |

## 사용 방법 (일관성 유지 절차)
1. **같은 Gemini 대화(채팅) 세션**에서 씬1 → 씬5 순서대로 이미지를 생성한다 (세션을 바꾸지 않는다).
2. 씬2부터는 프롬프트 앞에 "이전 이미지와 동일한 조명/색감/카메라 톤을 유지해서"를 붙이고, 가능하면 씬1 결과 이미지를 참고 이미지로 함께 첨부한다.
3. 모든 프롬프트(이미지용, 영상용 모두)에 고정 스타일 키워드를 포함한다: `warm amber tone, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, no visible face / silhouette or back view only`
4. **영상은 Gemini(Veo)에서 참고 이미지를 첨부하지 않고 텍스트 프롬프트만으로 생성한다.** (Veo는 이미지를 함께 입력하는 이미지→영상 방식에서 오류가 발생했으나, 텍스트만 입력하는 방식은 정상 작동 확인 — `docs/03_tools.md` "트러블슈팅 기록" 참고) 이미지와 별개로 생성되는 만큼, 영상 프롬프트에는 이미지 프롬프트의 구도/색감 묘사를 최대한 그대로 포함시켜 같은 장면을 재현하도록 한다.
5. Veo는 클립당 **최대 8초**(4/6/8초 중 선택)만 지원하므로, 모든 씬은 8초 이하로 맞춘다.
6. 파일명 규칙: `scene0{N}_key.png`(이미지), `scene0{N}_motion.mp4`(영상)

---

## 씬 1 — Intro (문제 제시) / 8초
- **사용 도구**: Gemini(Imagen) — 키비주얼 생성 / Gemini(Veo, text-to-video) — 느린 무빙 부여
- **입력 프롬프트(이미지, 최종본)**:
  > A cluttered living room right after someone came home from work, a coat and bag left near the door, shoes kicked off, cold white fluorescent light, evening blue-toned atmosphere outside the window, warm amber tone accent, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, empty room, no people
- **입력 프롬프트(영상, Veo / text-to-video)**:
  > A cluttered living room right after someone came home from work, a coat and bag left near the door, shoes kicked off, cold white fluorescent light, evening blue-toned atmosphere outside the window, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, empty room, no people. Slow subtle push-in camera movement, very slight ambient dust particles in the cold light, 8 seconds, no camera shake
- **출력 결과 요약**: (검토자 확인) 인물 없이 코트·가방·신발만으로 "방금 퇴근한 흔적"이 잘 표현됨, 차가운 형광등 조명과 창밖 저녁 하늘 톤도 의도대로 재현됨
- **결과 파일명**: `assets/scene01_key.png` / `assets/scene01_motion.mp4`

## 씬 2 — 전환의 시작 / 6초
- **사용 도구**: Gemini(Imagen) — 제품 클로즈업 / Gemini(Veo, text-to-video) — 다이얼 회전 모션
- **입력 프롬프트(이미지)**:
  > Close-up of a hand slowly turning a minimalist dial on a smart mood-light and scent diffuser device, product name "Lumin" subtly visible on device, warm amber tone starting to glow, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, keep same lighting mood as previous image
- **입력 프롬프트(영상, Veo / text-to-video)**:
  > Close-up of a hand slowly turning a minimalist dial on a smart mood-light and scent diffuser device, warm amber tone starting to glow, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior. Hand turns the dial slowly and deliberately, macro lens feel, light on the device gradually brightens as the dial turns, 6 seconds
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `assets/scene02_key.png` / `assets/scene02_motion.mp4`

## 씬 3 — 변화(라이트 & 스캔트) / 8초 *(기존 10초 → Veo 클립 상한 8초에 맞춰 조정)*
- **사용 도구**: Gemini(Imagen) — 조명 전환 장면 / Gemini(Veo, text-to-video) — 색온도 전환 + 연기 확산 모션
- **입력 프롬프트(이미지)**:
  > Wide shot of a living room where cold white light is transforming into warm amber light, soft scent smoke/particles diffusing gently in the air, visible light gradient across the room, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone, keep same style as previous images, no visible face
- **입력 프롬프트(영상, Veo / text-to-video)**:
  > Wide shot of a living room where cold white light is transforming into warm amber light, soft scent smoke/particles diffusing gently in the air, cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, no visible face. Smooth transition of light color temperature from cool white to warm amber across 8 seconds, scent particles slowly drifting and diffusing in the light beam, gentle camera drift
- **출력 결과 요약**: (검토자 확인) 프롬프트 수정 없이 1회 생성. 창밖 차가운 블루 톤과 실내 앰버 조명이 한 프레임 안에서 대비되며 전환을 표현, 연기/빛 입자 효과도 자연스러움. 인물은 얼굴이 보이지 않는 실루엣으로만 등장해 일관성 전략에 부합
- **결과 파일명**: `assets/scene03_key.png` / `assets/scene03_motion.mp4`

## 씬 4 — 체감(휴식) / 8초 *(기존 12초 → Veo 클립 상한 8초에 맞춰 조정)*
- **사용 도구**: Gemini(Imagen) — 인물 휴식 장면 / Gemini(Veo, text-to-video) — 미세한 호흡/움직임 느낌의 정적 모션
- **입력 프롬프트(이미지)**:
  > A person relaxing comfortably on a sofa under warm amber light, eyes closed or holding a warm cup, peaceful posture, back view or silhouette only (no visible face), cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone, consistent with previous scenes
- **입력 프롬프트(영상, Veo / text-to-video)**:
  > A person relaxing comfortably on a sofa under warm amber light, holding a warm cup, peaceful posture, back view or silhouette only (no visible face), cinematic lighting, 35mm lens, shallow depth of field, minimal Korean apartment interior, warm amber tone. Very subtle breathing motion, soft ambient light flicker from the diffuser, slow gentle zoom out, calm and still overall, 8 seconds
- **출력 결과 요약**: (생성 후 기록)
- **결과 파일명**: `assets/scene04_key.png` / `assets/scene04_motion.mp4`

## 씬 5 — 아웃트로(브랜드/CTA) / 8초
- **사용 도구**: Gemini(Imagen) — 로고/제품 실루엣 구도 / Gemini(Veo, text-to-video) — 페이드인 모션
- **텍스트 유무**: 있음 — "Lumin" 워드마크 + 슬로건 "당신의 저녁에, 쉼표를 켜다." (편집 단계에서 자막 오버레이로 추가, 이미지/영상 자체에는 텍스트 생성 요청하지 않음 — AI 생성 텍스트 왜곡 방지)
- **입력 프롬프트(이미지)**:
  > Dark minimal background with the Lumin device silhouette glowing warm amber light in the center, soft bokeh light particles, cinematic product photography style, 35mm lens, shallow depth of field, warm amber tone, consistent with previous scenes, empty negative space on the right side for text overlay
- **입력 프롬프트(영상, Veo / text-to-video)**:
  > Dark minimal background with a smart mood-light and scent diffuser device silhouette glowing warm amber light in the center, soft bokeh light particles, cinematic product photography style, 35mm lens, shallow depth of field, warm amber tone. Slow fade-in of the glowing device from darkness, gentle light pulse, 8 seconds, static camera
- **출력 결과 요약**: (검토자 확인) 프롬프트 수정 없이 1회 생성. 어두운 배경에 기기 실루엣이 따뜻한 앰버 빛으로 은은하게 부각되고, 보케 빛 입자와 우측 여백(텍스트 오버레이용)도 의도대로 확보됨. ⚠️ 우측 하단에 작은 워터마크로 추정되는 별 모양 아이콘이 포착됨 — 편집 단계에서 크롭 또는 가리기 필요
- **결과 파일명**: `assets/scene05_key.png` / `assets/scene05_motion.mp4`

---

## 오디오 프롬프트

### 오디오 진행 상황
| 항목 | 상태 |
|---|---|
| BGM (당초 Suno 예정 → Gemini로 전환, 정확한 기능명 확인 중) | ✅ 완료 |
| 내레이션 (ElevenLabs, 5개 대사를 하나의 통 오디오로 생성) | ✅ 완료 |

*(도구 전환 사유: Suno 무료 계정은 다운로드가 불가능해 Gemini로 대체 — `docs/03_tools.md`에도 반영 예정)*

### BGM (38초 단일 트랙)
> Lo-fi ambient track, warm and calming, soft piano and gentle synth pad, slow tempo (around 70 BPM), evening relaxation mood, minimal percussion, no vocals, 38 seconds
- **출력 결과 요약**: 프롬프트대로 생성 완료 (세부 검토는 편집 단계에서 진행)

### 내레이션 스크립트 (ElevenLabs, 한국어, 차분한 톤)
1. (씬1) "오늘 하루도, 켜둔 채 잊고 있던 마음."
2. (씬2) "다이얼 하나, 그것으로 충분합니다."
3. (씬3) "빛이 바뀌고, 향이 스며듭니다."
4. (씬4) "이제야, 하루가 끝난 것 같습니다."
5. (씬5, 자막과 동시) "Lumin — 당신의 저녁에, 쉼표를 켜다."

- **실제 생성 방식**: 5개 대사를 씬별로 나누지 않고 **하나의 통 오디오 파일**로 생성 → 편집 단계에서 타임코드에 맞춰 잘라 배치 필요 (`docs/05_editing_plan.md` 오디오 레이어링 절차 갱신 필요)
- **출력 결과 요약**: 생성 완료 (검토 대기)
- **결과 파일명**: `assets/bgm_track.mp3` (BGM), `assets/narration_full.mp3` (통합 내레이션)

---

## 프롬프트 수정 전/후 기록 (실제 제작 중 발생한 사례)

### 사례 1 — 씬1 이미지/영상 프롬프트 수정 (인물 → 무인물)
- **대상 씬**: 씬 1 (Intro)
- **수정 전**: "A tired person's silhouette walking into a cluttered living room after work..." — 인물 실루엣이 직접 등장하는 구도
- **문제**: Gemini(Veo)에 씬1 이미지를 참고로 첨부하고 영상 생성 시도 시 "I can't generate that video" 오류 발생. 처음에는 인물 묘사(실루엣이라도)가 콘텐츠 정책에 걸린 것으로 추정
- **수정 후**: 인물을 완전히 제거하고 "코트와 가방만 문 앞에 놓인" 구도로 변경, 프롬프트 끝에 `no people`을 명시적으로 추가
- **결과 변화**: 이미지 자체는 의도대로 생성됐으나(무인물 버전), 같은 방식(이미지 첨부)으로 영상 변환을 시도하자 동일하게 실패 → 사례 2로 이어짐

### 사례 2 — 오류 원인 재진단 및 파이프라인 확정 (이미지 입력 → 텍스트 전용)
- **대상**: 전체 비디오 생성 파이프라인 (`docs/03_tools.md` "트러블슈팅 기록" 참고)
- **1차 재진단(오판)**: 인물을 제거한 프롬프트로도 오류가 반복되자, 콘텐츠 정책이 아니라 팀 계정의 Veo 접근 권한/크레딧 문제로 추정 → Kling AI로 잠정 전환을 검토
- **재검증**: 전환 전 마지막으로 "참고 이미지 없이 텍스트만" 입력해 재시도 → **정상 작동 확인**. 즉 실제 원인은 권한 문제도 콘텐츠 정책도 아니라 **"이미지를 함께 입력하는 방식(image-to-video)" 자체에 대한 제한**이었음
- **최종 결정**: Gemini(Veo)를 그대로 사용하되, 텍스트-투-비디오 방식으로 파이프라인을 확정. 영상 프롬프트에 이미지 프롬프트의 구도/색감 묘사를 그대로 포함시켜 텍스트만으로 최대한 동일한 장면을 재현
- **부가 조정**: Veo 클립 길이 상한(4/6/8초)에 맞춰 씬3(10→8초), 씬4(12→8초)를 축소 (전체 영상 길이 44초 → 38초, 요구사항 30~60초 범위 내 유지)
- **배운 점**: 동일한 오류가 반복될 때 원인을 한 번에 단정하지 말고, "입력 방식(이미지 첨부 여부)"처럼 변수를 하나씩 분리해 재현 테스트하는 것이 정확한 원인 파악과 불필요한 도구 전환(시간 낭비)을 막는 데 중요함
