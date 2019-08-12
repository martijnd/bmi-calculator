<script>
  export let bmi = "&nbsp;";
  let color = "green";

  const subtitles = {
    blank: "Vul je gegevens in!",
    purple: "Je bent veel te licht voor je lengte",
    blue: "Je bent te licht voor je lengte",
    green: "Je gewicht past goed bij je lengte",
    orange: "Je bent te zwaar voor je lengte",
    red: "Je bent veel te zwaar voor je lengte"
  };

  const descriptions = {
    blank:
      "Wanneer je je gewicht en lengte invult, krijg je hier informatie te zien!",
    purple:
      "Daardoor bestaat de kans dat je een tekort aan voedingsstoffen krijgt. Neem contact op met je huisarts om de mogelijke oorzaak vast te stellen.",
    blue:
      "Daardoor bestaat de kans dat je een tekort aan voedingsstoffen krijgt. Zorg er in ieder geval voor dat je niet verder afvalt. ",
    green:
      "Houden zo! Met een gezond gewicht heb je een kleinere kans op bepaalde ziekten, dan als je te zwaar of te licht bent.",
    orange:
      "Met een lager, gezond gewicht heb je een kleinere kans op bepaalde ziekten. Zorg er in ieder geval voor dat je niet verder aankomt en probeer iets af te vallen.",
    red:
      "Daardoor heb je een veel grotere kans op bepaalde ziekten, dan mensen van dezelfde leeftijd met een lager, gezond gewicht."
  };

  const classNames = {
    green: "text-theme-green",
    orange: "text-theme-orange",
    red: "text-theme-red"
  };

  const getWeightValues = bmi => {
    switch (true) {
      case bmi < 25:
        return "green";
      case bmi < 30:
        return "orange";
      case bmi > 30:
        return "red";
      default:
        return "blank";
    }
  };

  $: classes = `${classNames[getWeightValues(bmi)]} font-bold text-6xl`;
</script>

<div
  class="Result relative -mt-24 mx-auto bg-primary-dark text-center max-w-xs
  rounded-lg">
  <div class="top p-6 relative z-10">
    <h2 class="text-3xl text-primary font-bold">Jouw BMI is</h2>
    <hr class="mt-6 border-primary w-12" />
    <span class={classes}>
      {@html bmi}
    </span>
    <div class="subtitle mt-2 text-light-text font-bold">
      {subtitles[getWeightValues(bmi)]}
    </div>
  </div>
  <div
    class="bottom relative bg-primary text-light-text p-8 italic text-lg
    font-light rounded-b-lg z-0 overflow-hidden">
    {descriptions[getWeightValues(bmi)]}
    <img class="absolute -top-6px left-1" src="quote.svg" alt="quote" />
  </div>
  <a
    href="https://www.berekenen.nl/bmi#algemeen"
    rel="noopener"
    class="absolute -bottom-10px inset-x-0 py-2 text-sm bg-primary-dark mx-4
    text-light-text rounded-lg">
    Meer over gezond gewicht
    <img src="launch.svg" alt="launch" class="inline" />
  </a>
</div>
