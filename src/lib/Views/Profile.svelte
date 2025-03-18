<script lang="ts">
  import { Icon, ArrowLeftStartOnRectangle } from "svelte-hero-icons";
  const profile = {
    name: "Juan Perez",
    email: "juan.perez@mail.com",
    matr: "118565",
    phone: "1234567890",
  };

  import Welcome from "../../assets/icon.png";

  let { onLogout } = $props();
</script>

<div class="min-h-full h-full flex flex-col flex-1 px-2">
  <div class="flex flex-col justify-center flex-1">
    <h1 class="text-2xl font-bold text-center mb-2 text-dark-bg">Perfil</h1>
    <div class="flex justify-center items-center">
      <img
        src={Welcome}
        alt={profile.name}
        class="w-[120px] mb-5 object-fill"
      />
    </div>

    <label for="nombre">Nombre</label>
    <input
      id="#nombre"
      class="h-[50px] bg-slate-300 rounded mb-2.5 p-1 pl-2.5 pr-5"
      placeholder="Nombre"
      type="text"
      value={profile.name}
      color="#2F031A"
      disabled
    />

    <label for="email">Correo</label>
    <input
      id="#email"
      class="h-[50px] bg-slate-300 rounded mb-2.5 p-1 pl-2.5 pr-5"
      placeholder="Correo"
      type="email"
      value={profile.email}
      color="#2F031A"
      disabled
    />

    <label for="matr">Matrícula</label>
    <input
      id="#matr"
      class="h-[50px] bg-slate-300 rounded mb-2.5 p-1 pl-2.5 pr-5"
      placeholder="Matricula"
      type="number"
      value={profile.matr}
      color="#2F031A"
      disabled
    />

    <label for="phone">Teléfono</label>
    <input
      id="#phone"
      class="h-[50px] bg-slate-300 rounded mb-2.5 p-1 pl-2.5 pr-5"
      placeholder="Telefono"
      type="tel"
      value={profile.phone}
      color="#2F031A"
      disabled
    />
  </div>
  <button class="absolute top-3 right-3 p-2" onclick={onLogout}>
    <Icon src={ArrowLeftStartOnRectangle} class="w-8 h-10 text-dark-bg" />
  </button>
</div>
