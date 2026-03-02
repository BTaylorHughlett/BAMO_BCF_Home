<template>
  <!-- ===== Top Navigation ===== -->
  <header class="site-header">
    <div class="container nav">
      <a class="brand" href="#" aria-label="Brewers Community Foundation home">
        <img src="assets/logo.svg" alt="Brewers Community Foundation logo" />
      </a>

      <button id="menuBtn" class="btn btn-menu" aria-controls="primary-nav" aria-expanded="false">
        ☰
      </button>

      <nav id="primary-nav" class="nav-links" aria-label="Primary">
        <a href="#about">About Us</a>
        <a href="#programs">Programs</a>
        <a href="#help">How to Help</a>
        <a href="#news">News</a>
        <a href="#contact">Contact</a>
      </nav>

      <div class="search-and-cta">
        <form role="search" class="search" aria-label="Site search" onsubmit="return false;">
          <label for="q" class="sr-only">Search</label>
          <input id="q" name="q" type="search" placeholder="Search…" />
          <button type="button" class="btn btn-search" id="searchBtn">Search</button>
        </form>
        <a href="#donate" class="btn btn-donate">Donate Now</a>
      </div>
    </div>
  </header>

  <main>
    <!-- ===== Hero ===== -->
    <section class="hero" aria-label="Foundation overview">
      <img class="hero-bg" src="assets/hero.jpg" alt="" />
      <div class="hero-overlay"></div>
      <div class="container hero-inner">
        <h1>Brewers Community Foundation</h1>

        <!-- Testimonials row -->
        <div class="testimonials">
          <article class="t-card">
            <a href="#story-1" class="t-link">
              <img src="assets/testimonial-1.jpg" alt="Community story 1" />
              <blockquote>“Thank you for changing my life.”</blockquote>
            </a>
          </article>
          <article class="t-card">
            <a href="#story-2" class="t-link">
              <img src="assets/testimonial-2.jpg" alt="Community story 2" />
              <blockquote>“This support means everything to us.”</blockquote>
            </a>
          </article>
          <article class="t-card">
            <a href="#story-3" class="t-link">
              <img src="assets/testimonial-3.jpg" alt="Community story 3" />
              <blockquote>“Brewers Community Foundation gave us hope.”</blockquote>
            </a>
          </article>
        </div>
      </div>
    </section>

    <!-- ===== History / Mission ===== -->
    <section class="history" id="about">
      <div class="container">
        <h2>History of Brewers Community Foundation</h2>
        <p>
          The Brewers Community Foundation has been dedicated to making a difference since 2008.
          Our mission is to provide support and resources to those in need. Through generosity,
          we have been able to touch countless lives, offering hope, healing, and opportunities
          for a better future.
        </p>
      </div>
    </section>

    <!-- ===== Action Grid ===== -->
    <section class="action-grid">
      <div class="container grid">
        <!-- Impact Tracker -->
        <article class="card impact" aria-labelledby="impact-title">
          <h3 id="impact-title">Donation Impact Tracker</h3>
          <ul class="impact-list">
            <li><span class="impact-number" id="familiesHelped">3245</span> Families Helped</li>
            <li><span class="impact-number" id="scholarships">785</span> Scholarships Awarded</li>
            <li><span class="impact-number" id="procedures">597</span> Funded Procedures</li>
          </ul>
          <div class="small-note">Powered by our internal data API</div>
        </article>

        <!-- How to Donate -->
        <article class="card donate" id="donate" aria-labelledby="donate-title">
          <h3 id="donate-title">How to Donate</h3>
          <p>Make a secure online donation or mail a check to:</p>
          <address>
            Brewers Community Foundation<br />
            P.O. Box 1234<br />
            City Base: 1234, City, ST 56789
          </address>
          <div class="donate-actions">
            <a href="#make-donation" class="btn btn-primary" id="donateBtn">Make a Donation</a>
            <a href="#volunteer" class="btn btn-secondary">Volunteer Your Time</a>
          </div>
        </article>

        <!-- Fundraiser CTA -->
        <article class="card fundraiser" aria-labelledby="fundraiser-title">
          <h3 id="fundraiser-title">Join us for our upcoming Color Run fundraiser!</h3>
          <p>Register today and help support youth programs across our community.</p>
          <a href="#fundraiser" class="btn btn-primary" id="fundraiserBtn">Learn More</a>
        </article>

        <!-- Find Help -->
        <article class="card help" id="help" aria-labelledby="help-title">
          <h3 id="help-title">Find Help Near You</h3>
          <ul class="link-list">
            <li><a href="#milwaukee-foundation">Milwaukee Foundation</a></li>
            <li><a href="#madison-foundation">Madison Foundation</a></li>
            <li><a href="#green-bay-foundation">Green Bay Foundation</a></li>
          </ul>
        </article>

        <!-- Game Score -->
        <article class="card scoreboard" aria-labelledby="score-title">
          <h3 id="score-title">Brewers Game Score</h3>
          <div class="score-row">
            <span class="team">MIL</span>
            <span class="score" id="scoreMil">5 1 1 0 0 7</span>
          </div>
          <div class="score-row">
            <span class="team">CHC</span>
            <span class="score" id="scoreChc">3 0 0 1 2 3</span>
          </div>
          <div class="score-banner" id="scoreBanner">Brewers Win!</div>
          <button class="btn btn-secondary btn-small" id="refreshScore">Refresh Score</button>
        </article>
      </div>
    </section>
  </main>

  <footer class="site-footer" id="contact">
    <div class="container footer-inner">
      <small>© <span id="year"></span> Brewers Community Foundation. All rights reserved.</small>
      <nav class="footer-nav" aria-label="Footer">
        <a href="#privacy">Privacy</a>
        <a href="#terms">Terms</a>
        <a href="#accessibility">Accessibility</a>
      </nav>
    </div>
  </footer>

</template>

<script setup>
// Mobile menu
import { onMounted } from 'vue';

onMounted(() => {
  const menuBtn = document.getElementById('menuBtn');
  const primaryNav = document.getElementById('primary-nav');
  menuBtn?.addEventListener('click', () => {
    const isOpen = primaryNav.classList.toggle('open');
    menuBtn.setAttribute('aria-expanded', String(isOpen));
  });

  // Search (demo)
  document.getElementById('searchBtn')?.addEventListener('click', () => {
    const q = (document.getElementById('q')?.value || '').trim();
    if (!q) {
      alert('Enter a search term.');
    } else {
      alert(`Searching for: ${q}`);
    }
  });

  // Donate (demo)
  document.getElementById('donateBtn')?.addEventListener('click', (e) => {
    e.preventDefault();
    window.location.href = 'https://example.org/donate';
  });

  // Fundraiser CTA (demo)
  document.getElementById('fundraiserBtn')?.addEventListener('click', (e) => {
    e.preventDefault();
    alert('Fundraiser details');
  });

  // Set current year
  document.getElementById('year').textContent = new Date().getFullYear();

  // Example score update
  document.getElementById('refreshScore')?.addEventListener('click', () => {
    alert('Score refreshed (demo only)');
  });
});
</script>

<style>
@import './style.css';
</style>