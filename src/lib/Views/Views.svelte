<script>
  let currentView = $state("groups");
  import Groups from "./Groups.svelte";
  import Profile from "./Profile.svelte";
  import { Icon, UserGroup, UserCircle } from "svelte-hero-icons";

  function changeView(view) {
    currentView = view;
  }
</script>

<div class="flex flex-col relative min-h-full">
  {#if currentView === "groups"}
    <Groups />
  {:else if currentView === "profile"}
    <Profile /> 
  {/if}
  <div
    class="sticky bottom-0 left-0 z-50 w-full h-16 bg-white border-t border-gray-200"
  >
    <div class="flex justify-evenly h-full max-w-lg mx-auto font-medium">
      <button
        type="button"
        class="inline-flex flex-col items-center justify-center px-5 group"
        on:click={() => changeView("groups")}
      >
        <Icon
          src={UserGroup}
          class={`w-6 h-6 text-gray-500 group-hover:text-dark-bg ${currentView === "groups" ? "text-red-900" : ""}`}
          solid
        />
        <span
          class={`text-sm text-gray-500 group-hover:text-dark-bg ${currentView === "groups" ? "text-red-900" : ""}`}
        >
          Grupos
        </span>
      </button>

      <button
        type="button"
        class="inline-flex flex-col items-center justify-center px-5 group"
        on:click={() => changeView("profile")}
      >
        <Icon
          src={UserCircle}
          class={`w-6 h-6 text-gray-500 group-hover:text-dark-bg ${currentView === "profile" ? "text-red-900" : ""}`}
          solid
        />
        <span
          class={`text-sm text-gray-500 group-hover:text-dark-bg ${currentView === "profile" ? "text-red-900" : ""}`}
        >
          Perfil
        </span>
      </button>
    </div>
  </div>
</div>
