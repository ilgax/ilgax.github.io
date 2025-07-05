<script>
  import { onMount } from 'svelte';

  let isDark = false;
  let mounted = false;

  // Initialize theme on component mount
  onMount(() => {
    // Get theme from localStorage or system preference
    const theme = (() => {
      const localStorageTheme = localStorage?.getItem("theme") ?? '';
      if (['dark', 'light'].includes(localStorageTheme)) {
        return localStorageTheme;
      }
      if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
        return 'dark';
      }
      return 'dark';
    })();

    isDark = theme === 'dark';

    if (theme === 'light') {
      document.documentElement.classList.remove('dark');
    } else {
      document.documentElement.classList.add('dark');
    }

    window.localStorage.setItem('theme', theme);

    mounted = true;
  });

  function toggleTheme() {
    isDark = !isDark;
    const element = document.documentElement;

    if (isDark) {
      element.classList.add("dark");
    } else {
      element.classList.remove("dark");
    }

    localStorage.setItem("theme", isDark ? "dark" : "light");
  }
</script>

<button id="themeToggle" on:click={toggleTheme} aria-label="Toggle theme">

</button>

<style>
  button {
    all: unset;

    cursor: pointer;
    margin-left: 1em;
    width: 1.2em;
    height: 1.2em;
    background-repeat: no-repeat;
    background-size: cover;

    transition: transform 0.12s linear;
  }

  button {
    background-image: url(/assets/sun.svg);
    filter: brightness(0%) saturate(100%) invert(100%);
  }

  :global(:not(.dark)) button {
    background-image: url(/assets/moon.svg);
    filter: brightness(0%) saturate(100%);
  }

  button:hover,
  button:focus {
    transform: scale(1.2);
    outline: none;
  }

  button:focus:not(:hover)::after {
    position: absolute;
    content: "";
    height: 1px;
    bottom: -4px;
    width: 100%;
    background: var(--color);
    transform: scale(1.2);
  }
</style>
