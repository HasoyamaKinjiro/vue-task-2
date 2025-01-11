<template>
  <main class="home">
    <section class="hero">
      <h1>Welcome to Test Task!</h1>
      <p>Your go-to app for all your needs.</p>
    </section>

    <section class="features">
      <h2>Our Features</h2>
      <div class="feature-list">
        <div class="feature-item">
          <h3>Feature One</h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam sed sapien nec felis luctus aliquet.</p>
        </div>
        <div class="feature-item">
          <h3>Feature Two</h3>
          <p>Suspendisse potenti. Ut id mi quis lectus tincidunt faucibus ac id orci. Vivamus a magna vel purus tempor.</p>
        </div>
        <div class="feature-item">
          <h3>Feature Three</h3>
          <p>Aliquam erat volutpat. Sed posuere lacus sed sapien tristique, et fermentum erat efficitur.</p>
        </div>
      </div>
    </section>

    <section class="cta">
      <h2>Have questions?</h2>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Take the first step towards a better experience.</p>
      <RouterLink to="/contact-us" class="button-cta">Contact Us</RouterLink>
    </section>
  </main>
</template>

<style scoped>
.home {
  font-family: Arial, sans-serif;
  padding: 2rem;
}

.hero {
  background: var(--green-bg-1);
  padding: 2rem;
  border-radius: 8px;
  margin-bottom: 2rem;
  text-align: center;
}

.hero h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.features {
  margin-bottom: 2rem;
}

.features h2 {
  text-align: center;
  margin-bottom: 1rem;
}

.feature-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

.feature-item {
  background: var(--green-bg-1);
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
}

.feature-item h3 {
  margin-bottom: 0.5rem;
}

.cta {
  background: var(--green-bg-1);
  padding: 2rem;
  border-radius: 8px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.cta h2 {
  font-size: 1.5rem;
}

.button-cta {
  width: fit-content;
  padding: 0.5rem 1rem;
  font-size: 1rem;
  background-color: #28a745;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.button-cta:hover {
  background-color: #218838;
}
</style>
