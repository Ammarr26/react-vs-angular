<template>
  <div id="app">
    <div class="background-animation">
      <div class="js-logo"></div>
      <div class="js-logo"></div>
      <div class="js-logo"></div>
      <div class="js-logo"></div>
      <div class="js-logo"></div>
      <div class="js-logo"></div>
    </div>

    <header>
      <h1>
        React <img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg" alt="React Logo" class="logo" />
        vs
        Angular <img src="https://angular.io/assets/images/logos/angular/angular.png" alt="Angular Logo" class="logo" />
      </h1>
      <nav>
        <ul>
          <li @click="currentTab = 'comparison'" :class="{ active: currentTab === 'comparison' }">Comparison</li>
        </ul>
      </nav>
    </header>

    <main>
      <div v-if="currentTab === 'comparison'">
        <h2>Comparison</h2>
        <table>
          <thead>
            <tr>
              <th>Feature</th>
              <th>React <img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg" alt="React Logo" class="logo" /></th>
              <th>Angular <img src="https://angular.io/assets/images/logos/angular/angular.png" alt="Angular Logo" class="logo" /></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(feature, index) in features" :key="index" class="feature-row">
              <td>{{ feature.name }}</td>
              <td>{{ feature.react }}</td>
              <td>{{ feature.angular }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </main>

    <footer>
      <p>By Ammar Yasser</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentTab: 'comparison',
      features: [
        { name: 'Type', react: 'Library', angular: 'Framework' },
        { name: 'Language', react: 'JavaScript (JSX)', angular: 'TypeScript' },
        { name: 'Data Binding', react: 'One-way', angular: 'Two-way' },
        { name: 'Learning Curve', react: 'Moderate', angular: 'Steep' },
        { name: 'Performance', react: 'Fast (Virtual DOM)', angular: 'Good (Real DOM)' },
        { name: 'Community', react: 'Large', angular: 'Large' },
      ],
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #000;
  color: #ffffff;
  font-family: 'Courier New', Courier, monospace;
}

#app {
  position: relative;
  text-align: center;
  padding: 20px;
}

.background-animation {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  overflow: hidden;
  pointer-events: none;
}

.js-logo {
  background-image: url('https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png');
  background-size: contain;
  background-repeat: no-repeat;
  position: absolute;
  width: 100px;
  height: 100px;
  opacity: 0.1;
  animation: moveAndFade 10s infinite;
}

.js-logo:nth-child(1) { top: 10%; left: 10%; animation-delay: 0s; }
.js-logo:nth-child(2) { top: 20%; left: 80%; animation-delay: 2s; }
.js-logo:nth-child(3) { top: 30%; left: 50%; animation-delay: 4s; }
.js-logo:nth-child(4) { top: 60%; left: 20%; animation-delay : 6s; }
.js-logo:nth-child(5) { top: 70%; left: 70%; animation-delay: 8s; }
.js-logo:nth-child(6) { top: 40%; left: 90%; animation-delay: 10s; }

@keyframes moveAndFade {
  0% {
    transform: translate(0, 0);
    opacity: 0.1;
  }
  50% {
    transform: translate(50px, 50px); 
    opacity: 0.3;
  }
  100% {
    transform: translate(0, 0);
    opacity: 0.1;
  }
}

header {
  position: relative;
  z-index: 1; 
  padding: 20px;
}

nav ul {
  list-style-type: none;
  padding: 0;
}

nav li {
  display: inline;
  margin: 0 15px;
  cursor: pointer;
  transition: color 0.3s;
}

nav li:hover, .active {
  color: #61dafb;
}

h1 {
  font-size: 2.5em;
  margin-bottom: 10px;
}

h2 {
  font-size: 2em;
  margin: 20px 0;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 20px 0;
  background-color: rgba(40, 44, 52, 0.8);
}

th, td {
  border: 1px solid #444;
  padding: 10px;
  text-align: left;
}

th {
  background-color: #444;
}

tbody tr {
  transition: background-color 0.3s, transform 0.2s, box-shadow 0.2s;
}

tbody tr:hover {
  background-color: #3a3f47;
  transform: scale(1.05);
  box-shadow: 0 4px 15px rgba(255, 255, 255, 0.2);
}

tbody tr:hover td {
  color: #61dafb;
  transition: color 0.3s;
}

footer {
  margin-top: 20px;
  font-size: 0.8em;
}

.logo {
  width: 24px;
  height: auto;
  vertical-align: middle;
  margin-left: 8px;
}
</style>