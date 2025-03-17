<script>
  let loading = $state(false);
  let { onLogin } = $props();

  import Welcome from "../assets/welcome.png";

  const handleLogin = () => {
    loading = true;

    setTimeout(() => {
      loading = false;
      onLogin();
      console.log("Logged in!");
    }, 1000);
  };
</script>

<div class="p-5 bg-dark-bg min-h-full flex flex-col">
  <div class="flex flex-col justify-center flex-1">
    <div class="flex justify-center items-center mb-5">
      <img
        src={Welcome}
        alt="Welcome"
        class="w-[310px] h-[210px] mb-5 object-fill"
      />
    </div>

    <input
      class="h-[50px] bg-slate-300 rounded mb-2.5 p-1 pl-2.5 pr-5"
      placeholder="Ingrese su correo"
      type="email"
      value="javier.lopez@mail.com"
      color="#2F031A"
      disabled
    />

    <input
      class="h-[50px] bg-slate-300 rounded mb-2.5 p-1 pl-2.5 pr-5"
      placeholder="Ingresa tu matricula"
      type="number"
      value="118565"
      color="#2F031A"
      disabled
    />

    <button
      class="bg-[#EA1465] text-white py-2 px-4 rounded mt-8 {loading
        ? 'opacity-50'
        : ''}"
      onclick={handleLogin}
      disabled={loading}
    >
      {loading ? "Cargando..." : "Iniciar Sesión"}
    </button>
  </div>
</div>
