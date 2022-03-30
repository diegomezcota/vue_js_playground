<script>
export default {
  data() {
    const images = ["https://side-out.org/wp-content/uploads/2021/07/5200.jpg", "https://www.cdc.gov/coronavirus/2019-ncov/daily-life-coping/images/cat-and-dog-happy.jpg?_=68620"];
    const land_activities = ["Salir a pasear.", "Comer croquetas.", "Jugar en el parque.", "Descansar.", "Hacer ruido en la noche."]
		let img_index = 0;
    
    return {
      pic_footer: 'Pie de foto indefinido',
      count: 0,
      images: images,
      img_index: img_index,
      activities: land_activities,
      first_foto_showing: true,
      gatito_range: 50,
      perrito_range: 50,
    }
  }
}
</script>

<template>
  <div class="centered">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
      <ul class="navbar" id="navbar">
        <li><a href="https://en.wikipedia.org/wiki/Pet" target="blank_">Definition</a></li>
        <li><a href="https://www.petsmart.com/" target="blank_">Pet supplies</a></li>
        <li><a href="https://www.dailypaws.com/pet-news-entertainment/feel-good-stories" target="blank_">Feel good stories</a></li>
      </ul>
      <h1>Pet land</h1>
      <button @click="img_index = (img_index + 1) % images.length; first_foto_showing = !first_foto_showing;">
        Cambiar foto
      </button>
      <br/>
      <br/>
      <div class="card">
        <img 
          class="centered"
          :src="images[img_index]"
          style="width: 50%;"
        />
        <div class="card-container">
          <div class="centered" v-if="first_foto_showing">Somos animales del mismo color!</div>
          <h3 class="centered">{{pic_footer}}</h3>
        </div>
      </div>
      <br/>
      <h2>
        Cambia el pie de foto:
      </h2>
      <input v-model="pic_footer">
      <br/><br/>
      <h2>
        Las actividades en Pet land son:
      </h2>
      <ul>
        <li v-for='act in activities'>
          {{ act }}
        </li>
      </ul>
      <div class="centered" v-if="perrito_range > gatito_range">Te gustan más los perritos!</div>
      <div class="centered" v-if="perrito_range < gatito_range">Te gustan más los gatitos!</div>
      <div class="centered" v-if="perrito_range == gatito_range">Te gustan igual los perritos y gatitos!</div>
      <h2>¿Qué tanto te gustan los perritos?</h2>
      <div class="slidecontainer">
        <input type="range" min="1" max="100" class="slider" id="perrito-range" v-model="perrito_range">
      </div>
      <h2>¿Qué tanto te gustan los gatitos?</h2>
      <div class="slidecontainer">
        <input type="range" min="1" max="100" class="slider" id="gatito-range" v-model="gatito_range">
      </div>
  </div>
</template>

<style>
  .centered {
    margin: auto;
    width: 50%;
    padding: 10px;
  }
  .navbar {
    list-style-type: none;
    margin: 0;
    padding: 0;
    background-color: rgb(255, 216, 138);
  }
  .card {
    /* Add shadows to create the "card" effect */
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
  }

  /* On mouse-over, add a deeper shadow */
  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
  }
  /* Add some padding inside the card container */
  .card-container {
    padding: 2px 16px;
  }
  .slidecontainer {
    width: 100%; /* Width of the outside container */
  }

  /* The slider itself */
  .slider {
    -webkit-appearance: none;  /* Override default CSS styles */
    appearance: none;
    width: 100%; /* Full-width */
    height: 25px; /* Specified height */
    background: #d3d3d3; /* Grey background */
    outline: none; /* Remove outline */
    opacity: 0.7; /* Set transparency (for mouse-over effects on hover) */
    -webkit-transition: .2s; /* 0.2 seconds transition on hover */
    transition: opacity .2s;
  }

  /* Mouse-over effects */
  .slider:hover {
    opacity: 1; /* Fully shown on mouse-over */
  }
  /* The slider handle (use -webkit- (Chrome, Opera, Safari, Edge) and -moz- (Firefox) to override default look) */
  .slider::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 25px; /* Set a specific slider handle width */
    height: 25px; /* Slider handle height */
    background: rgb(252, 157, 3); /* Green background */
    cursor: pointer; /* Cursor on hover */
  }

  .slider::-moz-range-thumb {
    width: 25px; /* Set a specific slider handle width */
    height: 25px; /* Slider handle height */
    background: rgb(252, 157, 3); /* Green background */
    cursor: pointer; /* Cursor on hover */
  }
  .sticky {
    position: fixed;
    top: 0;
    width: 100%;
  }
  #navbar {
    overflow: hidden;
  }
</style>
