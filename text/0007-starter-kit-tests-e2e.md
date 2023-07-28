- Date de début : 28/07/2023
- Version majeure cible : Design System v3
- PR d'implémentation : N/A

## Résumé

Cette RFC propose l'utilisation de [Playwright][Playwright] pour mettre en place des tests end-to-end (e2e) pour le Starter Kit Vue, en remplacement de Cypress.
Playwright est une bibliothèque de test moderne qui permet de simuler des actions utilisateur et des interactions avec une application web, dans le but de s'assurer que l'application fonctionne correctement et que les fonctionnalités sont conformes aux attentes.

## Motivation

Les tests e2e sont essentiels pour s'assurer du bon fonctionnement d'une application web. Ils permettent de détecter rapidement les erreurs et les anomalies, et de s'assurer que les fonctionnalités sont conformes aux attentes des utilisateurs. Cependant, la mise en place de tests e2e peut être complexe et fastidieuse.

Cypress est une bibliothèque de test populaire pour les tests e2e dans les applications web. Cependant, Playwright offre des fonctionnalités plus avancées que Cypress, tels que la prise en charge des navigateurs multiplateformes, la possibilité de capturer des captures d'écran et des vidéos des tests, et la capacité de simuler des interactions utilisateur plus complexes.

Playwright semble être un choix naturel pour les tests e2e dans le Starter Kit Vue, car il est plus moderne et plus avancé que Cypress.

## Conception détaillée

Playwright sera utilisé par défaut sur les nouveaux projets pour mettre en place des tests e2e.
Pour les projets existants, les utilisateurs devront [installer Playwright][yarn create playwright].

Par exemple, pour créer un test e2e qui vérifie que la page d'accueil de l'application est accessible et contient un titre spécifique, on peut écrire le code suivant :

```js
const { chromium } = require("playwright");

describe("Home page", () => {
  let browser;
  let page;

  beforeAll(async () => {
    browser = await chromium.launch();
    page = await browser.newPage();
  });

  afterAll(async () => {
    await browser.close();
  });

  test("should display the correct title", async () => {
    await page.goto("http://localhost:3000");
    const pageTitle = await page.title();
    expect(pageTitle).toBe("My title");
  });
});
```

Ce test utilise la méthode goto pour accéder à la page d'accueil de l'application, puis vérifie que le titre de la page correspond à la valeur attendue.

## Désavantages

L'utilisation de Playwright pour les tests e2e peut présenter certains désavantages.

Tout d'abord, les tests e2e peuvent être lents à s'exécuter, en particulier si l'application est complexe et contient de nombreuses fonctionnalités.

De plus, les tests e2e peuvent être fragiles et nécessiter des mises à jour fréquentes en cas de changements dans l'application.

Enfin, le remplacement de Cypress par Playwright peut nécessiter une certaine courbe d'apprentissage pour les développeurs qui sont habitués à utiliser Cypress.

## Alternatives

D'autres alternatives existent comme [TestCafé][TestCafé] ou [Puppeteer][Puppeteer] mais elles ne semblent pas être aussi intéressantes que Playwright.

## Stratégie d'adoption

Pour adopter Playwright dans un projet existant, il est recommandé de commencer par la mise en place de tests pour les fonctionnalités les plus critiques, en parallèle avec les tests existants écrits avec Cypress.

Les tests e2e peuvent être intégrés dans un pipeline de CI/CD pour s'assurer que l'application fonctionne correctement avant chaque déploiement. Les développeurs peuvent également utiliser Playwright pour effectuer des tests de régression après des modifications importantes de l'application.

Une fois que les développeurs sont à l'aise avec Playwright, il est possible de remplacer progressivement les tests existants écrits avec Cypress par des tests écrits avec Playwright.

[Playwright]: https://playwright.dev/
[Cypress]: https://www.cypress.io/
[TestCafé]: https://devexpress.github.io/testcafe/
[Puppeteer]: https://pptr.dev/
