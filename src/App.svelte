<script>
  import {Navbar, Button } from "spaper";
  import Officer from "./Officer.svelte";
  import { Discord, Github} from "@icons-pack/svelte-simple-icons";
  import Particles from "svelte-particles";
  import { loadSlim } from "tsparticles-slim"; 

  let particlesConfig = {
    particles: {
    number: {
      value: 12,
      density: {
        enable: true,
        value_area: 800
      }
    },
    color: {
      value: "#fff"
    },
    shape: {
      type: "circle",
      stroke: {
        width: 0,
        color: "#fff"
      },
      polygon: {
        nb_sides: 5
      },
      image: {
        src: "img/github.svg",
        width: 100,
        height: 100
      }
    },
    opacity: {
      value: 0.25,
      random: false,
      anim: {
        enable: false,
        speed: 1,
        opacity_min: 0.1,
        sync: false
      }
    },
    size: {
      value: 5,
      random: true,
      anim: {
        enable: false,
        speed: 15,
        size_min: 0.1,
        sync: false
      }
    },
    line_linked: {
      enable: true,
      distance: 300,
      color: "#fff",
      opacity: 0.25,
      width: 2
    },
    move: {
      enable: true,
      speed: 12,
      direction: "none",
      random: false,
      straight: false,
      out_mode: "out",
      bounce: false,
      attract: {
        enable: false,
        rotateX: 600,
        rotateY: 1200
      }
    }
  },
  fullscreen: {
    enable: true,
    zIndex: -1
  },
  interactivity: {
    detect_on: "canvas",
    events: {
      onhover: {
        enable: true,
        mode: "repulse"
      },
      onclick: {
        enable: true,
        mode: "push"
      },
      resize: true
    },
    modes: {
      grab: {
        distance: 800,
        line_linked: {
          opacity: 1
        }
      },
      bubble: {
        distance: 800,
        size: 80,
        duration: 2,
        opacity: 0.8,
        speed: 3
      },
      repulse: {
        distance: 250,
        duration: 0.4
      },
      push: {
        particles_nb: 1
      },
      remove: {
        particles_nb: 2
      }
    }
  },
  "retina_detect": true
};

  let onParticlesLoaded = event => {
      const particlesContainer = event.detail.particles;
  };

  let particlesInit = async engine => {
      await loadSlim(engine);
  };

  let text, email, name;
  let disabled = "";
  
  const officers = [
      {
      name: "XXX",
      description: "XXX",
      title: "Club Sponsor",
      image: "./images/",
    //github: "https://github.com",
      mail: "gmail.com",
    //linkedin: "https://linkedin.com"
      
    },
    {
      name: "XXX",
      description: "XXX",
      title: "President/Founder",
      image: "./images/",
      github: "https://github.com",
      mail: "gmail.com",
    //website: "",
      linkedin: "https://linkedin.com"
      
    },
    {
      name: "XXX",
      description: "XXX",
      title: "Vice President",
      image: "./images/",
      github: "https://github.com",
      mail: "gmail.com",
      linkedin: "https://linkedin.com",
    },
    {
      name: "XXX",
      description: "XXX",
      title: "Head of Back End",
      image: "./images/",
      mail: "gmail.com",
      github: "https://github.com",
      linkedin: "https://linkedin.com",
      
    },
    {
      name: "XXX",
      description: "XXX",
      title: "Head of Design",
      image: "./images/",
      github: "https://github.com",
      mail: "gmail.com",
      linkedin: "https://linkedin.com"
    },
    {
      name: "XXX",
      description: "XXX",
      title: "Head of Education",
      image: "./images/",
      github: "https://github.com",
      mail: "gmail.com",
      linkedin: "https://linkedin.com",

    },
    {
      name: "XXX",
      description: "XXX",
      title: "Head of Logistics",
      image: "./images/",
      github: "https://github.com",
      mail: "gmail.com",
      linkedin: "https://linkedin.com",

    }
  ];
  
  async function onSubmit() {
    disabled = "Sending...";
    const res = await fetch("https://formspree.io/f/mrgwpbdd", {
      headers: {
        "Content-Type": "application/json",
        "Data-Type": "json",
      },
      method: "POST",
      mode: "no-cors",
      body: JSON.stringify({ name, email, text }),
    });
    disabled = "Sent!";
    setTimeout(() => {
      disabled = "";
    }, 10000);
  }
</script>

<main style="background:#121212">
  <Navbar fixed style="background:#ffffff; border-color:#whitesmoke">
    <h3 slot="brand" class="brand-logo">
      <span class="header-character">CWDC&lpar;<img src=./images/clubicon.jpg alt="club logo" class="club-logo">&rpar; </span>
    </h3>

    <ul class="inline">
      <li><a href="#what" class="header-item">&lt;Our Work</a></li>
      <li><a href="#who" class="header-item">Our Team</a></li>
      <li><a href="#schedule" class="header-item"> Our Schedule</a></li>
      <li id="involved-li"><a href="#started" class="header-item"> Get Started/&gt;</a></li>
      <li>
        <Button style="font-size:1.25em;padding-bottom:0.15em;border-color:#808080" href="https://github.com/coppellwebdev" external>
          <Github/>
        </Button>
      </li>
      <li class="join-button">
        <Button
          style="font-size:1.25em;background-color:#ffcccb; color:#e74b36; border-color: #e74b36"
          type="secondary"
          href="https://docs.google.com/forms/d/e/1FAIpQLSdjIxz2aScSJ8_-D86noziVUxVQUxBU9ElKN4f02V-v6NHKPg/viewform?usp=sf_link"
          external
        >
          Join!
      </Button>
      </li>
    </ul>
  </Navbar>

  <Particles
         id="tsparticles"
         class="foo bar"
         style=""
         options={particlesConfig}
         on:particlesLoaded={onParticlesLoaded}
         particlesInit={particlesInit}
  />

  <div class="webdiv">
    <h1 id="title">Coppell HS Web Development</h1>
  </div>

  <div class="intro" id="what">
    <h2 class="section-header">Our Work</h2>
    <h3 id="info">CHS Web Dev is all about the magic: We make pixels dance and code transform.</h3>
    <p id="intro-p">
      Our mission is to expand students' interest in web development, and use it as a medium to help our community. 
      <br />We begin from scratch and progress seamlessly to create websites following the latest web development trends.
      <br />And of course... we look to dabble in a couple of innovative projects on the way!
    </p>
  </div>

  <h2 class="section-header" id="who">2023-2024 Team</h2>

  <div class="officers">
    {#each officers as officer}
      <Officer {...officer} />
    {/each}
  </div>

  <div>
    <h2 class="section-header" id="schedule">Our Schedule</h2>
  </div>
  
  <div class="responsive-iframe-container big-container">
    <iframe src="https://calendar.google.com/calendar/embed?src=fbbde5486af8a6ae64c78f3d72578f7448fb7da9e37b4066dfd34820cb2305a2%40group.calendar.google.com&ctz=America%2FChicago" title="CHS Web Development Club Calendar" class="calendar" width="800" height="600" frameborder="0" scrolling="no"></iframe>
  </div>

  <div class="responsive-iframe-container small-container">
    <iframe src="https://calendar.google.com/calendar/embed?src=fbbde5486af8a6ae64c78f3d72578f7448fb7da9e37b4066dfd34820cb2305a2%40group.calendar.google.com&ctz=America%2FChicago" title="CHS Web Development Club Calendar"  class="calendar" width="800" height="600" frameborder="0" scrolling="no"></iframe>
  </div>


  <div style="text-align:center" id="started">
    <h2 class="section-header">Get Started!</h2>
    <p id="involved-p">
      To best create an effective chain of communication, we use various platforms to stay in touch.
    </p>
  </div>

  <!-- buttons for discord and github-->
  <div class="contacts">
    <a
      href="https://discord.gg/jtrvsFQV"
      target="_blank"
      class="button cta discord"
    >
      Discord <Discord />
    </a>

<!--<a
      href="https://www.youtube.com"
      target="_blank"
      class="button cta youtube"
    >
      YouTube <Youtube />
    </a>-->

    <a
      href="https://github.com/coppellwebdev"
      target="_blank"
      class="button cta meeting-demos"
    >
      Github <Github />
    </a>
  </div>

  <h2 class="section-header">Our Tech Arsenal</h2>

  <div class="programming-images no-border">
    <img
      src="./images/node-js.png"
      alt="Node js Logo"
      class="progimage no-border"
    />
    <img
      src="./images/react.png"
      alt="React Logo"
      class="progimage no-border"
    />
    <img
      src="./images/JavaScript-logo.png"
      alt="JavaScript Logo"
      class="progimage no-border"
    />
    <img 
      src="./images/html.png" 
      alt="HTML Logo" 
      class="progimage no-border"
    />
    <img 
      src="./images/css.png" 
      alt="CSS Logo" 
      class="progimage no-border" 
    />
    <img
      src="./images/typescript.png"
      alt="TypeScript Logo"
      class="progimage no-border"
    />
    <img
      src="./images/svelte.png"
      alt="Svelte Logo"
      class="progimage no-border"
    />
  </div>

  <h2 class="section-header">Want to Know More? Contact Us Below!</h2>
  <div class="questions">
    <form on:submit|preventDefault={onSubmit}>
      <input
        type="name"
        placeholder="Name"
        bind:value={name}
        class="center-block"
        id="subject-input"
      />

      <input
        type="email"
        placeholder="Email"
        bind:value={email}
        class="center-block"
        id="subject-input"
      />
      <textarea
        name="message"
        type="textarea"
        bind:value={text}
        placeholder="Message"
        class="center-block"
        id="subject-text"
      />
      <div class="subtn" type="submit">
        <Button
          style= "background-color:#ffcccb; color:#e74b36; border-color: #e74b36"
          type="secondary"
          size="default"
          block
          outline
          disabled={email == null ||
            text == null ||
            email.length == 0 ||
            text.length == 0 ||
            name.length == 0 ||
            disabled.length !== 0}>{disabled || "Send!"}
        </Button>
      </div>
    </form>
  </div>
</main>

<style>
  :root {
    --accent-color: #e74b36;
  }

  .webdiv {
    width: 100%;
    border-radius: 10px;
    height: 3em;
    text-align: center;
    font-size: 2em;
    padding-top: 4em;
    color: var(--accent-color);
    display: table;
  }

  #title {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    color: var(--accent-color);
    z-index: 1;
  }

  .programming-images {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 2em;
    z-index: 1;
  }

  .club-logo {
    width:1em;
    height:1em;
    display:inline-block;

  }


  .header-character {
    white-space:nowrap;
  }


  .header-item {
    font-size:1.25em;
    color: #121212; 
    border-bottom-color: #121212;
  }
  
  .header-item:hover {
    font-size: 1.30em;
    border-bottom-color: var(--accent-color);
  }

  .responsive-iframe-container {
   position: relative;
   margin-left: 15%;
   width: 70%;
   padding-bottom: 40%;
   padding-top: 30px;
   height: 0;
   overflow: hidden;
  }

.responsive-iframe-container iframe,   

  .calendar {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 5px solid var(--accent-color);
    border-style: groove;
  }

  .progimage {
    margin: 1em;
    width: 100px;
  }

  .questions {
    text-align: center;
    position: relative;
    padding-bottom: 2rem;
  }

  .center-block {
    display: block;
    margin-right: auto;
    margin-left: auto;
  }

  #subject-input,
  #subject-text {
    margin-top: 1em;
    width: 500px;
    color: whitesmoke;
  }

  #subject-text {
    margin-top: 1em;
    height: 6em;
    color: whitesmoke;
  }

  #subject-text:focus {
    border-color:var(--accent-color)
  }

  #subject-input:focus {
    border-color: var(--accent-color)
  }

  .subtn {
    margin-top: 1rem;
    display: block;
    margin-right: auto;
    margin-left: auto;
    width: 500px;
  }

  .contacts {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 5%;
    z-index: 1;
  }

  .button,
  .cta {
    font-size: 1em;
    z-index: 1;
    border: 4px solid whitesmoke;
  }

  .brand-logo {
    font-size: 3rem;
    color: var(--accent-color);
  }

  .officers {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5em;
    justify-content: center;
    z-index: 1;
  }

  .discord {
    background-color: #738adb;
  }


  .meeting-demos {
    background-color: #24292e;
  }

  .intro {
    text-align: center;
  }

  .inline {
    margin-top: 0.8em;
    white-space: nowrap;
    
  }

  #info {
    font-size: 2em;
    margin-top: 1em;
    color: whitesmoke;
  }

  #intro-p {
    font-size: 1.25em;
    margin-left: 0.25em;
    margin-right: 0.25em;
    color: whitesmoke;
  }

  #involved-p {
    font-size: 1.25em;
    text-align: center;
    margin-bottom: 1.25em;
    color: whitesmoke;
  }

  a {
    text-decoration: none;
  }

  .section-header {
    text-align: center;
    color: whitesmoke;
  }

  @media screen and (max-width: 600px) {

    #intro-p {
      margin-left: 0.25em;
      margin-right: 0.25em;
      color: whitesmoke;
    }

    #info {
      margin-left: 0.25em;
      margin-right: 0.25em;
      color: whitesmoke;
    }

    #involved-p {
      font-size: 1.5em;
      margin-left: 0.2em;
      margin-right: 0.2em;
    }

    .contacts {
      display: flex;
      flex-wrap: wrap;
    }
    
    .button,
    .cta {
      font-size: 1.2em;
      margin-bottom: 0.6em;
    }

    .progimage {
      margin: 0.25em;
      width: 50px;
    }

    #title {
      font-size: 1.75em;
    }
    .responsive-iframe-container {
      width: 95%;
      margin-left: 2.5%;
      padding-bottom: 80%;

    }

    #subject-input,
    #subject-text {
      width: 80%;
    }

    .subtn {
      width: 80%;
    }
  }
  @media screen and (max-width: 770px) {
    .join-button {
      padding-top: 1em;
    }
    #involved-li {
      margin-bottom: 1.75em;
    }
  }
  @media (max-width: 550px) {
   .big-container {
       display: none;
   }
}
  @media (min-width: 550px) {
    .small-container {
        display: none;
    }
  }
  @media screen and (max-width: 1280px) {
    .responsive-iframe-container {
      width: 85%;
      margin-left: 7.5%;
      padding-bottom: 60%;

    }
    
  }



</style>
