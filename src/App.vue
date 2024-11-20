<script>
import { onMounted, ref } from "vue";
import TheWindow from "./components/TheWindow.vue";

class Carousel {
  constructor(container, images) {
    this.container = container;
    this.images = images;
    this.currentIndex = 0;

    this.render();
    this.addEventListeners();
  }

  render() {
    this.container.innerHTML = `
      <div class="carousel-wrapper relative overflow-hidden">
        <div class="carousel-images flex transition-transform duration-500"
             style="transform: translateX(-${this.currentIndex * 100}%);">
          ${this.images.map((src) => `<img src="${src}" class="w-full rounded-t-[10px] rounded-b-[3px]" alt="Slide">`).join('')}
        </div>
        <button class="carousel-prev absolute top-1/2 left-3 transform -translate-y-1/2 text-white bg-gray-800 bg-opacity-50 p-2 rounded-full">❮</button>
        <button class="carousel-next absolute top-1/2 right-3 transform -translate-y-1/2 text-white bg-gray-800 bg-opacity-50 p-2 rounded-full">❯</button>
      </div>
    `;
  }

  addEventListeners() {
    this.container.querySelector(".carousel-prev").addEventListener("click", () => this.prev());
    this.container.querySelector(".carousel-next").addEventListener("click", () => this.next());
  }

  next() {
    if (this.currentIndex < this.images.length - 1) {
      this.currentIndex++;
      this.update();
    }
  }

  prev() {
    if (this.currentIndex > 0) {
      this.currentIndex--;
      this.update();
    }
  }

  update() {
    const imagesContainer = this.container.querySelector(".carousel-images");
    imagesContainer.style.transform = `translateX(-${this.currentIndex * 100}%)`;
  }
}

export default {
  name: "App",
  components: {
    TheWindow,
  },
  setup() {
    const carouselData = ref([
      {
        id: "MusicSwipe",
        images: [
          "../public/img/MusicSwipeLog.png",
          "../public/img/MusicSwipeGuest.png",
          "../public/img/MusicSwipeSpotifyUser.png",
        ],
      },
      {
        id: "BinGo",
        images: [
          "../public/img/bin-go.png",
          "../public/img/bin-goModalBin.png",
        ],
      },
      {
        id: "ControlAcadémico",
        images: [
          "../public/img/ControlAcadémicoLogin1.jpg",
          "../public/img/ControlAcadémico-HomeStudent.jpg",
          "../public/img/ControlAcadémico-ProfileStudent.jpg",
          "../public/img/ControlAcadémico-EditProfile.jpg",
          
          "../public/img/ControlAcadémicoLogin2.jpg",
          "../public/img/ControlAcadémico-HomeAdmin.jpg",
          "../public/img/ControlAcadémico-DashboardAdmin.jpg",
          "../public/img/ControlAcadémico-DashboardAdmin-StudentInforation.jpg",
        ],
      },
    ]);

    onMounted(() => {
      carouselData.value.forEach(({ id, images }) => {
        const container = document.querySelector(`#${id}`);
        new Carousel(container, images);
      });
    });

    return { carouselData };
  },
};
</script>



<template>
  <main class="sm:pt-5 relative max-w-screen-md mx-auto p-5">
    <!-- P R E S E N T A C I O N -->
    <TheWindow class="mb-3" title="- P R E S E N T A C I Ó N -" color="senary">
      <div class="font-black text-5xl content-center mx-4">
        Hola, me presento soy <span class="text-[var(--color-secondary)]"> <br> J. Samuel P. Gonzalez</span>
      </div><br>
      <div class="font-bold text-lg mb-2 mx-4">
        Soy un apasionado del diseño y desarrollo, con habilidades y experiencia en la creación de sitios web que son
        tanto intuitivos como atractivos para el usuario.
        <br><br>
        Mi enfoque se centra en la creación de experiencias de usuario que sean fáciles de usar y visualmente
        atractivas,
        con el objetivo de mejorar la interacción y satisfacción del usuario con el sitio web.

        <i>*insert here some lorem
          ipsum*</i>
      </div>
    </TheWindow>
    <!-- S O B R E - M I -->
    <div class="flex max-sm:flex-col gap-3 mb-3">
      <TheWindow class="sm:basis-2/3" color="senary" title="- S O B R E - M Í -">
        <div class="font-bold text-md mx-4">
          <div>
            Actualmente estoy estudiando la carrera de Ingeniería en Sistemas Computacionales.
          </div><br>
          <div>
            Mi enfoque en el diseño y desarrollo web es crear interfaces limpias y atractivas que hagan que los usuarios
            se sientan cómodos y puedan navegar fácilmente. Lo que permite una experiencia de usuario óptima, trabajando
            con HTML, CSS y JavaScript, lo que me permite crear soluciones técnicas y funcionales.
          </div><br>
          <div>
            Cuento con un humor algo ácido y una personalidad muy carismática. Me considero una persona capaz y
            proactiva, con mucho interés en aprender cada día más, me encanta interactuar con la gente y trabajar en
            equipo.
          </div>

        </div>
      </TheWindow>
      <!-- R E D E S - E - I M A G E N -->
      <div class="flex flex-col">
        <TheWindow class="sm:w-56 hidden md:block md:" color="quinary" title="¿Yo?">
          <div class="picture">
            <img src="./assets/rndm/sago.png" alt="Imagen de perfil">
          </div>
        </TheWindow>
        <br class="hidden md:block">
        <!-- R E D E S -->
        <TheWindow class="sm:w-56" color="senary" title="- R E D E S -">
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <!-- G I T H U B -->
              <a class="flex items-center justify-center w-12 h-12 text-2xl bg-[var(--color-octonary)] shadow-solid rounded-xl border-4 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100"
                href="https://github.com/Bimori404" target="_blank">
                <font-awesome-icon icon="fa-brands fa-github" style="color: #ececec;" />
              </a>
              <!-- C V -->
              <a class="flex items-center justify-center w-12 h-12 text-2xl bg-[var(--color-octonary)] shadow-solid rounded-xl border-4 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100"
                alt="Curriculum Vitae"
                href="https://docs.google.com/document/d/1MRvqrTY27DCsa9qNB0ZTYnSoAhzfBj8H/edit?usp=sharing&ouid=115285703923727061955&rtpof=true&sd=true"
                target="_blank">

                <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 448 512">
                  <path fill="#ececec"
                    d="M224 256A128 128 0 1 0 224 0a128 128 0 1 0 0 256zm-45.7 48C79.8 304 0 383.8 0 482.3C0 498.7 13.3 512 29.7 512H418.3c16.4 0 29.7-13.3 29.7-29.7C448 383.8 368.2 304 269.7 304H178.3z" />
                </svg>
              </a>
              <!-- L I N K E D I N -->
              <a class="flex items-center justify-center w-12 h-12 text-2xl bg-[var(--color-octonary)] shadow-solid rounded-xl border-4 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100"
                href="https://www.linkedin.com/in/jsamuelpgonzalez/" target="_blank">
                <font-awesome-icon icon="fa-brands fa-linkedin" style="color: #ececec;" />
              </a>
            </div>
          </div>
          <br>
        </TheWindow>
      </div>
    </div>
    <!-- H A B I L I D A D E S -->
    <div class="flex max-sm:flex-col gap-3 mb-3 text-center">
      <!-- L E N G U A J E S -->
      <TheWindow color="senary" class="sm:basis-1/3"
        title="- L E N G U A J E S - D E - P R O G R A M A C I O N - (DSL y GPL) -">
        <div class="font-bold text-sm mb-2">
          <p>
            Cuento con experiencia en los siguientes lenguajes:
          </p>
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=java" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=html" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=css" />
              </a>
            </div>
          </div>
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=bootstrap" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=tailwind" />
              </a>
            </div>
          </div>

        </div>
      </TheWindow>
      <!-- S O F T W A R E -->
      <TheWindow color="senary" class="sm:basis-1/3" title="- S O F T W A R E -">
        <div class="font-bold text-sm mb-2">
          <p>
            He trabajado y tengo experiencia en el uso de estas herramientas para crear y diseñar diversos tipos de
            proyectos visuales.
          </p>
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=vscode" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=figma" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=xd" />
              </a>
            </div>
          </div>
        </div>
      </TheWindow>
      <!-- R U T A - A C T U A L -->
      <TheWindow color="senary" class="sm:basis-1/3" title="- A C T U A L - R U TA - D E - A P R E N  D I Z A J E -">
        <div class="font-bold text-sm mb-2">
          <p>
            He trabajado poco con estas herramientas y me gustaria aprender a manejarlas mejor.
          </p>
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=ai" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=ps" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=js" />
              </a>
            </div>

          </div>
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=vue" />
              </a>
              <a
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img src="https://skillicons.dev/icons?i=php" />
              </a>
            </div>
          </div>
        </div>
      </TheWindow>
    </div>
    <!-- P R O Y E C T O S -->
    <TheWindow class="mb-3" title="- P R O Y E C T O S -" color="senary">
      <div class="font-bold text-lg mb-2">
        <!--  -->
        <div class="flex flex-col md:flex-row md:space-x-4">
          <!--  -->
          <div class="max-w-sm rounded-b-xl">
            <!-- CONTROL-ACADEMICO -->
            <div class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl  bg-[var(--color-senary)]">
                <div id="ControlAcadémico" class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                </div>
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">Sistema de Control Académico</div>
                  <p class="text-gray-700 text-base">
                    - Administradores: Pueden visualizar gráficos clave, gestionar boletas, buscar por
                    filtros, y validar datos (automática o manualmente).
                    <br>
                    <!-- - Tutores Academicos: Pueden ver información académica, personal y la consulta de calificaciones
                    parciales y finales de los alumnos bajo su tutoría.
                    <br> -->
                    - Estudiantes: Pueden consultar su información académica, calificaciones y subir documentos
                    importantes.
                  </p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#FullStack</span>
                </div>
              </div>
            </div>
            <!-- FUNDAPROG -->
            <div class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl  bg-[var(--color-senary)]">
                <img class="w-full rounded-t-[10px] rounded-b-[3px]" src="./assets/rndm/fundaprog.png">
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">Fundaprog</div>
                  <p class="text-gray-700 text-base">
                    "Fundaprog" tiene como objetivo la creación de un sitio web educativo dedicado a difundir material
                    de Fundamentos de Programación.
                  </p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#UX/UI
                    Designer</span>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#Frontend</span>
                </div>
              </div>
            </div>
            <!-- BIN-GO -->
            <div class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl  bg-[var(--color-senary)]">
                <div id="BinGo" class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                </div>
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">Bin-Go</div>
                  <p class="text-gray-700 text-base">
                    Sistema web de gestión integral de residuos basado en IoT para controlar, manejar y optimizar la
                    disposición de residuos.
                  </p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#Frontend</span>
                </div>
              </div>
            </div>
            <!--  -->
          </div>
          <!--  -->
          <div class="max-w-sm rounded-b-xl">
            <!-- VERDIA -->
            <div class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl  bg-[var(--color-senary)]">
                <img class="w-full rounded-t-[10px] rounded-b-[3px]" src="./assets/rndm/verdia.png">
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">Verdia</div>
                  <p class="text-gray-700 text-base">
                    Plataforma web basada en inteligencia artificial (IA) para la detección temprana de enfermedades en
                    el cultivo de caña de azúcar.
                  </p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#Frontend</span>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#Graphic
                    Designer</span>
                </div>
              </div>
            </div>
            <!-- PRODEA - TECTRAMITES -->
            <div class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl  bg-[var(--color-senary)]">
                <img class="w-full rounded-t-[10px] rounded-b-[3px]"
                  src="./assets/rndm/diseño-figma-PRODEA(Proceso de Documentación Escolar y Académica).png">
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">Prodea - TecTramites</div>
                  <p class="text-gray-700 text-base">
                    Plataforma digital para simplificar el proceso de obtener documentos académicos, ofreciendo una
                    solución
                    eficiente y conveniente para estudiantes y instituciones educativas.
                  </p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#UX/UI
                    Designer</span>
                </div>
              </div>
            </div>
            <!-- MUSIC-SWIPE -->
            <div class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl  bg-[var(--color-senary)]">
                <div id="MusicSwipe" class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                </div>
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">Music Swipe</div>
                  <p class="text-gray-700 text-base">
                    Es una aplicación web que permite a los usuarios descubrir nueva música deslizando
                    pistas de diferentes géneros musicales. Los usuarios pueden escuchar vistas previas de las pistas,
                    deslizar hacia la izquierda para rechazar una pista o deslizar hacia la derecha para agregarla a su
                    lista de reproducción.
                  </p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#Frontend</span>
                </div>
              </div>
            </div>
          </div>
          <!--  -->
        </div>
      </div>
    </TheWindow>
  </main>
  <!-- <div class="bg-[var(--color-primary)]">1</div>
    <div class="bg-[var(--color-secondary)]">2</div>
    <div class="bg-[var(--color-tertiary)]">3</div>
    <div class="bg-[var(--color-quaternary)]">4</div>
    <div class="bg-[var(--color-quinary)]">5</div>
    <div class="bg-[var(--color-senary)]">6</div>
    <div class="bg-[var(--color-septenary)]">7</div>
    <div class="bg-[var(--color-octonary)]">8</div> -->

</template>