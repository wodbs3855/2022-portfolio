
<h2>안드로이드에서 JSOUP를 이용하여 크롤링을 통해 원하는 데이터 가져오기</h2>


<h3>1. 웹크롤링을 위해 필요한 내용 추가</h3>
<p>인터넷 권한을 주는 코드와, http통신을 가능하게 해주는 코드</p> 
AndroidManifest.xml에서 코드 추가 <br>

```c
<uses-permission android:name="android.permission.INTERNET" />
//application 태그 안에
 android:usesCleartextTraffic="true"
```


<h3>2. gradle의 Module 수준 파일을 열어서 Jsoup 라이브러리를 implementation 시키기</h3>

```c
implementation 'org.jsoup:jsoup:1.13.1

```

<h3>3. 쓰레드를 한개 생성</h3>
Jsoup를 onCreate 에서 실행하게 되면, 웹크롤링 해오는 로딩시간에 앱이 정상적으로 UI를 그릴 수 없음 <br>

**따라서 Thread를 하나 더 만들어주고, 그 쓰레드에서 웹크롤링을 수행함** <br>

```c
new Thread() {
            @Override
            public void run() {
                try {
                	//크롤링 할 구문
                } catch (IOException e) {
                    e.printStackTrace();
                }
         }
}.start();
```
<h3>4. 크롤링을 통해 가져올 데이터가 있는 URL복사</h3>

  <img src="https://user-images.githubusercontent.com/51393580/206897028-c45df1ff-7107-47c3-a05f-0e94fb9c3f6e.png" width ="100%" height="100%"/>

<h3>5. F12를 눌러 개발자 도구를 활성화</h3>
<p>1. 커서모양이 있는 버튼 누르기(select an element in the page to inspect it)</p> 
<p>2. 가져올 데이터가 어디에 소속되어 있는지 확인</p>
클래스 네임은 .class , id 네임은 #id , 즉 . 과 # 로 구분
  <img src="https://user-images.githubusercontent.com/51393580/206897226-9260c185-82ce-491a-bff7-e28c3c3f8cbe.png" width ="850" height="400"/>


<h3>6. try 구문 안에 웹크롤링 코드를 작성</h3>
bundle을 이용하여 데이터 전달
  <img src="https://user-images.githubusercontent.com/51393580/206897030-9c4642ce-5aa1-4a86-90b4-61cc7e6a8555.png" width ="850" height="400"/>
  
  
<h3>7. Handler를 이용해서 새로운 쓰레드에서 했던 작업의 결과물을 주고받기</h3>
<p>가져온 날씨의 데이터에 따라 보여주는 이미지가 달라짐</p>

  <img src="https://user-images.githubusercontent.com/51393580/206897032-332246da-69f1-45bb-89e3-449f9ac8e071.png" width ="850" height="400"/>
  

<img src="https://user-images.githubusercontent.com/51393580/206732146-6f3b32da-5c16-43ed-b0cc-81f9ca4bda32.png" width ="350" height="600"/>  


