QA Portfolio: Manual & Automation Testing
https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/tuusuario/
https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github&link=https://github.com/tuusuario
https://img.shields.io/badge/-Email-c14438?style=flat-square&logo=Gmail&logoColor=white&link=mailto:tuemail@example.com

"Quality is not an act, it is a habit." – Aristotle

Bienvenido/a a mi portafolio de aseguramiento de calidad. Este repositorio centraliza todos mis proyectos de testing, demostrando mis habilidades tanto en QA Manual como en Automation Testing.

El objetivo es mostrar cómo pienso como tester: desde la identificación de casos críticos, pasando por la documentación formal de bugs, hasta la automatización de esos mismos escenarios para asegurar la no regresión.

📂 Estructura del Repositorio
text
.
├── 1_manual_testing/ # Estrategia, diseño y documentación
│ ├── test-cases/ # Casos de prueba en formato Gherkin (Given/When/Then)
│ ├── bug-reports/ # Reportes de bug (prioridad, severidad, pasos, evidencia)
│ └── checklists/ # Checklists de humo, regresión y sanity
├── 2_api_testing/ # Pruebas de backend
│ ├── postman-collection.json # Colección de Postman con tests en JS
│ └── newman-report/ # Evidencia de ejecución en HTML
├── 3_automation/ # Frameworks de automatización
│ ├── selenium-python/ # Selenium + Pytest + Page Object Model
│ ├── cypress-e2e/ # Cypress + JavaScript + Fixtures
│ └── playwright-tests/ # Playwright + TypeScript + Cross-browser
├── 4_mobile_testing/ # Appium + Python (opcional)
└── README.md # Este archivo
🖊️ 1. Manual Testing (Habilidades blandas + metodología)
En esta sección encontrarás ejemplos concretos de mi enfoque analítico. Demuestro que entiendo el ciclo de vida del testing y la estrategia de pruebas.

Proyecto: E-commerce Demo (SauceDemo / Swag Labs)
La página de práctica por excelencia para QA.

Entregables incluidos:

Plan de pruebas: Define el alcance (qué se prueba: Login, Inventario, Carrito, Checkout)

Casos de prueba: Para la funcionalidad de Login (válido, inválido, usuario bloqueado, campo vacío)

Reportes de Bug: Documentación de bugs con estructura: Prioridad | Severidad | Pasos | Resultado Esperado vs Actual

Ejemplo de caso de prueba en Gherkin:

Feature: Login
Scenario: Usuario válido puede iniciar sesión
Given el usuario está en la página de login
When ingresa el usuario "standard_user" y la contraseña "secret_sauce"
And hace clic en el botón Login
Then es redirigido al inventario
And ve el título "Products"

Ejemplo de reporte de bug:

Campo Valor
Título El carrito no se vacía después de logout
Prioridad Alta
Severidad Media
Pasos 1. Agregar item al carrito 2. Hacer logout 3. Hacer login 4. Ver carrito
Resultado Actual El item sigue en el carrito
Resultado Esperado El carrito debe estar vacío
Proyecto: APIs Públicas (PokéAPI / Reqres.in)
Demuestro que sé validar la lógica del backend y la integridad de datos.

Evidencia en Manual:

Documentación de casos de consulta (GET) y creación (POST) con capturas de pantalla de Postman

TC-01: Validar que el status code del GET /users/2 sea 200

Uso de variables de entorno en Postman para pasar un productID de un GET a un PUT

Base de Datos (Opcional)
Archivo .sql mostrando cómo verifico que los datos se guardaron:
SELECT \* FROM users WHERE email = 'test@example.com';

Carpeta Contenido Habilidad demostrada
test-cases/ Casos de prueba en formato Gherkin y tablas de decisión Diseño de pruebas, cobertura funcional
bug-reports/ Reportes de bug profesionales Comunicación efectiva, seguimiento de issues
checklists/ Checklists de humo, regresión y sanity Eficiencia, organización
Proyecto destacado: E-commerce: SauceDemo - 35 casos de prueba para el flujo de compra, incluyendo edge cases (usuario bloqueado, carrito vacío).

🔌 2. API Testing (Backend & contratos)
Demuestro que no solo pruebo la interfaz, sino también la lógica del servidor y la integridad de los datos.

Proyectos incluidos:
Proyecto Tecnología Qué incluye
PokéAPI Postman + Newman Validación de schemas, status codes, parámetros dinámicos
Restful Booker Python + Requests Suite completa de CRUD (crear, leer, actualizar, eliminar reservas)
Ejemplo de test en Postman (JavaScript):

pm.test("Status code es 200", function () {
pm.response.to.have.status(200);
});

pm.test("Response tiene usuario con ID 2", function () {
var jsonData = pm.response.json();
pm.expect(jsonData.data.id).to.eql(2);
});

Evidencia destacada: Reporte de Newman - Ejecución automatizada con resultados en HTML.

🤖 3. Automation Testing (UI & E2E)
He construido frameworks desde cero siguiendo las mejores prácticas de la industria: Page Object Model (POM), datos fixture, reportes y CI/CD.

Selenium WebDriver + Python + Pytest
Proyecto: SauceDemo Automation

Características:

POM con páginas separadas (LoginPage, InventoryPage, CheckoutPage)

Captura de pantalla automática en fallos

Reportes con Allure Framework

Ejecución en paralelo con pytest-xdist

Estructura del proyecto:

selenium-python/
├── pages/
│ ├── login_page.py
│ ├── inventory_page.py
│ └── checkout_page.py
├── tests/
│ ├── test_login.py
│ ├── test_cart.py
│ └── test_checkout.py
├── reports/
├── conftest.py
├── requirements.txt
└── pytest.ini

Ejemplo de Page Object:

class LoginPage:
def init(self, driver):
self.driver = driver
self.username_input = (By.ID, "user-name")
self.password_input = (By.ID, "password")
self.login_button = (By.ID, "login-button")

def login(self, username, password):
self.driver.find_element(self.username_input).send_keys(username)
self.driver.find_element(self.password_input).send_keys(password)
self.driver.find_element(\*self.login_button).click()

Cypress + JavaScript
Proyecto: The-Internet E2E

Características:

Fixtures para datos de prueba (users.json, products.json)

Comandos personalizados para login reutilizable

GitHub Actions configurado (CI/CD)

Ejemplo de test en Cypress:

describe('Login Test', () => {
it('should login with valid credentials', () => {
cy.visit('/login');
cy.get('#username').type('standard_user');
cy.get('#password').type('secret_sauce');
cy.get('#login-button').click();
cy.url().should('include', '/inventory');
});
});

Playwright + TypeScript (Bonus)
Proyecto: DemoBlaze Playwright

Características:

Cross-browser testing (Chromium, Firefox, WebKit)

Trazas y videos en fallos

Modo headless para CI

📱 4. Mobile Testing (Opcional - Diferencial)
Framework: Appium + Python

Proyecto: Calculadora Android (AOSP)

Casos: Suma, resta, rotación de pantalla

Ejemplo de test:

def test_addition(self):
self.driver.find_element(By.ID, "digit_2").click()
self.driver.find_element(By.ID, "op_add").click()
self.driver.find_element(By.ID, "digit_3").click()
self.driver.find_element(By.ID, "eq").click()
result = self.driver.find_element(By.ID, "result").text
assert result == "5"

⚙️ Tech Stack Resumido
Área Herramientas / Lenguajes
Manual TestRail, Jira (Xray), Confluence, Zephyr
Automation UI Selenium WebDriver, Cypress, Playwright
Automation API Postman + Newman, Python requests, REST Assured
Lenguajes Python, JavaScript, TypeScript, SQL (básico)
CI/CD GitHub Actions, Jenkins (básico)
Reporting Allure Report, Mocha reporter, Newman HTML
Control de versiones Git, GitHub
🚀 Cómo explorar este repositorio
Para reclutadores / Hiring Managers: Comienza por la carpeta 1_manual_testing/ para ver mi capacidad analítica, luego salta a 3_automation/ para evaluar mi código.

Para developers / peers: Revisa los scripts de automatización, especialmente cómo implemento POM y las aserciones.

Para curiosos: Clona el repo y ejecuta las pruebas localmente (cada subproyecto tiene su propio README.md con instrucciones).

Comandos:

git clone https://github.com/tuusuario/qa-portfolio.git
cd qa-portfolio/3_automation/selenium-python
pip install -r requirements.txt
pytest tests/ --alluredir=reports

Ejecutar pruebas de Cypress:
cd ../cypress-e2e
npm install
npx cypress run

Ejecutar pruebas de API con Newman:
cd ../../2_api_testing
newman run postman-collection.json -e environment.json --reporters html

📈 Mi filosofía de testing
No basta con encontrar bugs; hay que prevenirlos y comunicarlos de forma que el equipo los entienda y los priorice.

Cobertura vs. Calidad: Prefiero 20 casos bien diseñados que 200 casos redundantes.

Manual vs. Automatización: Automatizo lo repetitivo, valido manualmente lo exploratorio.

Colaboración: Mis reportes de bug siempre incluyen: Pasos, Resultado Actual, Esperado, Evidencia y Contexto.

📫 Contacto
¿Quieres hablar sobre una oportunidad, colaborar en un proyecto o darme feedback? Escríbeme.

LinkedIn: https://www.linkedin.com/in/tuusuario/

Email: tuemail@example.com

GitHub: https://github.com/tuusuario

📝 Actualizaciones
Fecha Cambio
Marzo 2026 Versión inicial del portfolio
Próximamente Agregar pruebas de performance con JMeter
Próximamente Integración con Jenkins
