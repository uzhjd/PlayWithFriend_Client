<template>
  <div class="container">
    <v-card id="videoRoomCard">
        <v-card-title class="title">로그인</v-card-title>
          <v-card-text class="entry-room-container">
            <div class="entry-room-box">
              <div class="entry-room-form">
                <p class="entry-room-form__title">Id</p>
                <v-text-field
                  v-model="userId"
                  label="아이디를 입력해주세요."
                  v-on:keyup.enter="roomPass"
                  hide-details="auto"
                  maxlength="30"
                ></v-text-field>
              </div>
              <div class="entry-room-form">
                <p class="entry-room-form__title">Password</p>
                <v-text-field
                  v-model="password"
                  label="비밀 번호를 입력해주세요."
                  v-on:keyup.enter="password"
                  hide-details="auto"
                  maxlength="24"
                ></v-text-field>
              </div>

              <g-signin-button
                :params="googleSignInParams"
                @success="onSignInSuccess"
                @error="onSignInError">
                Sign in with Google
              </g-signin-button>
              <br>
              <br>
              <v-btn
                class="entry-room-box__enter-bnt"
                @click="joinRoom()"
              >
                입 장
              </v-btn>

              &nbsp;
              <v-btn
                class="entry-room-box__cancel-bnt"
                @click="back()"
              >
                취 소
              </v-btn>
            </div>
          </v-card-text>
    </v-card>
  </div>
</template>

<script>

export default {
  data() {
    return {
      googleSignInParams: {
        client_id: 'YOUR_APP_CLIENT_ID.apps.googleusercontent.com'
      }
    }
  },
  created() {
  },
  methods: {
    onSignInSuccess (googleUser) {
      // `googleUser` is the GoogleUser object that represents the just-signed-in user.
      // See https://developers.google.com/identity/sign-in/web/reference#users
      // const profile = googleUser.getBasicProfile() // etc etc
      googleUser.getBasicProfile() 
    },
    onSignInError (error) {
      // `error` contains any error occurred.
      console.log('OH NOES', error)
    },
    joinRoom(){
      this.$router.push('/')
    },
    back(){
      this.$router.push('/')
    }
    
  }
};
</script>

<style lang="scss" scoped>
.g-signin-button {
  /* This is where you control how the button looks. Be creative! */
  display: inline-block;
  padding: 4px 8px;
  border-radius: 3px;
  background-color: #3c82f7;
  color: #fff;
  box-shadow: 0 3px 0 #0f69ff;
}
</style>