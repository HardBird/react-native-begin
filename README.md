
# React-native-Project 📲


* xCode ver. latest 👌🏻
* Android Studio ver. 29.-👌🏻

*** 
## 코드규칙❕ 
```
// 카멜표기법 사용 (Caemel) 
// 첫 단어는 소문자 후 단어들은 앞에 대문자로 표기해준다. 
// 파일명도 동일
int manAge;
int womanAge;

int peopleAge(int man, int woman){
  return man+woman;
}
```
## 커밋규칙❕
```
git commit -m "[수행한 작업]입력 코멘트"

// 작업은 Fork 선언후에 fetch&merge형식을 이용 

//수행한 작업 예시 

// INIT : 초기화 
// CREATE : 새롭게 추가 되는 컴포넌트나 클래스등 새롭게 추가되는 부분 
// UPDATE : 로직 수정 및 변수 수정 
// DELETE : 로직 삭제 및 변수 삭제 
// ISSUE : 이슈 사항 해결 
```
***
## 사용법❕ 
```
// 기준은 IOS 기반으로 설명함 안드로이드는 참고사이트에 기재.
// REACT-NATIVE-PHOTO-EDITOR-MASTER -> Example 프로젝트 사용 

1. cd ios 
2. pod install 
3. cd .. 
// 상위폴더로 올라가서 패키지 RN 패키지 설치를해준다

4. npm install && yarn install 
5. yarn add react-native-photo-editor
// 필요한 패키징은 5.와 같이 진행하면 됩니다

6. react-native run-ios 혹은 run-android 
```
***
## 이슈 발생 및 해결법❕ 
***
### pod install 실행시 이슈 발생 (=cocoapod) 🤡
```
대부분에 오류는 CompilerC 가 발생한다. 해당 문제에 대한 솔루션은 레퍼런스가 굉장히 많지만,
해결이 되지 않아서 여러 레퍼런스를 찾아본 결과 Podfile에 fliper 패키지를 아래와같이 추가해준다.
pod에 기재하는법은 기존에 있는 패키지 밑에 새로 작성하거나 다 지우고 덮어씌운다음 pod install을 시행해도 된다.
의존성 패키지들은 pod.lock에 다 들어있기 때문이다.
```
```
  use_flipper!({ 'Flipper-Folly' => '2.3.0' }) # update this part
  post_install do |installer|
    flipper_post_install(installer)
    installer.pods_project.targets.each do |target|
      if target.name.include?('iOSPhotoEditor')
        target.build_configurations.each do |config|
          config.build_settings['SWIFT_VERSION'] = '5'
        end
      end
    end
  end
```
### xcode 이슈 발생 🤡
```
해당 오류는 코드 컴파일에서 발생하는 오류이다.
IOS 환경은 업데이트 할때마다 충돌이 굉장히 많아서 버전을 몇단계 내려서 고정하는게 좋은것 같다.

error Failed to build iOS project. We ran "xcodebuild" command but it exited with error code 65. To debug build logs further, consider building your app with Xcode.app, by opening Example.xcworkspace. Run CLI with —verbose flag for more details

해당 이슈가 발생하면 Example 프로젝트에 ios 폴더에 있는 Example.xcworkspace 프로젝트를 실행시켜서
컴파일해보자 ..! 그럼 오류가 발생하는 부분을 고쳐주면 된다. 
```
#### 단, 위에 Fliper부터 적용시킨 다음 검색해보자 대부분 이슈는 저기서 발생한다. 

### xcode 컴파일시 atomic 이슈 발생 🤡
```
해당 부분은 오류가 발생하는곳에 Folly:: 를 붙여주면 해결이 된다. 
이 친구도 Fliper 패키지에 있는 Folly function이다 .. 위 방법을 사용하고 나서도,
해당 오류가 발생하면 오류가 발생하는 부분에 Folly::를 앞에 달아주면 해결된다.
```

***
* [참고사이트1](https://zeddios.tistory.com/410)
* [참고사이트2](https://vero-study.tistory.com/58)
* [안드로이드세팅법](https://reactnative.dev/docs/environment-setup)
* [PHOTOEDITOR](https://github.com/prscX/react-native-photo-editor)
* [Fliper-Folly Folly:: 이슈 관련](https://github.com/facebook/flipper/issues/2215)
