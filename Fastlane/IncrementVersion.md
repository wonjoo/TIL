# IncrementVersion

## 목표
1. 운영중인 버전 확인
2. 운영 버전보다 patch 버전 1증가


## 코드
~~~ruby
desc "increment version number"
  lane :increment_version do

    if ENV['SCHEME'] != nil
      
      # reelase 버전 확인
      app_store_build_number(
        app_identifier: ENV['BUNDLE_IDENTIFIER'],
        username: "user@user.com"
      )

      releaseVersion = lane_context[SharedValues::LATEST_VERSION]
      increment_version_number(version_number: releaseVersion)# 릴리즈 버전 적용
      increment_version_number(bump_type:"patch")# 버전 중가

      puts(releaseVersion) 
    end
  end
  ~~~