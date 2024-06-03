<script>
export default {
  name: "Main",
  data() {
    return {
      formData: {
        offer:"",
        name: "",
        surname: "",
        tel_number: "",
        email: ""
      },
      showSection: false,
      items: [],
      errorMessage: ""
    };
  },
  methods: {
    saveToLocalStorage() {
      //resetto l'errore 
      this.errorMessage = "";

      // controllo se i campi sono compilati
      if (!this.formData.offer || !this.formData.name || !this.formData.surname || (!this.formData.tel_number && !this.formData.email)) {
      this.errorMessage = "Per favore, compila tutti i campi.";
      return;
    }

      // Aggiungo oggetto nell'array
      this.items.push({ ...this.formData });

      // Salva l'array
      localStorage.setItem("items", JSON.stringify(this.items));

      // Resetta il nuovo oggetto
      this.formData.name = "";
      this.formData.surname = "";
      this.formData.tel_number = "";
      this.formData.email = "";
      this.formData.offer = "";

      // Manda alert di conferma
      alert(
        "Inviato correttamente, un nostro collaboratore ti contatterà presto!"
      );
    },

    toggleSection(){
      this.showSection =!this.showSection
      
      this.$nextTick(() => {
          const targetElement = document.getElementById('targetElement');

          // Scrolla fino all'elemento target
          targetElement.scrollIntoView({ behavior: 'smooth' });
        });
    },

    setOfferAndShowForm(offer) {
      this.formData.offer = offer;
      this.showSection = true;

      this.$nextTick(() => {
          const targetElement = document.getElementById('targetElement');

          // Scrolla fino all'elemento target
          targetElement.scrollIntoView({ behavior: 'smooth' });
        });
    }

  },
  created() {
    const savedItems = localStorage.getItem("items");
    if (savedItems) {
      this.items = JSON.parse(savedItems);
    }
  },
};
</script>

<template>
  <main>
    <h1 class="title">Consulenza gratuita</h1>
    <h3 class="sub-title" >Scegli l'utenza</h3>

    <!-- card offerte -->
    <div class="container-img-offer">
      <div class="container-img" @click="setOfferAndShowForm('Luce')" alt="#form-compilazione">
        <img class="img-offer" src="/Luce.jpg" alt="">
        <span class="offer">Luce</span>
      </div>
      <div class="container-img" @click="setOfferAndShowForm('Gas')">
        <img class="img-offer" src="/gas.jpg" alt="">
        <span class="offer">Gas</span>
      </div>
      <div class="container-img" @click="setOfferAndShowForm('Internet')">
        <img class="img-offer" src="/internet.jpg" alt="">
        <span class="offer">Internet</span>
      </div>
    </div>
    <!-- /card offerte -->

    <p class="info-text">Compila il form per essere contattato dal nostro primo collaboratore disponibile, non è un ROBOT tranquillo! Scrivici anche tramite whatsapp.</p>

    <!-- toggle button -->
    <button class="btn-sub" @click="toggleSection">Clicca e compila &dArr;</button>
    <!-- toggle button -->
      
      <!-- compilare il form -->
      <form v-if="showSection" @submit.prevent="saveToLocalStorage" id="form-compilazione">
        
      <h2 class="form-title" >Compila i campi</h2>
      <!-- messaggio errore -->
      <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>

      <!-- select offerte -->
      <select name="offer" v-model="formData.offer" id="targetElement">
        <option value="Luce">Luce</option>
        <option value="Gas">Gas</option>
        <option value="Internet">Internet</option>
      </select>
      
      <input v-model="formData.name" placeholder="Name" width="100" height="48" />
      <input v-model="formData.surname" placeholder="Surname" />
      <input v-model="formData.tel_number" placeholder="Tel Number" />
      <input v-model="formData.email" placeholder="Email" />
      
      <button class="btn-sub" type="submit">Invia</button>
    </form>
      <!-- /compilare il form -->

  </main>
</template>


<style>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color:  rgb(22, 22, 22);
  height: 100%;
  padding: 80px;
}

.title{
  color: white;
}

.sub-title{
  color: white;
  margin-bottom: 15px;
}

.info-text{
  color: white;
  text-align: center;
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 400px;
}

select{
  margin: 5px;
  width: 50%;
}

input {
  display: block;
  padding: 10px;
  margin: 5px;
  border-radius: 5px;
  width: 300px;
}

.form-title {
  color: white;
  margin-top: 40px;
  margin-bottom: 10px;
}

.btn-sub {
  background-color: rgb(4, 192, 4);
  padding: 8px;
  border: 1px solid rgb(4, 192, 4);
  border-radius: 7px;
  margin-top: 10px;
  margin-bottom: 20px;
  color: white;
  width: 200px;
}

.container-img-offer{
  display: flex;
  justify-content: center;
  align-items: center;
}

.container-img{
  width: 30%;
  height: 180px;
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  margin: 4px;
}

.container-img:hover{
  border: 2px solid white;
}

.img-offer{
  width: 100%;
  opacity: .7
}

.offer{
  position: absolute;
  color: white;
  font-size: 2rem;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.error-message {
  color: red;
  margin-top: 10px;
}


@media screen and (min-width: 320px) and (max-width: 1024px) {
  main{
    padding: 40px;
  }
  .container-img-offer{
    display: block;
  }

  .container-img{
    width: 95%;
    height: 90px;
    margin-bottom: 15px;
    margin: 10px auto;
  }

  .title{
    text-align: center;
  }
  
  .sub-title{
    margin-top: 30px;
    font-style: italic;
  }
}
</style>
