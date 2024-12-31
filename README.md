# 프린세스 커넥트! Re:Dive (JP) Asset 추출 도구
게임 '프린세스 커넥트! Re:Dive' (JP)의 원본 게임 데이터를 온라인으로 다운로드 받은 후 Resource를 추출 및 변환하는 도구입니다.

(* 미처 발견하지 못한 오류가 있을 수 있습니다.)

<BR><BR><BR>

## 🔍 주요 기능
■ 가장 먼저 `{manifest_filter}`에 입력 된 값을 기준으로 원본 Resource 파일을 다운로드 받습니다. <BR>
(* 다운로드 되는 파일 정보는 다음과 같습니다.)
  - Assetbundles (*.unity3d)
  - Audio (*.awb, *.acb)
  - Video (*.usm)<BR><BR>

■ `{manifest_filter}`에 입력 된 값을 기준으로 모든 원본 Resource가 다운로드 됐다면 원본 파일을 변환합니다. <BR>
(* 확장자 별 변환 과정은 다음과 같습니다.)
  - *.unity3d -> *.png, *.txt
  - *.awb, *.acb -> *.wav
  - *.usm -> *.mp4
  - *storydata.bytes -> *.json

<BR><BR><BR>

## 🔄 업데이트 내역
### v1.1.0 (2024-12-31)
- **공통**
  - **Asset 다운로드 오류 수정**: https://github.com/lskyset/priconne-asset-extractor/commit/be439ee68c47c861f43b7c270c19c56a87548c0b
  - **사용자 안내 메시지 추가**: 주요 작업(예: 데이터 다운로드, `Dataminer` 인스턴스 생성 등)에 대해 안내 메시지를 출력하여 작업 상태를 사용자에게 알림.
  - **예외 처리 추가**: 실행 중 예기치 않은 오류 발생 시 프로그램 종료되지 않도록 `try-except` 블록 추가.
  - **프로그램 종료 대기**: 작업 완료 및 오류 발생 시 프로그램 종료를 막고, 사용자에게 `Enter`를 눌러 종료하도록 안내하는 기능 추가. <BR> <BR>

- **`05_Find_Character_Names_in_Storydata.py`**
  - **데이터 검색 로직 수정**: `*.json` 파일에서 검색 한 캐릭터의 이름 발견 시 가장 첫 번째 내역만 반환되는 문제 수정. <BR> <BR>

- **`.\src\dataminer.py`**
  - **병렬 처리 방식 변경**:
    - `multiprocessing.Pool`에서 `concurrent.futures.ProcessPoolExecutor`로 병렬 처리 방식 변경
    - `Pool.imap`을 `executor.map`으로 변경하여 코드 가독성 및 유연성 개선
    - 병렬 처리 효율성 개선 및 예외 처리 용이성 향상
  
  - **메모리 최적화**:
    - `__slots__` 추가로 메모리 사용 최적화
    - 객체 속성 동적 할당을 제한하여 메모리 효율성 증대 <BR> <BR>

- **`.\usmtoolkit\ffmpeg.exe`**
  - 최신 버전(* 2024-12-27)으로 업데이트 <BR> <BR>
 
- **기타**
  - `README.md` 수정

<BR>

<details>
<summary>📜 이전 업데이트 내역 - 클릭하여 열기</summary>

### v1.0.0 (2024-03-30)
- **기타**
  - `프린세스 커넥트! Re:Dive (JP) Asset 추출 도구` 게시
  
</details>

<BR><BR><BR>

## 💾 다운로드
[![icon_item_91001](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/89c074f2-f869-4377-8e10-fc6a1d7e5de4)](https://github.com/IZH318/priconne-asset-extractor/releases)
### ※ 추출 도구는 상단 쥬얼 아이콘을 클릭 또는 본 Repositories의 Releases로 이동하여 다운로드 하십시오. <br><br>
### ※ 본 도구를 사용할 때 필요한 모든 파일들은 zip 파일 내 `📁\01_Install` 폴더에 포함되어 있습니다. <BR>
***.zip 파일 내 제공 된 파일들을 사용하려는 경우 개별 다운로드 과정을 생략해도 되며, 제공 된 설치 파일들을 신뢰하지 않을 경우 아래 링크를 통해 개별 다운로드 하시기 바랍니다.** <BR>

| Program                                | URL                                                | 필수여부 | 비고                                                                                           |
|----------------------------------------|----------------------------------------------------|----------|------------------------------------------------------------------------------------------------|
| `Python 3.10.11`            | [Download](https://www.python.org/downloads/release/python-31011/)   | 필수     | ◼ Python Script 동작, 파이썬 3.10.xx 버전 중 아무거나 사용 가능<BR>◼ 단, 3.10.xx 버전이 아닌 다른 버전은 확인한 적 없으므로 정상적인 작동을 보장하지 못 함 |
| `dotNET 3.1` | [Download](https://dotnet.microsoft.com/en-us/download/dotnet/3.1) | 필수     | ◼ Audio 파일 또는 Video 파일을 변환할 때 사용                                                  |
| `K-Lite Codec Pack (Standard)`    | [Download](https://codecguide.com/download_k-lite_codec_pack_standard.htm) | 선택     | ◼ Audio 및 Video 코덱 설치<BR>◼ 추출 된 Audio 파일 또는 Video 파일이 정상적으로 재생되지 않을 때 설치<BR> |

<BR><BR><BR>

## ❗ 주의 사항 ❗
### ※ 반드시 온라인 환경에서 작업해야 합니다. _(오프라인 환경은 고민 중 입니다...)_
### ※ 발견 된 문제를 미리 확인하여 작업 중 적절히 대처할 수 있도록 준비하십시오.

<details>
  <summary>📛 지금까지 발견 된 문제</summary><BR>


`01. 다운로드`<BR>
a 폴더에 다운로드 되는 모든 manifest들은 없는 파일만 다시 다운로드 후 변환 과정을 거치나, `movie2manifest`와 `soundmanifest`는 파일 존재 여부 상관 없이 모든 파일을 다시 처음부터 다운로드 후 변환 과정을 거쳐 시간이 많이 소요 됨.

<BR>

`02. 알 수 없는 문제 발생`<BR>
Scrpit를 통해 다운로드 또는 변환 과정을 거치는 중 알 수 없는 오류가 발생하여 진행이 멈추거나 아무 경고 없이 창이 꺼짐, 작업이 끝나지 않았는데 창이 꺼짐등 과 같은 문제가 발생 함.<BR>
이 경우 창을 닫고 다시 실행하여 동일 작업을 거쳐주면 정상적으로 진행하나, `💾 다운로드`에서 언급 한 `movie2manifest`와 `soundmanifest`는 필요 이상으로 시간이 많이 소요되는 단점이 있음.<BR>

<BR>

`03. PC 성능 저하`<BR>
Scrpit를 통해 다운로드 또는 변환 과정을 거치는 중 필요 이상으로 PC Resource를 사용하여 PC 성능이 낮아지는 문제(ex. RAM 점유율 100%, 가상메모리 점유율 상승, CPU 점유율 상승 등)가 발생.<BR>
특히 저사양 PC 환경이거나, 현재 사용중인 PC의 Windows가 설치 된 `C:\` 또는 `C:\ 하위 폴더 (ex. 바탕화면, 다운로드, 문서 등)`에서 작업을 하는 경우 자주 발견 됨.<BR>
이 경우 현재 사용중인 PC의 Windows가 설치 된 저장 장치에서 작업하지 않고 다른 저장장치에서 작업하면 해결 됐음.<BR>

</details>

<BR>

### ※ 반드시 저장 장치의 여유 공간을 확인 후 작업하시기 바랍니다.
### ※ 모든 내용은 2024-03-23 AM 02:20 기준이며, 작업 시점에 따라 총 용량 및 파일 개수가 달라집니다. <BR> <BR>
### ※ 작업 시점(* 2024-12-31 AM 03:51) 기준, Video 및 Audio Asset만 모두 정상적으로 다운로드 되며, Unity Asset Resource과 관련 된 모든 manifest_assetmanifest 요소들은 접근 권한 문제로 일부 파일만 다운로드 됨. <BR><BR>

**각 manifest 파일 별 추출 및 변환 파일이 저장되는 필요 최소 여유 공간은 아래 표를 참고하십시오.** <BR>
| [MANIFEST FILE NAME] | 디스크 할당 크기 | 내용 |
| --- | --- | --- |
all2_assetmanifest | 3.02GB (3,246,854,144 바이트) | 파일 27,334, 폴더 2,525
animation2_assetmanifest | 3.66MB (3,846,144 바이트) | 파일 276, 폴더 2
arcade2_assetmanifest | 2.85MB (2,990,080 바이트) | 파일 28, 폴더 5
banner2_assetmanifest | 52.3MB (54,845,440 바이트) | 파일 968, 폴더 2
bg2_assetmanifest | 3.44GB (3,699,675,136 바이트) | 파일 11,142, 폴더 1,100
caravan2_assetmanifest | 64.2MB (67,366,912 바이트) | 파일 631, 폴더 109
clanbattle2_assetmanifest | 7.50MB (7,864,320 바이트) | 파일 56, 폴더 2
colosseum2_assetmanifest | 408KB (417,792 바이트) | 파일 20, 폴더 4
comic2_assetmanifest | 50.5MB (53,014,528 바이트) | 파일 600, 폴더 2
consttext2_assetmanifest | 152KB (155,648 바이트) | 파일 1, 폴더 2
dailytask2_assetmanifest | 3.83MB (4,026,368 바이트) | 파일 7, 폴더 5
dungeon2_assetmanifest | 1.56MB (1,642,496 바이트) | 파일 28, 폴더 5
event2_assetmanifest | 893MB (937,369,600 바이트) | 파일 3,948, 폴더 416
font2_assetmanifest | 10.3MB (10,821,632 바이트) | 파일 4, 폴더 2
gacha2_assetmanifest | 2.16MB (2,269,184 바이트) | 파일 20, 폴더 3
howtoplay2_assetmanifest | 126MB (132,472,832 바이트) | 파일 386, 폴더 3
icon2_assetmanifest | 709MB (743,440,384 바이트) | 파일 27,687, 폴더 85
jukebox2_assetmanifest | 11.8MB (12,476,416 바이트) | 파일 698, 폴더 3
knightenhance2_assetmanifest | 7.86MB (8,245,248 바이트) | 파일 152, 폴더 6
lipsyncothers2_assetmanifest | 7.82MB (8,208,384 바이트) | 파일 1,812, 폴더 2
loginbonus2_assetmanifest | 151MB (158,404,608 바이트) | 파일 413, 폴더 54
masterdata_assetmanifest | 9.16MB (9,605,120 바이트) | 파일 1, 폴더 2
minigame2_assetmanifest | 261MB (274,653,184 바이트) | 파일 1,725, 폴더 165
resourcedefine2_assetmanifest | 52.0KB (53,248 바이트) | 파일 3, 폴더 2
room2_assetmanifest | 221MB (232,427,520 바이트) | 파일 5,826, 폴더 2,739
shader2_assetmanifest | 176KB (180,224 바이트) | 파일 2, 폴더 8
ㄴ a | 176KB (180,224 바이트) | 파일 1, 폴더 2
ㄴ assets | 79바이트 (79 바이트) | 파일 1, 폴더 4
spine2_assetmanifest | 1.88GB (2,026,528,768 바이트) | 파일 15,074, 폴더 2,953
storydata2_assetmanifest | 4.26GB (4,577,447,936 바이트) | 파일 37,785, 폴더 13,434
talentquest2_assetmanifest | 1.07MB (1,122,304 바이트) | 파일 7, 폴더 4
travel2_assetmanifest | 152MB (159,477,760 바이트) | 파일 695, 폴더 149
unit2_assetmanifest | 702MB (736,591,872 바이트) | 파일 8,136, 폴더 9
wac2_assetmanifest | 65.3MB (68,558,848 바이트) | 파일 453, 폴더 48
manifest_assetmanifest | / | /
movie2manifest | 108GB (115,967,754,240 바이트) | 파일 5,134, 폴더 3
soundmanifest | 239GB (256,754,122,752 바이트) | 파일 298,681, 폴더 8
ㄴ b | 59.6GB (64,071,749,632 바이트) | 파일 3,050, 폴더 1
ㄴ s | 2.30GB (2,478,477,312 바이트) | 파일 3,179, 폴더 1
ㄴ v | 177GB (190,203,895,808 바이트) | 파일 292,452, 폴더 3

<details>
  <summary>🤔 개인적인 폴더 이름 추측(* 확실하지 않음)</summary><BR>

```
\a = Asset
\b = BGM
\s = SE(Sound Effect)
\v = Voice
```

</details>

<BR>

**전체 manifest 파일 작업 시 필요 최소 여유 공간은 아래 표를 참고하십시오.** <BR>

| 구분 | 디스크 할당 크기 | 내용 |
| --- | --- | --- |
원본 파일 삭제 한 전체 파일 크기 | 275GB (295,939,731,456 바이트) | 파일 367,270, 폴더 23,818
원본 파일 삭제 안 한 전체 파일 크기 | 363GB (389,966,929,920 바이트) | 파일 449,763, 폴더 23,862

<BR>

**각 manifest의 구조는 아래 목록을 클릭하여 참고하십시오.** <BR>
<details>
  <summary>🧾 All Manifests (Level 2)</summary><BR>

```
📁 Priconne_Extractor
  ├📁 a
  │  ├📁 all
  │  ├📁 animation
  │  ├📁 arcade
  │  ├📁 banner
  │  ├📁 bg
  │  ├📁 caravan
  │  ├📁 clanbattle
  │  ├📁 colosseum
  │  ├📁 comic
  │  ├📁 consttext
  │  ├📁 dailytask
  │  ├📁 dungeon
  │  ├📁 event
  │  ├📁 font
  │  ├📁 gacha
  │  ├📁 howtoplay
  │  ├📁 icon
  │  ├📁 jukebox
  │  ├📁 knightenhance
  │  ├📁 lipsyncothers
  │  ├📁 loginbonus
  │  ├📁 masterdata
  │  ├📁 minigame
  │  ├📁 resourcedefine
  │  ├📁 room
  │  ├📁 roomeffect
  │  ├📁 roomfinger
  │  ├📁 roomgrid
  │  ├📁 roomicon
  │  ├📁 roomitem
  │  ├📁 roomthumb
  │  ├📁 shader
  │  ├📁 spine
  │  ├📁 storydata
  │  ├📁 talentquest
  │  ├📁 travel
  │  ├📁 unit
  │  └📁 wac
  ├📁 assets
  ├📁 b
  ├📁 m
  │  └📁 t
  ├📁 manifest
  ├📁 s
  └📁 v
     └📁 t
```

</details>

<BR>

**모든 manifest의 구조와 파일 목록을 확인하고 싶으시다면 아래 목록을 클릭하여 참고하십시오.** <BR>
[🗂 All Manifests (Full)](https://github.com/IZH318/PRICONNE_EXTRACTION_TOOLS/blob/main/All%20Manifests%20(Full).txt)  <BR>

<BR><BR><BR>

## ⏩ 사용 방법
01. zip 파일 다운로드 후 적절한 위치에 압축 해제 합니다. <BR>
![2024-03-23 21 07 06](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/d8c0bd93-36fe-44be-afe1-e6b814415a52) <BR><BR><BR>



2. `01_Install` 폴더로 이동 후 본문 상단 `💾 다운로드`을 참고하여 파일을 설치합니다. <BR>
![2024-03-23 21 07 37](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/d3ebf8ce-080e-49c0-9f6b-3ebb3444e335) <BR>
![2024-03-23 21 10 09](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/c7556e8e-76d8-4fe3-b074-3d26fa43425a) <BR>
**[ ※ 주의 ] Add python.exe to PATH 에 반드시 체크 후 Install Now 클릭** <BR>
(📌 미처 누르지 못했다면 설치파일을 다시 실행 또는 소프트웨어 제거 후 재 설치) <BR><BR><BR>



3. 모두 설치가 끝났다면 `02_Tools` 폴더로 이동합니다. <BR>
![2024-03-23 21 11 06](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/3ab44e7f-c5fb-473e-895b-db47198eb569) <BR><BR><BR>



4. `Priconne_Extractor.zip` 파일을 압축 해제 합니다. <BR>
   **[ ⚠️ 중요 ⚠️ ] 모든 데이터들은 Priconne_Extractor.zip 파일을 압축 해제 한 경로에 저장됩니다.** <BR>
   ![2024-03-23 21 11 31](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/328960d5-7a1d-4e5c-a1cb-054582b98dcd) <BR><BR><BR>



5. `00_Install_required_Python_packages.bat` 파일을 실행하여 Python Package를 설치합니다. <BR>
![2024-03-23 21 12 30](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/2f38827c-7cee-4b4a-9366-f1b56ca6d95f) <BR>
![2024-03-23 21 12 42](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/c223c840-cf1d-4abf-b5d6-3d295be3c43d) <BR>
![2024-03-23 21 12 58](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/44477a1c-76e8-45a1-a494-3ac7b4b595c2) <BR>
(📌 필요 Python Package 설치가 끝나면 위와 같은 화면이 표기됩니다.) <BR><BR><BR>



6. `01_Priconne_Manifest_Extractor.py` 파일을 실행하여 필요한 manifest 정보를 다운로드 받습니다. <BR>
![2024-03-23 21 13 09](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/513b5cfc-62f1-4060-9060-7e8eeed8aeb2) <BR>
![2024-03-23 21 13 25](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/83372f25-6c7e-4572-a2e1-ca001935adda) <BR>
(📌 manifest 추출이 끝나면 위와 같이 파일이 생깁니다.) <BR><BR><BR>



7. `02_Priconne_Original_Resource_Download_to_Convert.py` 파일을 실행하여 다운로드 및 변환 할 manifest 정보를 입력하고 Enter키를 누릅니다. <BR>
![2024-03-23 21 13 40](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/657ac134-e740-4914-9094-bfe64fd1dfab) <BR>
![2024-03-23 21 13 58](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/3e2b1fce-0ba5-4152-bc4e-ead27f5030ba) <BR><BR>

**[ 🛑 경고 🛑 ] 작업하고자 하는 menifest의 최소 여유 공간을 확인하지 않았을 경우 반드시 `❗ 주의 사항 ❗`을 확인 후 작업하십시오.** <BR><BR><BR>
 
![_2024_03_23_21_15_29_34-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/025f37d3-648f-470f-83ad-e6ecf3f67755) <BR>
(📌 `banner2_assetmanifest` 입력 결과) <BR><BR><BR>

![2024-03-23 21 34 48](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/c1cd31f9-8e3b-4d40-96b1-26c9546f8d05) <BR>
**만약 위 사진처럼 예상치 못한 오류로 인해 작업이 중단 또는 멈춘다면 창을 닫고 다시 열어 다시 작업 해 주시기 바랍니다.** <BR><BR><BR>

![2024-03-23 21 15 49](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/a5c05a23-1043-40a5-a754-ccbb35861f11) <BR>
![2024-03-23 21 15 58](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/36d200ae-b3d2-46dc-b1bf-a613e4caa1ba) <BR>
(📌 `banner2_assetmanifest` 입력 결과) <BR><BR>

![2024-03-30 02 06 07](https://github.com/IZH318/PRICONNE_EXTRACTION_TOOLS/assets/99892351/edae366b-51c7-4b14-b0dc-517a204c05ea) <BR>
(📌 `movie2manifest` 입력 결과) <BR><BR>

작업이 성공적으로 끝나면 새로운 폴더와 함께 원본 파일 및 변환 된 파일을 확인할 수 있습니다.

<BR><BR><BR>

## 선택 작업
**아래 작업은 필수 작업은 아니며, 필요에 따라 사용하시면 됩니다.** <BR><BR>

**[선택 작업]** <BR>
원본 Resource 파일을 모두 제거하려는 경우 `03_Priconne_Original_Resource_Remover.bat` 파일을 실행하여 원본 Resource 파일을 제거합니다. <BR><BR>
![2024-03-23 21 16 09](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/23a983ed-5d14-445e-8b22-ff94c48fdffc) <BR>
![_2024_03_23_21_40_55_699-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/138d888e-9da5-41ed-9871-ba3dd0ab1cf5)

<BR><BR><BR>

**[선택 작업]** <BR>
캐릭터 명을 모두 추출하고 싶다면 `04_Find_Character_List.py` 파일을 실행합니다. <BR><BR>
![2024-03-23 21 17 06](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/218c4b3d-c335-49fb-8189-f66cea4085cd) <BR>
![_2024_03_23_21_45_30_866-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/2914305b-b991-4b95-9c42-0e72141c17ad)

<BR><BR><BR>

**[선택 작업]** <BR>
입력 한 캐릭터명 전체 또는 일부를 기준으로 대사 정보 및 Audio 파일 정보를 찾고싶다면 `05_Find_Character_Names_in_Storydata.py` 파일을 실행합니다. <BR><BR>
![2024-03-23 21 49 57](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/0ac69fab-c8b0-4316-8d75-d0120dd4b772) <BR>
![SHANA_2024_03_23_21_50_37_194-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/a9da55db-3b00-441e-848d-17378091521c) <BR>

예를 들어, 'コッコロ(=콧코로)'를 입력하지 않고, 'コ'만 입력 후 검색을 하면 모든 캐릭터 이름 중 'コ'가 포함 된 캐릭터 모두 결과값을 반환합니다. <BR>
(📌 위 GIF에 녹화 된 내용 기준으로 'コッコロ(콧코로)', 'ペコリーヌ(=페코린느)', 'マコト(=마코토)', 'ミヤコ(=미야코)' 가 포함 된 결과가 출력 된 것을 확인할 수 있습니다.)

<BR><BR><BR>

## ⚙ 고급 설정 (선택)
### ※ 이 작업은 Python 언어로 작성 된 Script의 내용을 이해하고 응용할 수 있는 분들께 추천드리는 작업입니다. <BR><BR>

### ❗ 필수 작업 ❗ <BR>
### 아래 작업은 PRICONNE EXTRACTION TOOLS (v1.0.0) 만 해당됩니다. <BR>
![2024-03-30 02 18 44](https://github.com/IZH318/PRICONNE_EXTRACTION_TOOLS/assets/99892351/935aef2e-f653-448e-8c0d-8c1a7d8fb5c0) <BR>
`파일 -> 옵션 -> 보기 -> 숨김 파일 및 폴더`상태를 `숨김 파일, 폴더 및 드라이브 표시`로 변경 후 확인 <BR><BR>

![2024-03-30 02 23 35](https://github.com/IZH318/PRICONNE_EXTRACTION_TOOLS/assets/99892351/020ff6da-1dcd-4b5a-834a-abaabd2e2c70) <BR>
수정하고자 하는 파일 선택 후 `마우스 우클릭 -> 속성 -> 일반 -> 특성`항목 중 `읽기 전용(R)`상태 해제 후 확인 <BR><BR>

**위 작업은 PRICONNE EXTRACTION TOOLS (v1.0.0) 만 해당됩니다.**

<BR> <BR> <BR>

<details>
  <summary>🛠 특정 파일만 다운로드 받은 다음 변환하고자 하는 경우?</summary><BR>

`02_Priconne_Original_Resource_Download_to_Convert.py`파일 실행 후 아래 내용 중 `assetbundle_filter=""`와 `file_filter=""`부분 수정 <BR><BR><BR>
```
    # 만약, png 파일만 저장되게 하고 싶다면?

    dm.datamine(
        manifest_filter=manifest_filter,
        assetbundle_filter="",
        file_filter=".png",
    )
```

```
    # manifest를 입력받지 않고 특정 manifest(`bg2_assetmanifest`)를 바로 다운로드 받고 싶다면?

    ▼ 여기서부터 ▼
    while True:
        manifest_filter = input(">>> ")

        if manifest_filter not in allowed_filenames:
            print("파일명이 올바르지 않습니다. ")
            print()
            continue

        break

    print()
    ▲ 여기까지 모두 삭제 ▲

    dm.datamine(
        # ▼ ▼ ▼ manifest_filter=manifest_filter를 manifest_filter=""로 변경 후 쌍 따옴표 안에 특정 manifest 파일 명 삽입
        manifest_filter="bg2_assetmanifest",
        assetbundle_filter="",
        file_filter="",
    )
```

**보다 자세한 설정은 원 제작자가 제공 한 샘플(`example.py`)을 확인하시기 바랍니다.** <BR>
<details>
  <summary>📔 example.py</summary><BR>

```
from src import Dataminer


def examples():
    # initializes the dataminer
    dm = Dataminer()

    # Extracting a whole manifest
    dm.datamine(
        manifest_filter="wac",
        assetbundle_filter="",
        file_filter="",
    )

    # Extracting images
    dm.datamine(
        manifest_filter="bg",
        assetbundle_filter=r"still_unit_1001[0-9]{2}",
        file_filter=r"still_unit_1001[0-9]{2}\.png",
    )

    # Sound and Movie manifests only contain regular files so the assetbundle filter isn't needed.
    dm.datamine(
        manifest_filter="sound",
        assetbundle_filter="",
        file_filter=r"bgm_M36\.",
    )
    dm.datamine(
        manifest_filter="sound",
        assetbundle_filter="",
        file_filter="bgm_M152",
    )
    dm.datamine(
        manifest_filter="movie",
        assetbundle_filter="",
        file_filter=r"character_1001[0-9]{2}",
    )

    def sd_skel_example():
        # 000000 files contains animations shared by all units
        dm.datamine(
            manifest_filter="spine",
            assetbundle_filter="000000",
            file_filter="cysp",
        )

        # the common cysp contain animations shared by units from the same same class (eg. sword units)
        dm.datamine(
            manifest_filter="spine",
            assetbundle_filter="common",
            file_filter="cysp",
        )

        # filters for the specific unit animations, include all uncap versions
        dm.datamine(
            manifest_filter="spine",
            assetbundle_filter=r"1001[0-9]{2}",
            file_filter=r"1001[0-9]{2}",
        )

        # assemble .cysp files into a .skel file for a given unit_id
        dm.get_skel(100111)

    sd_skel_example()


if __name__ == "__main__":
    # keep all scripting in this scope to avoid bugs with multiprocessing
    examples()

```

</details>

<BR>

</details>

<BR>

<details>
  <summary>🛠 *.usm 파일을 *.mp4 파일이 아닌 다른 확장자로 변환하고자 하는 경우?</summary><BR>

`PRICONNE_EXTRACTION_TOOLS`에 포함 된 `UsmToolkit`은 FFmpeg 표준 구문을 사용합니다.<BR><BR>

01. `\Priconne_Extractor\src\files`로 이동 후 `movie_file.py`파일 내용 중 `extract_path`부분 수정 <BR>
02. `\Priconne_Extractor\usmtoolkit`로 이동 후 `config.json`파일 내용 중 `OutputFormat`부분 수정<BR><BR>
```
    # 만약, *.mp4 파일이 아닌 *.mkv 파일로 저장하고 싶다면?

    # ▼ movie_file.py 파일 내용 중 일부 ▼
    def extract(self) -> None:
        self.download()
        extract_path = self.path.parent.parent / (self.path.stem + ".mkv")  # <--- 확장자 수정
        if extract_path.exists():
            return

    # ▼ config.json 파일 내용 ▼
{
    "VideoParameter" : "-c:v copy",
    "AudioParameter" : "-c:a ac3 -b:a 640k -af pan='stereo|FL=FL+FC+0.5*BL+BR|FR=FR+LFE+0.5*BL+BR'",
    "OutputFormat" : "mkv"
}
    # ▲ OutputFormat을 mkv로 수정 ▲
```

<BR>

**보다 자세한 설정은 FFmpeg 표준 구문을 확인하시기 바랍니다.** <BR>
[📚 FFmpeg 표준 구문 보러 가기](https://ffmpeg.org/ffmpeg-codecs.html)

</details>

<BR><BR><BR>

## 해야 할 일
- 게임 출석
- 콧코로 수첩
- 지역
- 이벤트 스토리
- 던전
- 아레나, 프레나
- 클랜전

<BR><BR><BR>

## Special Thanks to
✨ https://github.com/lskyset <BR>
✨ Princess Connect! Re:Dive Game Users <BR>
