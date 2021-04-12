# Вступ

<img align="right" height="140" src="images/Vue.png">

Vue — прогресивний фреймворк для створення інтерфейсів для користувачів. На відміну від інших фреймворків, Vue повністю розроблений для поступового впровадження. Основна бібліотека орієнтована лише на відображення; її легко зрозуміти та використовувати з іншими бібліотеками або в існуючих проєктах. Але Vue також здатний легко живити складні *SPA* (**S**ingle-**P**age **A**pplications — односторінкові веб-застосунки), коли використовується у поєднанні з сучасними підтримуючими бібліотеками.
<br><br>

> ...it was originally named "Seed"... I didn't have a better name for it and actually "Seed" was taken on npm. When I was about to publish the package, I found "Oh, the name is already taken!", so I had to come up with a new name. And I thought "Ok, this is a view library", but just calling it English "View" sounds a bit too literal, so I threw "view" into Google Translate and found the French translation of it. It's just three letters, it looked cool, it's not taken on npm. So I was like "Ok, this is it!". So that'show I picked the name."
>
> — Evan You, творець Vue

# Упровадження

Як зазначено у вступі, Vue розроблений для поступового впровадження у проєкт. Це означає можливість його використання у кілька способів у залежності від вимог:
<br><br>

* Імпортування на сторінку як *CDN*-пакет (**C**ontent **D**elivey **N**etwork — мережа розповсюдження даних).
Це зручно для створення прототипів або навчання. Потрібно просто додати один рядок у тег `head`:
    ```html
    <script src="https://unpkg.com/vue@next"></script>
    ```
    Це забезпечить використання останньої версії Vue.
<br><br>

* Установлення через **npm**. Рекомендований спосіб для створення великих проєктів. Він повністю узгоджений із зв'язниками модулів, такими як [Webpack](https://webpack.js.org/) та [Rollup](https://rollupjs.org/guide/en/). Для встановлення останньої версії Vue, потрібно виконати команду:
    ```powershell
    npm install vue@next
    ```
<br>

* Використання Vue CLI (**C**ommand-**L**ine **I**nterface — інтерфейс через командний рядок). Є розширенням попереднього пункту, яке дозволяє швидко створювати *SPA*. Він має налаштування зібрання проєкту для сучасного робочого процесу. Можна швидко бачити результат разом з *hot reload* (миттєве відображення змін без перезавантаження сторінки), *lint on save* (виявлення вад коду з його збереженням) та готовими збірками проєкту. Для встановлення останньої версії Vue CLI, з правами адміністратора потрібно виконати команду:
    ```powershell
    npm install -g @vue/cli

    # '-g' вказує встановити Vue CLI глобально
    ```
    У проєкті **"What is this?"** використовується саме цей спосіб.
<br><br>

* Завантаження JavaScript-файлів та власний їх хостинг. Так можна уникнути зібрання проєкту та імпортування Vue як *CDN*-пакет.
<br><br>

# Створення проєкту та його структура

Для створення застосунку Vue потрібно виконати команду:
```powershell
npm create what-is-this

# 'what-is-this' - назва застосунку
```
Вона запитує налаштування та надає 3 варіанти відповіді:
```powershell
? Please pick a preset:
  Default ([Vue 2] babel, eslint)
  Default (Vue 3 Preview) ([Vue 3] babel, eslint)
> Manually select features
```
Обираємо третій варіант — обрання налаштувань власноруч. Запропонований список має багато пунктів, про які можна не думати на початку. Залишаємо вказання версії Vue та `Linter / Formatter`:
```powershell
? Check the features needed for your project:
 (*) Choose Vue version
 ( ) Babel
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 ( ) Router
 ( ) Vuex
 ( ) CSS Pre-processors
>(*) Linter / Formatter
 ( ) Unit Testing
 ( ) E2E Testing
```
Обираємо останню версію Vue:
```powershell
? Choose a version of Vue.js that you want to start the project with
  2.x
> 3.x (Preview)
```
Решта налаштувань — на ваш смак. Тепер ми маємо папку зі вказаною назвою, в якій знаходиться застосунок Hello World. Він має структуру будь-якого іншого, створеного з Vue. Розглянемо, як код перетворюється на веб-сторінку.

Весь код знаходиться у папці `src`, зміст якої:
* папка `assets` зберігає допоміжні файли (наприклад, зображення)
* папка `components` зберігає [*компоненти*](#Компоненти), з яких складається застосунок
* файл `App.vue` — головний файл застосунку, який є компонентом за структурою
* єдина функція файлу `main.js` — додання компонента `App.vue` у відповідне місце в документі-шаблоні `index.html`, який знаходиться у папці `public` поруч із папкою `assets`

# Компоненти

# Атрибути
