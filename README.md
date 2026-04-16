# Optical Ray Simulator — Telescope Edition

A 2D/3D interactive optical ray-tracing simulator that runs entirely in the browser.
브라우저에서 실행되는 2D/3D 광선 추적 시뮬레이터 — 망원경 에디션.

---

## 🇰🇷 한국어 (새 기능 요약)

### 이번 버전 추가 기능
망원경 시뮬레이션에 필요한 기능을 전부 추가했습니다.

**1. ⭐ Star at Infinity (무한거리 평행광) — 기본 모드**
- 별에서 오는 평행광을 시뮬레이션합니다.
- **Field angle**: 시야각 (°). 0°이면 광축 위의 별, 양수/음수이면 광축에서 벗어난 별. 비점수차/코마 같은 off-axis 수차를 관찰할 때 유용합니다.
- **Beam width**: 광축에 수직인 평행광 다발의 폭 (mm). 대개 대물렌즈 구경과 같게 설정합니다.

**2. 🎯 Detector / Screen (검출기/스크린)**
- CCD나 접안 관찰면 역할을 하는 소자입니다.
- 광선이 이 위치를 통과하면 하단 패널에 자동으로 강도 프로파일(intensity profile)이 표시됩니다.
- 히스토그램 + Gaussian smoothing으로 실제 상(像) 모양과 비슷하게 보여줍니다.

**3. 🔬 PSF Inset (점 확산 함수)**
- 초점 근처의 광선 집속 상태를 확대해서 보여줍니다.
- RMS 값(수차 정도)이 표시됩니다.
- 색수차 모드에서는 RGB가 서로 다른 위치에 찍히는 걸 볼 수 있습니다.

**4. 📊 Ray Fan Diagram (광선 부채꼴 수차 그래프)**
- 가로축: 입사동 높이(pupil height)
- 세로축: 초점에서의 횡방향 수차(transverse aberration)
- 이상적인 렌즈라면 수평선, 수차가 있으면 곡선이 나타납니다.
- 망원경 성능 평가의 표준 도구입니다.

**5. 📐 Telescope Metrics HUD (망원경 지표)**
화면 상단에 실시간 표시됩니다:
- `f_objective`: 대물렌즈 초점거리
- `f_eyepiece`: 접안렌즈 초점거리
- `Magnification`: 배율 (= f_obj / f_eye)
- `Tube length`: 경통 길이
- `f/ratio`: 조리개값 (f/D)
- `True FOV`: 실시야 (접안경 표준 AFOV 50° 기준)

**6. 🔭 Telescope Presets (망원경 프리셋 4종)**
- **Keplerian**: 볼록 대물 + 볼록 접안 (고배율, 천문용 표준)
- **Galilean**: 볼록 대물 + 오목 접안 (저배율, 오페라글라스)
- **Newtonian**: 오목 주경 + 볼록 접안 (반사망원경, 근사)
- **Cassegrain**: 오목 주경 + 볼록 부경 + 접안 (접는 반사망원경)
- 주의: Newtonian과 Cassegrain은 본 시뮬레이터가 단일 반사 경로만 처리하므로 **근사 배치**입니다. 실제 접힌 광로는 단순화되어 있습니다.

**7. 🚫 Aperture Stop (조리개)**
- 광선을 기계적으로 차단하는 소자.
- `Hole size`: 구멍 크기. 이 크기를 벗어나는 광선은 차단되며 반투명하게 표시됩니다.
- 망원경의 입사동 크기 제한, 비네팅 관찰용.

**8. 📏 Measurement Tool (거리 눈금자)**
- Display 섹션의 "Measurement tool" 체크
- 캔버스에서 두 점을 클릭 → 거리, Δx, Δy가 표시됩니다
- 소자 간 간격, 초점거리 검증용

**9. 💾 Export / Import JSON**
- `Export JSON`: 현재 설정을 JSON 파일로 저장
- `Import JSON`: 저장한 파일 불러오기
- 실험 세팅 공유, 저장용

**10. 🎨 Collapsible Sections**
- 각 섹션의 `−` / `+` 를 클릭해서 접고 펼칠 수 있습니다.

### 광원 모드 4종
| Mode | 설명 |
|---|---|
| **Point source** | 한 점에서 발산하는 발산광 (기존) |
| **Star at infinity** | 무한거리 별에서 오는 평행광. Field angle로 off-axis 지정 (기본값) |
| **Parallel beam** | 유한 거리에서 출발하는 수평 평행광 다발 |
| **Collimated fan** | 한 점에서 나오는 좁은 부채꼴 |

### 실습 시나리오

**시나리오 1: Keplerian 망원경 기본**
1. "Keplerian" 프리셋 클릭 → 자동 구성됨
2. 상단 Metrics HUD에서 배율 8×, f/2.5 확인
3. Display에서 "PSF inset" 체크 → 초점이 얼마나 잘 맺히는지 확인

**시나리오 2: 색수차 관찰**
1. Keplerian 프리셋 로드
2. "Chromatic dispersion (RGB)" 체크
3. 초점 위치에서 RGB가 분리되는 것을 확인
4. PSF inset에서 세 색이 다른 위치에 맺히는 걸 관찰

**시나리오 3: Off-axis 별 (코마/비점수차)**
1. Keplerian 프리셋 로드
2. Light Source → Field angle을 0에서 3°로 변경
3. Ray Fan diagram 켜기 → S자 곡선이 나타나면 코마 수차
4. 별 아이콘이 비스듬히 이동한 것을 확인

**시나리오 4: 조리개로 구경 제한**
1. Keplerian 프리셋 로드
2. "+ Aperture Stop" 추가 → 대물렌즈 앞에 배치 (x 조정)
3. Hole size를 80mm로 설정
4. 차단된 광선이 반투명으로 표시됨을 확인
5. f/ratio가 변하는 것을 Metrics HUD에서 확인

**시나리오 5: 검출기로 실제 상 관찰**
1. 프리셋 로드
2. "+ Detector / Screen" 추가
3. 검출기 위치를 초점 근처로 드래그
4. 하단에 강도 프로파일이 나타남
5. Detector 위치를 움직이면서 프로파일 변화 관찰 (초점 내, 초점, 초점 밖)

**시나리오 6: 매질 변화의 영향**
1. 볼록렌즈 하나 배치
2. Medium의 n₀를 1.00 → 1.33으로 변경
3. 렌즈의 실효 초점이 물속에서 어떻게 변하는지 확인

---

## 🇬🇧 English

### New features in this edition

| Feature | Purpose |
|---|---|
| **Star at Infinity mode** | Parallel rays from infinity with field angle + beam width. Primary mode for telescope work. |
| **Detector / Screen** | Records ray hits and displays a 1-D intensity profile at the bottom. |
| **PSF inset** | Spot diagram near convergence, RMS error shown. |
| **Ray fan diagram** | Transverse aberration vs. pupil height. Gold-standard aberration plot. |
| **Telescope metrics HUD** | Auto-computed f_obj, f_eye, magnification, tube, f/ratio, TFOV. |
| **4 telescope presets** | Keplerian, Galilean, Newtonian, Cassegrain. |
| **Aperture stop** | Mechanical blocker; rays outside the hole are drawn translucent. |
| **Measurement ruler** | Click two points to measure distances. |
| **JSON import/export** | Save and restore complete setups. |
| **Collapsible sections** | Click `−`/`+` to fold panels. |

### Light-source modes
- **Point source (finite)** — Diverging rays from a position.
- **Star at infinity** — Parallel bundle entering at a field angle (default).
- **Parallel beam (finite)** — Horizontal parallel rays from a finite-distance plane.
- **Collimated fan** — Narrow fan from a point.

### Infinity-mode details
In infinity mode the source is represented as a star icon far off-axis. The incoming beam is:
- perpendicular to the tilted direction (field angle)
- `beam_width` mm wide (should match objective aperture)
- composed of `ray_count` parallel rays

Non-zero field angles let you study off-axis aberrations like coma and astigmatism.

### Detector
Drop a detector anywhere in the optical path. Rays are recorded (they pass through) and the bottom strip shows a smoothed histogram of hit positions — essentially what you'd see on a CCD at that plane. Place one at the focal plane, then try moving it ±5 mm to see through-focus behaviour.

### Ray-fan interpretation
- **Straight horizontal line** — perfect paraxial imaging.
- **Tilted line** — defocus (the detector is not at the best focus).
- **S-shape** — coma.
- **Parabolic curve** — spherical aberration.
- **Different colours diverging** — chromatic aberration.

### Presets quick guide
| Preset | Configuration | Magnification |
|---|---|---|
| Keplerian | f=400 convex objective + f=50 convex eyepiece | 8× |
| Galilean | f=400 convex objective + f=-80 concave eyepiece | 5× |
| Newtonian | f=300 concave primary + f=25 eyepiece (simplified) | 12× |
| Cassegrain | f=400 concave primary + f=-150 convex secondary + eyepiece | varies |

> Note on reflective telescopes: this simulator traces each mirror as a single reflection, so folded beam paths (Newtonian and Cassegrain) are geometric approximations rather than exact layouts.

### Units
All distances are in **millimetres**. Wavelength in **nanometres**. Angles in **degrees**.

---

## Physics reference / 물리 공식

| Concept | Formula |
|---|---|
| Thin lens | `1/f = 1/s₀ + 1/sᵢ` |
| Lensmaker (with medium) | `f_eff = f · (n−1) / (n/n_m − 1)` |
| Cauchy dispersion | `n(λ) = n₀ + B(1/λ² − 1/λ_ref²)` |
| Mirror focal | `f = R/2` |
| Magnification (refractor) | `M = f_objective / f_eyepiece` |
| f-ratio | `f/# = f / D` (D = aperture) |
| True FOV | `TFOV ≈ AFOV_eyepiece / M` (AFOV ≈ 50°) |

---

## Keyboard / mouse cheat sheet

| Input | Action |
|---|---|
| Mouse drag on element | Move element (if unlocked) |
| Mouse drag on source | Move light source (finite modes only) |
| Mouse wheel | Zoom toward cursor |
| Shift + drag / middle-click / right-click | Pan view |
| 2D / 3D button | Switch view mode |
| 3D drag | Orbit camera |
| 3D scroll | Dolly in/out |
| Ruler checked + click | Place ruler endpoints |

---

## Known limitations / 알려진 제한

- Paraxial thin-element model · 근축 얇은 소자 근사
- No spherical aberration modelling (only chromatic) · 구면수차는 모델링되지 않음 (색수차만)
- All elements perpendicular to X-axis · 모든 소자가 X축에 수직
- Mirrors handle single reflection only · 거울은 단일 반사만 처리
- Newtonian / Cassegrain presets are geometric approximations · 반사망원경 프리셋은 근사 배치

---

_Built with vanilla HTML / CSS / JS. No dependencies, fully offline._
_순수 HTML/CSS/JS, 외부 라이브러리 없음, 오프라인 동작._
