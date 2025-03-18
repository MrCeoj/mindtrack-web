<script lang="ts">
  import Phone from "./lib/Phone.svelte";
  import blob from "./assets/blob.svg";
  import outline from "./assets/outline.svg";
</script>

<main
  class="flex flex-col items-center justify-around h-auto md:flex-row md:bg-linear-to-l bg-linear-to-tl from-red-400 to-dark-bg"
>
  <div class="w-full md:w-[70%]">
    <header class="mt-5 md:mt-0 text-center text-white">
      <h1
        class="text-3xl font-black md:text-6xl [text-shadow:_0_8px_8px_rgb(0_0_0_/_0.8)]"
      >
        MindTrack
      </h1>
      <p
        class="text-xl font-semibold md:text-2xl [text-shadow:_0_4px_4px_rgb(0_0_0_/_0.8)]"
      >
        Aplicación de seguimiento escolar
      </p>
    </header>
    <section class="text-white py-5 relative overflow-hidden">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-8 text-center [text-shadow:_0_4px_4px_rgb(0_0_0_/_0.6)]">Funciones de la Aplicación</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div class="feature-card p-6 border border-gray-700">
            <div class="feature-icon w-12 h-12 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"></path>
                <polyline points="10 17 15 12 10 7"></polyline>
                <line x1="15" y1="12" x2="3" y2="12"></line>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-2">Inicio de Sesión</h3>
            <p class="opacity-80">Permite a los usuarios iniciar sesión en la aplicación de forma segura y sencilla.</p>
          </div>
    
          <div class="feature-card p-6 border border-gray-700">
            <div class="feature-icon w-12 h-12 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                <circle cx="9" cy="7" r="4"></circle>
                <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
                <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-2">Visualización de Grupos</h3>
            <p class="opacity-80">Muestra una lista de grupos a los que pertenece el usuario con acceso rápido.</p>
          </div>
    
          <div class="feature-card p-6 border border-gray-700">
            <div class="feature-icon w-12 h-12 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
                <polyline points="14 2 14 8 20 8"></polyline>
                <line x1="16" y1="13" x2="8" y2="13"></line>
                <line x1="16" y1="17" x2="8" y2="17"></line>
                <polyline points="10 9 9 9 8 9"></polyline>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-2">Detalle de Grupo</h3>
            <p class="opacity-80">Permite ver los detalles de un grupo seleccionado, incluyendo los alumnos y sus calificaciones.</p>
          </div>
    
          <div class="feature-card p-6 border border-gray-700">
            <div class="feature-icon w-12 h-12 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                <circle cx="12" cy="7" r="4"></circle>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-2">Detalle de Alumno</h3>
            <p class="opacity-80">Muestra información detallada de un alumno, incluyendo datos personales, calificaciones, asistencia y más.</p>
          </div>
    
          <div class="feature-card p-6 border border-gray-700">
            <div class="feature-icon w-12 h-12 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                <circle cx="12" cy="7" r="4"></circle>
                <line x1="12" y1="15" x2="12" y2="15"></line>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-2">Perfil de Usuario</h3>
            <p class="opacity-80">Permite al usuario ver y gestionar su perfil con información personal.</p>
          </div>
    
          <!-- Navigation Card -->
          <div class="feature-card p-6 border border-gray-700">
            <div class="feature-icon w-12 h-12 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polygon points="3 11 22 2 13 21 11 13 3 11"></polygon>
              </svg>
            </div>
            <h3 class="text-xl font-bold mb-2">Navegación entre Vistas</h3>
            <p class="opacity-80">Permite cambiar entre la vista de grupos y la vista de perfil de manera intuitiva.</p>
          </div>
        </div>
      </div>
    </section>
  </div>

  <div class="w-auto flex items-center h-[90vh] md:h-[100vh]">
    <Phone />
  </div>
</main>

<style>
  .feature-card {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    backdrop-filter: blur(5px);
    transition:
      transform 0.3s ease,
      box-shadow 0.3s ease;
  }

  .feature-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  }

  .feature-icon {
    background: linear-gradient(135deg, #f87171, #7f1d1d);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  }
</style>
