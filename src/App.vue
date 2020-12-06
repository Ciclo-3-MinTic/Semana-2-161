<template>
  <div id="app">
  </div>
</template>

<script>

export default {
  name: 'App',
 
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

