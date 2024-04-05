<template>
  <div>
    <header>
      <div class="user">
        <img src="./img/profil.jpeg" alt="">
        <h3 class="name">Rifky Rahmel Purnesi Ho</h3>
        <p class="post">Informatics Enginnering</p>
      </div>

      <nav class="navbar">
        <ul>
          <li><a @click="scrollToSection('#home')">Home</a></li>
          <li><a @click="scrollToSection('#about')">About</a></li>
          <li><a @click="scrollToSection('#skills')">Skills</a></li>
          <li><a @click="scrollToSection('#contact')">Contact</a></li>
        </ul>
      </nav>
    </header>

    <div id="menu" class="fas fa-bars" @click="toggleMenu"></div>

    <section class="home" id="home">
      <h3>Hallo Selamat Datang!</h3>
      <h1>Saya, <span>Rifky Rahmel</span></h1>
      <p>Seorang Mahasiswa teknik informatika Universitas Islam Riau yang berfokus dalam karier teknologi dan bisnis.</p>
      <Button @click="scrollToSection('#about')">About Me <i class="fas fa-user"></i></Button>
    </section>

    <section class="about" id="about">
      <h1 class="heading"><span>About</span> Me</h1>
      <div class="row">
        <div class="info">
          <h3><span>Nama : </span> Rifky Rahmel Purnesi Ho</h3>
          <h3><span>Jenis Kelamin : </span> Laki - Laki</h3>
          <h3><span>Umur : </span> 20 tahun</h3>
          <h3><span>Tempat Lahir : </span> Kepulauan Riau, Tanjung Balai Karimun</h3>
          <h3><span>Tanggal Lahir : </span> 20 Januari 2004</h3>
          <h3><span>Agama : </span> Islam</h3>
        </div>
      </div>
    </section>

    <section class="skills" id="skills">
      <h1 class="heading"><span>My</span> Skills</h1>
      <div class="overview">
        <div class="info">
          <h3>Beberapa skills yang sudah saya kembangkan selama studi saya di Teknik Informatika:</h3>
        </div>
        <div class="skillicon-container">
          <div class="skill" v-for="skill in skills" :key="skill.id">
            <div class="skill-icon">
              <i :class="skill.icon"></i>
            </div>
            <span>{{ skill.name }}</span>
          </div>
        </div>
        <h3>Alat-alat ini membantu saya dalam mengerjakan tugas-tugas project </h3>
      </div>
    </section>

    <section class="contact" id="contact">
      <h1 class="heading"><span>My</span> Contact</h1>
      <div class="row">
        <div class="content">
          <h3 class="title">Contact Info</h3>
          <div class="info">
            <h3><i class="fas fa-envelope"></i> rifkyrahmel6@gmail.com</h3>
            <h3><i class="fas fa-phone"></i>+62 8583-5402-412</h3>
            <h3><i class="fas fa-location-dot"></i>Indonesia</h3>
          </div>
        </div>
        <form>
          <input type="text" placeholder="name" class="box">
          <input type="email" placeholder="email" class="box">
          <input type="text" placeholder="project" class="box">
          <textarea name="" id="" cols="30" rows="10" class="box message" placeholder="message"></textarea>
          <Button class="btn">Kirim <i class="fas fa-paper-plane"></i></Button>
        </form>
      </div>
    </section>
  </div>
</template>

<script>
import Button from './components/button.vue';
export default {
  components: {
    Button
  },
  data() {
    return {
      skills: [
        { id: 1, name: 'HTML5', icon: 'fab fa-html5' },
        { id: 2, name: 'CSS3', icon: 'fab fa-css3' },
        { id: 3, name: 'JavaScript', icon: 'fab fa-js' },
        { id: 4, name: 'Python', icon: 'fab fa-python' }
      ]
    };
  },
  methods: {
    scrollToSection(sectionId) {
      const section = document.querySelector(sectionId);
      section.scrollIntoView({ behavior: 'smooth' });
    },
    toggleMenu() {
      const header = document.querySelector('header');
      header.classList.toggle('toggle');
    },
    closeMenuOnScroll() {
      const menuIcon = document.getElementById('menu');
      const header = document.querySelector('header');
      menuIcon.classList.remove('fa-times');
      header.classList.remove('toggle');
    },
    closeMenuOnLoad() {
      const menuIcon = document.getElementById('menu');
      const header = document.querySelector('header');
      menuIcon.classList.remove('fa-times');
      header.classList.remove('toggle');
    }
  },
  mounted() {
    const menuIcon = document.getElementById('menu');
    menuIcon.style.display = 'block'; // Ensure menu button is visible on mount
    window.addEventListener('scroll', this.closeMenuOnScroll);
    window.addEventListener('load', this.closeMenuOnLoad);
  },
  beforeUnmount() {
    const menuIcon = document.getElementById('menu');
    window.removeEventListener('scroll', this.closeMenuOnScroll);
    window.removeEventListener('load', this.closeMenuOnLoad);
  }
};
</script>


<style scoped>
#menu{
  position: fixed;
  top:2rem; right: 2rem;
  background: #333;
  color: #fff;
  cursor: pointer;
  font-size: 2.5rem;
  padding: 1rem 1.5rem;
  z-index: 1000;
  display: none;
}

.home{
  display: flex;
  justify-content: center;
  flex-flow: column;
  padding: 0 15rem;
}

.home h3{
  font-size: 2.5rem;
  color: #fff;
}

.home h1{
  font-size: 5rem;
  color: #fff;
}

.home h1 span{
  color: var(--yellow);
}

.home p{
  font-size: 2rem;
  color: #eee;
  padding: 1rem 0;
}

.about .row{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  padding: 1rem 0;
}

.about .row .info{
  flex: 1 1 48rem;
  padding: 2rem 1rem;
  padding-left: 6rem;
}

.about .row .info h3{
  font-size: 2rem;
  color: var(--yellow);
  padding:1rem 0;
  font-weight: normal;
}

.about .row .info h3 span{
  color: #fff;
  padding: 0 .5rem;
}

.skills .overview h3{
  color: #fff;
  font-size: 2rem;
  padding-top: 4rem;
  justify-content: center;
  text-align: center;
  font-weight: normal;
  padding-bottom: 5rem;
}


.skillicon-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 2rem; /* Add padding between skills */
}

.skill {
  text-align: center;
  margin-bottom: 20px;
  flex: 0 0 calc(25% - 4rem); /* Adjust width for 4 skills in a row with gap */
}


.skill-icon {
  color: #fff;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 10px;
  display: inline-block;
}

.skill-icon:hover{
  background-color: white;
}

.skill-icon:hover i{
  color: #333;
}

.skill-icon i {
  color: #fff;
  font-size: 50px;
}

.skill span {
  color: #fff;
  display: block;
}

.contact .row{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

.contact .row .content{
  flex: 1 1 30rem;
  padding: 4rem;
  padding-bottom: 0;
}

.contact .row form{
  flex: 1 1 30rem;
  padding: 2rem;
  margin: 2rem;
  padding-bottom: 4rem;
}

.contact .row form .box{
  padding: 1.5rem;
  margin: 1rem 0;
  background: #3333;
  color: #fff;
  text-transform: none;
  font-size: 1.7rem;
  width: 100%;
}

.contact .row form .box::placeholder{
  text-transform: capitalize;
}

.contact .row form .message{
  height: 15rem;
  resize: none;
}

.contact .row .content .title{
  text-transform: uppercase;
  color: #fff;
  font-size: 3rem;
  padding-bottom: 2rem;
}

.contact .row .content .info h3{
  display: flex;
  align-items: center;
  font-size: 2rem;
  color: #fff;
  padding: 1rem 0;
  font-weight: normal;
}

.contact .row .content h3 i{
  padding-right: 1rem;
  color: var(--yellow);
}
</style>
