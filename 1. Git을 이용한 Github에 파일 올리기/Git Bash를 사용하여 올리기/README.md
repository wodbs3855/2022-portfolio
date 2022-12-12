
### Git Bash를 사용하여 Github에 올리기

<h2>1. Github에 올리고 싶은 파일 오른쪽 클릭을 해 Git Bash Here선택</h2>

<p>Git Bash Here 선택</p>
 <img src="https://user-images.githubusercontent.com/51393580/206869674-7fc18844-9094-41cf-8bdb-45af30cf7004.png" width ="350" height="400"/>
 

<h2>2. 환경설정시 이름과 이메일을 등록과 확인</h2>
이름과 이메일 등록하기 <br>
git config --global user.name 이름 <br>
git config --global user.email 이메일<br>
<br>

제대로 등록되었는지 확인 <br>
git config --list

 <img src="https://user-images.githubusercontent.com/51393580/206868423-81919fb6-d91e-4079-9750-adbc8136e476.png" width ="450" height="400"/>
 
<h2>3. 현재 폴더를 로컬 저장소로 지정하고 현재 상태 확인</h2>
git init (초기화)<br>
git status으로 로컬 저장소의 현재 상태를 확인 <br>
 <img src="https://user-images.githubusercontent.com/51393580/206870281-e65fd54d-dffd-4e74-9a93-2e187d3e46e8.png" width ="650" height="400"/>
 
 해당 폴더에 .git 폴더가 생성
 
 <img src="https://user-images.githubusercontent.com/51393580/206869993-77aa7525-7380-40f1-b97b-68023c381834.png" width ="550" height="400"/>


<h2>4. 브랜치명 변경</h2>
push하는 과정에서 브랜치명이 일치하지 않으면 오류가 발생 <br>
 <img src="https://user-images.githubusercontent.com/51393580/206870391-2adfa054-9e0e-4794-acd1-e7ba323e8e63.png" width ="500" height="100"/>

<h2>5. 파일들을 준비영역에 추가</h2>
git add . (여기서 주의!! add 다음에 띄우고 .)
<img src="https://user-images.githubusercontent.com/51393580/206870503-ea635423-6f14-4337-acd8-1a0a48af26a9.png" width ="700" height="300"/>

<h2>6. 로컬 저장소에 commit하기</h2>
git commit -m "메세지입력"으로 commit
<img src="https://user-images.githubusercontent.com/51393580/206870571-7a5b8e62-8eba-4d9e-8fc9-f6c51cd833ed.png" width ="500" height="600"/>


<h2>7. 로컬 저장소와 원격 저장소를 연결및 별칭 내역 확인</h2>
git remote add origin Git Repository [주소] 로 연결 <br>
<br>
별칭 내역을 확인 <br> 
git remote -v

<img src="https://user-images.githubusercontent.com/51393580/206870644-c68673de-96bc-432e-958a-e466e0154ecb.png" width ="700" height="200"/>

<h2>8. 로컬 저장소의 파일들을 원격 저장소로 올리기.</h2>
git push origin main <br>


<img src="https://user-images.githubusercontent.com/51393580/206870793-495bd2ea-c725-4fea-b8a0-2cef1e596372.png" width ="700" height="200"/>

push 하는 과정에서 이와 같은 에러가 발생 원격 저장소와 로컬 저장소가 달라서 나는 오류 <br>
이럴경우 pull을 먼저 해서 상태를 같게 한 다음 push를 해주면 됨 <br>
git pull origin main

<img src="https://user-images.githubusercontent.com/51393580/206870895-ac433fac-f7d9-46e4-94f2-531dee955cbb.png" width ="700" height="200"/>

<h2>9. pull 먼저 하고 push를 하였는데도 오류가 발생하면 강제로 push 가능</h2>
강제로 push 하기 <br>
git push origin +main

<img src="https://user-images.githubusercontent.com/51393580/206871001-e704a752-8b20-4275-b1a7-771f8ce55a27.png" width ="500" height="200"/>

<h2>9. 제대로 올라왔는지 확인</h2>
<img src="https://user-images.githubusercontent.com/51393580/206871202-9182fb35-476a-406a-922b-ff2a30faa4a0.png" width ="700" height="500"/>

---
[Gitbash로 올린 저장소 바로가기](https://github.com/wodbs3855/gitbash.git) <br>
[참고한 사이트들 ](https://github.com/wodbs3855/2022-portfolio/wiki/Reference-Site)
[Git과 안드로이드 사용하여 Github에 올리기](https://github.com/wodbs3855/2022-portfolio/tree/main/1.%20Git%EC%9D%84%20%EC%9D%B4%EC%9A%A9%ED%95%9C%20Github%EC%97%90%20%ED%8C%8C%EC%9D%BC%20%EC%98%AC%EB%A6%AC%EA%B8%B0/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C%20%EC%8A%A4%ED%8A%9C%EB%94%94%EC%98%A4%EC%97%90%EC%84%9C%20%EC%98%AC%EB%A6%AC%EA%B8%B0)


