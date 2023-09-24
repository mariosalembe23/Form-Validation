<script>
export default {
  data() {
    return {
      inputIsOnFocusMode: false,
      styleIcon: "w-6 h-6 stroke-gray-800",
    };
  },
};
</script>

<template>
  <main class="w-full h-screen flex items-center justify-center">
    <section class="w-full max-w-3xl grid grid-cols-5 gap-2">
      <!-- form -->
      <div class="p-5 col-span-3">
        <form @submit="(e) => e.preventDefault()">
          <header class="pb-5 text-center space-y-2">
            <h1 class="font-bold text-purple-700 text-2xl">Inscreva-se</h1>
            <p class="text-[13px] text-gray-700">
              Asseguramos-nos da segurança dos Dados
            </p>
          </header>
          <div class="w-full grid grid-cols-1 gap-3">
            <div
              class="inputGroup w-full focus-within:border-gray-400 transition-all ease-in-out flex items-center space-x-1 bg-gray-100 border rounded-md px-2"
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
                class="bg-transparent w-full font-medium outline-none px-1 py-2.5"
                type="text"
                name="name"
                id="name"
                placeholder="Insira seu nome"
              />
            </div>

            <div
              class="inputGroup focus-within:border-gray-400 transition-all ease-in-out w-full flex items-center space-x-1 bg-gray-100 border rounded-md px-2"
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
                class="bg-transparent w-full font-medium outline-none px-1 py-2.5"
                type="email"
                name="email"
                id="email"
                placeholder="Digite seu E-mail"
              />
            </div>
            <div
              class="inputGroup focus-within:border-gray-400 transition-all ease-in-out w-full flex items-center space-x-1 bg-gray-100 border rounded-md px-2"
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
                class="bg-transparent w-full font-medium outline-none px-1 py-2.5"
                type="password"
                name="senha"
                id="senha"
                placeholder="Senha"
              />
            </div>
            <div class="w-full">
              <button
                type="submit"
                class="flex items-center justify-center text-center transition-all ease-in-out hover:bg-purple-800 bg-purple-700 w-full py-2.5 text-white font-semibold rounded-md"
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
      <div class="col-span-2">oi</div>
    </section>
  </main>
</template>

<style scoped>
h1 {
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
