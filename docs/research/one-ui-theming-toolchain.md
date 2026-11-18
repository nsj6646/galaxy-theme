# One UI 6.1+ 비루팅 개인 테마 제작 툴체인 및 에셋 규격 조사

> **Ticket**: [nsj6646/galaxy-theme#2](https://github.com/nsj6646/galaxy-theme/issues/2) | **Map**: [nsj6646/galaxy-theme#1](https://github.com/nsj6646/galaxy-theme/issues/1)  
> **Scope**: 루팅·파트너 심사 없는 순정 One UI(6.1 ~ 8.5, 바형 Galaxy) 개인용 Theme 툴체인, 노출 슬롯, 에셋 규격 및 Mac→Galaxy 임포트 절차

---

## 1. 핵심 결론 및 권장 툴체인

비루팅·비파트너 순정 One UI 6.1+ 환경에서 안정적으로 동작하는 툴체인은 **삼성 Good Lock 생태계**(핵심: **Theme Park**, **LockStar**, **ClockFace**, **Home Up**, **Wonderland**, **QuickStar**)가 사실상 유일하다.

- **시스템 UI·퀵패널·아이콘·폴더**: **Theme Park** (`v1.1.00.08`부터 APK 빌드 대신 단말 네이티브 테마/팔레트 방식 적용; One UI 7+ 폴더·커스텀 마스크 지원; One UI 8.0/8.5 아이콘 효과 추가)[^tp_1100][^gl_oneui7][^gl_oneui8][^gl_oneui85]
- **잠금화면·AOD**: **LockStar** + **ClockFace** (One UI 7+ 잠금화면 기본 편집 통합; One UI 8.0/8.5 지문·해제 애니메이션·텍스트·전체화면 AOD 밝기 확대)[^gl_oneui7][^gl_oneui8][^gl_oneui85]
- **홈 자유 배치·스티커·폴더 보완**: **Home Up** (DIY Home, 즐겨찾기/페이지 인디케이터 숨김, 큰 폴더·아이콘 라벨 편집)[^news_homeup][^gl_oneui8][^gl_oneui85]
- **동적 배경화면·AOD 전환**: **Wonderland** (One UI 7+ 홈/잠금 개별 적용, AOD→잠금 전환 효과)[^news_wonderland][^gl_oneui7]
- **아이콘 공급 전략**:
  1. **표준 Icon Pack APK 빌드 + Theme Park 임포트** (`appfilter.xml` + `432×432`/`512×512` 투명 PNG): 다수 앱 일괄 매핑·버전 관리에 유리.
  2. **Theme Park 갤러리 수동 PNG/WEBP 지정**: 소수 앱 또는 부분 교체에 적합.
- **사용 불가/제외**: **Hex Installer**(`v30 hex_eol`, One UI 6.1.1+ 미지원)[^hex_eol], **Repainter/ColorBlendr**(One UI 6+ 비루팅 전체 제어 불가)[^colorblendr_gh], **Galaxy Themes Studio**(파트너 전용)[^gt_dev].

---

## 2. One UI 6.1 ~ 8.5 도구별 현황

### 2.1 공식 도구 (Good Lock & One UI 네이티브)

| 도구 | 패키지 / 배포처 | One UI 6.1 ~ 8.5 주요 변화 | 출처 |
| :--- | :--- | :--- | :--- |
| **Good Lock** | Galaxy Store / Play Store | **One UI 7.0**부터 Google Play Store 글로벌 지원, UI 개편 및 '내 페이지' 탭 추가. | [^gl_oneui7] |
| **Theme Park** | `com.samsung.android.themedesigner` | **One UI 6.1 (`v1.1.00.08`)**: 기존 ~40초 APK 설치 방식 폐지 → 단말 네이티브 테마 적용(속도 향상, 편집·덮어쓰기, 신규 앱 자동 반영; 단 앱별 테마·키캡·폴더 모양 일시 삭제).<br>**One UI 7.0**: **폴더 아이콘 모양·색상** 복원·확장, **사용자 이미지 커스텀 아이콘 마스크**(기본 11종 외) 추가.<br>**One UI 8.0**: 아이콘 효과 4종(필름 그레인·듀오톤·유리·그라데이션).<br>**One UI 8.5**: 엠보싱, 모노크롬 스타일 추가. | [^tp_1100][^tp_review][^gl_oneui7][^news_tp][^gl_oneui8][^gl_oneui85] |
| **LockStar** | Good Lock 모듈 | **One UI 6.1 (`v6.1.0.11`)**: AOD 편집/수동 밝기(전체화면 AOD 기기 ex. S24 제외, AOD `v8.7.99.11`+ 필요).<br>**One UI 7.0**: 잠금화면 기본 편집 통합.<br>**One UI 8.0**: 지문 효과 5종.<br>**One UI 8.5**: 해제 애니메이션, 잠금/AOD 텍스트(8.0+), 전체화면 AOD 수동 밝기 확대. | [^tp_1100][^gl_oneui7][^gl_oneui8][^gl_oneui85] |
| **ClockFace** | `com.samsung.android.app.clockface` | 잠금화면/AOD 커스텀 시계(텍스트·이미지·GIF 삽입). One UI 6.1+ 호환 유지. | [^clockface_store] |
| **Home Up** | Good Lock 모듈 | **One UI 7.0**: One UI 홈 직접 설정, **DIY Home**(자유 배치·크기·스티커 아래 앱 숨김), 즐겨찾기 숨김, 폴더 팝업.<br>**One UI 8.0**: 정렬 가이드·그룹·잠금·스티커 액션·페이지 인디케이터 숨김.<br>**One UI 8.5**: 큰 폴더 크기/블러 제거, 아이콘 라벨 편집, 위젯 블러 제거. | [^gl_oneui7][^news_homeup][^gl_oneui8][^gl_oneui85] |
| **Wonderland** | Good Lock 모듈 | **One UI 7.0**: 홈/잠금 **개별 적용**, 배경 기반 글자 시인성 개선, AOD→잠금 전환.<br>**One UI 8.0**: 전환 블러 방향 설정. | [^gl_oneui7][^news_wonderland][^gl_oneui8] |
| **QuickStar** | `com.samsung.android.qstuner` | 상단바 아이콘 숨김, 투폰 멀티유저 아이콘 숨김(7.0).<br>**One UI 8.5**: 가로모드 편집, 패널 항목 크기·**이미지 설정**, 조절바 수치 표시. | [^gl_oneui7][^quickstar_store][^gl_oneui85] |
| **색상 팔레트** | One UI 네이티브 설정 | 배경화면 기반 Material You 팔레트 및 아이콘 색조 적용. **Theme Park와 동시 사용 시 충돌**(4.3절). | [^samsung_cp][^cp_conflict] |

### 2.2 비공식 / 파트너 전용 / 중단 도구

- **Galaxy Themes Studio**: 오픈 윈도우 기간 포트폴리오 3종 승인 파트너 전용(2023년 이후 신규 모집 정책 개편 공지)[^gt_dev][^gt_icon_blog]. 개인용 범위 제외.
- **Hex Installer (`#hex_`)**: 2024년 3월 **`v30 hex_eol`**로 개발 종료(EOL). One UI 6.1.1 이후 보안·테마 엔진 변경으로 신규 컴파일/적용 불가(Shizuku 동결 우회법은 비공식·불안정)[^hex_eol].
- **Repainter / ColorBlendr**: One UI 6+ 시스템 팔레트 구조 변경으로 비루팅 전체 제어 불가(ColorBlendr Issue #42 `Closed as not planned`)[^colorblendr_gh].

---

## 3. UI 표면별 커스터마이징 매트릭스 및 제약

| UI 표면 | 주력 도구 | 보조 도구 | 범위 및 제약 |
| :--- | :--- | :--- | :--- |
| **홈 / 잠금 배경화면** | One UI 설정 / Wonderland | — | Wonderland로 멀티레이어·3D 모션 및 홈/잠금 개별 적용 가능(One UI 7+)[^news_wonderland][^gl_oneui7]. |
| **앱 아이콘** | **Theme Park** (`Icon`) | Home Up(라벨·크기) | Icon Pack APK + 앱별 PNG/WEBP 교체 + 커스텀 마스크/효과. One UI 홈/앱스/폴더 위주 반영; DeX(One UI 8.0)는 아이콘만 제한 지원[^samsung_cp]. |
| **폴더 아이콘 / 팝업** | **Theme Park** (`Icon`) + **Home Up** | — | One UI 7.0 Theme Park에서 폴더 모양·색상 복원[^gl_oneui7][^news_tp]; Home Up으로 팝업·큰 폴더·블러 제어[^gl_oneui85]. |
| **퀵패널** | **Theme Park** (`Quick panel`) | QuickStar | Theme Park가 배경·블러·타일·알림 색상을 제어; QuickStar가 상단바·항목 크기/이미지(8.5) 보완[^gl_oneui85]. |
| **설정 / 전화 / 메시지** | **Theme Park** (`Theme`) | — | 설정·전화·삼성 메시지 말풍선 등 색상 반영. 단, Google 앱은 Material You를 따르며, One UI 8.5 내 파일·연락처 등 일부 고정 컨테이너는 토큰 미상속 보고됨[^tp_sun_moon]. |
| **잠금화면 / AOD** | **LockStar** + **ClockFace** | Wonderland | 시계·위젯·스티커·텍스트·지문/해제 애니메이션 구성. **AOD GIF는 절전 정책상 화면 꺼질 때 1회만 재생 후 정지**[^aod_gif]. |

> **범위 외**: 키보드(Keys Cafe), 음량 패널(Sound Assistant), 서드파티 런처/위젯(KWGT 등).

---

## 4. Theme Park 색상 슬롯 및 라이트/다크 모드

- **탭 구성**: `Theme` / `Keyboard` / `Quick panel` / `Icon` / `Volume panel`.
- **네이티브 적용 전환(One UI 6.1+)**: `v1.1.00.08` 이후 별도 APK 설치 없이 네이티브 테마 방식으로 즉시 저장·적용·덮어쓰기 가능[^tp_1100][^tp_review].
- **라이트 / 다크 모드**: 에디터 우측 상단 **해/달(Sun/Moon) 토글**로 하나의 Theme 안에 **라이트 모드와 다크 모드 팔레트를 독립 설정**할 수 있다[^tp_sun_moon]. 단일 주력 모드에 집중하더라도, 실기기 모드 전환 시 대비 붕괴를 막기 위해 보조 모드 슬롯도 안전한 기본/동일 톤으로 정리하는 것이 안전하다.
- **주요 시맨틱 색상 슬롯 (`Theme` / `Quick panel`)** *(삼성 공식 전체 슬롯 명세표 미공개; 커뮤니티 확인 토큰 기준)*:
  - `Primary` (`Primary Dark` / `Primary Light`): 활성 퀵패널 타일, 슬라이더, 설정 스위치, 삼성 메시지 발신/수신 말풍선.
  - `Secondary` / `Highlight`: 보조 강조, 배지, 포커스 상태.
  - `Background`: 설정·전화·퀵패널 기저 바탕(및 투명도/블러).
  - `Surface`: 카드, 서브메뉴, 비활성 타일, 알림 카드 면.
  - `On Background` / `On Surface`: 바탕/카드 위 텍스트 대비색.
- **Color Palette 충돌 주의**: `설정 > 배경화면 및 스타일 > 색상 팔레트`가 켜져 있으면 Theme Park 색상을 덮어쓰거나 풀림 현상이 발생하므로[^cp_conflict], **Theme Park 적용 전 시스템 `색상 팔레트`를 반드시 OFF**한다.

---

## 5. 에셋 규격 (배경화면, 아이콘, AOD)

### 5.1 바형(Bar-type) Galaxy 배경화면 / 잠금화면

삼성 공식 S24 / S25 시리즈 사양 기준 바형 플래그십 해상도·비율은 **`19.5:9`**다[^s24_s25]:

- **기본형 (S24 / S25, 6.2")**: `1080 × 2340 px` (FHD+)
- **플러스 / 울트라 (S24+/S25+ 6.7", S24U/S25U 6.8"~6.9")**: **`1440 × 3120 px` (QHD+)**
- **권장 마스터**: **`1440 × 3120 px` PNG** (무손실) 또는 고품질 JPEG/WEBP. (20:9 구형 기기 호환은 티켓 #4 기종 확인 후 크롭 결정.)
- **잠금화면 동영상**: MP4(또는 3GP), 최대 **15초**, 최대 **100 MB** (검색 인덱싱된 삼성 NZ 지원 문서 기준; JS 렌더링 페이지라 티켓 #4 실기기 확인 필요)[^lock_mp4].
- **배치 주의**: 상단 상태바·잠금 시계/위젯·하단 지문 센서/바로가기·홈 독(Dock)과 핵심 캐릭터가 겹치지 않게 안전 여백 확보.

### 5.2 앱 아이콘 규격 및 임포트 방식

- **Android Adaptive Icon 공식 규격**[^adaptive_icons]:
  - 전체 캔버스: **`108 × 108 dp`** (`xxxhdpi` 4× 기준 **`432 × 432 px`**)
  - 외곽 블리드: 사방 **`18 dp`** (마스크·패럴랙스용)
  - 안전 영역(Safe Zone): 중앙 **`66 × 66 dp`** (로고/핵심 그래픽은 **`48 × 48 dp` ~ `66 × 66 dp`** 이내 유지 시 어떤 OEM 마스크에도 잘리지 않음)
  - *(참고: 파트너용 Galaxy Themes Studio는 `144 × 144 px`, 72ppi PNG 및 `576 px` 마스터를 권장하나[^gt_icon_blog], 비파트너 개인용은 `432 × 432 px` 또는 `512 × 512 px` 1:1 투명 PNG가 적합.)*
- **Theme Park 임포트 비교**:
  1. **갤러리 수동 PNG/WEBP (`Theme Park > Icon > Create New > ⋮ > Change Icons > Gallery`)**: `432×432`~`512×512 px` 투명 **PNG/WEBP** 지원. **SVG 직접 임포트는 비권장**(래스터 변환 누락 시 사각 배경 잔존 위험 → Mac에서 PNG 선변환 필수). 모양 선택 끝 `+` 버튼으로 갤러리 PNG를 **커스텀 마스크**로 지정 가능(One UI 7+)[^gl_oneui7].
  2. **표준 Icon Pack APK (`res/xml/appfilter.xml` + `res/drawable-nodpi/` PNG)**: `ComponentInfo{pkg/activity}` 매핑 APK를 설치하면 Theme Park `Icon Pack` 메뉴에서 수십 개 앱을 일괄 매핑 가능. 미지정 앱은 Theme Park 전역 모양·효과 및 폴더 아이콘 스타일로 폴백.

### 5.3 AOD 스티커 / GIF

- 정지 스티커는 투명 **PNG**, 애니메이션은 **`.gif`** 지원(LockStar / ClockFace). GIF는 AOD에서 **1회 재생 후 정지**하므로[^aod_gif] 마지막 프레임이 완성된 구도로 제작해야 한다.

---

## 6. Mac → Galaxy 전송 및 기기 적용 워크플로우

1. **에셋 내보내기 (Mac)**: 배경(`1440×3120 px` PNG), 아이콘(`432×432` 또는 `512×512 px` 투명 PNG, `66/108` 안전 영역), 잠금/AOD PNG·GIF 생성.
2. **전송 수단**:
   - **유선 CLI (`adb`, 최우선 권장)**: `brew install android-platform-tools` 후 `adb push <dir> /sdcard/Pictures/GalaxyTheme/`로 에셋 일괄 전송, Icon Pack APK는 `adb install -r <pack>.apk`로 설치[^adb_docs].
   - **무선 (`Quick Share`)**: Mac(2020+)↔Galaxy 무선 파일 공유 활용 가능(환경별 지원 여부는 티켓 #4/#6에서 확인).
   - **기타**: OpenMTP (구형 Android File Transfer 대체), **Smart Switch for Mac** (macOS 10.13+, 전체 백업·복원용)[^smart_switch].
3. **적용 순서**: ① `색상 팔레트` OFF[^cp_conflict] → ② 주력 라이트/다크 모드 고정 → ③ 배경화면(또는 Wonderland) → ④ Theme Park `Theme`·`Quick panel` → ⑤ Theme Park `Icon`(Icon Pack APK 또는 수동 PNG + 폴더/마스크) → ⑥ LockStar·ClockFace·Home Up 마무리.

---

## 7. 후속 티켓(#4, #5, #6) 검증 필요 항목

1. 대상 실기기 모델·해상도(`19.5:9` vs `20:9`)·One UI 버전 및 전체화면 AOD 지원 여부(티켓 #4).
2. 설치된 Theme Park 버전의 정확한 한글/영문 컬러 슬롯 전체 UI 라벨(공식 온라인 명세 미공개 → 티켓 #4/#5 실기기 대조).
3. 자체 빌드 `appfilter.xml` Icon Pack APK의 최신 One UI(7/8/8.5) 삼성 기본 앱·폴더 아이콘 매핑 동작 스모크 테스트(티켓 #6).

---

## 8. 참고 출처

[^gl_oneui7]: 삼성 Good Lock 공지, *굿락 One UI 7 업데이트 소식* (2025-01-01): https://r1.community.samsung.com/t5/good-lock/%EA%B5%BF%EB%9D%BD-one-ui-7-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-%EC%86%8C%EC%8B%9D/td-p/31156891
[^gl_oneui8]: 삼성 Good Lock 공지, *One UI 8.0 Good Lock 소식* (2025-07-21): https://community.samsung.com/kr/conversations/good-lock/one-ui-8-0-good-lock-%EC%86%8C%EC%8B%9D/r1_34286184
[^gl_oneui85]: 삼성 Good Lock 공지, *One UI 8.5 Good Lock 소개* (2026-01-21): https://community.samsung.com/kr/conversations/good-lock/one-ui-8-5-good-lock-%EC%86%8C%EA%B0%9C/r1_36606559
[^news_homeup]: Samsung Global Newsroom, *Exploring Good Lock ①* (2025-04-09): https://news.samsung.com/global/exploring-good-lock-%E2%91%A0-the-ultimate-personalization-tool-discover-the-all-new-home-up
[^news_tp]: Samsung Global Newsroom, *Exploring Good Lock ②* (2025-04-11): https://news.samsung.com/global/exploring-good-lock-%E2%91%A1-unveiling-the-most-popular-good-lock-features
[^news_wonderland]: Samsung Global Newsroom, *Exploring Good Lock ③* (2025-04-15): https://news.samsung.com/global/exploring-good-lock-%E2%91%A2-3-features-recommended-by-samsung-developers-and-newsroom-editors
[^tp_1100]: Samsung Members, *LockStar, 테마파크, KeysCafe S24Ultra기준* (v1.1.00.08, 2024-04-22): https://r1.community.samsung.com/t5/good-lock/%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-lockstar-%ED%85%8C%EB%A7%88%ED%8C%8C%ED%81%AC-keyscafe-s24ultra%EA%B8%B0%EC%A4%80/td-p/26603040
[^tp_review]: Samsung Members, *굿락 테마파크 <Version : 1.1.00.08> 리뷰* (2024-04-22): https://r1.community.samsung.com/t5/good-lock/%ED%8C%81-%ED%9B%84%EA%B8%B0-%EA%B5%BF%EB%9D%BD-%ED%85%8C%EB%A7%88%ED%8C%8C%ED%81%AC-lt-version-1-1-00-08-gt-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-%EB%A6%AC%EB%B7%B0/td-p/26594406
[^clockface_store]: Galaxy Store, *ClockFace*: https://galaxystore.samsung.com/detail/com.samsung.android.app.clockface
[^quickstar_store]: Galaxy Store, *QuickStar*: https://galaxystore.samsung.com/detail/com.samsung.android.qstuner
[^samsung_cp]: Samsung US Support, *Change the theme and icons on your Galaxy phone*: https://www.samsung.com/us/support/answer/ANS10001905/
[^cp_conflict]: Samsung Community, *Theme Park not working with colour pallete OneUI 6*: https://r1.community.samsung.com/t5/galaxy-s/theme-park-not-working-with-colour-pallete-oneui-6/td-p/24358354
[^tp_sun_moon]: Samsung US Community, *Theme Park themes and One UI 8.5 native apps* (2026-09): https://us.community.samsung.com/t5/Samsung-Apps-and-Services/Theme-Park-themes-and-One-UI-8-5-native-apos/m-p/3675318
[^gt_dev]: Samsung Developers, *Galaxy Themes*: https://developer.samsung.com/galaxy-themes
[^gt_icon_blog]: Samsung Developers Blog, *How To Design Galaxy Themes App Icons*: https://developer.samsung.com/sdp/blog/en/2019/07/23/how-to-design-galaxy-themes-app-icons
[^hex_eol]: Samsung Canada Community, *HEX Installer Updated To Support One UI V6.1 (v30 hex_eol)*: https://r1.community.samsung.com/t5/others/hex-installer-updated-to-support-one-ui-v6-1/td-p/25940530
[^colorblendr_gh]: GitHub `Mahmud0808/ColorBlendr#42`: https://github.com/Mahmud0808/ColorBlendr/issues/42
[^s24_s25]: Samsung Support, *S25 series comparison with S24 series*: https://www.samsung.com/lb/support/mobile-devices/s25-series-comparison-with-s24-series/
[^lock_mp4]: Samsung NZ Support, *How to set up Video file as Wallpaper*: https://www.samsung.com/nz/support/mobile-devices/how-to-setup-video-wallpaper/
[^adaptive_icons]: Android Developers, *Adaptive icons*: https://developer.android.com/develop/ui/views/launch/icon_design_adaptive
[^aod_gif]: Samsung Members, *[팁] AOD에 GIF를 넣어보자*: https://r1.community.samsung.com/t5/%EA%B0%A4%EB%9F%AD%EC%8B%9C-s/%ED%8C%81-aod%EC%97%90-gif%EB%A5%BC-%EB%84%A3%EC%96%B4%EB%B3%B4%EC%9E%90/td-p/6004492
[^adb_docs]: Android Developers, *Android Debug Bridge (adb)*: https://developer.android.com/tools/adb
[^smart_switch]: Samsung Korea, *Smart Switch*: https://www.samsung.com/sec/apps/smart-switch/
