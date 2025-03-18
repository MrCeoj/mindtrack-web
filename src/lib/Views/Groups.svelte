<script lang="ts">
  const groups = [
    {
      name: "Matemáticas Discretas",
      schedule: "Lunes y Miércoles de 8:00 a 10:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Programación Web",
      schedule: "Martes y Jueves de 10:00 a 12:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Base de Datos",
      schedule: "Lunes y Miércoles de 10:00 a 12:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Cálculo Diferencial",
      schedule: "Martes y Jueves de 8:00 a 10:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Cálculo Integral",
      schedule: "Lunes y Miércoles de 12:00 a 14:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Física",
      schedule: "Martes y Jueves de 12:00 a 14:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Química",
      schedule: "Lunes y Miércoles de 14:00 a 16:00",
      teacher: "Mtro. Juan Pérez",
    },
    {
      name: "Biología",
      schedule: "Martes y Jueves de 14:00 a 16:00",
      teacher: "Mtro. Juan Pérez",
    },
  ];

  import { Icon, DocumentChartBar } from "svelte-hero-icons";
  import Group from "./Group.svelte";

  let isGroupSelected = $state(false);
  let selectedGroup = $state({});

  function selectGroup(group: any) {
    selectedGroup = group;
    isGroupSelected = true;
  }

  function desselectGroup() {
    selectedGroup = {};
    isGroupSelected = false;
  }

</script>

{#if isGroupSelected}
  <Group {selectedGroup} {desselectGroup} />
{:else}
  <div class="flex flex-col flex-1 min-h-full">
    <h1 class="text-2xl font-bold text-center my-5 min-h-full text-dark-bg">Mis Grupos</h1>
    <div class="flex flex-col gap-5 mb-5">
      {#each groups as group}
        <div
          class="bg-[#EA1465] opacity-80 text-white mx-2 flex justify-between p-5 rounded-lg shadow-md"
        >
          <div class="flex-col flex">
            <h2 class="text-lg font-semibold">{group.name}</h2>
            <p class="text-sm text-slate-100">{group.schedule}</p>
            <p class="text-sm text-slate-100">Profesor: {group.teacher}</p>
          </div>
          <button
            class="flex-col flex justify-center items-center text-center w-auto"
            onclick={() => selectGroup(group)}
          >
            <Icon src={DocumentChartBar} class="w-10 h-10 text-white" />
            <p class="text-sm font-semibold">Revisar</p>
          </button>
        </div>
      {/each}
    </div>
  </div>
{/if}
