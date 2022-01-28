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
    <h2 id="h2">Choose your character set:</h2>
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
