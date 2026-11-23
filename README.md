# Hi, I'm Fabricio Sanjines 👋

QA Automation Engineer from La Paz, Bolivia, with 7+ years of experience testing SaaS applications across the web UI and API layers. I build test automation frameworks that are reliable, easy to maintain and run in CI, and I use AI tools every day to speed up testing. Before QA, I worked at the Bolivian Stock Exchange, where I tested trading calculations, which is where my interest in fintech comes from.

## 🛠️ Technical skills

- **Web Automation:** Playwright (headless), Selenium, TestCafe, Chrome DevTools, CSS selectors, XPath
- **HTTP & APIs:** REST, GraphQL (Apollo), Postman, Jest; headers, cookies, sessions, auth (SSO)
- **Scraping:** Scrapy, httpx, parsel / BeautifulSoup, scrapy-playwright, proxy rotation, Redis, Kafka
- **Programming:** Python, TypeScript/JavaScript, Bash, HTML/CSS/DOM, SQL
- **Data & Databases:** MySQL, JSON and CSV processing, data validation, data integrity, database-to-UI validation
- **DevOps & Tools:** Docker (Compose), Kubernetes, AWS, Git, GitHub Actions (CI/CD), Jira, Azure DevOps, Allure
- **Performance:** JMeter, InfluxDB, Grafana
- **AI / Productivity:** Claude, AI-assisted testing and test automation

## 🧪 Projects

### [PlaywrightProject](https://github.com/fabricio159/PlaywrightProject)
A Playwright framework that tests the [Swag Labs](https://www.saucedemo.com/) demo store and a REST API from one codebase. The same UI scenarios (login, products and cart) are written three ways, to compare the approaches side by side:

- **Playwright Test**, with the Page Object Model and custom fixtures
- **BDD with playwright-bdd**, which turns Gherkin `.feature` files into Playwright specs
- **BDD with Cucumber**, kept in its own package with its own config, because the two BDD libraries can't share one setup


### [PracticeDataExt](https://github.com/fabricio159/PracticeDataExt)
A small Python framework for HTTP data extraction, built on [httpx](https://www.python-httpx.org/) (with HTTP/2) and [parsel](https://parsel.readthedocs.io/) f
or HTML parsing.

- **`week01_http.client`**: the core. `create_client()` returns an `httpx.Client` with browser-like headers, timeouts and redirect handling. `fetch()`, `get()`
 and `post()` retry network errors and retryable status codes (429, 5xx) with exponential backoff plus jitter, follow `Retry-After`, and only retry non-idempot
ent methods (POST, PATCH) when asked to. When every attempt fails they raise `FetchError`.
- **`week01_http.login`**: a CSRF-token login flow for quotes.toscrape.com.
- **`week01_http.scrape`**: logs in, scrapes quote pages into structured records, and writes `quotes.json`.
- **`week01_http.status_probe`**: shows how the client reacts to different HTTP status codes.

### [JmeterProject](https://github.com/fabricio159/JmeterProject)
Performance testing with Apache JMeter, with a real-time monitoring stack. It includes test plans that cover:

- **Basic HTTP load tests** with thread groups, loop controllers and response assertions
- **Correlation:** extracting an auth token from a login response with a JSON Extractor and reusing it in later authenticated requests
- **Data-driven tests:** logging in many users read from a CSV file with CSV Data Set Config
- **Recorded user flows** using JMeter's HTTP(S) Test Script Recorder, such as a flight booking flow and the Swag Labs site, with cookie, cache and header managers and think-time timers

Results stream live through a Backend Listener to **InfluxDB**, and are shown on a **Grafana** dashboard. Both run with **Docker Compose**, and the data source and dashboard are set up automatically through provisioning files. The repo also includes my own JMeter course notes, from fundamentals to CLI runs, distributed testing and CI/CD.

### [SeleniumProject](https://github.com/fabricio159/SeleniumProject)
UI test automation with Selenium WebDriver and pytest, written in Python against the Swag Labs demo site (saucedemo.com). It's built on the **Page Object Model**:

- **Page objects:** a `BasePage` holds shared actions (find, click, type, read text) that use explicit waits, and the login and inventory pages build on it
- **Login tests:** a standard user logs in successfully, a locked-out user is blocked with an error message, and a slow "performance glitch" user still logs in within the timeout
- **Cross-browser runs:** a driver factory starts Chrome, Firefox or Edge, headed or headless, and Selenium Manager handles the driver binaries
- **Configuration:** settings like base URL, browser, waits and credentials come from a `.env` file, and can be overridden with the `--browser` and `--headless` command-line options


