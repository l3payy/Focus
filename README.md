<div align="center">

<img width="1040" height="510" alt="image" src="https://github.com/user-attachments/assets/bb216eef-4b8a-4607-b571-cdedf2ba13c1" />


# Focus — новая вкладка, спроектированная на красоту и скорость

*Три независимых пространства вместо бесконечной ленты. Всё локально. Ноль телеметрии.*

![Chrome MV3](https://img.shields.io/badge/Chrome-MV3-6155F5?logo=googlechrome&logoColor=white)
![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-0_зависимостей-F7DF1E?logo=javascript&logoColor=black)
![Local First](https://img.shields.io/badge/Local--First-IndexedDB_%2B_Cache-8A7CFF)
![No Telemetry](https://img.shields.io/badge/telemetry-zero-22c55e)
![Version](https://img.shields.io/badge/version-0.2.2-DDd3FF)


</div>

---

## ☁️ Облачка — визуальная доска

> Кидай, пиши, рисуй. Всё остаётся в браузере.

- 🖼️ **Картинки** из буфера (`Ctrl+V`) и drag-and-drop
- 📝 **Короткие заметки** — прямо на сетке
- ✏️ **Рисование карандашом** с отменой / очисткой
- 💾 Всё хранится **локально** в IndexedDB

<p align="center">
  <img width="1919" alt="Облачка" src="https://github.com/user-attachments/assets/673970ec-fc77-41eb-a33e-9f4da332ced0" />
</p>

---

## 🎯 Фокус — остров из любимых сайтов

> Только самое важное. Открывается мгновенно, работает без сети.

- 🔖 До **16 сайтов**
- 💾 Фавиконки подтягиваются **один раз** (DuckDuckGo `ip3`) и дальше берутся **с диска**
- 📴 Полный **офлайн** после первого добавления
- 🔍 Свой поисковик + своя видимость поиска

<p align="center">
  <img width="1919" alt="Фокус" src="https://github.com/user-attachments/assets/6a059da1-7891-4bc8-93e0-c87f12d3ed99" />
</p>

---

## 🚀 Фокус+ — сетка до 72 сайтов

> Вся коллекция под рукой. С названиями.

- 🗂️ Сетка до **72 сайтов** с названиями
- 📁 Папки — *обсуждается, нужно ли?*
- ⚡ Тот же дисковый кеш иконок, тот же мгновенный старт

<p align="center">
  <img width="1919" alt="Фокус плюс" src="https://github.com/user-attachments/assets/e82c7fc7-0dc5-4d5f-8b32-4b78d1ab4968" />
</p>

---

## ⚡ Почему быстро

- 🧱 **Никаких фреймворков** — чистый Vanilla JS, ноль сетевых запросов при открытии
- 💿 **Фоны, иконки и картинки из дискового кеша** через service worker — сеть дёргается один раз при добавлении:
  - `favicons → Cache Storage (focus-fav-v1)`
  - `фоны → Cache Storage (focus-bg-v1, /__bg__/<space>)`
  - `BAKE_ICON` прогревает кеш заранее, открытия вкладок — только диск
- 🖼️ **Первый кадр рисуется синхронно** — последнее пространство, тема и скелетоны без ожидания хранилищ (`boot-shell.js` в `<head>`)

```mermaid
graph LR
  A[Новая вкладка] --> B{boot-shell в head}
  B -->|localStorage sync| C[слепок: тема + space + скелетон]
  C --> D[Service Worker: /__fav__ + /__bg__ с диска]
  D --> E[фрейм пространства]
```

---

## 🌙 Почему спокойно

- 🎨 **Две темы из коробки** — сиреневая и тёмная
- ✨ **Уникальные стили иконок через `sites-db.js`** — чтобы иконки всегда были красивыми и узнаваемыми:

```js
// sites-db.js — только исключения, остальное по стандарту
var SITES_DB = {
  'twitch.tv':  { bg: '#FFFFFF', icon: 38, fit: 'long', name: 'Twitch' },
  'github.com': { bg: '#FFFFFF', icon: 38, fit: 'long', name: 'GitHub' },
  'kick.com':   { bg: '#000000', icon: 42 },
};
```

- 🔍 **Свой поисковик и видимость поиска** — отдельно для каждого пространства
- 🔒 **Ноль телеметрии** — данные не покидают браузер, аккаунт не нужен

---

## 🚀 Установка

<details>
<summary><b>Вариант 1 — распакованным расширением (сейчас)</b></summary>

```bash
1. Скачайте / склонируйте репозиторий
2. Откройте chrome://extensions
3. Включите «Режим разработчика»
4. «Загрузить распакованное расширение» → выберите папку Focus/
5. Откройте новую вкладку ✨
```

</details>

<details>
<summary><b>Вариант 2 — из Chrome Web Store (скоро)</b></summary>

> Пока не залито в стор. 

</details>

---

<div align="center">

**Focus — ужасное внимание к деталям лишь для того, чтобы их не замечать**


</div>
