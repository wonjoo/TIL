# FirebaseAndroidDeploy

## 목표
1. firebase app upload


## 작업

Android 프로젝트의 루트에서 다음 명령어를 실행합니다.
~~~ruby
fastlane add_plugin firebase_app_distribution
~~~
!!주의사항!!
Pluginfile 파일이 루트가 아닌 폴더에 생성 시 fastlane action 오류 발생


## 코드
~~~ruby
desc "distribute to AppDistribution"
  lane :deploy do
  
    gradle(task:'assemble', flavor: 'flavor', build_type: 'dev')
    
    APK_LOCATION = "#{Actions.lane_context[SharedValues::GRADLE_APK_OUTPUT_PATH]}"
    puts("App Build Complete")
    puts("apk location : " + APK_LOCATION)

    firebase_app_distribution(
      app: firebaseAppId,
      firebase_cli_token:firebase_app_token,
      apk_path:APK_LOCATION,
      testers:"tester@gmail.com",
      release_notes:"test for fastlane"
    )
  end
~~~
