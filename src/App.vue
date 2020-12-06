<template>
  <div>
    <div id="seccion3" class="pt-5">
      <div v-if="this.dataText.length >= 4" class="row justify-content-center">
        <books-api
          v-for="(data, index) in this.dataText"
          :key="index"
          :title="data.title"
          :desc="data.content_short"
          :img="data.thumbnail"
          :link="data.url_download"
        >
        </books-api>
      </div>
    </div>
    <div id="seccion4" class="row justify-content-center pt-5">
      <team-card
        v-for="(inte, index) in this.datateam"
        :key="index"
        :name="inte.name"
        :type="inte.type"
        :desc="inte.desc"
        :img="inte.img"
        :boots="inte.boots"
      >
      </team-card>
    </div>
  </div>
</template>

<script>

import TeamCard from './components/TeamCard';
import DataTeam from "./assets/team.json";
import BooksApi from './components/BooksApi.vue';

export default {
  name: 'App',

  data() {
    return {
      dataText: [],
      datateam: DataTeam,
    };
  },
  components: {
    BooksApi,
    TeamCard,
  },
 
 async beforeCreate() {
    const getNews = async () => {
      
       let urlText =
        "https://www.etnassoft.com/api/v1/get/?any_tags=[html,css,javascript]&order=newest&num_items=4&lang=spanish";
      const resultText = await fetch(urlText, {
        method: "GET",
      });

      const result = await resultText.json();

      if (result.length >= 4) {
        this.dataText = result;

        console.log(this.dataText);
      }
    };
    const getImgHead = async () => {
      let urlText = "";
      const key = "19402912-b07e2ff6c1760abfdc58e2299";

      urlText = `https://pixabay.com/api/?key=${key}&q=code+programing&orientation=horizontal&category=computer+backgrounds&image_type=photo&min_width=1200&min_height=300`;
      const resultText = await fetch(urlText, {
        method: "GET",
      });

      const result = await resultText.json();
      console.log(result);
      if (result.hits.length > 0) {
        this.dataImg = result.hits;

        console.log(this.dataImg);
        for (var i = 1; i < this.dataImg.length - 3; i++)
          this.sizeDataImg.push(i);
      }
      console.log(this.sizeDataImg);
    };

    await getNews();

    await getImgHead();
  },
}
</script>

