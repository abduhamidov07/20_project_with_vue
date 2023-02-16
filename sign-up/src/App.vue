<template>
  <div id="app">
    <div class="form">
      <div class="center">
        <h1>Sign Up Now!</h1>
        <form>
          <div class="inputbox">
            <input v-model="email" type="email" required />
            <span>Email</span>
          </div>
          <div class="inputbox">
            <input :type="passwordFieldType" v-model="password" required />
            <span>Password</span>
            <button type="button" @click="switchV">
              <span v-if="showElem">
                <i class="fa-regular fa-eye-slash"></i>
              </span>
              <span v-else>
                <i class="fa-regular fa-eye"></i>
              </span>
            </button>
          </div>
          <div class="info">
            <p>Email: {{ showEmail }}</p>
            <div class="infoPass">
              <p>
                Password: <span v-if="showPass">{{ showPassword }}</span>
              </p>
              <button type="button" @click="showPassBtn">
                <span v-if="showPass">
                  <i class="fa-regular fa-eye"></i>
                </span>
                <span v-else>
                  <i class="fa-regular fa-eye-slash"></i>
                </span>
              </button>
            </div>
          </div>
          <button type="submit" class="btn">submit</button>
        </form>
      </div>
    </div>
  </div>
</template>

<!-- JavaScript -->
<script>
export default {
  data() {
    return {
      showElem: true,
      showPass: true,
      email: "",
      password: "",
      passwordFieldType: "password",
    };
  },
  methods: {
    switchV() {
      (this.passwordFieldType =
        this.passwordFieldType === "password" ? "text" : "password"),
        (this.showElem = !this.showElem);
      // this.active = !this.active;
    },
    showPassBtn() {
      this.showPass = !this.showPass;
    },
  },
  computed: {
    showEmail() {
      return this.email;
    },
    showPassword() {
      return this.password;
    },
  },
};
</script>

<!-- style sheet -->
<style>
@import url("https://fonts.googleapis.com/css2?family=Cuprum:wght@700&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.form {
  display: grid;
  place-items: center;
  height: 100vh;
  background-image: url("./assets/bg-img.jpg");
  font-family: "Cuprum", sans-serif;
  background-size: cover;
}

.center {
  padding: 50px 50px;
  backdrop-filter: blur(4px);
  border: 1.5px solid rgba(255, 255, 255, 0.1);
  box-shadow: 20px 20px 120px #000;
  border-radius: 10px;
  color: #fff;
}

.center form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.center h1 {
  font-size: 2em;
  border-left: 5px solid dodgerblue;
  padding: 10px;
  color: #fff;
  letter-spacing: 5px;
  margin-bottom: 50px;
  font-weight: bold;
}

.center .inputbox {
  position: relative;
  width: 300px;
  height: 50px;
  margin-bottom: 40px;
}

.center .inputbox button {
  position: absolute;
  right: 50px;
  margin-top: 4px;
  color: #fff;
  border: none;
  background: transparent;
}

.center input {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  border: 2px solid #fff;
  color: #fff;
  outline: none;
  background: none;
  padding: 10px;
  border-radius: 10px;
  font-size: 1.2em;
}

.center .inputbox span {
  position: absolute;
  top: 14px;
  left: 20px;
  font-size: 1em;
  transition: 0.6s;
}

.center .inputbox input:focus ~ span,
.center .inputbox input:valid ~ span {
  transform: translateX(-13px) translateY(-35px);
}

.info {
  text-align: start;
  width: 100%;
  margin-bottom: 30px;
}

.infoPass {
  display: flex;
  justify-content: space-between;
}

.infoPass button {
  background: transparent;
  border: none;
  color: #fff;
}

.center .btn {
  width: 200px;
  height: 50px;
  border-radius: 10px;
  border: none;
  text-transform: uppercase;
  letter-spacing: 2px;
  cursor: pointer;
  transition: 0.2s;
}

.center .btn:hover {
  background-color: rgb(207, 207, 207);
  letter-spacing: 3px;
}
</style>
