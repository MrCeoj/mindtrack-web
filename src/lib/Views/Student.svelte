<script>
  import { Icon, ChevronLeft } from "svelte-hero-icons";
  import "@fortawesome/fontawesome-free/css/all.min.css";
  import Chart from "../components/Chart.svelte";
  let { selectedAlumno, desselectAlumno, selectedGroup, getAvg } = $props();

  let hasDisabs = $state(false);
  let hasAllergies = $state(false);
  let hasDiseases = $state(false);
  let hasMedications = $state(false);

  /**
   * {
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
          asperger: true,
          autismo: true,
          tdah: false,
          dislexia: false,
          allergies: ['Paracetamol', 'Mariscos'],
          medications: ['Ritalin', 'Clonazepam'],
          diseases: ['Asma'],
        },
      ],
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
  */

  if (selectedAlumno.disab && selectedAlumno.disab.length > 0) {
    if (
      selectedAlumno.disab[0].visual ||
      selectedAlumno.disab[0].auditiva ||
      selectedAlumno.disab[0].habla ||
      selectedAlumno.disab[0].motriz ||
      selectedAlumno.disab[0].asperger ||
      selectedAlumno.disab[0].autismo ||
      selectedAlumno.disab[0].tdah ||
      selectedAlumno.disab[0].dislexia
    ) {
      hasDisabs = true;
    }

    if (selectedAlumno.allergies && selectedAlumno.allergies.length > 0) {
      hasAllergies = true;
    }
    if (selectedAlumno.diseases && selectedAlumno.diseases.length > 0) {
      hasDiseases = true;
    }
    if (selectedAlumno.medications && selectedAlumno.medications.length > 0) {
      hasMedications = true;
    }
  }

  let asistance = [
    { x: "Asistencias", y: 80 },
    { x: "Faltas", y: 65 },
    { x: "Justificados", y: 10 },
  ];
</script>

<div class="bg-white min-h-full flex flex-col flex-1">
  <header class="">
    <div
      class="flex items-center justify-between px-3 py-2 border-b border-gray-200"
    >
      <button class="flex items-center space-x-2">
        <Icon
          src={ChevronLeft}
          class="w-8 h-8 text-dark-bg font"
          onclick={desselectAlumno}
        />
        <span class="text-sm text-dark-bg font-semibold"
          >{selectedAlumno.name} | {selectedGroup.name}</span
        >
      </button>
    </div>
  </header>

  <div class="flex flex-col m-2">
    <h3 class="text-lg font-semibold mb-2">Datos</h3>
    <div class="flex flex-col gap-1">
      <span class="flex items-center gap-2"
        ><i class="fa-solid fa-id-card text-dark-bg"></i>
        <p>{selectedAlumno.matr}</p></span
      >
      <span class="flex items-center gap-2"
        ><i class="fa-solid fa-envelope text-dark-bg"></i>
        <p>{selectedAlumno.email}</p></span
      >
      <span class="flex items-center gap-2"
        ><i class="fa-solid fa-user text-dark-bg"></i>
        <p>{selectedAlumno.tutor}</p></span
      >
      <span class="flex items-center gap-2"
        ><i class="fa-solid fa-phone text-dark-bg"></i>
        <p>{selectedAlumno.contacto}</p></span
      >
    </div>
  </div>

  <div class="flex flex-col gap-5 m-2">
    <div class="flex flex-col gap-2">
      <h3 class="text-lg font-semibold">Calificaciones</h3>
      <table
        class="table-auto w-full text-center border-collapse border border-gray-300"
      >
        <thead>
          <tr>
            <th>Parcial 1</th>
            <th>Parcial 2</th>
            <th>Parcial 3</th>
            <th>Promedio</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>{selectedAlumno.calif_1}</td>
            <td>{selectedAlumno.calif_2}</td>
            <td>{selectedAlumno.calif_3}</td>
            <td
              >{getAvg(
                selectedAlumno.calif_1,
                selectedAlumno.calif_2,
                selectedAlumno.calif_3
              )}</td
            >
          </tr>
        </tbody>
      </table>
    </div>

    <div class="mt-2">
      <h3 class="text-lg font-semibold mb-2">Relación de asistencias</h3>
      <div class="flex justify-center">
        <Chart data={asistance} />
      </div>
    </div>

    {#if hasDisabs || hasAllergies || hasDiseases || hasMedications}
      <div class="flex flex-col">
        <h3 class="text-lg font-semibold mb-2">Condiciones</h3>
        <div class="flex flex-wrap gap-2">
          {#if selectedAlumno.disab[0].visual}
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-eye text-dark-bg"></i>
              <p>Discapacidad visual</p>
            </div>
          {/if}

          {#if selectedAlumno.disab[0].auditiva}
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-ear-deaf text-dark-bg"></i>
              <p>Discapacidad auditiva</p>
            </div>
          {/if}

          {#if selectedAlumno.disab[0].habla}
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-bullhorn text-dark-bg"></i>
              <p>Discapacidad del habla</p>
            </div>
          {/if}

          {#if selectedAlumno.disab[0].motriz}
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-wheelchair-move text-dark-bg"></i>
              <p>Discapacidad motriz</p>
            </div>
          {/if}

          {#if selectedAlumno.disab[0].asperger || selectedAlumno.disab[0].autismo || selectedAlumno.disab[0].tdah || selectedAlumno.disab[0].dislexia}
            <div class="flex flex-col gap-1 w-full">
              <div class="flex items-center gap-2">
                <i class="fa-solid fa-brain text-dark-bg"></i>
                <p>Trastornos del aprendizaje:</p>
              </div>
              <div class="flex flex-wrap gap-2 ml-6">
                {#if selectedAlumno.disab[0].asperger}
                  <span class="bg-purple-100 text-purple-800 px-2 py-1 rounded"
                    >Asperger</span
                  >
                {/if}
                {#if selectedAlumno.disab[0].autismo}
                  <span class="bg-purple-100 text-purple-800 px-2 py-1 rounded"
                    >Autismo</span
                  >
                {/if}
                {#if selectedAlumno.disab[0].tdah}
                  <span class="bg-purple-100 text-purple-800 px-2 py-1 rounded"
                    >TDAH</span
                  >
                {/if}
                {#if selectedAlumno.disab[0].dislexia}
                  <span class="bg-purple-100 text-purple-800 px-2 py-1 rounded"
                    >Dislexia</span
                  >
                {/if}
              </div>
            </div>
          {/if}
        </div>

        {#if hasDiseases}
          <div>
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-stethoscope text-dark-bg"></i>
              <p>Enfermedades:</p>
            </div>
            <div class="flex flex-wrap gap-2 ml-6">
              {#each selectedAlumno.diseases as disease}
                <span class="bg-yellow-100 text-yellow-800 px-2 py-1 rounded"
                  >{disease}</span
                >
              {/each}
            </div>
          </div>
        {/if}
        {#if hasMedications}
          <div>
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-tablets text-dark-bg"></i>
              <p>Medicamentos:</p>
            </div>
            <div class="flex flex-wrap gap-2 ml-6">
              {#each selectedAlumno.medications as medication}
                <span class="bg-green-100 text-green-800 px-2 py-1 rounded"
                  >{medication}</span
                >
              {/each}
            </div>
          </div>
        {/if}
        {#if hasAllergies}
          <div>
            <div class="flex items-center gap-2">
              <i class="fa-solid fa-box-tissue text-dark-bg"></i>
              <p>Alergias:</p>
            </div>
            <div class="flex flex-wrap gap-2 ml-6">
              {#each selectedAlumno.allergies as allergy}
                <span class="bg-red-100 text-red-800 px-2 py-1 rounded"
                  >{allergy}</span
                >
              {/each}
            </div>
          </div>
        {/if}
      </div>
    {/if}

    {#if selectedAlumno.docs && selectedAlumno.docs.length > 0}
      <div class="flex flex-col my-2">
        <h3 class="text-lg font-semibold">Evidencia Médica</h3>
        {#each selectedAlumno.docs as doc}
          <div class="bg-[#f0f0f0] border-gray-300 border-b-2 p-2">
            <p class="text-md font-semibold text-gray-800">{doc.name}</p>
            <p class="text-sm font-light text-gray-800">{doc.date}</p>
            <p class="text-sm font-normal text-blue-700 underline">
              {doc.file}
            </p>
          </div>
        {/each}
      </div>
    {/if}
  </div>
</div>
