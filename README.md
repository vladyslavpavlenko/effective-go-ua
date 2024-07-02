# Ефективна Go (Effective Go)
Оригінал: [«Effective Go»](https://go.dev/doc/effective_go)

## Зміст
- [Вступ](#Вступ)
  - [Приклади](#Приклади)
- [Форматування](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/01.%20Форматування.md#Форматування)
- [Коментарі](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/02.%20Коментарі.md#Коментарі)
- [Найменування](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/03.%20Найменування.md#Найменування)
  - [Назви пакетів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/03.%20Найменування.md#Назви-пакетів)
  - [Геттери](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/03.%20Найменування.md#Геттери)
  - [Назви інтерфейсів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/03.%20Найменування.md#Назви-інтерфейсів)
  - [MixedCaps](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/03.%20Найменування.md#MixedCaps)
- [Крапки з комою](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/04.%20Крапки%20з%20комою.md#Крапки-з-комою)
- [Керуючі структури](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/05.%20Керуючі%20структури.md#Керуючі-структури)
  - [If](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/05.%20Керуючі%20структури.md#If)
  - [Перевизначення й перепризначення](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/05.%20Керуючі%20структури.md#Перевизначення-й-перепризначення)
  - [For](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/05.%20Керуючі%20структури.md#For)
  - [Switch](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/05.%20Керуючі%20структури.md#Switch)
  - [Типізований switch](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/05.%20Керуючі%20структури.md#Типізований-switch)
- [Функції](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/06.%20Функції.md#Функції)
  - [Множинне повернення результатів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/06.%20Функції.md#Множинне-повернення-результатів)
  - [Найменування параметрів результату](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/06.%20Функції.md#Найменування-параметрів-результату)
  - [Defer](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/06.%20Функції.md#Defer)
- [Дані](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Дані)
  - [Створення за допомогою new](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Створення-за-допомогою-new)
  - [Конструктори та складені літерали](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Конструктори-та-складені-літерали)
  - [Створення за допомогою make](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Створення-за-допомогою-make)
  - [Масиви](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Масиви)
  - [Зрізи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Зрізи)
  - [Двовимірні зрізи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Двовимірні-зрізи)
  - [Мапи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Мапи)
  - [Друк](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Друк)
  - [Приєднання](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/07.%20Дані.md#Приєднання)
- [Ініціалізація](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/08.%20Ініціалізація.md#Ініціалізація)
  - [Константи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/08.%20Ініціалізація.md#Константи)
  - [Змінні](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/08.%20Ініціалізація.md#Змінні)
  - [Функція init](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/08.%20Ініціалізація.md#Функція-init)
- [Методи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/09.%20Методи.md#Методи)
  - [Вказівники чи значення](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/09.%20Методи.md#Вказівники-чи-значення)
- [Інтерфейси та інші типи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/10.%20Інтерфейси%20та%20інші%20типи.md#Інтерфейси-та-інші-типи)
  - [Інтерфейси](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/10.%20Інтерфейси%20та%20інші%20типи.md#Інтерфейси)
  - [Перетворення](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/10.%20Інтерфейси%20та%20інші%20типи.md#Перетворення)
  - [Конвертація інтерфейсів та твердження типів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/10.%20Інтерфейси%20та%20інші%20типи.md#Конвертація-інтерфейсів-і-твердження-типів)
  - [Узагальнені типи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/10.%20Інтерфейси%20та%20інші%20типи.md#Узагальнені-типи)
  - [Інтерфейси й методи](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/10.%20Інтерфейси%20та%20інші%20типи.md#Інтерфейси-й-методи)
- [Порожній ідентифікатор](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/11.%20Порожній%20ідентифікатор.md#Порожній-ідентифікатор)
  - [Порожній ідентифікатор у множинному присвоюванні](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/11.%20Порожній%20ідентифікатор.md#Порожній-ідентифікатор-у-множинному-присвоюванні)
  - [Невикористовувані імпортування й значення](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/11.%20Порожній%20ідентифікатор.md#Невикористовувані-імпортування-й-значення)
  - [Імпортування для сторонніх ефектів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/11.%20Порожній%20ідентифікатор.md#Імпортування-для-сторонніх-ефектів)
  - [Перевірки інтерфейсів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/11.%20Порожній%20ідентифікатор.md#Перевірки-інтерфейсів)
- [Вкладення](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/12.%20Вкладення.md#Вкладення)
- [Конкурентність](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Конкурентність)
  - [Розподіл за повідомленнями](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Розподіл-за-повідомленнями)
  - [Горутини](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Горутини)
  - [Канали](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Канали)
  - [Канали каналів](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Канали-каналів)
  - [Паралелізм](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Паралелізм)
  - [Поточний буфер](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/13.%20Конкурентність.md#Поточний-буфер)
- [Помилки](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/14.%20Помилки.md#Помилки)
  - [Паніка](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/14.%20Помилки.md#Паніка)
  - [Відновлення](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/14.%20Помилки.md#Відновлення)
- [Вебсервер](https://github.com/vladyslavpavlenko/effective-go-ua/blob/main/15.%20Вебсервер.md#Вебсервер)

## Вступ
Go — це нова мова. Запозичуючи ідеї з наявних мов, вона має й свої незвичайні властивості, які роблять ефективні програми на Go відмінними за характером від програм, написаних на подібних їй. Прямий переклад програм, написаних на C++ або Java, на Go навряд чи дасть задовільний результат — програми на Java написані на Java, а не на Go. З іншого боку, обдумування проблеми з перспективи Go може призвести до створення успішної, але зовсім іншої програми. Іншими словами, щоб добре писати на Go, важливо розуміти її властивості та ідіоми. Також важливо знати встановлені конвенції для програмування на Go, такі як найменування, форматування, побудова програм і так далі, щоб програми, які ви пишете, були зрозумілими для інших програмістів на Go.

Цей документ містить поради щодо написання зрозумілого, ідіоматичного коду мовою Go. Він доповнює [специфікацію мови](https://go.dev/ref/spec) (англ.), [«Тур із Go»](https://go-tour-ua-translation.lm.r.appspot.com/welcome/1) (укр.) та [«Як писати код на Go»](https://go.dev/doc/code) (англ.), які вам слід прочитати першими.

**Примітка, додана у січні 2022 року:** Цей документ було написано до випуску Go у 2009 році, і відтоді він суттєво не оновлювався. Хоча це хороший посібник для розуміння того, як користуватися самою мовою, завдяки стабільності мови, в ньому мало сказано про бібліотеки й нічого про значні зміни в екосистемі Go з моменту написання, такі як система збірки, тестування, модулі та поліморфізм. Ми не плануємо її оновлювати, оскільки змін було багато, а велика кількість документів, блогів та книг, що постійно зростає, чудово описують сучасне використання Go. Цей документ продовжує бути корисним, але ви повинні розуміти, що тут викладено далеко не всю інформацію. Додатковий контекст дивіться у [питанні 28782](https://github.com/golang/go/issues/28782).

### Приклади
Вихідні коди пакетів Go призначені не лише для використання у якості основної бібліотеки, але і як приклади використання мови. Щобільше, багато пакетів містять робочі, самодостатні виконувані приклади, які ви можете запустити безпосередньо з вебсайту [go.dev](https://go.dev), наприклад, [цей](https://go.dev/pkg/strings/#example-Map) (якщо потрібно, натисніть на слово «Приклад», щоб відкрити його). Якщо у вас є питання про те, як підійти до проблеми або як щось можна реалізувати, документація, код і приклади в бібліотеці можуть надати відповіді, ідеї та підказки.