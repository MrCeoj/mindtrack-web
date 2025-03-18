<script lang="ts">
  import {
    Icon,
    ChevronLeft,
    DocumentMagnifyingGlass,
  } from "svelte-hero-icons";
  import Student from "./Student.svelte";
  let { selectedGroup, desselectGroup } = $props();

  let alumnos = [
    {
      name: "Juan Pérez",
      email: "juan.perez@mail.com",
      matr: 118565,
      calif_1: 10,
      calif_2: 9,
      calif_3: 8,
      disab: [
        {
          visual: false,
          auditiva: false,
          habla: false,
          motriz: false,
          asperger: false,
          autismo: false,
          tdah: false,
          dislexia: false,
        },
      ],
      allergies: ["Paracetamol", "Mariscos"],
      medications: ["Ritalin", "Clonazepam"],
      diseases: ["Asma"],
      docs: [
        {
          name: "Diagnostico Asperger",
          date: "2021-10-01",
          file: "https://some.sample.url/file/d/51684.pdf",
        },
        {
          name: "Receta Medicación",
          date: "2021-10-01",
          file: "https://some.sample.url/file/d/51684.pdf",
        },
      ],
      tutor: "María González",
      contacto: "686-123-4567",
    },
    {
      name: "María González",
      email: "maria.gonzalez@mail.com",
      matr: 118566,
      calif_1: 8,
      calif_2: 9,
      calif_3: 9,
      disab: [
        {
          visual: true,
          auditiva: false,
          habla: false,
          motriz: false,
          asperger: false,
          autismo: true,
          tdah: false,
          dislexia: false,
        },
      ],
      allergies: [],
      medications: [],
      diseases: [],
      docs: [
        {
          name: "Diagnóstico Discapacidad Visual",
          date: "2022-03-15",
          file: "https://some.sample.url/file/d/51685.pdf",
        },
        {
          name: "Recomendaciones Adaptativas",
          date: "2022-04-10",
          file: "https://some.sample.url/file/d/51686.pdf",
        },
      ],
      tutor: "María González",
      contacto: "686-123-4567",
    },
    {
      name: "Carlos Rodríguez",
      email: "carlos.rodriguez@mail.com",
      matr: 118567,
      calif_1: 7,
      calif_2: 8,
      calif_3: 9,
      disab: [
        {
          visual: false,
          auditiva: true,
          habla: false,
          motriz: false,
          asperger: false,
          autismo: false,
          tdah: false,
          dislexia: false,
        },
      ],
      allergies: ["Gatos"],
      medications: [],
      diseases: [],
      docs: [
        {
          name: "Evaluación Audiológica",
          date: "2021-11-20",
          file: "https://some.sample.url/file/d/51687.pdf",
        },
        {
          name: "Certificado Uso de Audífono",
          date: "2022-01-05",
          file: "https://some.sample.url/file/d/51688.pdf",
        },
      ],
      tutor: "María González",
      contacto: "686-123-4567",
    },
    {
      name: "Laura Martínez",
      email: "laura.martinez@mail.com",
      matr: 118568,
      calif_1: 9,
      calif_2: 9,
      calif_3: 10,
      disab: [
        {
          visual: false,
          auditiva: false,
          habla: false,
          motriz: false,
          asperger: false,
          autismo: false,
          tdah: true,
          dislexia: false,
        },
      ],
      allergies: [],
      medications: ["Oximetazolina"],
      diseases: [],
      docs: [
        {
          name: "Diagnóstico TDAH",
          date: "2022-02-18",
          file: "https://some.sample.url/file/d/51689.pdf",
        },
        {
          name: "Plan de Tratamiento",
          date: "2022-03-01",
          file: "https://some.sample.url/file/d/51690.pdf",
        },
        {
          name: "Seguimiento Psicológico",
          date: "2022-06-15",
          file: "https://some.sample.url/file/d/51691.pdf",
        },
      ],
      tutor: "María González",
      contacto: "686-123-4567",
    },
    {
      name: "Roberto Sánchez",
      email: "roberto.sanchez@mail.com",
      matr: 118569,
      calif_1: 8,
      calif_2: 7,
      calif_3: 9,
      disab: [
        {
          visual: false,
          auditiva: false,
          habla: false,
          motriz: false,
          asperger: false,
          autismo: false,
          tdah: false,
          dislexia: true,
        },
      ],
      allergies: [],
      medications: ["Salbutamol"],
      diseases: ["Asma"],
      docs: [
        {
          name: "Evaluación de Dislexia",
          date: "2022-01-12",
          file: "https://some.sample.url/file/d/51692.pdf",
        },
        {
          name: "Informe Psicopedagógico",
          date: "2022-02-28",
          file: "https://some.sample.url/file/d/51693.pdf",
        },
      ],
      tutor: "María González",
      contacto: "686-123-4567",
    },
    {
      name: "Ana López",
      email: "ana.lopez@mail.com",
      matr: 118570,
      calif_1: 10,
      calif_2: 10,
      calif_3: 9,
      disab: [
        {
          visual: false,
          auditiva: false,
          habla: false,
          motriz: false,
          asperger: false,
          autismo: false,
          tdah: false,
          dislexia: false,
        },
      ],
      allergies: [],
      medications: [],
      diseases: [],
      docs: [],
      tutor: "María González",
      contacto: "686-123-4567",
    },
  ];

  function getAvg(calif_1: number, calif_2: number, calif_3: number) {
    return ((calif_1 + calif_2 + calif_3) / 3).toFixed(1);
  }

  let selectedAlumno = $state({});
  let isAlumnoSelected = $state(false);

  function selectAlumno(alumno: any) {
    selectedAlumno = alumno;
    isAlumnoSelected = true;
  }

  function desselectAlumno() {
    selectedAlumno = {};
    isAlumnoSelected = false;
  }
</script>

{#if isAlumnoSelected}
  <Student {selectedAlumno} {desselectAlumno} {selectedGroup} {getAvg} />
{:else}
  <div class="flex-1 min-h-full">
    <header>
      <div
        class="flex items-center justify-between px-3 py-2 border-b border-gray-200"
      >
        <button class="flex items-center space-x-2">
          <Icon
            src={ChevronLeft}
            class="w-8 h-8 text-dark-bg font"
            onclick={desselectGroup}
          />
          <span class="text-md text-dark-bg font-semibold"
            >{selectedGroup.name}</span
          >
        </button>
      </div>
    </header>
    <div class="flex flex-col mb-5 mt-2 px-3">
      {#each alumnos as al}
        <div
          class="flex justify-between bg-[#f9f9f9] border-gray-400 border-b-2 px-2 py-4"
        >
          <div class="flex flex-col justify-between">
            <h2 class="text-lg font-semibold">{al.name}</h2>
            <p class="text-sm text-gray-500">Matrícula: {al.matr}</p>
            <p class="text-sm text-gray-500">
              Promedio: {getAvg(al.calif_1, al.calif_2, al.calif_3)}
            </p>
          </div>
          <button
            class="flex flex-col items-center self-center text-center mr-5"
            onclick={() => selectAlumno(al)}
          >
            <Icon
              src={DocumentMagnifyingGlass}
              class="w-12 h-12 text-dark-bg"
            />
            <p class="text-xs text-dark-bg font-semibold">
              Revisar<br />historial
            </p>
          </button>
        </div>
      {/each}
    </div>
  </div>
{/if}
