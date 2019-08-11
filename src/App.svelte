<script>
  import Card from "./Card.svelte";
  let weight;
  let height;
  let age;
  let gender;
  let bmi;

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

    if (weight && length && age) {
      bmi = weight / height ** height;
    }
  };
</script>

<div class="w-screen min-h-screen bg-primary antialiased">
  <div class="container mx-auto p-6">
    <h1
      class="text-yellow-500 text-center text-3xl uppercase font-bold"
      style="line-height: 0.8;">
      Bereken je
      <span class="block text-8xl">BMI</span>
    </h1>
    <Card title="Gewicht" unit="kg" on:update={updateBMI} />
  </div>
</div>
