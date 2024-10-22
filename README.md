# Pirulug PMA Theme

en el head `templates\header.twig` antes del `</head>`

```html
 <script>
  (function () {
    const storedTheme = localStorage.getItem('theme');
    const prefersDarkScheme = window.matchMedia('(prefers-color-scheme: dark)').matches;
    const theme = storedTheme || (prefersDarkScheme ? 'dark' : 'light');
    document.documentElement.setAttribute('data-bs-theme', theme);
  })();
</script>
```

en el footer `templates\footer.twig` antes del `</body>`

```html
<!-- Dark & Ligth-->
<div class="dropdown position-fixed bottom-0 end-0 mb-3 me-3 bd-mode-toggle z-99">
  <button class="btn btn-primary py-2 dropdown-toggle d-flex align-items-center" id="bd-theme" type="button" aria-expanded="false" data-bs-toggle="dropdown" aria-label="Toggle theme (auto)"><span class="theme-icon-active mr-1" id="bd-theme-icon"><i class="fa fa-sun"></i></span><span class="visually-hidden" id="bd-theme-text">Toggle theme</span></button>
  <ul class="dropdown-menu dropdown-menu-end shadow" aria-labelledby="bd-theme-text">
    <li>
      <button class="dropdown-item d-flex align-items-center" type="button" data-bs-theme-value="light" aria-pressed="false">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="me-1"><circle cx="12" cy="12" r="5"></circle><line x1="12" y1="1" x2="12" y2="3"></line><line x1="12" y1="21" x2="12" y2="23"></line><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line><line x1="1" y1="12" x2="3" y2="12"></line><line x1="21" y1="12" x2="23" y2="12"></line><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line></svg>
        Light
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="pr-check ms-auto d-none"><polyline points="20 6 9 17 4 12"></polyline></svg>
      </button>
    </li>
    <li>
      <button class="dropdown-item d-flex align-items-center" type="button" data-bs-theme-value="dark" aria-pressed="false">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="me-1"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path></svg>
        Dark
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="pr-check ms-auto d-none"><polyline points="20 6 9 17 4 12"></polyline></svg>
      </button>
    </li>
    <li>
      <button class="dropdown-item d-flex align-items-center" type="button" data-bs-theme-value="auto" aria-pressed="true">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="me-1"><path d="M5 17H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2h-1"></path><polygon points="12 15 17 21 7 21 12 15"></polygon></svg>
        Auto
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="pr-check ms-auto d-none"><polyline points="20 6 9 17 4 12"></polyline></svg>
      </button>
    </li>
  </ul>
</div>

<script>
  (() => {
    "use strict";

    const storedTheme = localStorage.getItem("theme");

    const getPreferredTheme = () => {
      if (storedTheme) {
        return storedTheme;
      }

      return window.matchMedia("(prefers-color-scheme: dark)").matches
        ? "dark"
        : "light";
    };

    const setTheme = function (theme) {
      if (
        theme === "auto" &&
        window.matchMedia("(prefers-color-scheme: dark)").matches
      ) {
        document.documentElement.setAttribute("data-bs-theme", "dark");
      } else {
        document.documentElement.setAttribute("data-bs-theme", theme);
      }
    };

    setTheme(getPreferredTheme());

    const showActiveTheme = (theme) => {
      const activeThemeIcon = document.querySelector(".theme-icon-active");
      const btnToActive = document.querySelector(
        `[data-bs-theme-value="${theme}"]`
      );

      document.querySelectorAll("[data-bs-theme-value]").forEach((element) => {
        element.classList.remove("active");
      });

      btnToActive.classList.add("active");
      activeThemeIcon.innerHTML = btnToActive.innerHTML;
    };

    const updateThemeIcon = (theme) => {
      const themeIcon = document.querySelector("#bd-theme .theme-icon-active");

      if (theme === "light") {
        themeIcon.innerHTML = '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="5"></circle><line x1="12" y1="1" x2="12" y2="3"></line><line x1="12" y1="21" x2="12" y2="23"></line><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line><line x1="1" y1="12" x2="3" y2="12"></line><line x1="21" y1="12" x2="23" y2="12"></line><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line></svg>';
      } else if (theme === "dark") {
        themeIcon.innerHTML = '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" ><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path></svg>';
      } else {
        themeIcon.innerHTML = '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" ><path d="M5 17H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2h-1"></path><polygon points="12 15 17 21 7 21 12 15"></polygon></svg>';
      }
    };

    window.addEventListener("DOMContentLoaded", () => {
      showActiveTheme(getPreferredTheme());
      updateThemeIcon(getPreferredTheme());

      document.querySelectorAll("[data-bs-theme-value]").forEach((toggle) => {
        toggle.addEventListener("click", () => {
          const theme = toggle.getAttribute("data-bs-theme-value");
          localStorage.setItem("theme", theme);
          setTheme(theme);
          showActiveTheme(theme);
          updateThemeIcon(theme);
        });
      });
    });
  })();
</script>
```


```html
<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="pr-check ms-auto d-none"><polyline points="20 6 9 17 4 12"></polyline></svg>
```