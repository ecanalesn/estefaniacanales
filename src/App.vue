<template>
  <div id="app" :class="{ 'dark-theme': isDarkMode, 'light-theme': !isDarkMode }">
    <!-- Header with navigation -->
    <header class="header-container" role="banner">
      <div class="header-content">
        <div class="logo">
          <a href="#inicio" aria-label="Go to portfolio home">{{ currentTranslations.name }}</a>
        </div>
        <nav :class="{ 'responsive': menuVisible }" id="nav" role="navigation" aria-label="Main navigation">
          <ul>
            <li><a href="#inicio" @click="selectMenu" aria-label="Go to home section">{{ currentTranslations.menu.home }}</a></li>
            <li><a href="#sobremi" @click="selectMenu" aria-label="Go to about section">{{ currentTranslations.menu.about }}</a></li>
            <li><a href="#portfolio" @click="selectMenu" aria-label="Go to portfolio section">{{ currentTranslations.menu.portfolio }}</a></li>
            <li><a href="#skills" @click="selectMenu" aria-label="Go to skills section">{{ currentTranslations.menu.skills }}</a></li>
            <li><a href="#contacto" @click="selectMenu" aria-label="Go to contact section">{{ currentTranslations.menu.contact }}</a></li>
          </ul>
        </nav>
        <div class="header-controls">
          <button @click="toggleTheme" class="theme-toggle" :title="currentTranslations.themeToggle" aria-label="Change theme">
            <i :class="isDarkMode ? 'fa-solid fa-sun' : 'fa-solid fa-moon'" aria-hidden="true"></i>
          </button>
          <button @click="toggleLanguage" class="language-toggle" :title="currentTranslations.languageToggle" aria-label="Change language">
            <i class="fa-solid fa-globe" aria-hidden="true"></i>
            <span>{{ currentLanguage.toUpperCase() }}</span>
          </button>
          <button class="nav-responsive" @click="showHideMenu" aria-label="Open navigation menu" aria-expanded="false">
            <i class="fa-solid fa-bars" aria-hidden="true"></i>
          </button>
        </div>
      </div>
    </header>

    <!-- Home Section -->
    <section id="inicio" class="home" data-aos="fade-up">
      <div class="banner-content">
        <div class="img-container" data-aos="zoom-in" data-aos-delay="200">
          <img src="/images/estefania.png" alt="Estefanía Canales - Full Stack Developer">
        </div>
        <h1 data-aos="fade-up" data-aos-delay="400">{{ currentTranslations.home.name }}</h1>
        <h2 data-aos="fade-up" data-aos-delay="600">{{ currentTranslations.home.title }}</h2>
        <div class="social-links" data-aos="fade-up" data-aos-delay="800">
          <a href="https://github.com/ecanalesn" target="_blank" aria-label="Visitar perfil de GitHub de Estefanía Canales">
            <i class="fa-brands fa-github" aria-hidden="true"></i>
          </a>
          <a href="https://www.linkedin.com/in/ecanalesn/" target="_blank" aria-label="Visitar perfil de LinkedIn de Estefanía Canales">
            <i class="fa-brands fa-linkedin-in" aria-hidden="true"></i>
          </a>
        </div>
      </div>
    </section>

    <!-- About Me Section -->
    <section id="sobremi" class="about-me" data-aos="fade-up">
      <div class="section-content">
        <h2 data-aos="fade-up" data-aos-delay="200">{{ currentTranslations.about.title }}</h2>
        <p data-aos="fade-up" data-aos-delay="400">
          <span>{{ currentTranslations.about.greeting }}</span>
          {{ currentTranslations.about.description }}
        </p>

        <div class="row">
          <div class="col" data-aos="fade-right" data-aos-delay="600">
            <h3>{{ currentTranslations.about.personalData }}</h3>
            <ul>
              <li>
                <span class="col-title">{{ currentTranslations.about.birthDate }}</span>
                07-12-1991
              </li>
              <li>
                <span class="col-title">{{ currentTranslations.about.phone }}</span>
                616 47 15 34
              </li>
              <li>
                <span class="col-title">{{ currentTranslations.about.email }}</span>
                estefania.canalesn@gmail.com
              </li>
              <li>
                <span class="col-title">{{ currentTranslations.about.location }}</span>
                {{ currentTranslations.about.cordoba }}
              </li>
            </ul>
          </div>

          <div class="col" data-aos="fade-left" data-aos-delay="600">
            <h3>{{ currentTranslations.about.interests }}</h3>
            <div class="interests-container">
              <div class="interest" v-for="(interest, index) in currentTranslations.about.interestList" :key="interest.name" 
                   data-aos="zoom-in" :data-aos-delay="800 + (index * 100)">
                <i :class="interest.icon" aria-hidden="true"></i>
                <span>{{ interest.name }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio" class="portfolio" data-aos="fade-up">
      <div class="section-content">
        <h2 data-aos="fade-up" data-aos-delay="200">{{ currentTranslations.portfolio.title }}</h2>
        <div class="gallery">
          <template v-for="(project, index) in currentTranslations.portfolio.projects" :key="project.name">
            <a v-if="project.url" :href="project.url" target="_blank" 
               data-aos="zoom-in" :data-aos-delay="400 + (index * 200)"
               :aria-label="`Ver proyecto ${project.name} - ${project.description}`">
              <div class="project">
                <img :src="project.image" :alt="`Proyecto ${project.name} desarrollado con ${project.description}`">
                <div class="overlay">
                  <h3>{{ project.name }}</h3>
                  <p>{{ project.description }}</p>
                </div>
              </div>
            </a>
            <div v-else class="project" 
                 data-aos="zoom-in" :data-aos-delay="400 + (index * 200)">
              <img :src="project.image" :alt="`Proyecto ${project.name} desarrollado con ${project.description}`">
              <div class="overlay">
                <h3>{{ project.name }}</h3>
                <p>{{ project.description }}</p>
              </div>
            </div>
          </template>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills" data-aos="fade-up">
      <div class="section-content">
        <h2 data-aos="fade-up" data-aos-delay="200">{{ currentTranslations.skills.title }}</h2>
        <div class="row">
          <div class="col" data-aos="fade-right" data-aos-delay="400">
            <h3>{{ currentTranslations.skills.technical }}</h3>
            <div class="skill" v-for="(skill, index) in currentTranslations.skills.technicalSkills" :key="skill.name"
                 data-aos="fade-up" :data-aos-delay="600 + (index * 100)">
              <span>{{ skill.name }}</span>
              <div class="skill-bar" role="progressbar" :aria-valuenow="skill.percentage" aria-valuemin="0" aria-valuemax="100" :aria-label="`${skill.name}: ${skill.percentage}%`">
                <div class="progress" :class="skill.class" :data-skill="skill.class">
                  <span>{{ skill.percentage }}%</span>
                </div>
              </div>
            </div>
          </div>
          <div class="col" data-aos="fade-left" data-aos-delay="400">
            <h3>{{ currentTranslations.skills.professional }}</h3>
            <div class="skill" v-for="(skill, index) in currentTranslations.skills.professionalSkills" :key="skill.name"
                 data-aos="fade-up" :data-aos-delay="600 + (index * 100)">
              <span>{{ skill.name }}</span>
              <div class="skill-bar" role="progressbar" :aria-valuenow="skill.percentage" aria-valuemin="0" aria-valuemax="100" :aria-label="`${skill.name}: ${skill.percentage}%`">
                <div class="progress" :class="skill.class" :data-skill="skill.class">
                  <span>{{ skill.percentage }}%</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contacto" class="contact" data-aos="fade-up">
      <div class="section-content">
        <h2 data-aos="fade-up" data-aos-delay="200">{{ currentTranslations.contact.title }}</h2>
        <div class="row">
          <div class="col" data-aos="fade-right" data-aos-delay="400">
            <form name="contact" method="POST" data-netlify="true" netlify-honeypot="bot-field" role="form" aria-label="Formulario de contacto" @submit.prevent="handleContactSubmit">
              <input type="hidden" name="form-name" value="contact" />
              <p style="display: none;">
                <label>Don't fill this out: <input name="bot-field" /></label>
              </p>
              <input type="text" name="name" :placeholder="currentTranslations.contact.name" required aria-label="Nombre completo" />
              <input type="tel" pattern="[0-9]{9}" name="phone" :placeholder="currentTranslations.contact.phone" aria-label="Número de teléfono" title="9 dígitos, sin espacios ni prefijo" @invalid="onPhoneInvalid" @input="clearCustomValidity">
              <input type="email" name="email" :placeholder="currentTranslations.contact.email" required aria-label="Dirección de correo electrónico" @invalid="onEmailInvalid" @input="clearCustomValidity">
              <input type="text" name="subject" :placeholder="currentTranslations.contact.subject" required aria-label="Asunto del mensaje">
              <textarea name="message" cols="30" rows="10" :placeholder="currentTranslations.contact.message" required aria-label="Mensaje"></textarea>
              <button type="submit" :disabled="formStatus === 'sending'" aria-label="Enviar mensaje de contacto">
                {{ formStatus === 'sending' ? currentTranslations.contact.sending : currentTranslations.contact.send }} <i class="fa-regular fa-paper-plane" aria-hidden="true"></i>
                <span class="overlay"></span>
              </button>
              <p v-if="formStatus === 'success'" class="form-status form-status--success" role="status">{{ currentTranslations.contact.successMessage }}</p>
              <p v-else-if="formStatus === 'error'" class="form-status form-status--error" role="alert">{{ currentTranslations.contact.errorMessage }}</p>
            </form>
          </div>
          <div class="col" data-aos="fade-left" data-aos-delay="400">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d50378.57937324657!2d-4.825684773561472!3d37.89160495712012!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd6cdf26f95e0aef%3A0x4df1d2e8108456c3!2zQ8OzcmRvYmE!5e0!3m2!1ses!2ses!4v1723049383936!5m2!1ses!2ses" 
                    width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade" 
                    title="Mapa de Córdoba, España" aria-label="Mapa interactivo de Córdoba, España"></iframe>
            <div class="info" data-aos="zoom-in" data-aos-delay="600">
              <ul>
                <li>
                  <i class="fa-solid fa-location-dot" aria-hidden="true"></i>
                  {{ currentTranslations.contact.cordoba }}
                </li>
                <li>
                  <i class="fa-solid fa-mobile-screen" aria-hidden="true"></i>
                  {{ currentTranslations.contact.contactPhone }}
                </li>
                <li>
                  <i class="fa-solid fa-envelope" aria-hidden="true"></i>
                  {{ currentTranslations.contact.contactEmail }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer role="contentinfo">
      <a href="#inicio" class="up" aria-label="Volver al inicio de la página">
        <i class="fa-solid fa-angles-up" aria-hidden="true"></i>
      </a>
      <div class="social-links">
        <a href="https://github.com/ecanalesn" target="_blank" aria-label="Visitar perfil de GitHub">
          <i class="fa-brands fa-github" aria-hidden="true"></i>
        </a>
        <a href="https://www.linkedin.com/in/ecanalesn/" target="_blank" aria-label="Visitar perfil de LinkedIn">
          <i class="fa-brands fa-linkedin-in" aria-hidden="true"></i>
        </a>
      </div>
      <div class="copyright">
        <p>{{ currentTranslations.footer.copyright }}</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted, computed } from 'vue'

// Reactive state
const menuVisible = ref(false)
const isDarkMode = ref(true)
const currentLanguage = ref('es')

// Translations
const translations = reactive({
  es: {
    name: 'Estefanía',
    themeToggle: 'Cambiar tema',
    languageToggle: 'Cambiar idioma',
    menu: {
      home: 'INICIO',
      about: 'SOBRE MI',
      portfolio: 'PORTFOLIO',
      skills: 'HABILIDADES',
      contact: 'CONTACTO'
    },
    home: {
      name: 'ESTEFANÍA CANALES',
      title: 'Full Stack Developer | HTML · CSS · JavaScript (Vue · React · Node.js) · PHP/Laravel · Java · MySQL · PostgreSQL | 🎓 Técnico Superior en Desarrollo de Aplicaciones Web'
    },
    about: {
      title: 'Sobre Mí',
      greeting: '¡Hola! soy Estefanía Canales.',
      description: 'Full Stack Developer con CFGS en Desarrollo de Aplicaciones Web. Diseño y desarrollo aplicaciones web de alto rendimiento, accesibles y centradas en la experiencia de usuario (UX).',
      personalData: 'Datos Personales',
      birthDate: 'Fecha de nacimiento',
      phone: 'Teléfono',
      email: 'Correo electrónico',
      location: 'Dirección',
      cordoba: 'Córdoba, España',
      interests: 'Intereses',
      interestList: [
        { name: 'JUEGOS DE MESA', icon: 'fa-solid fa-dice' },
        { name: 'LIBROS', icon: 'fa-solid fa-book' },
        { name: 'CAMINAR', icon: 'fa-sharp fa-solid fa-person-hiking' },
        { name: 'VIAJES', icon: 'fa-solid fa-suitcase' },
        { name: 'MÚSICA', icon: 'fa-solid fa-music' },
        { name: 'DEPORTE', icon: 'fa-solid fa-dumbbell' },
        { name: 'COCINA', icon: 'fa-solid fa-kitchen-set' },
        { name: 'CINE', icon: 'fa-solid fa-film' }
      ]
    },
    portfolio: {
      title: 'Portfolio',
      projects: [
        { name: 'Plataforma Forma-T', description: 'Vue y Laravel', image: '/images/img01.png', url: 'https://github.com/ecanalesn/forma-t/blob/main/MANUAL.md' },
        { name: 'Tu Aula Musical', description: 'Vue.js', image: '/images/img02.png', url: 'https://tuaulamusical.com' },
        { name: 'Landing Roomio', description: 'React', image: '/images/img03.png', url: 'https://landingroomio.netlify.app/' },
        { name: 'Tienda Footlily', description: 'React', image: '/images/img04.png', url: 'https://footlily.netlify.app/' },
        { name: 'PasapalabraDaw', description: 'JavaScript', image: '/images/img05.png', url: 'https://pasapalabradaw.netlify.app/' },
        { name: 'Musimemory', description: 'JavaScript', image: '/images/img06.png', url: 'https://juego-musimemory.netlify.app/' },
        { name: 'Calculadora', description: 'JavaScript', image: '/images/img07.png', url: 'https://calculadoranumerix.netlify.app/' }
      ]
    },
    skills: {
      title: 'Habilidades',
      technical: 'Habilidades técnicas',
      professional: 'Habilidades profesionales',
      technicalSkills: [
        { name: 'HTML & CSS', percentage: 90, class: 'htmlcss' },
        { name: 'JavaScript', percentage: 85, class: 'javascript' },
        { name: 'Vue.js / React', percentage: 75, class: 'vue' },
        { name: 'PHP/Laravel', percentage: 75, class: 'php' },
        { name: 'Node.js', percentage: 70, class: 'nodejs' },
        { name: 'C#', percentage: 65, class: 'csharp' },
        { name: 'Python', percentage: 65, class: 'python' },
        { name: 'Java', percentage: 65, class: 'java' }
      ],
      professionalSkills: [
        { name: 'Comunicación', percentage: 100, class: 'comunicacion' },
        { name: 'Mejora de procesos', percentage: 95, class: 'mejora' },
        { name: 'Capacidad de análisis', percentage: 90, class: 'analisis' },
        { name: 'Resolución de incidencias', percentage: 90, class: 'resolutiva' },
        { name: 'Gestión de proyectos', percentage: 90, class: 'gestion' },
        { name: 'Proactividad', percentage: 85, class: 'proactividad' },
        { name: 'Trabajo en equipo', percentage: 85, class: 'trabajo' },
        { name: 'Automatización', percentage: 85, class: 'automatizacion' }
      ]
    },
    contact: {
      title: 'Contacto',
      name: 'Nombre',
      phone: 'Número de teléfono',
      email: 'Dirección de correo',
      subject: 'Asunto',
      message: 'Mensaje',
      send: 'Enviar mensaje',
      sending: 'Enviando...',
      successMessage: '¡Gracias! Tu mensaje se ha enviado correctamente.',
      errorMessage: 'No se pudo enviar el mensaje. Inténtalo de nuevo o escríbeme directamente a estefania.canalesn@gmail.com.',
      phoneInvalid: 'Introduce un teléfono válido de 9 dígitos (ej. 616471534).',
      emailInvalid: 'Introduce una dirección de correo válida (ej. usuario@dominio.com).',
      cordoba: 'Córdoba, España',
      contactPhone: 'Contacto: 616 47 15 34',
      contactEmail: 'Correo electrónico: estefania.canalesn@gmail.com'
    },
    footer: {
      copyright: '© 2025 Portfolio Estefanía'
    }
  },
  en: {
    name: 'Estefanía',
    themeToggle: 'Toggle theme',
    languageToggle: 'Toggle language',
    menu: {
      home: 'HOME',
      about: 'ABOUT ME',
      portfolio: 'PORTFOLIO',
      skills: 'SKILLS',
      contact: 'CONTACT'
    },
    home: {
      name: 'ESTEFANÍA CANALES',
      title: 'Full Stack Developer | HTML · CSS · JavaScript (Vue · React · Node.js) · PHP/Laravel · Java · MySQL · PostgreSQL | 🎓 Higher Technician in Web Application Development'
    },
    about: {
      title: 'About Me',
      greeting: 'Hello! I am Estefanía Canales.',
      description: 'Full Stack Developer with a Higher Technician (CFGS) in Web Application Development. I design and develop high-performance, accessible web applications centered on user experience (UX).',
      personalData: 'Personal Data',
      birthDate: 'Birth date',
      phone: 'Phone',
      email: 'Email',
      location: 'Address',
      cordoba: 'Córdoba, Spain',
      interests: 'Interests',
      interestList: [
        { name: 'BOARD GAMES', icon: 'fa-solid fa-dice' },
        { name: 'BOOKS', icon: 'fa-solid fa-book' },
        { name: 'WALKING', icon: 'fa-sharp fa-solid fa-person-hiking' },
        { name: 'TRAVELS', icon: 'fa-solid fa-suitcase' },
        { name: 'MUSIC', icon: 'fa-solid fa-music' },
        { name: 'SPORTS', icon: 'fa-solid fa-dumbbell' },
        { name: 'COOKING', icon: 'fa-solid fa-kitchen-set' },
        { name: 'CINEMA', icon: 'fa-solid fa-film' }
      ]
    },
    portfolio: {
      title: 'Portfolio',
      projects: [
        { name: 'Forma-T Platform', description: 'Vue and Laravel', image: '/images/img01.png', url: 'https://github.com/ecanalesn/forma-t/blob/main/MANUAL.md' },
        { name: 'Tu Aula Musical', description: 'Vue.js', image: '/images/img02.png', url: 'https://tuaulamusical.com' },
        { name: 'Roomio Landing', description: 'React', image: '/images/img03.png', url: 'https://landingroomio.netlify.app/' },
        { name: 'Footlily Store', description: 'React', image: '/images/img04.png', url: 'https://footlily.netlify.app/' },
        { name: 'PasapalabraDaw', description: 'JavaScript', image: '/images/img05.png', url: 'https://pasapalabradaw.netlify.app/' },
        { name: 'Musimemory', description: 'JavaScript', image: '/images/img06.png', url: 'https://juego-musimemory.netlify.app/' },
        { name: 'Calculator', description: 'JavaScript', image: '/images/img07.png', url: 'https://calculadoranumerix.netlify.app/' }
      ]
    },
    skills: {
      title: 'Skills',
      technical: 'Technical skills',
      professional: 'Professional skills',
      technicalSkills: [
        { name: 'HTML & CSS', percentage: 90, class: 'htmlcss' },
        { name: 'JavaScript', percentage: 85, class: 'javascript' },
        { name: 'Vue.js / React', percentage: 75, class: 'vue' },
        { name: 'PHP/Laravel', percentage: 75, class: 'php' },
        { name: 'Node.js', percentage: 70, class: 'nodejs' },
        { name: 'C#', percentage: 65, class: 'csharp' },
        { name: 'Python', percentage: 65, class: 'python' },
        { name: 'Java', percentage: 65, class: 'java' }
      ],
      professionalSkills: [
        { name: 'Communication', percentage: 100, class: 'comunicacion' },
        { name: 'Process improvement', percentage: 95, class: 'mejora' },
        { name: 'Analytical capacity', percentage: 90, class: 'analisis' },
        { name: 'Incident resolution', percentage: 90, class: 'resolutiva' },
        { name: 'Project management', percentage: 90, class: 'gestion' },
        { name: 'Proactivity', percentage: 85, class: 'proactividad' },
        { name: 'Teamwork', percentage: 85, class: 'trabajo' },
        { name: 'Automation', percentage: 85, class: 'automatizacion' }
      ]
    },
    contact: {
      title: 'Contact',
      name: 'Name',
      phone: 'Phone number',
      email: 'Email address',
      subject: 'Subject',
      message: 'Message',
      send: 'Send message',
      sending: 'Sending...',
      successMessage: 'Thank you! Your message has been sent successfully.',
      errorMessage: 'Could not send the message. Please try again or email me directly at estefania.canalesn@gmail.com.',
      phoneInvalid: 'Enter a valid 9-digit phone number (e.g. 616471534).',
      emailInvalid: 'Enter a valid email address (e.g. user@domain.com).',
      cordoba: 'Córdoba, Spain',
      contactPhone: 'Contact: 616 47 15 34',
      contactEmail: 'Email: estefania.canalesn@gmail.com'
    },
    footer: {
      copyright: '© 2025 Estefanía Portfolio'
    }
  }
})

// Computed to get current translations
const currentTranslations = computed(() => translations[currentLanguage.value])

// Methods
const showHideMenu = () => {
  menuVisible.value = !menuVisible.value
}

const selectMenu = () => {
  menuVisible.value = false
}

const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value
  localStorage.setItem('theme', isDarkMode.value ? 'dark' : 'light')
}

const toggleLanguage = () => {
  currentLanguage.value = currentLanguage.value === 'es' ? 'en' : 'es'
  localStorage.setItem('language', currentLanguage.value)
}

// Contact form: custom bilingual validation messages
const clearCustomValidity = (event) => {
  event.target.setCustomValidity('')
}

const onPhoneInvalid = (event) => {
  event.target.setCustomValidity(currentTranslations.value.contact.phoneInvalid)
}

const onEmailInvalid = (event) => {
  event.target.setCustomValidity(currentTranslations.value.contact.emailInvalid)
}

// Contact form: submit via fetch so Netlify Forms doesn't navigate away from the SPA
const formStatus = ref('idle')

const handleContactSubmit = async (event) => {
  const form = event.target
  formStatus.value = 'sending'
  try {
    const response = await fetch('/', {
      method: 'POST',
      headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
      body: new URLSearchParams(new FormData(form)).toString()
    })
    if (!response.ok) throw new Error(`Netlify form submission failed: ${response.status}`)
    formStatus.value = 'success'
    form.reset()
  } catch (error) {
    console.error(error)
    formStatus.value = 'error'
  }
}

// Load saved preferences
onMounted(() => {
  // Restore saved theme/language, falling back to dark + Spanish on first visit
  const savedTheme = localStorage.getItem('theme')
  const savedLanguage = localStorage.getItem('language')
  isDarkMode.value = savedTheme ? savedTheme === 'dark' : true
  currentLanguage.value = savedLanguage === 'en' ? 'en' : 'es'

  // Skills animation
  const skillsEffect = () => {
    const skills = document.getElementById('skills')
    if (skills) {
      const skillsDistance = window.innerHeight - skills.getBoundingClientRect().top
      if (skillsDistance >= 300) {
        const skillsElements = document.getElementsByClassName('progress')
        Array.from(skillsElements).forEach((element) => {
          element.classList.add(element.getAttribute('data-skill'))
        })
      }
    }
  }

  window.addEventListener('scroll', skillsEffect)

  // Ensure AOS initializes after app mounts so elements are visible
  if (typeof window !== 'undefined') {
    const initAOS = () => {
      if (window.AOS) {
        window.AOS.init({ duration: 1000, easing: 'ease-in-out', once: true, offset: 100 })
        window.AOS.refreshHard()
      }
    }
    if (window.AOS) {
      initAOS()
    } else {
      window.addEventListener('load', initAOS)
    }
  }
})
</script>