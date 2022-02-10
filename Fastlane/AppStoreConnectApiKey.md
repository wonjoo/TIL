# AppStoreConnectApiKey

## 목표
fastlane 이용 시 2차인증 없이 이용할 수 있는 api key 이용

## 코드
~~~ruby
 app_store_connect_api_key(
        key_id: "ABCD12",
        issuer_id: "1234-123465-43567-2345",
        key_filepath: "./Fastlane_AuthKey_ABCD12.p8",
        duration: 1200, # optional (maximum 1200)
        in_house: false # optional but may be required if using match/sigh
      )
~~~

## 매개변수 설명

in_house
엔터프라이즈 계정일때 true
