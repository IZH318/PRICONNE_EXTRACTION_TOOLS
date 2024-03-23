# 프린세스 커넥트! Re:Dive Asset 추출기 (개발중)
게임 '프린세스 커넥트! Re:Dive'의 원본 Asset을 다운로드 받은 후 Resource를 추출 및 변환하는 도구입니다.

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
01. zip 파일 다운로드 후 적절한 위치에 압축 해제 합니다.<BR>
02. 01_Install 폴더로 이동 후 본문 상단 필수 요구사항과 선택 사항을 참고하여 파일을 설치합니다.<BR>
03. 모두 설치가 끝났다면 02_Tools 폴더로 이동합니다.<BR>
04. Priconne_Extractor.zip 파일을 압축 해제 합니다.<BR><BR><BR>



05. 00_Install_required_Python_packages.bat 파일을 실행하여 Python Package를 설치합니다.
6. 01_Priconne_Manifest_Extractor.py 파일을 실행하여 필요한 manifest 정보를 다운로드 받습니다.
7. 02_Priconne_Original_Resource_Download_to_Convert.py 파일을 실행하여 다운로드 및 변환 할 manifest 정보를 입력하고 Enter키를 누릅니다.
8. [선택사항] 원본 Resource 파일을 모두 제거하려는 경우 03_Priconne_Original_Resource_Remover.bat 파일을 실행하여 원본 Resource 파일을 제거합니다.
9. [선택사항] 캐릭터 명을 모두 추출하고 싶다면 04_Find_Character_List.py 파일을 실행합니다.
10. [선택사항] 입력 한 캐릭터명 전체 또는 일부를 기준으로 대사 정보 및 Audio 파일 정보를 찾고싶다면 05_Find_Character_Names_in_Storydata.py 파일을 실행합니다.

<BR>

## TODO (ORG)
- Extract from DMM install
- Make the tool more user friendly
- Add more configs
- Remove dependecies
