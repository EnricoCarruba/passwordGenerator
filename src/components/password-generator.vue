<template>
  <header>
    <h1>PASSWORD GENERATOR</h1>
  </header>
  <div id="box">
    <h1 id="generated-password">{{ password }}</h1>
  </div>

  <section>
    <button id="copy-to-clipboard">Copy to Clipboard</button>
    <h2 id="character-set-label">Choose your character set:</h2>
    <div class="checkboxes">
      <input
        type="checkbox"
        name="lowercase"
        v-model="checkLowerCase"
        value="lowercase"
        id="lowercase"
        v-on:click="generatePassword()"
      />
      <label for="lowercase">Lowercase</label>

      <input
        type="checkbox"
        name="uppercase"
        value="uppercase"
        v-model="checkUpperCase"
        id="uppercase"
        v-on:click="generatePassword()"
      />
      <label for="uppercase">Uppercase</label>

      <input
        v-on:click="generatePassword()"
        type="checkbox"
        value="numbers"
        name="numbers"
        id="numbers"
        v-model="checkNumbers"
      />
      <label for="numbers">Numbers</label>

      <input
        v-on:click="generatePassword()"
        type="checkbox"
        name="symbols"
        value="symbols"
        id="symbols"
        v-model="checkSymbols"
      />
      <label for="symbols">Symbols</label>
    </div>
    <!-- Slider  -->

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
    password: "click below",
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
@import url("https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@100&display=swap");

html {
  font-family: "JetBrains Mono", monospace;
  text-align: center;
  background-color: #5585b5;
  color: #bbe4e9;
  margin-top: 10px;
}

header {
  font-size: 1.5rem;
  color: #bbe4e9;
  text-shadow: 0.1em 0.1em 0 hsl(180, 80%, 40%);
  font-family: "JetBrains Mono", monospace;
}

#box {
  background-color: lightgray;
  align-content: center;

  width: 100%;
  height: auto;
  display: block;
  color: red;
}

#generated-password {
  color: red;
  text-align: center;
}

#copy-to-clipboard {
  font-size: 1.4rem;
  text-align: center;
  background-color: #8c9aec;
  color: black;
  border-radius: 10px;
  width: 220px;
  height: 60px;
}

#character-set-label {
  color: white;
}

input[type="checkbox"] {
  display: none;
}

input:checked + label {
  background-color: rgb(68, 79, 241);
  font-weight: bolder;
}

label {
  font-size: 1.8rem;
  margin: 0.5rem;
  border: 4px solid #6f5fb8;
  border-radius: 10px;
  display: block;
}

#slider-label {
  color: white;
  display: block;
  border: none;
}

#slider {
  size: 50%;
  margin-top: 1rem;
}

@media screen and (min-width: 760px) {
  label {
    width: 50vw;
    display: inline;
  }

  #slider {
    display: inline;
  }

  #slider-label {
    display: block;
    margin: 0 auto;
  }
}
</style>
