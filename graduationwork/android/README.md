### android 

<h1>9/15일 안드로이드 50% 완료</h1> <br>

<p>파이어베이스와 안드로이드 스튜디오 연동을 통해 이메일을 통한 로그인 구현 </p>

```c 
 private void firebaseAuthWithGoogle(GoogleSignInAccount acct) {
        AuthCredential credential = GoogleAuthProvider.getCredential(acct.getIdToken(), null);
        firebaseAuth.signInWithCredential(credential)
                .addOnCompleteListener(this, new OnCompleteListener<AuthResult>() {
                    @Override
                    public void onComplete(@NonNull Task<AuthResult> task) {
                        if (task.isSuccessful()) {
                            // Sign in success, update UI with the signed-in user's information
                            //Snackbar.make(findViewById(R.id.layout_main), "Authentication Successed.", Snackbar.LENGTH_SHORT).show();
                            FirebaseUser user = firebaseAuth.getCurrentUser();
                            updateUI(user);
                            Toast.makeText(getApplicationContext(), "Complete", Toast.LENGTH_LONG).show();

                        } else {
                            // If sign in fails, display a message to the user.
                            //Snackbar.make(findViewById(R.id.layout_main), "Authentication Failed.", Snackbar.LENGTH_SHORT).show();
                            Toast.makeText(getApplicationContext(), "Authentication Failed", Toast.LENGTH_LONG).show();

                        }
                    }
                });
    }
```

<h1>9월 22일 </h1>
 
 게시판 디자인 <br>
 디자인은 완료 코드 구현만 하면 
 
<div>
 
 <img src="https://user-images.githubusercontent.com/51393580/206746328-4868c690-6b0c-48dd-8f38-7f8f3ae62e81.png" width ="350" height="600"/>

<img src="https://user-images.githubusercontent.com/51393580/206746342-8979474c-c223-4c43-b5e3-54a7591c65fe.png" width ="350" height="600"/>
 

 
</div>


<h1>9월30일 70%완료 </h1><br>

<p>게시판(커뮤니티)화면 만들기</p>
 

```c

public void getBoard() { 
        mDatabase.child("board").child("text").addChildEventListener(new ChildEventListener() {
            @Override
            public void onChildAdded(@NonNull DataSnapshot dataSnapshot, @Nullable String s) {
                Map<String, String> map = (Map) dataSnapshot.getValue();
                mainListView.setAdapter(listAdapter);
                for (DataSnapshot snapshot : dataSnapshot.getChildren()) {
                    Board board = snapshot.getValue(Board.class);

                    arr_uid.add(board.getUid());
                    arr_board_key.add(snapshot.getKey());
                    arr_order_date.add(board.getOrder_date());

                    listAdapter.addItem(board.getTitle(), board.getDate(), board.getName(), board.getClick(), board.getOrder_date());
                }

                Comparator<Board> textDesc = new Comparator<Board>() {
                    @Override
                    public int compare(Board item1, Board item2) {
                        return item2.getOrder_date().compareTo(item1.getOrder_date());
                    }
                };
                Collections.sort(itemList, textDesc);
                listAdapter.notifyDataSetChanged();

                Comparator<String> dateDesc = new Comparator<String>() {
                    @Override
                    public int compare(String item1, String item2) {
                        return item2.compareTo(item1);
                    }
                };
                Collections.sort(arr_order_date, dateDesc);
            }
            @Override
            public void onChildChanged(@NonNull DataSnapshot dataSnapshot, @Nullable String s) {
            }
            @Override
            public void onChildRemoved(@NonNull DataSnapshot dataSnapshot) {
            }
            @Override
            public void onChildMoved(@NonNull DataSnapshot dataSnapshot, @Nullable String s) {
            }
            @Override
            public void onCancelled(@NonNull DatabaseError databaseError) {
            }
        });
    }
```    

<img src="https://user-images.githubusercontent.com/51393580/206732303-c75d8970-82b6-4d38-a56c-b870f45629a6.png" width ="350" height="600"/>
 
 <h1>10월 5일 </h1>
 
  마이페이지 디자인 <br>
  개인 계정 관련 코드만 완성하면 완료
  
 <div> 
  <img src="https://user-images.githubusercontent.com/51393580/206747290-d12e5518-061a-4852-969b-611e1e4270b0.png" width ="350" height="600"/>
  
  <img src="https://user-images.githubusercontent.com/51393580/206747293-e3c7e526-134c-4bfb-93a7-f12b973cac8c.png" width ="350" height="600"/>
  </div>
  
  <h1>10월 13일 </h1>
계정 관련 설정들 완료 <br>
이름과 비밀번호는 이메일을 통한 변경 가능 <br>
현재 아이디 변경은 불가능 

```c

private void send(){
        if(email.length() !=0){
            firebaseAuth.sendPasswordResetEmail(email).addOnCompleteListener(task -> {
                if (task.isSuccessful()){
                    Toast.makeText(this,"이메일을 보냈습니다.",Toast.LENGTH_SHORT).show();
                }
            });
        }
        else {
            Toast.makeText(this,"입력을 완료해 주세요.",Toast.LENGTH_SHORT).show();
        }

    }
    
```
  

<h1>10월 20일</h1>

~~게시판 조회 오류 발견~~ 
<br>
이전 버전으로 돌아가 수정완료

<h1>11월 5일 </h1>
디자인 담당과 디자인 합치기

<div>

<img src="https://user-images.githubusercontent.com/51393580/206749996-05484850-b33f-4de2-834d-27f70300e1df.png" width ="350" height="600"/>

<img src="https://user-images.githubusercontent.com/51393580/206732146-6f3b32da-5c16-43ed-b0cc-81f9ca4bda32.png" width ="350" height="600"/>

</div>

<h1>11월 10일</h1>
 댓글 달기 구현 완료
 
 ```c
 
  public void getBoard() {
        mDatabase.child("board").child("comment").child(board_uid).child(board_key).addChildEventListener(new ChildEventListener() {
            @Override
            public void onChildAdded(@NonNull DataSnapshot dataSnapshot, @Nullable String s) {
                Map<String, String> map = (Map) dataSnapshot.getValue();
                commentListView.setAdapter(commentAdapter);
                int count = 0;

                for (DataSnapshot snapshot : dataSnapshot.getChildren()) {
                    Board board = snapshot.getValue(Board.class);

                    arr_uid.add(board.getUid());
                    arr_board_key.add(snapshot.getKey());

                    commentAdapter.addItem(board.getName(), board.getDate(), board.getComment());

                    count += 1;
                }
                textView_count.setText("댓글 " + Integer.toString(count));
            }

            @Override
            public void onChildChanged(@NonNull DataSnapshot dataSnapshot, @Nullable String s) {

            }

            @Override
            public void onChildRemoved(@NonNull DataSnapshot dataSnapshot) {

            }

            @Override
            public void onChildMoved(@NonNull DataSnapshot dataSnapshot, @Nullable String s) {

            }

            @Override
            public void onCancelled(@NonNull DatabaseError databaseError) {

            }
        });
    }
    
```
 
 
~~11월 14일 오류 수정 100%~~<br>
~~11월 15일 최종 발표~~<br>
완성

