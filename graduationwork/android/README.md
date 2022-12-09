
### android 

<br>

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

<h1>9월 22일 <h1>
 <p>게시판 디자인</p>

<div>
 
 <img src="https://user-images.githubusercontent.com/51393580/206745742-cd81cc2c-177a-44d4-9bf8-f6033d70dd03.png" width ="350" height="600"/>

<img src="https://user-images.githubusercontent.com/51393580/206745749-1ba0ac18-3750-4a7d-882f-ab3baa3c154f.png" width ="350" height="600"/>
 
</div>


<h1>9월30일 70%완료 </h1><br>

<p>게시판(커뮤니티)화면 만들기</p>
 

```c

public void getBoard() { // 원래는 텍스트하고 포토 하고 구분을 할려고 했는데 일단 text만 따로 뽑기로 하겠습니다
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




~~11월 14일 오류 수정 100%~~<br>
~~11월 15일 최종 발표~~<br>
완성

