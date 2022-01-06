 # GithubAction

 ## 목표
 - push trigger 발생 시 fastlane 실행
 ## 오류
 1. 지원하지 않는 Ruby 버전오류
    - 설치된 MacOS 가상머신의 Ruby버전이 맞지 않으면 오류 발생
    - MacOS 혹은 Ruby버전을 가상머신이 이용하고 있는 Ruby버전으로 변경
 2. fastlane 실행 폴더 경로 오류
    - 폴더 경로가 잘못된 경우 오류 발생
    - **'subdirectory'** 경로 설정으로 오류 해결

## yml 작성
---
### push 발생 시 Trigger 발생
~~~yml
    on:
      push:
        branches: [ develop ]
~~~
### 빌드 머신 설정 / matrix
실행하고자 하는 OS 설정 / 동시에 다른 버전의 빌드를 이용하고 싶을 때 matrix 설정
- 최신버전의 MacOS를 이용
- ruby 2.7 이용

~~~yml
jobs:
  build:
    runs-on: macos-latest
    strategy:
      matrix:
        ruby: [ 2.7]
~~~

### steps 설정
순차적으로 어떤 동작을 할지 작성




<!-- 
    name: Swift

on:
  push:
    branches: [ develop ]
#   pull_request:
#     branches: [ develop ]

jobs:
  build:
    runs-on: macos-latest
    strategy:
      matrix:
        ruby: [ 2.7]
    

    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Install ruby
      uses: actions/setup-ruby@v1
      with:
        ruby-version: ${{ matrix.ruby }}
        
    - name: List files in the repository
      run: |
          ls ${{ github.workspace }}
    - run: echo "🍏 This job's status is ${{ job.status }}."
    # - run: cd ColoringBook & pod install
    - uses: maierj/fastlane-action@v2.0.1
      with:
        lane: 'custom_lane'
        subdirectory: 'ColoringBook' -->
## 참고자료

- **fastlane 이용 가능한 Action**
[Fastlane Action - GitHub Marketplace](https://github.com/marketplace/actions/fastlane-action)