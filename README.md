# 🤖 Projeto de Automação com WebdriverIO e Cucumber

Este repositório contém um projeto de estudos em **automação de testes end-to-end** utilizando **WebdriverIO** com o framework **Cucumber**.

---

## 📁 Estrutura de Pastas

├── features/

│ ├── step-definitions/

│ │ └── google.steps.js

│ └── google.feature

├── pageobjects/

│ └── googlepage.js

├── wdio.conf.js

├── package.json

└── README.md


---

## 🧩 O que faz cada parte

| Arquivo                        | Função                                                                 |
|-------------------------------|------------------------------------------------------------------------|
| `googlepage.js`               | Mapeia os elementos da página e define métodos de interação.          |
| `google.steps.js`             | Liga os passos do Gherkin aos métodos do Page Object.                 |
| `google.feature`              | Especificação dos testes em linguagem Gherkin (Given, When, Then).    |
| `wdio.conf.js`                | Arquivo de configuração do WebdriverIO.                               |

---

## 🔍 Exemplo: Page Object (`googlepage.js`)

```js
class GooglePage {
    get campoBusca() {
        return $('input[name="q"]');
    }

    async abrir() {
        await browser.url('https://www.google.com');
    }

    async buscar(termo) {
        await this.campoBusca.waitForExist({ timeout: 5000 });
        await this.campoBusca.setValue(termo);
        await browser.keys('Enter');
    }
}

module.exports = new GooglePage();
