# trpo-pr01-Nandysheva2
# Практическая работа №2
Нандышева Амуланга Аюкаевна, ЭПБО-01-25

## Описание результата
каталог из 18 карточек с панелью фильтров слева
Данные карточек взяты из `data/catalog.csv`, цвета, радиус и отступ — из `data/theme.json`
(перенесены в `scss/_variables.scss`)
Папка `data` — это dataset работы
## Запуск
1. Клонировать репозиторий: `git clone`
2. Перейти в папку: `cd trpo-pr02-Nandysheva1`
3. Установить зависимости: `npm install`
4. Разовая сборка SCSS в CSS: `npm run build`
5. Режим наблюдения: `npm run watch`, остановить — `Ctrl+C`
6. Открыть `index.html` в браузере

## Структура каталогов
`index.html` — страница
`scss/` — исходники стилей: `styles.scss` (главный), `_variables`, `_functions`, `_mixins`, `_base`, `_layout`, `components/`
`css/styles.css` — результат компиляции
`data/` — dataset: `catalog.csv`, `theme.json`
`images/` — картинки товаров

### Чем переменная SCSS отличается от CSS custom property?
SCSS-переменная (`$accent`) существует только на этапе компиляции: компилятор подставляет
значение, и в готовом CSS переменной уже нет. CSS custom property (`--accent` и `var(--accent)`) живёт
в браузере: её можно менять в DevTools, через JavaScript или в медиазапросе, она наследуется
по дереву элементов. В работе я использовал SCSS-переменные, потому что тема из theme.json фиксирована при
сборке, и значения нужны в вычислениях (`rgba($accent, 0.45)`, `space()`)

### Зачем нужны partial-файлы?
Файл с нижним подчёркиванием (`_card.scss`) не компилируется сам по себе, а подключается
в главный `styles.scss` через `@use`. Они позволяют держать каждый компонент в отдельном
небольшом файле, быстро находить нужный код и переиспользовать общие части (переменные, mixin).
Результат при этом один — `css/styles.css`

### Где применён mixin?
`container` — в `.container` и `.site-header__inner` (`scss/_layout.scss`)
`focus-ring` — в `.nav__link` (`scss/_layout.scss`) и `.button` (`scss/components/_button.scss`)
`up-to` — в `.page`, `.card`, и в медиазапросе для `.nav`