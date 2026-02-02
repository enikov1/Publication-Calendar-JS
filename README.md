# jQuery Publication Calendar

Календарь публикаций с поддержкой русского языка. Плагин для jQuery.

## Установка

Подключите jQuery и файлы плагина:

```html
<link rel="stylesheet" href="dist/jquery.publication-calendar.min.css">
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="dist/jquery.publication-calendar.min.js"></script>
```

## Быстрый старт

```html
<div id="calendar"></div>

<script>
$('#calendar').publicationCalendar({
    currentMonth: 10,  // Ноябрь (0-11)
    currentYear: 2025,
    publications: {
        '2025-11-15': 5,
        '2025-11-20': 12
    }
});
</script>
```

## Параметры

| Параметр | Тип | По умолчанию | Описание |
|----------|-----|--------------|----------|
| `currentMonth` | number | текущий месяц | Начальный месяц (0-11, где 0 = Январь) |
| `currentYear` | number | текущий год | Начальный год |
| `publications` | object | {} | Данные о публикациях (см. форматы ниже) |
| `onDateClick` | function | null | Callback при клике на дату |
| `showMonthArrows` | boolean | true | Показывать стрелки переключения месяца |
| `showYearArrows` | boolean | true | Показывать стрелки переключения года |
| `showStats` | boolean | true | Показывать статистику внизу календаря |
| `showModal` | boolean | false | Показывать модальное окно при клике на дату (десктоп) |
| `monthSelectPlaceholder` | string | null | Текст placeholder для селектора месяца |
| `yearSelectPlaceholder` | string | null | Текст placeholder для селектора года |
| `animationDuration` | number | 300 | Длительность анимации в миллисекундах |
| `monthNames` | array | ['Январь', ...] | Названия месяцев |
| `monthNamesPrepositional` | array | ['январе', ...] | Названия месяцев в предложном падеже |
| `dayNames` | array | ['Пн', 'Вт', ...] | Названия дней недели |
| `selectArrowIcon` | string | SVG | Иконка стрелки в селекторах |
| `arrowUpIcon` | string | SVG | Иконка стрелки вверх |
| `arrowDownIcon` | string | SVG | Иконка стрелки вниз |

## Форматы данных publications

### Простой формат (только количество)

```javascript
publications: {
    '2025-11-15': 5,
    '2025-11-20': 12
}
```

### Формат с URL

```javascript
publications: {
    '2025-11-15': {
        count: 5,
        url: 'https://example.com/article'
    }
}
```

### Формат с текстом

```javascript
publications: {
    '2025-11-15': {
        text: 'Важное событие'
    }
}
```

### Комбинированный формат

```javascript
publications: {
    '2025-11-15': {
        count: 5,
        url: 'https://example.com/article',
        text: 'Описание события'
    }
}
```

## Методы API

После инициализации можно получить доступ к методам:

```javascript
var calendar = $('#calendar').publicationCalendar(options).data('publicationCalendar');

// Обновить данные публикаций
calendar.setPublications({
    '2025-12-01': 10,
    '2025-12-15': 3
});

// Перейти к определенному месяцу
calendar.goToMonth(11, 2025);  // Декабрь 2025

// Обновить отображение
calendar.refresh();
```

## Callback onDateClick

```javascript
$('#calendar').publicationCalendar({
    publications: {...},
    onDateClick: function(date, count, url, text) {
        console.log('Дата:', date);        // '2025-11-15'
        console.log('Количество:', count); // 5
        console.log('URL:', url);          // 'https://...' или null
        console.log('Текст:', text);       // 'Описание' или null
    }
});
```

## Пример с placeholder

```javascript
$('#calendar').publicationCalendar({
    currentMonth: 10,
    currentYear: 2025,
    publications: {...},
    monthSelectPlaceholder: 'Выбрать месяц',
    yearSelectPlaceholder: 'Выбрать год',
    showStats: false,
    showYearArrows: false
});
```

## Пример полной конфигурации

```javascript
$('#calendar').publicationCalendar({
    currentMonth: 10,
    currentYear: 2025,
    publications: {
        '2025-11-03': { text: 'Праздник' },
        '2025-11-07': { count: 5, url: 'https://example.com/news' },
        '2025-11-15': 3,
        '2025-11-20': { count: 10, text: 'Важная дата', url: 'https://example.com' }
    },
    showMonthArrows: true,
    showYearArrows: false,
    showStats: true,
    showModal: true,
    monthSelectPlaceholder: null,
    yearSelectPlaceholder: null,
    onDateClick: function(date, count, url, text) {
        if (url) {
            window.open(url, '_blank');
        }
    }
});
```

## Файлы

- `dist/jquery.publication-calendar.js` - основной файл без комментариев
- `dist/jquery.publication-calendar.min.js` - минифицированная версия
- `dist/jquery.publication-calendar.css` - стили без комментариев
- `dist/jquery.publication-calendar.min.css` - минифицированные стили

## Поддержка браузеров

- Chrome (последние 2 версии)
- Firefox (последние 2 версии)
- Safari (последние 2 версии)
- Edge (последние 2 версии)
- IE 11

## Лицензия

MIT
