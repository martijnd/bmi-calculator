<script>
  import Card from "./Card.svelte";
  import Result from "./Result.svelte";

  let weight;
  let height;
  let age;
  let gender;
  let bmi;

  const roundValue = value => {
    return Math.round(value * 10) / 10;
  };

  const updateBMI = event => {
    const { title, data } = event.detail;

    switch (title.toLowerCase()) {
      case "gewicht":
        weight = data;
        break;
      case "leeftijd":
        age = data;
        break;
      case "lengte":
        height = data;
        break;
      case "geslacht":
        gender = data;
      default:
        console.error("wrong data type returned: ", event);
        break;
    }

    if (weight && height && +height > 100) {
      bmi = roundValue(+weight / (+height / 100) ** 2);
    }
  };
</script>

<div class="w-screen bg-primary antialiased">
  <div class="container mx-auto p-6 mb-24">
    <h1
      class="text-yellow-500 text-center text-3xl uppercase font-bold"
      style="line-height: 0.8;">
      Bereken je
      <span class="block text-8xl">BMI</span>
    </h1>
    <Card title="Gewicht" unit="kg" on:update={updateBMI} />
    <Card title="Lengte" unit="cm" on:update={updateBMI} />
    <Card title="Leeftijd" unit="jaar" on:update={updateBMI} />

  </div>
  <div class="w-screen bg-light-text">
    <div class="container mx-auto p-6">
      <Result {bmi} />
    </div>
  </div>
  <span class="text-theme-red text-theme-orange text-theme-green" />
</div>
