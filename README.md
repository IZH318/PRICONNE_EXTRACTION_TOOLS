# 프린세스 커넥트! Re:Dive Asset 추출기 (개발중)
게임 '프린세스 커넥트! Re:Dive'의 원본 Asset을 다운로드 받은 후 Resource를 추출 및 변환하는 도구입니다.

(* 미처 발견하지 못한 오류가 있을 수 있습니다.)

<BR>

## 특징
※ 반드시 온라인 환경에서 작업해야 합니다.

▶ {manifest_filter}에 입력 된 값을 기준으로 원본 Resource 파일을 다운로드 받습니다.<BR>
(* 다운로드 되는 파일 정보는 다음과 같습니다.)
  - Assetbundles (*.unity3d)
  - Audio (*.awb, *.acb)
  - Video (*.usm)

▶ 다운로드 된 원본 파일을 변환합니다.<BR>
(* 확장자 별 변환 과정은 다음과 같습니다.)
  - *.unity3d -> *.png, *.txt
  - *.awb, *.acb -> *.wav
  - *.usm -> *.mp4
  - *storydata.bytes -> *.json

<BR>

## 필수 요구사항
#### ※ 본 도구를 사용할 때 필요한 모든 파일들은 zip 파일 내 \01_Install 폴더에 압축 되어 있습니다.<BR>
#### 제공 한 설치 파일들을 신뢰하지 않을 경우 아래 링크를 통해 다운로드 하시기 바랍니다.<BR><BR>
#### ( ※ zip 파일 내 제공 된 파일들을 사용하려는 경우 이 단계를 생략해도 됩니다.)<BR><BR>

[파일명] python-3.10.11-amd64.exe <BR>
[URL] https://www.python.org/downloads/release/python-31011/ <BR>
[안내] Python Script 동작, 파이썬 3.10.xx 버전 중 아무거나 사용 가능 (단, 3.10.xx 버전이 아닌 다른 버전 사용 시 오류 발생 가능성 높음.)

[파일명] windowsdesktop-runtime-3.1.32-win-x64.exe <BR>
[URL] https://dotnet.microsoft.com/en-us/download/dotnet/3.1 <BR>
[기능] Audio 또는 Video 파일을 변환할 때 사용

<BR>

## 선택 사항 (\01_Install＼_Option 폴더)
#### ( ※ zip 파일 내 제공 된 파일들을 사용하려는 경우 이 단계를 생략해도 됩니다.)<BR><BR>
[파일명] K-Lite_Codec_Pack_1820_Mega.exe
[URL] https://codecguide.com/download_k-lite_codec_pack_basic.htm <BR>
[기능] Audio 및 Video 코덱 설치 (* 추출 된 Audio 또는 Video 파일이 정상적으로 재생되지 않을 시 설치)

<BR>

## 사용 방법
01. zip 파일 다운로드 후 적절한 위치에 압축 해제 합니다.
02. 01_Install 폴더로 이동 후 본문 상단 필수 요구사항과 선택 사항을 참고하여 파일을 설치합니다.
03. 모두 설치가 끝났다면 02_Tools 폴더로 이동합니다.

4. Priconne_Extractor.zip 파일을 압축 해제 합니다.<br>
   [ ※ 주의 ] 모든 데이터들은 Priconne_Extractor.zip 파일을 압축 해제 한 경로에 저장됩니다.
   
6. 00_Install_required_Python_packages.bat 파일을 실행하여 Python Package를 설치합니다.
7. 01_Priconne_Manifest_Extractor.py 파일을 실행하여 필요한 manifest 정보를 다운로드 받습니다.
8. 02_Priconne_Original_Resource_Download_to_Convert.py 파일을 실행하여 다운로드 및 변환 할 manifest 정보를 입력하고 Enter키를 누릅니다.<br>
   ( ※ manifest 파일 별 필요 최소 용량은 아래 표를 참고하십시오. (2024-03-23 AM 02:20 기준))

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


9. [선택사항] 원본 Resource 파일을 모두 제거하려는 경우 03_Priconne_Original_Resource_Remover.bat 파일을 실행하여 원본 Resource 파일을 제거합니다.<br><br>
10. [선택사항] 캐릭터 명을 모두 추출하고 싶다면 04_Find_Character_List.py 파일을 실행합니다.<br><br>
11. [선택사항] 입력 한 캐릭터명 전체 또는 일부를 기준으로 대사 정보 및 Audio 파일 정보를 찾고싶다면 05_Find_Character_Names_in_Storydata.py 파일을 실행합니다.

<BR>

## TODO (ORG)
- Extract from DMM install
- Make the tool more user friendly
- Add more configs
- Remove dependecies
