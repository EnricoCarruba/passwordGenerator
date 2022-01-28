<template>
  <section>
    <header>
      <h1>PASSWORD</h1>
      <h1>GENERATOR</h1>
    </header>
    <div id="box">
      <h1 id="generated-password">{{ password }}</h1>
    </div>
    <button id="copy-to-clipboard">Copy to Clipboard</button>
    <h2 id="character-set-label">Choose your character set:</h2>
    <input
      type="checkbox"
      name="lowercase"
      v-model="checkLowerCase"
      value="lowercase"
      class="button-character-set"
      v-on:click="generatePassword()"
    />
    <label for="lowercase">Lowercase</label>

    <input
      type="checkbox"
      name="uppercase"
      value="uppercase"
      v-model="checkUpperCase"
      class="button-character-set"
      v-on:click="generatePassword()"
    />
    <label for="uppercase">Uppercase</label>

    <input
      v-on:click="generatePassword()"
      type="checkbox"
      value="numbers"
      name="numbers"
      v-model="checkNumbers"
      class="button-character-set"
    />
    <label for="numbers">Numbers</label>

    <input
      v-on:click="generatePassword()"
      type="checkbox"
      name="symbols"
      value="symbols"
      v-model="checkSymbols"
      class="button-character-set"
    />
    <label for="symbols">Symbols</label>
    <input
      v-on:click="generatePassword()"
      type="range"
      min="8"
      max="35"
      value="8"
      id="slider"
      name="slider"
      v-on:change="changePasswordLength()"
    />
    <label id="slider-label" for="slider"
      >Password length: {{ passwordLength }}</label
    >
  </section>
</template>
<script>
export default {
  data: () => ({
    password: "ABC",
    passwordLength: "8",
    checkLowerCase: false,
    checkUpperCase: false,
    checkNumbers: false,
    checkSymbols: false,
  }),
  methods: {
    generatePassword() {
      let characters = "";
      let password = "";
      if (this.checkLowerCase) {
        characters += "abcdefghijklmnopqrstuvwxyz";
      }
      if (this.checkUpperCase) {
        characters += "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      }
      if (this.checkNumbers) {
        characters += "0123456789";
      }
      if (this.checkSymbols) {
        characters += "!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~";
      }

      for (let i = 0; i < this.passwordLength; i++) {
        password += characters.charAt(
          Math.floor(Math.random() * characters.length)
        );
      }
      this.password = password;
      console.log(this.password);
      console.log(this.checkLowerCase);
    },

    changePasswordLength() {
      let slider = document.getElementById("slider");
      this.passwordLength = slider.value;
    },
  },
  watch: {
    checkLowerCase(newVal) {
      if (newVal == true) {
        this.generatePassword();
      } else {
        this.generatePassword();
      }
    },
    checkUpperCase(newVal) {
      if (newVal == true) {
        this.generatePassword();
      } else {
        this.generatePassword();
      }
    },
    checkNumbers(newVal) {
      if (newVal == true) {
        this.generatePassword();
      } else {
        this.generatePassword();
      }
    },
    checkSymbols(newVal) {
      if (newVal == true) {
        this.generatePassword();
      } else {
        this.generatePassword();
      }
    },
    passwordLength(newVal, oldVal) {
      if (newVal != oldVal) {
        this.generatePassword();
      }
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Arvo");

html {
  font-family: Arvo;
  text-align: center;
  background-color: black;

  color: #2292a4;
  margin-top: 60px;
}

header {
  font-size: 2rem;
}

#box {
  background-color: lightgray;
  align-content: center;

  height: 3rem;
  width: 30rem;
  display: block;
  color: red;
}
#generated-password {
  color: red;
  text-align: center;
}
#copy-to-clipboard {
  font-family: Arvo;
  font-size: 1.5rem;
  text-align: center;
  background-color: #2292a4;
  color: black;
}
#character-set-label {
  color: white;
}
.button-character-set {
  font-family: Arvo;
  font-size: 1.5rem;
  background-color: black;
  color: #2292a4;
  border: 10px solid lightgray;
}
input[type="checkbox"] {
  all: unset;
}
input[type="checkbox"]:checked + label {
  background-color: #2292a4;
}
input[type="checkbox"]:focus + label {
  border: 5px;
}

#slider-label {
  color: white;
  display: block;
}

#slider {
  size: 50%;
}
</style>
