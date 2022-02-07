# UploadToTestflight

## 목표
1. TestFlgith 앱 업로드기능


## 변수
1. ipa파일 정의
빌드없이 파일을 업로드 하기 위해서는 ipa파일 경로 지정 필요
~~~ruby
upload_to_testflight(
    ipa:"../fastlane/BuildApps/app.ipa"
)
~~~

2. Beta 테스터 앱 배포
앱 업로드 / Beta테스터 앱 공지하기 위해서는 아래 코드가 필수로 들어가야 한다.
~~~ruby
upload_to_testflight(
    distribute_external:true,
    groups: "group1"
)
~~~


## 참고자료
[Fastlane Action - upload_to_testflight](https://docs.fastlane.tools/actions/upload_to_testflight/)