### android 

~~안드로이드와 파이어베이스 연동 완료~~
~~기본 구성 배치 완료~~



<h1>9/15일 로그인 기능 구현 완료</h1> <br>

<p>파이어베이스와 안드로이드 스튜디오 연동을 통해 이메일을 통한 로그인 구현 </p>

```java
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

<h1>9월 22일 게시판 디자인 완료</h1>
 
 ListAdapter로 구조와 디자인 완료 코드만 구현하면 됨 
 
<div>
 
 <img src="https://user-images.githubusercontent.com/51393580/206746328-4868c690-6b0c-48dd-8f38-7f8f3ae62e81.png" width ="350" height="600"/>

<img src="https://user-images.githubusercontent.com/51393580/206746342-8979474c-c223-4c43-b5e3-54a7591c65fe.png" width ="350" height="600"/>
 
</div>

<h1>9월30일 게시판 코딩 완료 </h1><br>

<p>게시판(커뮤니티)화면 만들기</p>


<p>파이어베이스에 게시판 데이터 올리기</p>

<img src="https://user-images.githubusercontent.com/51393580/206906266-7ffbb619-c721-4f0b-8ecc-16b5a0372787.png" width ="600" height="500"/>


<p>파이어베이스에 올린 데이터를 가져와 보여주기</p>
 
```java

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

<p>완성된 게시판</p>

<img src="https://user-images.githubusercontent.com/51393580/206732303-c75d8970-82b6-4d38-a56c-b870f45629a6.png" width ="350" height="600"/>
 
 <h1>10월 5일 마이페이지 디자인</h1>
 
  개인 계정 관련 코드만 완성하면 완료
  
 <div> 
  <img src="https://user-images.githubusercontent.com/51393580/206747290-d12e5518-061a-4852-969b-611e1e4270b0.png" width ="350" height="600"/>
  
  <img src="https://user-images.githubusercontent.com/51393580/206747293-e3c7e526-134c-4bfb-93a7-f12b973cac8c.png" width ="350" height="600"/>
  </div>
  
  <h1>10월 13일 마이페이지 계정 관련 설정들 완료</h1>
 
이름과 비밀번호는 이메일을 통한 변경 가능 <br>
현재 아이디 변경은 불가능 

```java

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

<h1>11월 10일 댓글 달기 구현 완료</h1>
 
 ```java
 
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
<h1>11월 12일 컨텍스트 메뉴를 이용한 길게 누르면 메뉴 나오기</h1>
<p>1. res아래 menu파일을 만들고 context파일 생성</p>

컨텍스트 메뉴 설정

```java

@Override
    public void onCreateContextMenu(ContextMenu menu, View v, ContextMenu.ContextMenuInfo menuInfo) {

        MenuInflater inflater= getMenuInflater();
        inflater.inflate(R.menu.context, menu);

        super.onCreateContextMenu(menu, v, menuInfo);
    }

    @Override
    public boolean onContextItemSelected(MenuItem item) {

        //context.xml파일에 작성한 메뉴항목들의 id를 식별하여 토스트 보여주기
        switch ( item.getItemId() ){
            case R.id.menu_mod:
                button_del.setVisibility(View.INVISIBLE);
                button_edit.setVisibility(View.INVISIBLE);
                button_add.setVisibility(View.INVISIBLE);
                editComment.setVisibility(View.INVISIBLE);
                button_ok.setVisibility(View.VISIBLE);
                button_cancle.setVisibility(View.VISIBLE);
                textView_count.setVisibility(View.INVISIBLE);
                commentListView.setVisibility(View.INVISIBLE);
                textView_read_board.setText("게시글 수정");

                editText_read_board_title.setText(textView_read_board_title2.getText().toString());
                textView_read_board_title2.setVisibility(View.INVISIBLE);
                editText_read_board_title.setVisibility(View.VISIBLE);
                editText_read_board_content.setText(textView_read_board_content.getText().toString());
                textView_read_board_content.setVisibility(View.INVISIBLE);
                editText_read_board_content.setVisibility(View.VISIBLE);
                
                break;

            case R.id.menu_delete:
                DialogInterface.OnClickListener confirm = new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        mDatabase.child("board").child("text").child(board_uid).child(board_key).removeValue();
                        Intent intent = new Intent(getApplicationContext(), BoardActivity.class);
                        startActivity(intent);
                        finish();
                    }
                };
                DialogInterface.OnClickListener cancle = new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                    }
                };
                new AlertDialog.Builder(ReadBoardActivity.this).setTitle("게시글을 삭제하시겠습니까?")
                        .setPositiveButton("삭제", confirm)
                        .setNegativeButton("취소", cancle).show();
                break;
        }

        return super.onContextItemSelected(item);
    }

```    



<h1>11월 14일 </h1>

~~게시판 조회오류와 블루투스 오작동~~
<br>
100% 최종 수정 완료

<h1>11월 15일</h1>
발표 완료 

