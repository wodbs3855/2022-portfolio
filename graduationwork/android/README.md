
### android 

<br>

~~9/15일 안드로이드 50% 완료..~~ <br>
<p>파이어베이스와 안드로이드 스튜디오 연동을 통해 이메일을 통한 로그인 구현

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






~~9월30일 70%완료~~ <br>
~~11월 14일 오류 수정 100%~~<br>
~~11월 15일 최종 발표~~<br>
완성

