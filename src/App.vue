<template>
  <div class="bgo">
    
    <div id="seccion2" class="mt-5 pb-2 px-4 p-2 ">
      <div
        id="carouselExampleCaptions"
        class="carousel slide row"
        data-ride="carousel"
      >
        <ol class="carousel-indicators">
          <li
            data-target="#carouselExampleCaptions"
            data-slide-to="0"
            class="active"
          ></li>
          <li
            v-for="index in this.sizeDataImg"
            :key="index"
            data-target="#carouselExampleCaptions"
            :data-slide-to="index"
          ></li>
        </ol>
        <div class="row justify-content-center">
          <div class="carousel-inner justify-content-center">
            <img-carousel
              
              :img="dataImg[0].webformatURL"
              
              :img2="dataImg[1].webformatURL"
              active="active"
            >
            </img-carousel>
            <img-carousel
              v-for="index in this.sizeDataImg"
              :key="index"
              
              :img="dataImg[index].webformatURL"
              
              :img2="dataImg[index+1].webformatURL"
              active=" "
            >
            </img-carousel>
          </div>
        </div>

        <a
          class="carousel-control-prev"
          href="#carouselExampleCaptions"
          role="button"
          data-slide="prev"
        >
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="sr-only">Previous</span>
        </a>
        <a
          class="carousel-control-next"
          href="#carouselExampleCaptions"
          role="button"
          data-slide="next"
        >
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="sr-only">Next</span>
        </a>
      </div>
    </div>
    
    
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
    <div id="seccion4" class="row justify-content-center pt-5 px-3">
      <team-card
        v-for="(inte, index) in this.datateam"
        :key="index"
        :member="inte"
      >
      </team-card>
    </div>
  </div>
</template>

<script>
import TeamCard from "./components/TeamCard";
import DataTeam from "./assets/team.json";
import BooksApi from "./components/BooksApi";
import ImgCarousel from "./components/ImgCarousel";

export default {
  name: "App",

  data() {
    return {
      dataText: [],
      dataImg: [],
      sizeDataImg: [],
      datateam: DataTeam,
    };
  },

  components: {
    BooksApi,
    TeamCard,
    ImgCarousel,
  },

  async mounted() {
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
      const resultImages = await fetch(urlText, {
        method: "GET",
      });

      const resultImg = await resultImages.json();
      
      if (resultImg.hits.length > 0) {
        this.dataImg = resultImg.hits;
        for (var j = 0; j < this.dataImg.length; j++) {
          if (this.dataImg[j].webformatHeight < 420 ) {
            this.dataImg.splice(j, 1);
          }
        }
          console.log(this.dataImg)


        for (var i = 1; i < this.dataImg.length - 4; i++){

          this.sizeDataImg.push(i);
        }
      }
     
    };

    await getNews();

    await getImgHead();
  },
};
</script>
<style >
.bgo{
 background-color: rgba(163, 163, 163,0.7);
}
</style>

