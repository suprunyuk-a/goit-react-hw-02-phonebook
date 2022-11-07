# goit-react-hw-02-phonebook

# Телефонна книга

Написати застосунок зберігання контактів телефонної книги.

## Крок 1

Застосунок повинен складатися з форми і списку контактів. На поточному кроці реалізувати додавання імені контакту та відображення списку контактів. Застосунок не повинен зберігати контакти між різними сесіями (оновлення сторінки).

Використовувати цю розмітку інпуту з вбудованою валідацією для імені контакту.

```html
<input
  type="text"
  name="name"
  pattern="^[a-zA-Zа-яА-Я]+(([' -][a-zA-Zа-яА-Я ])?[a-zA-Zа-яА-Я]*)*$"
  title="Name may contain only letters, apostrophe, dash and spaces. For example Adrian, Jacob Mercer, Charles de Batz de Castelmore d'Artagnan"
  required
/>
```

Стан, що зберігається в батьківському компоненті `<App>`, обов'язково повинен бути наступного вигляду, додавати нові властивості не можна.

```bash
state = {
  contacts: [],
  name: ''
}
```

Кожен контакт повинен бути об'єктом з властивостями `name` та `id`. Для генерації ідентифікаторів використовувати будь-який відповідний пакет, наприклад [nanoid](https://www.npmjs.com/package/nanoid) або `crypto.randomUUID()`. Після завершення цього кроку, застосунок повинен виглядати приблизно так.

![preview](https://raw.githubusercontent.com/goitacademy/react-homework/master/homework-02/phonebook/mockup/step-1.png)

## Крок 2

Розширити функціонал застосунку, дозволивши користувачам додавати номери телефонів. Для цього додати `<input type="tel">` у форму і властивість для зберігання його значення в стані.

```bash
state = {
  contacts: [],
  name: '',
  number: ''
}
```

Слід використовувати цю розмітку інпуту з вбудованою валідацією для номеру контакту.

```html
<input
  type="tel"
  name="number"
  pattern="\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}"
  title="Phone number must be digits and can contain spaces, dashes, parentheses and can start with +"
  required
/>
```

Після завершення цього кроку, застосунок повинен виглядати приблизно так.

![preview](https://raw.githubusercontent.com/goitacademy/react-homework/master/homework-02/phonebook/mockup/step-2.png)

## Крок 3

Додати поле пошуку, яке можна використовувати для фільтрації списку контактів за ім'ям.

- Поле пошуку – це інпут без форми, значення якого записується у стан (контрольований елемент).
- Логіка фільтрації повинна бути нечутливою до регістру.

```bash
state = {
  contacts: [],
  filter: '',
  name: '',
  number: ''
}
```

![preview](https://raw.githubusercontent.com/goitacademy/react-homework/master/homework-02/phonebook/mockup/step-3.gif)

Коли ми працюємо над новим функціоналом, буває зручно жорстко закодувати деякі дані у стан. Це позбавить необхідності вручну вводити дані в інтерфейсі для тестування роботи нового функціоналу. Наприклад, можна використовувати такий початковий стан.

```bash
state = {
  contacts: [
    {id: 'id-1', name: 'Rosie Simpson', number: '459-12-56'},
    {id: 'id-2', name: 'Hermione Kline', number: '443-89-12'},
    {id: 'id-3', name: 'Eden Clements', number: '645-17-79'},
    {id: 'id-4', name: 'Annie Copeland', number: '227-91-26'},
  ],
  filter: '',
  name: '',
  number: ''
}
```

## Крок 4

Виконати рефакторинг, виділивши відповідні частини в окремі компоненти. У стані кореневого компонента `<App>` залишаться тільки властивості `contacts` і `filter`.

```bash
state = {
  contacts: [],
  filter: ''
}
```

Достатньо виділити чотири компоненти: форма додавання контактів, список контактів, елемент списку контактів та фільтр пошуку.

Після рефакторингу кореневий компонент програми виглядатиме так.

```jsx
<div>
  <h1>Phonebook</h1>
  <ContactForm ... />

  <h2>Contacts</h2>
  <Filter ... />
  <ContactList ... />
</div>
```

## Крок 5

Заборонити користувачеві можливість додавати контакти, імена яких вже присутні у телефонній книзі. При спробі виконати таку дію необхідно вивести `alert` із попередженням.

![preview](https://raw.githubusercontent.com/goitacademy/react-homework/master/homework-02/phonebook/mockup/step-5.png)

## Крок 6

Розширити функціонал застосунку, дозволивши користувачеві видаляти раніше збережені контакти.

![preview](https://raw.githubusercontent.com/goitacademy/react-homework/master/homework-02/phonebook/mockup/step-6.gif)
