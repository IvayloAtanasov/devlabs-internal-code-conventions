#SASS Conventions:

###Directory Structure
Спазвайте правилна структура на Вашите папки. Разбийте style кода си на модули и ги разпределете в правилните директории:

```html
sass/ 
| 
|– components/ 
|   |– _fonts.scss       # Fonts
|   |– _buttons.scss     # Buttons
|   |– _carousel.scss    # Carousel
|   |– _dropdown.scss    # Dropdown 
|   |– _navigation.scss  # Navigation 
|   ...                  # Etc… 
| 
|– helpers/ 
|   |– _variables.scss   # Sass Variables 
|   |– _functions.scss   # Sass Functions 
|   |– _mixins.scss      # Sass Mixins 
|   |– _helpers.scss     # Class & placeholders helpers 
|   ...                  # Etc… 
| 
|– layout/ 
|   |– _grid.scss        # Grid system 
|   |– _header.scss      # Header 
|   |– _footer.scss      # Footer 
|   |– _sidebar.scss     # Sidebar 
|   |– _forms.scss       # Forms 
|   ...                  # Etc… 
| 
|– pages/ 
|   |– _home.scss        # Home specific styles 
|   |– _contact.scss     # Contact specific styles 
|   ...                  # Etc… 
| 
|– plugins/ 
|   |– _bootstrap.scss   # Bootstrap 
|   |– _jquery-ui.scss   # jQuery UI
|   |– _datepicker.scss  # Datepicker
|   ...                  # Etc… 
| 
| 
`– main.scss             # основният Sass файл 
```
###Подходящи имена на променливи
Избирайте подходящи имена за Вашите промениливи

Избягвайте да кръщавате променливите с директните им свойства:
```css
$red-button: #ff000;
```
Желателно е да ги кръщавате спрямо към какво се отнасят
```css
$primary-color: #333;
$base-font-family: Helvetica, Arial, sans-serif !default;
```
###Последователност
Последователността на свойствата е изключително важен фактор, особено когато нов член към екипа чете кода ни:
- $variables;
- @extends;
- @includes;
- свойства на елемента;
- действие към елемента;
- комбинация с други класове;
- комбинация с други елементи;
Оставяйте по един свободен ред между отделните типове.

```css
.element {
    $bg-color: #D90000;

    @extend .rounded-border;

    @include data-module;

    cursor: pointer;
    height: 300px;
    margin: 0 auto;
    padding: 0;
    width: 400px;

    &:hover {
        text-decoration: underline;
    }

    &.active {
        color: #fff;
    }

    & > li {
        margin: 10px;
    }

    & + ul {
        margin-left: 10px;
    }
}
```
###Как да кръщаваме имената на елементите спрямо съществително или прилагателно
Когато четем един SASS код е хубаво да имаме ясна представа за структурата на HTML елементите и в какво състояние са те:

От тип object - традиционно използваните елементи:
```css
.noun {}            // examples: .button, .menu, .textbox, .header
```

От тип parent-child - когато има връзка между елементите и също е съществително:
```css
.noun {}            // parent: .post
.noun-noun {}       // child:  .post-title
```

От тип subclasses - когато елемента е превъзхождан от прилагателно:
```css
adjective-noun {}  // example: .dropdown-button
```

От тип modifiers - когато винаги са прилагателни:
```css
.is-state {}        // state: is-selected, is-hidden
.adjective {}       // examples: .left, .right, .block, .inline
```

###Стъпаловидна структура

Бъдете внимателни със вашите нива на стъпаловидност. Препоръчителното максимално ниво е до 3 нива навътре:
```css
.weather {
    .cities {
        li {
            // no more!
        }
    }
}
```
Препоръчителни максималните редове на Вашата стъпаловидна структура са до 50 реда. Ако Вашият SASS block код превиши 50 реда има голяма вероятност да не събере на Вашият editor screen и да се превърне в труден за четене. Прегледайте си кода, може да използвате @import или @mixins, а проверихте ли Naming конвенциите.

###Използвайте SourceMapping
Не забравяйте да добавите опцията за SourceMapping когато конвентирате кода от sass към css. Той ви помага да намерите всяко едно property от inspect elementa, в кой от всичките инклуднати SASS файловете се намира и на кой ред.