
# React-native-Project ๐ฒ


* xCode ver. latest ๐๐ป
* Android Studio ver. 29.-๐๐ป

*** 
## ์ฝ๋๊ท์นโ 
```
// ์นด๋ฉํ๊ธฐ๋ฒ ์ฌ์ฉ (Caemel) 
// ์ฒซ ๋จ์ด๋ ์๋ฌธ์ ํ ๋จ์ด๋ค์ ์์ ๋๋ฌธ์๋ก ํ๊ธฐํด์ค๋ค. 
// ํ์ผ๋ช๋ ๋์ผ
int manAge;
int womanAge;

int peopleAge(int man, int woman){
  return man+woman;
}
```
## ์ปค๋ฐ๊ท์นโ
```
git commit -m "[์ํํ ์์]์๋ ฅ ์ฝ๋ฉํธ"

// ์์์ Fork ์ ์ธํ์ fetch&mergeํ์์ ์ด์ฉ 

//์ํํ ์์ ์์ 

// INIT : ์ด๊ธฐํ 
// CREATE : ์๋กญ๊ฒ ์ถ๊ฐ ๋๋ ์ปดํฌ๋ํธ๋ ํด๋์ค๋ฑ ์๋กญ๊ฒ ์ถ๊ฐ๋๋ ๋ถ๋ถ 
// UPDATE : ๋ก์ง ์์  ๋ฐ ๋ณ์ ์์  
// DELETE : ๋ก์ง ์ญ์  ๋ฐ ๋ณ์ ์ญ์  
// ISSUE : ์ด์ ์ฌํญ ํด๊ฒฐ 
```
***
## ์ฌ์ฉ๋ฒโ 
```
// ๊ธฐ์ค์ IOS ๊ธฐ๋ฐ์ผ๋ก ์ค๋ชํจ ์๋๋ก์ด๋๋ ์ฐธ๊ณ ์ฌ์ดํธ์ ๊ธฐ์ฌ.
// REACT-NATIVE-PHOTO-EDITOR-MASTER -> Example ํ๋ก์ ํธ ์ฌ์ฉ 

1. cd ios 
2. pod install 
3. cd .. 
// ์์ํด๋๋ก ์ฌ๋ผ๊ฐ์ ํจํค์ง RN ํจํค์ง ์ค์น๋ฅผํด์ค๋ค

4. npm install && yarn install 
5. yarn add react-native-photo-editor
// ํ์ํ ํจํค์ง์ 5.์ ๊ฐ์ด ์งํํ๋ฉด ๋ฉ๋๋ค

6. react-native run-ios ํน์ run-android 
```
***
## ์ด์ ๋ฐ์ ๋ฐ ํด๊ฒฐ๋ฒโ 
***
### pod install ์คํ์ ์ด์ ๋ฐ์ (=cocoapod) ๐คก
```
๋๋ถ๋ถ์ ์ค๋ฅ๋ CompilerC ๊ฐ ๋ฐ์ํ๋ค. ํด๋น ๋ฌธ์ ์ ๋ํ ์๋ฃจ์์ ๋ ํผ๋ฐ์ค๊ฐ ๊ต์ฅํ ๋ง์ง๋ง,
ํด๊ฒฐ์ด ๋์ง ์์์ ์ฌ๋ฌ ๋ ํผ๋ฐ์ค๋ฅผ ์ฐพ์๋ณธ ๊ฒฐ๊ณผ Podfile์ fliper ํจํค์ง๋ฅผ ์๋์๊ฐ์ด ์ถ๊ฐํด์ค๋ค.
pod์ ๊ธฐ์ฌํ๋๋ฒ์ ๊ธฐ์กด์ ์๋ ํจํค์ง ๋ฐ์ ์๋ก ์์ฑํ๊ฑฐ๋ ๋ค ์ง์ฐ๊ณ  ๋ฎ์ด์์ด๋ค์ pod install์ ์ํํด๋ ๋๋ค.
์์กด์ฑ ํจํค์ง๋ค์ pod.lock์ ๋ค ๋ค์ด์๊ธฐ ๋๋ฌธ์ด๋ค.
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
### xcode ์ด์ ๋ฐ์ ๐คก
```
ํด๋น ์ค๋ฅ๋ ์ฝ๋ ์ปดํ์ผ์์ ๋ฐ์ํ๋ ์ค๋ฅ์ด๋ค.
IOS ํ๊ฒฝ์ ์๋ฐ์ดํธ ํ ๋๋ง๋ค ์ถฉ๋์ด ๊ต์ฅํ ๋ง์์ ๋ฒ์ ์ ๋ช๋จ๊ณ ๋ด๋ ค์ ๊ณ ์ ํ๋๊ฒ ์ข์๊ฒ ๊ฐ๋ค.

error Failed to build iOS project. We ran "xcodebuild" command but it exited with error code 65. To debug build logs further, consider building your app with Xcode.app, by opening Example.xcworkspace. Run CLI with โverbose flag for more details

ํด๋น ์ด์๊ฐ ๋ฐ์ํ๋ฉด Example ํ๋ก์ ํธ์ ios ํด๋์ ์๋ Example.xcworkspace ํ๋ก์ ํธ๋ฅผ ์คํ์์ผ์
์ปดํ์ผํด๋ณด์ ..! ๊ทธ๋ผ ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ ๋ถ๋ถ์ ๊ณ ์ณ์ฃผ๋ฉด ๋๋ค. 
```
#### ๋จ, ์์ Fliper๋ถํฐ ์ ์ฉ์ํจ ๋ค์ ๊ฒ์ํด๋ณด์ ๋๋ถ๋ถ ์ด์๋ ์ ๊ธฐ์ ๋ฐ์ํ๋ค. 

### xcode ์ปดํ์ผ์ atomic ์ด์ ๋ฐ์ ๐คก
```
ํด๋น ๋ถ๋ถ์ ์ค๋ฅ๊ฐ ๋ฐ์ํ๋๊ณณ์ Folly:: ๋ฅผ ๋ถ์ฌ์ฃผ๋ฉด ํด๊ฒฐ์ด ๋๋ค. 
์ด ์น๊ตฌ๋ Fliper ํจํค์ง์ ์๋ Folly function์ด๋ค .. ์ ๋ฐฉ๋ฒ์ ์ฌ์ฉํ๊ณ  ๋์๋,
ํด๋น ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ฉด ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ ๋ถ๋ถ์ Folly::๋ฅผ ์์ ๋ฌ์์ฃผ๋ฉด ํด๊ฒฐ๋๋ค.
```

***
* [์ฐธ๊ณ ์ฌ์ดํธ1](https://zeddios.tistory.com/410)
* [์ฐธ๊ณ ์ฌ์ดํธ2](https://vero-study.tistory.com/58)
* [์๋๋ก์ด๋์ธํ๋ฒ](https://reactnative.dev/docs/environment-setup)
* [PHOTOEDITOR](https://github.com/prscX/react-native-photo-editor)
* [Fliper-Folly Folly:: ์ด์ ๊ด๋ จ](https://github.com/facebook/flipper/issues/2215)
