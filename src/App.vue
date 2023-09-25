<script>
export default {
  data() {
    return {
      nameUserValue: "",
      emailUser: "",
      userPass: "",
      buttonDisabled: false,
      containsNumbers: false,
      containsUpper: true,
      specialChars: false,
      emailValid: false,
      passwordIsVisible: false,
      passCorrect: false,
    };
  },
  methods: {
    verifyRequisitsName() {
      const regexToVerifyNumbers = /\d/.test(this.nameUserValue);
      const regexToVerifyStringUpper = /[A-Z]/.test(this.nameUserValue);
      const regexToVerifyIfExistsSpecialChars = /^[a-zA-Z0-9]+$/.test(
        this.nameUserValue
      );

      if (regexToVerifyNumbers) {
        this.containsNumbers = true;
      } else {
        this.containsNumbers = false;
      }

      if (!regexToVerifyStringUpper && this.nameUserValue !== "") {
        this.containsUpper = false;
      } else {
        this.containsUpper = true;
      }

      if (regexToVerifyIfExistsSpecialChars && this.nameUserValue !== "") {
        this.specialChars = true;
      } else {
        this.specialChars = false;
      }
    },

    verifyEmailUser() {
      const regexToVerifyEmail =
        /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(this.emailUser);

      if (regexToVerifyEmail && this.emailUser !== "") {
        this.emailValid = true;
      } else {
        this.emailValid = false;
      }
    },

    showPass() {
      const senha = document.getElementById("senha");

      if (senha.type == "password") {
        senha.type = "text";
        this.passwordIsVisible = true;
      } else {
        senha.type = "password";
        this.passwordIsVisible = false;
      }
    },
    verifyLengthPass() {
      const verifyLengthPass = this.userPass.length <= 8;

      if (!verifyLengthPass && this.userPass !== "") {
        this.passCorrect = true;
      } else {
        this.passCorrect = false;
      }
    },
  },
};
</script>

<template>
  <main
    class="w-full h-screen flex items-center justify-center subpixel-antialiased"
  >
    <section
      class="w-full max-w-3xl grid grid-cols-1 md:grid-cols-5 gap-4 divide-x divide-zinc-300"
    >
      <!-- form -->
      <div class="p-5 col-span-3">
        <form @submit="(e) => e.preventDefault()">
          <header class="pb-5 text-center space-y-2">
            <h1 class="font-bold text-purple-500 text-2xl">Inscreva-se</h1>
            <p class="text-[13px] text-gray-700">
              Asseguramos-nos da segurança dos Dados
            </p>
          </header>
          <div class="w-full grid grid-cols-1 gap-3">
            <div
              class="inputGroup w-full focus-within:border-gray-400 transition-all ease-in-out flex items-center space-x-1 bg-white border rounded-md px-2"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6 stroke-gray-800"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M17.982 18.725A7.488 7.488 0 0012 15.75a7.488 7.488 0 00-5.982 2.975m11.963 0a9 9 0 10-11.963 0m11.963 0A8.966 8.966 0 0112 21a8.966 8.966 0 01-5.982-2.275M15 9.75a3 3 0 11-6 0 3 3 0 016 0z"
                />
              </svg>
              <input
                @input="verifyRequisitsName"
                class="bg-transparent w-full font-medium outline-none px-1 py-2.5"
                type="text"
                name="name"
                id="name"
                v-model="nameUserValue"
                placeholder="Crie seu nome de Utilizador"
              />
            </div>

            <div
              class="inputGroup focus-within:border-gray-400 transition-all ease-in-out w-full flex items-center space-x-1 bg-white border rounded-md px-2"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6 stroke-gray-800"
              >
                <path
                  stroke-linecap="round"
                  d="M16.5 12a4.5 4.5 0 11-9 0 4.5 4.5 0 019 0zm0 0c0 1.657 1.007 3 2.25 3S21 13.657 21 12a9 9 0 10-2.636 6.364M16.5 12V8.25"
                />
              </svg>

              <input
                @input="verifyEmailUser"
                class="bg-transparent w-full font-medium outline-none px-1 py-2.5"
                type="email"
                name="email"
                id="email"
                v-model="emailUser"
                placeholder="Digite seu E-mail"
              />
            </div>
            <div
              class="inputGroup focus-within:border-gray-400 transition-all ease-in-out w-full flex items-center space-x-1 bg-white border rounded-md px-2"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6 stroke-gray-800"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751h-.152c-3.196 0-6.1-1.248-8.25-3.285z"
                />
              </svg>

              <input
                @input="verifyLengthPass"
                class="bg-transparent w-full font-medium outline-none px-1 py-2.5"
                type="password"
                name="senha"
                id="senha"
                v-model="userPass"
                placeholder="Senha"
              />
              <button @click="showPass">
                <svg
                  v-show="passwordIsVisible == false"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="w-5 h-5 stroke-purple-800"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M2.036 12.322a1.012 1.012 0 010-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178z"
                  />
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"
                  />
                </svg>

                <svg
                  v-show="passwordIsVisible == true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="w-5 h-5 stroke-purple-800"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M3.98 8.223A10.477 10.477 0 001.934 12C3.226 16.338 7.244 19.5 12 19.5c.993 0 1.953-.138 2.863-.395M6.228 6.228A10.45 10.45 0 0112 4.5c4.756 0 8.773 3.162 10.065 7.498a10.523 10.523 0 01-4.293 5.774M6.228 6.228L3 3m3.228 3.228l3.65 3.65m7.894 7.894L21 21m-3.228-3.228l-3.65-3.65m0 0a3 3 0 10-4.243-4.243m4.242 4.242L9.88 9.88"
                  />
                </svg>
              </button>
            </div>
            <div class="w-full">
              <button
                type="submit"
                class="flex items-center shadow-lg disabled:opacity-50 justify-center text-center transition-all ease-in-out hover:bg-purple-800 bg-purple-700 w-full py-2.5 text-white font-semibold rounded-md"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="w-6 h-6"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M6 12L3.269 3.126A59.768 59.768 0 0121.485 12 59.77 59.77 0 013.27 20.876L5.999 12zm0 0h7.5"
                  />
                </svg>
              </button>
            </div>
          </div>
        </form>
      </div>
      <aside class="col-span-2 py-5 px-8">
        <header class="">
          <h4 class="text-purple-500 font-medium pb-2">Guia de Inscrição</h4>
          <small class="text-gray-700">Preencha os Campos para Ver!</small>
        </header>

        <div class="mt-4">
          <ul class="space-y-2 select-none">
            <li
              class="text-[13px] font-medium"
              :class="{
                'line-through text-zinc-800 opacity-40': containsNumbers,
                ' text-purple-700': containsNumbers == false,
              }"
            >
              - Insira números no seu Nome
            </li>
            <li
              class="text-[13px] font-medium"
              :class="{
                'line-through text-zinc-800 opacity-40': containsUpper == false,
                'text-purple-700': containsUpper,
              }"
            >
              - Sem Letras Maísculas
            </li>
            <li
              class="text-[13px] font-medium"
              :class="{
                'line-through text-zinc-800 opacity-40': specialChars,
                ' text-purple-700': specialChars == false,
              }"
            >
              - Sem Caracteres Especiais
            </li>
            <li
              class="text-[13px] font-medium"
              :class="{
                'line-through text-zinc-800 opacity-40': emailValid,
                ' text-purple-700': emailValid == false,
              }"
            >
              - E-mail Válido
            </li>
            <li
              class="text-[13px] font-medium"
              :class="{
                'line-through text-zinc-800 opacity-40': passCorrect,
                ' text-purple-700': passCorrect == false,
              }"
            >
              - 8 ou mais Dígitos para Senha
            </li>
          </ul>
        </div>
      </aside>
    </section>
  </main>
</template>

<style scoped>
h1,
h4 {
  font-family: "Poppins", sans-serif;
}
input {
  font-size: 15px;
}

input::placeholder {
  color: #1f2937bd;
  font-size: 15px;
}
</style>
