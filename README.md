# 프린세스 커넥트! Re:Dive (JP) Asset 추출 도구 (개발 및 수정중)
게임 '프린세스 커넥트! Re:Dive' (JP)의 원본 게임 데이터를 온라인으로 다운로드 받은 후 Resource를 추출 및 변환하는 도구입니다.

(* 미처 발견하지 못한 오류가 있을 수 있습니다.)

<BR>

## 🔍 주요 기능
■ 가장 먼저 `{manifest_filter}`에 입력 된 값을 기준으로 원본 Resource 파일을 다운로드 받습니다. <BR>
(* 다운로드 되는 파일 정보는 다음과 같습니다.)
  - Assetbundles (*.unity3d)
  - Audio (*.awb, *.acb)
  - Video (*.usm)<BR><BR><BR>

■ `{manifest_filter}`에 입력 된 값을 기준으로 모든 원본 Resource가 다운로드 됐다면 원본 파일을 변환합니다. <BR>
(* 확장자 별 변환 과정은 다음과 같습니다.)
  - *.unity3d -> *.png, *.txt
  - *.awb, *.acb -> *.wav
  - *.usm -> *.mp4
  - *storydata.bytes -> *.json

<BR><BR><BR>

## ⚠ 필수 요구사항 ⚠
[![icon_item_91001](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/89c074f2-f869-4377-8e10-fc6a1d7e5de4)](https://github.com/IZH318/priconne-asset-extractor/releases)
### ※ 추출 도구는 상단 쥬얼 아이콘을 클릭 또는 본 Repositories의 Releases로 이동하여 다운로드 하십시오. <br>

### ※ 본 도구를 사용할 때 필요한 모든 파일들은 zip 파일 내 `📁\01_Install` 폴더에 압축 되어 있습니다. <BR>
**제공 한 설치 파일들을 신뢰하지 않을 경우 아래 링크를 통해 다운로드 하시기 바랍니다.** <BR>
( ※ zip 파일 내 제공 된 파일들을 사용하려는 경우 이 단계를 생략해도 됩니다.) <BR><BR><BR>

**[파일명]** `python-3.10.11-amd64.exe` <BR>
**[URL]** https://www.python.org/downloads/release/python-31011/ <BR>
**[안내]** Python Script 동작, 파이썬 3.10.xx 버전 중 아무거나 사용 가능 (단, 3.10.xx 버전이 아닌 다른 버전은 확인한 적 없으므로 정상적인 작동을 보장하지 못 함.) <BR><BR><BR>

**[파일명]** `windowsdesktop-runtime-3.1.32-win-x64.exe` <BR>
**[URL]** https://dotnet.microsoft.com/en-us/download/dotnet/3.1 <BR>
**[안내]** Audio 파일 또는 Video 파일을 변환할 때 사용

<BR><BR><BR>

## 선택 사항 (`📁\01_Install\_Option`)
#### ( ※ zip 파일 내 제공 된 파일들을 사용하려는 경우 이 단계를 생략해도 됩니다.) <BR><BR>
**[파일명]** `K-Lite_Codec_Pack_1820_Mega.exe` <BR>
**[URL]** https://codecguide.com/download_k-lite_codec_pack_basic.htm <BR>
**[안내]** Audio 및 Video 코덱 설치 (* 추출 된 Audio 파일 또는 Video 파일이 정상적으로 재생되지 않을 시 설치)

<BR><BR><BR>

## ❗ 주의 사항 ❗
### ※ 반드시 온라인 환경에서 작업해야 합니다. _(오프라인 환경은 고민 중 입니다...)_
### ※ 반드시 저장 장치의 여유 공간을 확인 후 작업하시기 바랍니다.
### ※ 모든 내용은 2024-03-23 AM 02:20 기준이며, 작업 시점에 따라 총 용량 및 파일 개수가 달라집니다. <BR><BR>
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
ㄴ \a | 176KB (180,224 바이트) | 파일 1, 폴더 2
ㄴ \assets | 79바이트 (79 바이트) | 파일 1, 폴더 4
spine2_assetmanifest | 1.88GB (2,026,528,768 바이트) | 파일 15,074, 폴더 2,953
storydata2_assetmanifest | 4.26GB (4,577,447,936 바이트) | 파일 37,785, 폴더 13,434
talentquest2_assetmanifest | 1.07MB (1,122,304 바이트) | 파일 7, 폴더 4
travel2_assetmanifest | 152MB (159,477,760 바이트) | 파일 695, 폴더 149
unit2_assetmanifest | 702MB (736,591,872 바이트) | 파일 8,136, 폴더 9
wac2_assetmanifest | 65.3MB (68,558,848 바이트) | 파일 453, 폴더 48
manifest_assetmanifest | / | /
movie2manifest | 108GB (115,967,754,240 바이트) | 파일 5,134, 폴더 3
soundmanifest | 239GB (256,754,122,752 바이트) | 파일 298,681, 폴더 8
ㄴ \b | 59.6GB (64,071,749,632 바이트) | 파일 3,050, 폴더 1
ㄴ \s | 2.30GB (2,478,477,312 바이트) | 파일 3,179, 폴더 1
ㄴ \v | 177GB (190,203,895,808 바이트) | 파일 292,452, 폴더 3

<br><br><br>


**전체 manifest 파일 작업 시 필요 최소 여유 공간은 아래 표를 참고하십시오.** <BR>

| 구분 | 디스크 할당 크기 | 내용 |
| --- | --- | --- |
원본 파일 삭제 한 전체 파일 크기 | 275GB (295,939,731,456 바이트) | 파일 367,270, 폴더 23,818
원본 파일 삭제 안 한 전체 파일 크기 | 363GB (389,966,929,920 바이트) | 파일 449,763, 폴더 23,862

<BR><BR><BR>

**각 manifest의 구조는 아래 목록을 클릭하여 참고하십시오.** <BR>
<details>
  <summary>📄 manifest (Level 2)</summary><BR>

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

<BR><BR><BR>

## ⏩ 사용 방법
01. zip 파일 다운로드 후 적절한 위치에 압축 해제 합니다. <BR>
![2024-03-23 21 07 06](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/d8c0bd93-36fe-44be-afe1-e6b814415a52) <BR><BR><BR>



2. `01_Install` 폴더로 이동 후 본문 상단 필수 요구사항과 선택 사항을 참고하여 파일을 설치합니다. <BR>
![2024-03-23 21 07 37](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/d3ebf8ce-080e-49c0-9f6b-3ebb3444e335) <BR>
![2024-03-23 21 10 09](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/c7556e8e-76d8-4fe3-b074-3d26fa43425a) <BR>
**[ ※ 주의 ] Add python.exe to PATH 에 반드시 체크 후 Install Now 클릭** <BR>
(* 미처 누르지 못했다면 설치파일을 다시 실행 또는 소프트웨어 제거 후 재 설치) <BR><BR><BR>



3. 모두 설치가 끝났다면 `02_Tools` 폴더로 이동합니다. <BR>
![2024-03-23 21 11 06](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/3ab44e7f-c5fb-473e-895b-db47198eb569) <BR><BR><BR>



4. `Priconne_Extractor.zip` 파일을 압축 해제 합니다. <BR>
   **[ ※ 주의 ] 모든 데이터들은 Priconne_Extractor.zip 파일을 압축 해제 한 경로에 저장됩니다.** <BR>
   ![2024-03-23 21 11 31](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/328960d5-7a1d-4e5c-a1cb-054582b98dcd) <BR><BR><BR>



6. `00_Install_required_Python_packages.bat` 파일을 실행하여 Python Package를 설치합니다. <BR>
![2024-03-23 21 12 30](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/2f38827c-7cee-4b4a-9366-f1b56ca6d95f) <BR>
![2024-03-23 21 12 42](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/c223c840-cf1d-4abf-b5d6-3d295be3c43d) <BR>
![2024-03-23 21 12 58](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/44477a1c-76e8-45a1-a494-3ac7b4b595c2) <BR>
(* 필요 Python Package 설치가 끝나면 위와 같은 화면이 표기됩니다.) <BR><BR><BR>



7. `01_Priconne_Manifest_Extractor.py` 파일을 실행하여 필요한 manifest 정보를 다운로드 받습니다. <BR>
![2024-03-23 21 13 09](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/513b5cfc-62f1-4060-9060-7e8eeed8aeb2) <BR>
![2024-03-23 21 13 25](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/83372f25-6c7e-4572-a2e1-ca001935adda) <BR>
(* manifest 추출이 끝나면 위와 같이 파일이 생깁니다.) <BR><BR><BR>



8. `02_Priconne_Original_Resource_Download_to_Convert.py` 파일을 실행하여 다운로드 및 변환 할 manifest 정보를 입력하고 Enter키를 누릅니다. <BR>
![2024-03-23 21 13 40](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/657ac134-e740-4914-9094-bfe64fd1dfab) <BR>
![2024-03-23 21 13 58](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/3e2b1fce-0ba5-4152-bc4e-ead27f5030ba) <BR><BR>

**※ 작업하고자 하는 menifest의 최소 여유 공간을 확인하지 않았을 경우 반드시 주의 사항을 확인 후 작업하십시오.** <BR><BR><BR>
 
![_2024_03_23_21_15_29_34-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/025f37d3-648f-470f-83ad-e6ecf3f67755) <BR>
(* Ex. `banner2_assetmanifest` 입력 결과) <BR><BR><BR>

![2024-03-23 21 34 48](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/c1cd31f9-8e3b-4d40-96b1-26c9546f8d05) <BR>
**만약 위 사진처럼 예상치 못한 오류로 인해 작업이 중단 또는 멈춘다면 창을 닫고 다시 열어 다시 작업 해 주시기 바랍니다.** <BR><BR><BR>

![2024-03-23 21 15 49](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/a5c05a23-1043-40a5-a754-ccbb35861f11) <BR>
![2024-03-23 21 15 58](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/36d200ae-b3d2-46dc-b1bf-a613e4caa1ba) <BR>
작업이 성공적으로 끝나면 새로운 폴더와 함께 원본 파일 및 변환 된 파일을 확인할 수 있습니다.

<BR><BR><BR>

## 선택 작업
**아래 작업은 필수 작업은 아니며, 필요에 따라 사용하시면 됩니다.** <BR><BR><BR>


**[선택 작업]** <BR>
원본 Resource 파일을 모두 제거하려는 경우 `03_Priconne_Original_Resource_Remover.bat` 파일을 실행하여 원본 Resource 파일을 제거합니다. <BR><BR>
![2024-03-23 21 16 09](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/23a983ed-5d14-445e-8b22-ff94c48fdffc) <BR>
![_2024_03_23_21_40_55_699-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/138d888e-9da5-41ed-9871-ba3dd0ab1cf5) <BR><BR><BR>



**[선택 작업]** <BR>
캐릭터 명을 모두 추출하고 싶다면 `04_Find_Character_List.py` 파일을 실행합니다. <BR><BR>
![2024-03-23 21 17 06](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/218c4b3d-c335-49fb-8189-f66cea4085cd) <BR>
![_2024_03_23_21_45_30_866-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/2914305b-b991-4b95-9c42-0e72141c17ad) <BR><BR><BR>



**[선택 작업]** <BR>
입력 한 캐릭터명 전체 또는 일부를 기준으로 대사 정보 및 Audio 파일 정보를 찾고싶다면 `05_Find_Character_Names_in_Storydata.py` 파일을 실행합니다. <BR><BR>
![2024-03-23 21 49 57](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/0ac69fab-c8b0-4316-8d75-d0120dd4b772) <BR>
![SHANA_2024_03_23_21_50_37_194-ezgif com-video-to-gif-converter](https://github.com/IZH318/priconne-asset-extractor/assets/99892351/a9da55db-3b00-441e-848d-17378091521c) <BR>

예를 들어, 'コッコロ(=콧코로)'를 입력하지 않고, 'コ'만 입력 후 검색을 하면 모든 캐릭터 이름 중 'コ'가 포함 된 캐릭터 모두 결과값을 반환합니다. <BR>
(* 위 GIF에 녹화 된 내용 기준으로 'コッコロ(콧코로)', 'ペコリーヌ(=페코린느)', 'マコト(=마코토)', 'ミヤコ(=미야코)' 가 포함 된 결과가 출력 된 것을 확인할 수 있습니다.)

<BR><BR><BR>

## ⚙ 고급 설정
### ※ 이 작업은 Python 언어와 작성 된 Script의 내용을 어느정도 이해하고 응용할 수 있는 분들께 추천드리는 작업입니다. <BR>



🛠 특정 파일만 다운로드 받은 다음 변환하고자 하는 경우? <BR>



🛠 *.usm 파일을 *.mp4 파일이 아닌 다른 확장자로 변환하고자 하는 경우? <BR>



<BR><BR><BR>

■ {manifest_filter}에 입력 된 값을 기준으로 모든 원본 Resource가 다운로드 됐다면 원본 파일을 변환합니다. <BR>
(* 확장자 별 변환 과정은 다음과 같습니다.)
  - *.unity3d -> *.png, *.txt
  - *.awb, *.acb -> *.wav
  - *.usm -> *.mp4
  - *storydata.bytes -> *.json

<BR><BR><BR>

## 해야 할 일
- 게임 출석
- 콧코로 수첩
- 지역
- 이벤트 스토리
- 던전
- 아레나, 프레나
- 클랜전

<BR>

## Special Thanks to
★ https://github.com/lskyset <BR>
★ Princess Connect! Re:Dive Game Users <BR>
