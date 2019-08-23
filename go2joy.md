# Wisetracker In-App Events Documentation
When some issues occur while you're adding Wisetracker's code, submit those issues with specific information - logs, code snippets and etc. - to John Jeong(humblejohn@wisetracker.co.kr).

# Table of Content
* [Events](./go2joy.md#Events)
	* [Log In](./go2joy.md#Log-In)
		* [Note](./go2joy.md#Note)
		* [Code](./go2joy.md#Code)
	* [Sign-up](./go2joy.md#Sign-up)
		* [Note](./go2joy.md#Note-1)
		* [Code](./go2joy.md#Code-1)
		* [Example](./go2joy.md#Example)
	* [Reading Reviews](./go2joy.md#Reading-Reviews)
		* [Note](./go2joy.md#Note-2)
		* [Code](./go2joy.md#Code-2)
		* [Example](./go2joy.md#Example-1)
	* [Initiated Checkout](./go2joy.md#Initiated-Checkout)
		* [Note](./go2joy.md#Note-3)
		* [Code](./go2joy.md#Code-3)
	* [후기 등록](./go2joy.md#후기-등록)
		* [분석 코드](./go2joy.md#분석-코드-4)
	* [결제 & 매출 분석](./go2joy.md#결제--매출-분석)
		* [주의사항](./go2joy.md#주의사항-2)
		* [분석 코드](./go2joy.md#분석-코드-5)
		* [분석 코드 적용 예시](./go2joy.md#분석-코드-적용-예시)
* [적용 후 데이터 검증](./go2joy.md#적용-후-데이터-검증)
	* [AOS](./go2joy.md#AOS)
	* [iOS](./go2joy.md#iOS)


# Events

### Log In
By adding code below, you cannot only record how many users log in to but also know your user's demographic information.

#### Note
1) This event must be triggered when users log in sucseccfully including 'Auto Log in'.
2) Must check below tables to pass `gender code`, `age code` & `province ID` values.

Gender | Gender Code
-------- | --------
Male | M
Female | F
except the above | U

Age | Age Code
-------- | --------
0 - 10 | A
11 - 19 | B
20 - 29 | C
30 - 39 | D
40 - 49 | E
50 - 59 | F
60 - 69 | G
70 -  | H

Province | Province ID
-------- | --------
Hồ Chí Minh | 1
Hà Nội | 2
Hà Giang | 3
Cao Bằng | 4
Bắc Kạn	| 5
Tuyên Quang	| 6
Lào Cai	| 7
Điện Biên | 8
Lai Châu | 9
Sơn La | 10
Yên Bái	| 11
Hoà Bình | 12
Thái Nguyên | 13
Lạng Sơn | 14
Quảng Ninh | 15
Bắc Giang | 16
Phú Thọ | 17
Vĩnh Phúc | 18
Bắc Ninh | 19
Hải Dương | 20
Hải Phòng | 21
Hưng Yên | 22
Thái Bình | 23
Hà Nam | 24
Nam Định | 25
Ninh Bình | 26
Thanh Hóa | 27
Nghệ An | 28
Hà Tĩnh | 29
Quảng Bình | 30
Quảng Trị | 31
Thừa Thiên Huế | 32
Đà Nẵng | 33
Quảng Nam | 34
Quảng Ngãi | 35
Bình Định | 36
Phú Yên | 37
Khánh Hòa | 38
Ninh Thuận | 39
Bình Thuận | 40
Kon Tum | 41
Gia Lai | 42
Đắk Lắk | 43
Đắk Nông | 44
Lâm Đồng | 45
Bình Phước | 46
Tây Ninh | 47
Bình Dương | 48
Đồng Nai | 49
Bà Rịa - Vũng Tàu | 50
Long An | 51
Tiền Giang | 52
Bến Tre | 53
Trà Vinh | 54
Vĩnh Long | 55
Đồng Tháp | 56
An Giang | 57
Kiên Giang | 58
Cần Thơ | 59
Hậu Giang | 60
Sóc Trăng | 61
Bạc Liêu | 62
Cà Mau | 63


#### Code
Android
``` kotlin
WiseTracker.setPageIdentity("LIR");
WiseTracker.setGoal("g2", 1);
WiseTracker.setGender("gender code");
WiseTracker.setAge("age code");
WiseTracker.setUserAttribute("uvp1", "province ID");
WiseTracker.sendTransaction();
```

iOS - Objective-C
``` objc
[WiseTracker setPageIdentity:@"LIR"];
[WiseTracker setGoal:@"g2" value: 1];
[WiseTracker setGender:@"gender code"];
[WiseTracker setAge:@"age code"];
[WiseTracker setUserAttribute:@"uvp1" name:"province ID"];
[WiseTracker sendTransaction];
```

iOS - Swift
``` swift
WiseTracker.setPageIdentity("LIR")
WiseTracker.setGoal("g2", 1)
WiseTracker.setGender("gender code")
WiseTracker.setAge("age code")
WiseTracker.setUserAttribute("uvp1", "province ID")
WiseTracker.sendTransaction()
```

#### Example
If a 35 years old Male user from Bình Thuận logs in, following lines must be executed.

Android
``` kotlin
WiseTracker.setPageIdentity("LIR");
WiseTracker.setGoal("g2", 1);
WiseTracker.setGender("M");
WiseTracker.setAge("D");
WiseTracker.setUserAttribute("uvp1", "40");
WiseTracker.sendTransaction();
```

iOS - Objective-C
``` objc
[WiseTracker setPageIdentity:@"LIR"];
[WiseTracker setGoal:@"g2" value: 1];
[WiseTracker setGender:@"gender code"];
[WiseTracker setAge:@"age code"];
[WiseTracker setUserAttribute:@"uvp1" name:"40"];
[WiseTracker sendTransaction];
```

iOS - Swift
``` swift
WiseTracker.setPageIdentity("LIR")
WiseTracker.setGoal("g2", 1)
WiseTracker.setGender("M")
WiseTracker.setAge("D")
WiseTracker.setUserAttribute("uvp1", "40")
WiseTracker.sendTransaction()
```

### Sign-up
You can record how many users sign-up via your app.

#### Note
This event should be triggered when users complete sign-up process. Therefore, adding following lines in 'Sign-up Complete Page' is one of good ways to implement. 

#### Code
Android
``` kotlin
WiseTracker.setPageIdentity("RGR");
WiseTracker.setGoal("g1", 1);
WiseTracker.sendTransaction();
```

iOS - Objective-C
``` objc
[WiseTracker setPageIdentity:@"RGR"];
[WiseTracker setGoal:@"g1" value: 1];
[WiseTracker sendTransaction];
```

iOS - Swift
``` swift
WiseTracker.setPageIdentity("RGR")
WiseTracker.setGoal("g1", 1)
WiseTracker.sendTransaction()
```


### Reading Reviews
You can record what hotel's review is read by users.

#### Note
1) This event must be triggered when 'Reading Reviews' button is clicked. Theirfore, we recommend you to add following lines on 'click event' of the button.
2) There are two 'Reading Reviews' buttons in Hotel Detail Page. Make sure to add following lines to those two buttons.
![buttons](http://www.wisetracker.co.kr/wp-content/uploads/2019/08/Untitled-1.jpg)

#### Code
Android
``` kotlin
WiseTracker.setGoal("g10", 1);
WiseTracker.sendGoalData();
```

iOS - Objective-C
``` objc
[WiseTracker setGoal:@"g10" value: 1];
[WiseTracker sendGoalData];
```

iOS - Swift
``` swift
WiseTracker.setGoal("g10", 1)
WiseTracker.sendGoalData()
```

### Initiated Checkout
You can record how many times start to checkout in each hotels.

### Note
1) This event must be triggered when the user successfully reaches 'Billing Information' page only by clicks 'Book now!' button in [this page](http://www.wisetracker.co.kr/wp-content/uploads/2019/08/room-type.jpg).
2) Thus, this code must not be executed in such cases as shown below.
![case](http://www.wisetracker.co.kr/wp-content/uploads/2019/08/Untitled-2.jpg)

#### Code
Android
``` kotlin
WiseTracker.setGoal("g11", 1);
WiseTracker.sendGoalData();
```

iOS - Objective-C
``` objc
[WiseTracker setGoal:@"g11" value: 1];
[WiseTracker sendGoalData];
```

iOS - Swift
``` swift
WiseTracker.setGoal("g11", 1)
WiseTracker.sendGoalData()
```


## 적용 후 데이터 검증
SDK와 API가 올바르게 적용 되었는지 확인하기 위해서는 아래 코드(디버그 모드 활성화)를 적용한 테스트 앱을 저희 쪽으로 보내주시면 됩니다. 보내주신 테스트 앱에서 데이터를 확인한 후 결과에 대해서 회신 드리고 있습니다.

### AOS
AndroidManifest.xml 파일에 아래 메타 데이터 태그를 추가합니다.
``` kotlin
<meta-data android:name="WiseTrackerLogState" android:value="true" />
// 개발용 테스트 앱에는 true로, 배포용 앱에는 false로 설정
```

### iOS
Info.plist 파일에 아래 그림과 같이 값을 추가 합니다.

![iOS Debug Mobe](http://www.wisetracker.co.kr/wp-content/uploads/2019/05/ios-debug.png)

``` swift
<key>WiseTrackerLogState</key>
<string>true</string>
```