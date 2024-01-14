# UiButton

👶🏻 _Несложная задача_\
💼 _Часть проекта_

<!--start_statement-->

Требуется разработать компонент кнопку **UiButton**:

- Входные параметры:
  - `tag` - элемент (или компонент), который используется для кнопки (по умолчанию `'button'`). Часто визуально кнопка
    может быть не элементом `<button>`, а ссылкой или другим компонентом.
  - `variant` - строка `'primary' | 'secondary' | 'danger'` с типом кнопки, который определяется соответственно классами
    `.button_primary, .button_secondary, .button_danger` (по умолчанию - `secondary`).
  - `block` - логический, является ли кнопка блоком (с классом `button_block`);
  - Другие параметры - при необходимости;
- Слот по умолчанию — содержимое кнопки.

У HTML кнопки `<button>` есть неудобная особенность. По умолчанию она ведёт себя, как кнопка `type="submit"`. Реализуйте
компонент таким образом, чтобы у кнопки `<button>` устанавливался `type="button"`, если он не задан явно пользователем
компонента. Но только у кнопки `<button>`!

<img src="https://i.imgur.com/R8aKxcG.png" alt="Example" style="max-width: 100%" />
<!--end_statement-->

---

### Инструкция

📝 Для решения задачи отредактируйте файлы: `components/UiButton.vue`.

🚀 Команда запуска для ручного тестирования: `npm run serve`;\
приложение будет доступно на [http://localhost:8080/06-wrappers/02-UiButton/](http://localhost:8080/06-wrappers/02-UiButton/).

✅ Доступно автоматическое тестирование: `npm test UiButton`.