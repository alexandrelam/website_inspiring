<template>
  <div class="container">
    <div class="left">
      <Navbar type="1" class="navbar" />
      <div class="formBox">
        <div class="form">
          <p class="title">Se connecter</p>
          <div class="formEmail">
            <label for="email" class="emailLab">Email</label>
            <input
              type="email"
              id="email"
              name="email"
              placeholder="nom.prenom@gmail.com"
            />
          </div>
          <div class="formMdp">
            <label for="mdp" class="mdpLab">Mot de passe</label>
            <input
              type="password"
              id="mdp"
              name="mdp"
              placeholder="au moins 8 caractères"
            />
          </div>
          <div class="formConnect">
            <input type="checkbox" id="stayconnect" name="stayconnect" />
            <label for="stayconnect" class="connectLab">Rester connecté</label>
          </div>

          <button @click="checkLogin">Se connecter</button>
          <div v-show="error" class="error">
            <p>identifiant ou mdp erroné</p>
          </div>
        </div>
      </div>
    </div>
    <div class="right"></div>
  </div>
</template>

<script>
import Navbar from "./Navbar";
export default {
  components: {
    Navbar,
  },
  data() {
    return {
      error: false,
    };
  },
  methods: {
    checkLogin() {
      /////////////////fonction a changer apres//////////
      var login = document.getElementById("email").value;
      var mdp = document.getElementById("mdp").value;
      if (login != "admin" && mdp != "admin") {
        this.error = true;
        console.log("bad log");
      } else {
        console.log("good log");
        this.error = false;
        this.$router.push({ name: "yearselect" });
      }
    },
  },
};
</script>

<style scoped>
@media all and (max-width: 1098px) {
  .right {
    display: none;
  }
  .left {
    width: 100% !important;
  }
  .form {
    margin: 0 !important;
  }
  .formBox {
    justify-content: flex-start !important;
  }
}
@media all and (max-width: 595px) {
  .title {
    font-size: 50px !important;
  }
  .form {
    width: 100% !important;
    display: flex;
    flex-direction: column;
    height: 100%;
    align-items: center;
    justify-content: space-around !important;
  }
  .formEmail,
  .formMdp {
    font-size: 15px !important;
    display: flex !important;
    flex-direction: column !important;
    align-items: center !important;
    width: 100% !important;
  }
  .formEmail input,
  .formMdp input {
    width: 80% !important;
  }
  button {
    width: 80% !important;
  }
  .form .title,
  .formEmail,
  .formMdp,
  .formConnect {
    margin: 0 !important;
  }
}
.error {
  margin-top: 10px;
  color: red;
  width: 100%;
  text-align: center;
  animation-name: errorAppear;
  animation-duration: 1s;
  font-size: 1.5em;
}
@keyframes errorAppear {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.error p {
  font-family: roboto !important;
}
#stayconnect {
  appearance: none;
  background-color: #fafafa;
  border: 1px solid #cacece;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05),
    inset 0px -15px 10px -12px rgba(0, 0, 0, 0.05);
  padding: 9px;
  border-radius: 3px;
  display: inline-block;
  position: relative;
  outline: none;
}
#stayconnect:active,
#stayconnect:checked:active {
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05),
    inset 0px 1px 3px rgba(0, 0, 0, 0.1);
}

#stayconnect:checked {
  background-color: #e9ecee;
  border: 1px solid #adb8c0;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05),
    inset 0px -15px 10px -12px rgba(0, 0, 0, 0.05),
    inset 15px 10px -12px rgba(255, 255, 255, 0.1);
  color: #99a1a7;
}
#stayconnect:checked:after {
  content: "\2714";
  font-size: 14px;
  position: absolute;
  top: 0px;
  left: 3px;
  color: #99a1a7;
}
.form .title,
.formEmail,
.formMdp,
.formConnect {
  margin: 50px 0;
}
.form {
  margin-bottom: 80px;
}
.formConnect {
  margin-left: 55px;
}
.connectLab {
  font-size: 1.8em;
  margin-left: 20px;
}
.formEmail input,
.formMdp input {
  display: block;
  margin-left: 20px;
  padding-left: 10px;
  border-radius: 13px;
  border: 1px solid var(--main);
  height: 40px;
  width: 500px;
  font-family: roboto;
  font-size: 1.4em;
  color: var(--main);
  outline: none;
}

.formEmail input {
  font-family: Roboto;
}
.emailLab {
  color: var(--purple);
  font-size: 2.5em;
}
.mdpLab {
  color: var(--orange);
  font-size: 2.5em;
}
.connectLab {
  color: var(--main);
}
.formBox {
  display: flex;
  flex-direction: column;
  justify-content: baseline;
  align-items: center;
  width: 100%;
  flex: 1;
}
.form .title {
  color: var(--blue);
  font-size: 4.2em;
}
.container {
  display: flex;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
.right {
  height: 100%;
  width: 45%;
  background: url("../assets/masquotte.jpg") center/200% no-repeat;
  background-size: cover;
}
.left {
  height: 100%;
  width: 55%;
  display: flex;
  flex-direction: column;
}
button {
  background: linear-gradient(
    180deg,
    #06446b 0%,
    rgba(67, 101, 123, 0.69) 100%
  );
  width: 500px;
  height: 40px;
  border: none;
  border-radius: 13px;
  font-size: 1.7em;
  color: white;
  cursor: pointer;
  margin-top: 20px;
}
</style>
