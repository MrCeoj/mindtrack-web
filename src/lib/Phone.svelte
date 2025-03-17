<script lang="ts">
  import Login from "./Login.svelte"; // Asegúrate de tener este componente creado

  let isLogged = $state(false);

  let currentView = $state("groups");

  $effect(() => {
    console.log("parent", isLogged);
  });

  function onLogin() {
    isLogged = true;
  }

  
</script>

<div class="phone-ui">
  <div class="phone-frame">
    {#if isLogged}
      <h1>¡Bienvenido!</h1>
    {:else}
      <Login {onLogin}/>
    {/if}
  </div>
</div>

<style>
  .phone-ui {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .phone-frame {
    width: 375px; /* Ancho típico de un teléfono */
    height: 667px; /* Alto típico de un teléfono */
    border: 16px solid black;
    border-radius: 36px;
    background-color: white;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    overflow: auto;
    scrollbar-width: none;
  }

  .phone-frame::-webkit-scrollbar {
    display: none;
  }

  @media (max-width: 768px) {
    .phone-frame {
      width: 100%;
      height: 100%;
      border: none;
      border-radius: 0;
      padding: 0;
      box-shadow: none;
    }
  }
</style>
