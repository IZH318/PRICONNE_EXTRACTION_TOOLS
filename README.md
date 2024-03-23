# 프린세스 커넥트! Re:Dive Asset 추출기
게임 '프린세스 커넥트! Re:Dive'의 원본 Asset을 다운로드 받은 후 Resource를 추출 및 변환하는 도구입니다.

<BR>

## 특징
※ 반드시 온라인 환경에서 작업해야 합니다.

▶ {manifest_filter}에 입력 된 값을 기준으로 파일을 다운로드 받습니다.<BR>
(* 다운로드 되는 원본 파일 확장자 정보는 다음과 같습니다.)
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

## 설치
- 최신 릴리즈 소스 코드를 다운로드 합니다.
- 다운 받은 *.zip 파일을 적절한 위치에 압축 해제 합니다.
- 필수 요구사항 단계를 참고하여 작업을 진행하십시오.

<BR>

## 필수 요구사항




[UsmToolkit] (https://github.com/Rikux3/UsmToolkit) (Audio and Video)
릴리스 페이지(윈도우 전용)에서 다운로드하여 루트 폴더에 넣거나 이미 가지고 있는 경우 src/config.py 의 경로를 편집합니다.
UsmToolkit이 없는 Windows 사용자는 플랫폼에 맞게 직접 구축해야 합니다.

<BR>

## Depends on
[master.db](https://github.com/lskyset/nozomi-cb-data/blob/main/master.db)

<BR>

## 사용 방법
- run `python priconne_asset_extractor.py` once to download all the manifests
- Edit the filters in priconne_asset_extractor.py

```py
    # Example: to download all background assets from bg2_assetmanifest
    dm.datamine(
        manifest_filter="bg",
        assetbundle_filter="",
        file_filter="",
    )
```

For more examples see `example.py`

<BR>

## TODO (ORG)
- Extract from DMM install
- Make the tool more user friendly
- Add more configs
- Remove dependecies
