<script>
  var today = new Date();
  var dd = String(today.getDate()).padStart(2, "0");
  var mm = String(today.getMonth() + 1).padStart(2, "0"); //January is 0!
  var yyyy = today.getFullYear();
  const date = yyyy + "-" + dd + "-" + mm;
  console.log(date);
  var active;
  const apiKey = "SUzid8msGrSLtqAP61POz1wYTEMZNQ4XYvEjipTl";
  var url = `https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?earth_date=${date}&api_key=${apiKey}`;
  var link_array = [];
  function displaydata(data) {
    let jsonstring = JSON.stringify(data);
    const obj = JSON.parse(jsonstring);
    const photoarray = obj.photos;
    const len = Object.keys(photoarray).length;

    console.log(len);
    for (let i = 0; i < Object.keys(photoarray).length; i++) {
      
      link_array.push(photoarray[i].img_src);
      console.log(link_array);
      link_array = link_array;
      active = link_array[0];
      active = active;
      
    }
  }
  function fetchData() {
    try {
      fetch(url)
        .then((response) => response.json())
        .then((json) => {
          console.log(json);
          displaydata(json);
        });
    } catch (error) {
      console.log(error);
    }
  }
  fetchData();

  </script>
<div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-inner">
    <div class="carousel-item active">
      
      <img src="{active}" class="d-block w-100" alt="...">
      
    </div>
  {#each link_array as link}
<div class="carousel-item">
  <img src="{link}" class="d-block w-100" alt="...">
</div>
{/each}
  </div>
  <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>
</div>
