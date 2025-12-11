<script setup lang="ts">
// No script needed for static footer
</script>

<template>
  <footer class="footer">
    <div class="footer-container">
      <div class="footer-top">
        <div class="links-section">
          <div class="link-column">
            <h3>Produits</h3>
            <ul>
              <li><a href="p">Analyse video</a></li>
              <li><a href="p">Tracking</a></li>
              <li><a href="p">Statistique</a></li>
            </ul>
          </div>
          <div class="link-column">
            <h3>Entreprise</h3>
            <ul>
              <li><a href="p">Notre vision</a></li>
              <li><a href="p">Press</a></li>
              <li><a href="p">Recrutement</a></li>
              <li><a href="p">Contact</a></li>
            </ul>
          </div>
          <div class="link-column">
            <h3>Ressource</h3>
            <ul>
              <li><a href="p">Centre aide</a></li>
              <li><a href="p">SAV</a></li>
              <li><a href="p">Contact</a></li>
              <li><a href="p">FAQ</a></li>
            </ul>
          </div>
        </div>

        <div class="info-section">
          <p class="copyright">2025 Pitchline. Tous droit réservés.</p>
          <div class="social-icons">
            <!-- TikTok -->
            <a href="#" class="social-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"/></svg>
            </a>
            <!-- Instagram -->
            <a href="#" class="social-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
            </a>
            <!-- YouTube -->
            <a href="#" class="social-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22.54 6.42a2.78 2.78 0 0 0-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 0 0-1.94 2A29 29 0 0 0 1 11.75a29 29 0 0 0 .46 5.33A2.78 2.78 0 0 0 3.4 19c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 0 0 1.94-2 29 29 0 0 0 .46-5.25 29 29 0 0 0-.46-5.33z"/><polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02"/></svg>
            </a>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <img src="~/assets/img/Footer.svg" alt="Pitchline" class="footer-logo" />
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #000;
  color: #fff;
  border-top-left-radius: 40px;
  border-top-right-radius: 40px;
  padding: 60px 40px 20px 40px;
  font-family: sans-serif;
  margin-top: auto;
}

.footer-container {
  max-width: 1400px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 0px;
}

.footer-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
  gap: 40px;
}

.links-section {
  display: flex;
  gap: 60px;
  flex-wrap: wrap;
}

.link-column h3 {
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 20px;
  color: #fff;
}

.link-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.link-column ul li {
  margin-bottom: 12px;
}

.link-column ul li a {
  color: #9ca3af; /* Gray-400 */
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.2s;
}

.link-column ul li a:hover {
  color: #fff;
}

.info-section {
  text-align: right;
  display: flex;
  flex-direction: column;
  gap: 15px;
  align-items: flex-end;
}

.copyright {
  color: #9ca3af;
  font-size: 0.9rem;
}

.social-icons {
  display: flex;
  gap: 15px;
}

.social-icon {
  color: #9ca3af;
  transition: color 0.2s;
}

.social-icon:hover {
  color: #fff;
}

.footer-bottom {    
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.footer-logo {
  width: 100%;
  height: auto;
  display: block;
}

@media (max-width: 768px) {
  .footer {
    padding: 40px 20px;
    border-radius: 24px 24px 0 0;
  }

  .footer-top {
    flex-direction: column;
    gap: 40px;
  }
  
  .links-section {
    gap: 30px;
    width: 100%;
    justify-content: flex-start;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  .info-section {
    align-items: flex-start;
    text-align: left;
    width: 100%;
  }
}

@media (max-width: 480px) {
  .links-section {
    grid-template-columns: 1fr;
    gap: 24px;
  }
}
</style>
