<script>
  import Card from "./Card.svelte";
  import Result from "./Result.svelte";
  import Header from "./Header.svelte";

  let weight, height, bmi;

  const roundValue = value => Math.round(value * 10) / 10;

  const updateBMI = event => {
    const { title, value } = event.detail;

    title.toLowerCase() === "gewicht" ? (weight = value) : (height = value);

    if (weight && height && +height > 100) {
      bmi = roundValue(+weight / (+height / 100) ** 2);
    }
  };
</script>

<div class="bg-primary antialiased">
  <div class="container mx-auto p-6 mb-24">
    <Header />
    <Card title="Gewicht" unit="kg" on:update={updateBMI} />
    <Card title="Lengte" unit="cm" on:update={updateBMI} />

  </div>
  <div class="bg-light-text">
    <div class="container mx-auto p-6">
      <Result {bmi} />
    </div>
  </div>
  <div class="footer bg-footer p-6">
    <div class="container text-center mx-auto text-footer-text uppercase">
      Gemaakt door
      <a href="https://martijndorsman.nl/" rel="noopener" target="_blank">
        Martijn Dorsman
      </a>
      &copy; {new Date().getFullYear()}
    </div>
  </div>
</div>
