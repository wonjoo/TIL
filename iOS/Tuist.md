# Tuist


## 기본 프로젝트 구조 설명
Sources : Source 파일 저장 폴더
Test : Test Class

## 기본 설치방법

1. 설치
   1. 비어있는 프로젝트 폴더를 생성합니다.
   2. Terminal을 실행 합니다.
   3. project directory로 이동합니다.
   4. init 명령어를 실행합니다.

   ~~~ruby
   cd/Projects/TuistSample
   tuist init --platform ios
   ~~~

2. Project 구조 설정
   1. Feature Project 추가하기
      1. Feature Folder 생성
      2. tuist init 실행
      3. MainProject Target 설정 시 Dependency 주입

      ~~~Swift
      let dependencies = TargetDependency.project(target: "View", path: "./View")
      let mainTarget = Target(
            name: name,
            platform: platform,
            product: .app,
            bundleId: "io.tuist.\(name)",
            infoPlist: .extendingDefault(with: infoPlist),
            sources: ["Targets/\(name)/Sources/**"],
            resources: ["Targets/\(name)/Resources/**"],
            dependencies: dependencies //target 생성 시 Dependency 추가
        )
      ~~~

   2. Swift Package 추가하기
      1. Tuist 폴더안에 Dependencies.swift 생성

        ~~~Swift
         import ProjectDescription

         let dependencies = Dependencies(carthage: [], swiftPackageManager: [.remote(url: "https://github.com/Alamofire/Alamofire.git", requirement: .upToNextMajor(from: "5.6.1"))], platforms: [.iOS])
        ~~~

      2. SPM Package 경로 추가
      3. Terminal 실행 'tuist dependencies fetch' SKD Load
   3. 프로젝트 생성

   ~~~ruby
   tuist generate
   ~~~

3. Workspace Feature Project 추가하기

## TODO

1. Workspace.swift 추가 방법
2. Error
   1. package name error
   2. Dependencies.swift directory 경로 오류
   3. Target, Framework 파일 경로 오류 or 파일 미생성
