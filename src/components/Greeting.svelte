<script>
  let greeting = "Welcome to my website!";
  let subtext = "Thanks for visiting!";
</script>

<div class="banner">
  <h1>{greeting}</h1>
  <p>{subtext}</p>
</div>

<style>
  .banner {
    background: linear-gradient(to right, #4a00e0, #8e2de2);
    color: white;
    padding: 2rem;
    border-radius: 0.5rem;
    text-align: center;
    margin: 1rem 0;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  h1 {
    margin: 0 0 0.5rem 0;
    font-size: 2rem;
  }

  p {
    margin: 0;
    font-size: 1.2rem;
    opacity: 0.9;
  }
</style>