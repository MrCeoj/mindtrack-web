<script lang="ts">
  import Login from "./Login.svelte";
  import Views from "./Views/Views.svelte";

  let isLogged = false;

  function onLogin() {
    isLogged = true;
  }

  function onLogout() {
    isLogged = false;
  }
</script>

<div class="phone-container">
  <div class="phone-ui">
    <div class="phone-frame">
      {#if isLogged}
        <Views {onLogout}/>
      {:else}
        <Login {onLogin}/>
      {/if}
    </div>
  </div>
</div>

<style>
  .phone-container {
    display: flex;
    justify-content: center;
    align-items: center;
    max-height: 50%;
    width: 375px;
    height: 667px;
    z-index: 100;
  }

  .phone-ui {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .phone-frame {
    width: 375px;
    height: 667px;
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
      width: 320px;
      height: 100%;
      box-shadow: none;
      max-height: 600px;
    }
  }
</style>