<script lang="ts">
  import Phone from './lib/Phone.svelte';
  
</script>

<main class="p-10">
  <header class="text-center text-weird-color">
    <h1>MindTrack</h1>
    <p>La mejor app para la gestión escolar</p>
  </header>
  
  <section class="flex flex-wrap justify-around mt-10">
    <div class="w-96 p-2.5 border-2 border-[#ccc] rounded-lg text-center">
      <h2>Historial Académico</h2>
      <p>Revisa el rendimiento académico de los alumnos de manera detallada.</p>
    </div>
    <div class="w-96 p-2.5 border-2 border-[#ccc] rounded-lg text-center">
      <h2>Historial Clínico</h2>
      <p>Accede a la información clínica de los alumnos para un mejor seguimiento.</p>
    </div>
    <div class="w-96 p-2.5 border-2 border-[#ccc] rounded-lg text-center">
      <h2>Fácil de Usar</h2>
      <p>Interfaz intuitiva y fácil de usar para docentes y administradores.</p>
    </div>
    <Phone />
  </section>

</main>