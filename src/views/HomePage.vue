<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>{{ $route.params.id }}</ion-title>
      </ion-toolbar>
    </ion-header>
    
    
    <ion-content :fullscreen="true">
      <pre>

        <!-- {{ characters }} -->
      </pre>
      <template v-for="(character, index) in characters" :key="index">
        <ion-card>
          <img alt="Silhouette of mountains" :src="character.image" />
          <ion-card-header>
            <ion-card-title>{{ character.name }}</ion-card-title>
            <ion-card-subtitle>{{ character.species }}</ion-card-subtitle>
          </ion-card-header>

          <ion-card-content>
            Here's a small text description for the card content. Nothing more, nothing less.
          </ion-card-content>
        </ion-card>
        <!-- <ion-card>
          <ion-card-header>
            <ion-card-title>{{ character.name }}</ion-card-title>
            <ion-card-subtitle>{{ character.species }}</ion-card-subtitle>
            <ion-card-subtitle>{{ character.image }}</ion-card-subtitle>

          </ion-card-header>
  
          <ion-card-content>
            Here's a small text description for the card content. Nothing more, nothing less.
          </ion-card-content>
        </ion-card> -->
      </template>

      <!-- <button @click="getResources">Get resources</button> -->


      <ion-fab vertical="bottom" horizontal="center" slot="fixed">
        <ion-fab-button @click="takePhoto()">
          <ion-icon :icon="camera"></ion-icon>asdfsad
        </ion-fab-button>
      </ion-fab>
    </ion-content>
  </ion-page>
</template>

<script>
import { defineComponent } from 'vue';
import { ref, onMounted } from 'vue'

export default defineComponent({
  name: 'HomePage',

  setup() {
    let characters = ref(null)

    onMounted( async () => {
      const response = await getResources()
      characters.value = response.results
    })

    const getResources = async () => {
      const res = await fetch('https://rickandmortyapi.com/api/character')
      const data = await res.json()
      // characters.value = data.results
      return data
    }

    return {
      characters,
      getResources
    }
  }
})
</script>

<style>

</style>