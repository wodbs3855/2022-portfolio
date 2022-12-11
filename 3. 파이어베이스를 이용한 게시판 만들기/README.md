
<h2>파이어베이스를 이용한 게시판 만들기</h2>

이미 파이어베이스와 안드로이드가 연동되어있다고 가정하고 진행 <br>
연동이 안되어있다면 [사이트 참고](https://minggu92.tistory.com/75?category=928636)


<h2>1. JSON이해</h2>
<p>파이어베이스는 JSON형태의 데이터를 사용</p>
<p>Key-Value를 사용하여 데이터를 주고 받도록 제공 </p>
<p>트리 구조로 데이터를 저장</p>

<div>

  <img src="https://user-images.githubusercontent.com/51393580/206905006-8e0c0fac-f28c-4a71-a143-baac04968408.png" width ="400" height="500"/>

  <img src="https://user-images.githubusercontent.com/51393580/206904890-2e4c487d-17c1-4aa7-9d16-33a0272db8f0.png" width ="400" height="500"/>
</div>

<hr>

<h2>2. 게시판 클래스 생성</h2>
<p>파이어베이스는 데이터 전달을 클래스를 통해 진행</p>
<img src="https://user-images.githubusercontent.com/51393580/206905755-9d7ed0a2-94dd-4ad5-a7f6-b98ca8936fa0.png" width ="600" height="500"/>

<h2>3. 게시판 클래스를 이용하여 파이어베이스에 데이터 올리기</h2>
<p></p>

<img src="https://user-images.githubusercontent.com/51393580/206906266-7ffbb619-c721-4f0b-8ecc-16b5a0372787.png" width ="600" height="500"/>


<p>파이어베이스에 올라간 게시판 데이터</p>
<img src="https://user-images.githubusercontent.com/51393580/206906533-1ef8fb1c-96ef-4622-9b1d-e11d5cc1f5a9.png" width ="90%" height="700"/>


<h2>4. 파이어베이스에 올라간 안드로이드에 보여주기</h2>
<p>ListAdapter를 이용한 게시판 형식 지정</p>
<img src="https://user-images.githubusercontent.com/51393580/206907182-660256c6-595d-498f-8958-801ae4a3237d.png" width ="800" height="500"/>

<p>게시판 내용 가져오는 함수를 생성</p>

<img src="https://user-images.githubusercontent.com/51393580/206906263-2aaed7ab-0971-4b02-96b1-37e2ae87d5f7.png" width ="800" height="500"/>

<h2>5. 게시판 내용보여주기</h2>
<p>ListAdapter를 이용한 게시판 보여주기</p>
<img src="https://user-images.githubusercontent.com/51393580/206732303-c75d8970-82b6-4d38-a56c-b870f45629a6.png" width ="350" height="600"/>

<hr>

[적용한 파일 바로가기](https://github.com/wodbs3855/2022-portfolio/tree/main/graduationwork/android/Carekicks) <br>
[참고한 사이트들 바로가기](https://github.com/wodbs3855/2022-portfolio/wiki/Reference-Site)


