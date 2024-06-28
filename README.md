# Ефективна Go (Effective Go)
Оригінал: [Effective Go](https://go.dev/doc/effective_go)

## Зміст
- [Вступ](#Вступ)
  - [Приклади](#Приклади)
- [Форматування](#Форматування)
- [Коментарі](#Коментарі)
- [Найменування](#Найменування)
  - [Назви пакетів](#Назви-пакетів)
  - [Геттери](#Геттери)
  - [Назви інтерфейсів](#Назви-інтерфейсів)
  - [MixedCaps](#MixedCaps)
- [Середники](#Середники)
- [Керуючі структури](#Керуючі-структури)
  - [If](#If)
  - [Перевизначення й переприсвоювання](#Перевизначення-й-переприсвоювання)
  - [For](#For)
  - [Switch](#Switch)
  - [Типізований switch](#Типізований-switch)
- [Функції](#Функції)
  - [Множинне повернення результатів](#Множинне-повернення-результатів)
  - [Найменування параметрів результату](#Найменування-параметрів-результату)
  - [Defer](#Defer)
- [Дані](#Дані)
  - [Створення за допомогою new](#Створення-за-допомогою-new)
  - [Конструктори та складені літерали](#Конструктори-та-складені-літерали)
  - [Створення за допомогою make](#Створення-за-допомогою-make)
  - [Масиви](#Масиви)
  - [Зрізи](#Зрізи)
  - [Двовимірні зрізи](#Двовимірні-зрізи)
  - [Карти](#Карти)
  - [Друк](#Друк)
  - [Приєднання](#Приєднання)
- [Ініціалізація](#Ініціалізація)
  - [Константи](#Константи)
  - [Змінні](#Змінні)
  - [Функція init](#Функція-init)
- [Методи](#Методи)
  - [Вказівники чи значення](#Вказівники-чи-значення)
- [Інтерфейси та інші типи](#Інтерфейси-та-інші-типи)
  - [Інтерфейси](#Інтерфейси)
  - [Перетворення](#Перетворення)
  - [Конвертація інтерфейсів та прив'язка типів](#Конвертація-інтерфейсів-і-прив'язка-типів)
  - [Загальність](#Загальність)
  - [Інтерфейси й методи](#Інтерфейси-й-методи)
- [Порожній ідентифікатор](#Порожній-ідентифікатор)
  - [Порожній ідентифікатор у множинному присвоюванні](#Порожній-ідентифікатор-у-множинному-присвоюванні)
  - [Невикористовувані імпортування й значення](#Невикористовувані-імпортування-й-значення)
  - [Імпортування для сторонніх ефектів](#Імпортування-для-сторонніх-ефектів)
  - [Перевірки інтерфейсів](#Перевірки-інтерфейсів)
- [Вкладення](#Вкладення)
- [Конкурентність](#Конкурентність)
  - [Розподіл за повідомленнями](#Розподіл-за-повідомленнями)
  - [Горутини](#Горутини)
  - [Канали](#Канали)
  - [Канали каналів](#Канали-каналів)
  - [Паралелізм](#Паралелізм)
  - [Поточний буфер](#Поточний-буфер)
- [Помилки](#Помилки)
  - [Паніка](#Паніка)
  - [Відновлення](#Відновлення)
- [Вебсервер](#Вебсервер)

## Вступ
Go — це нова мова. Запозичуючи ідеї з існуючих мов, вона  має й свої незвичайні властивості, які роблять ефективні програми на Go відмінними за характером від програм, написаних на подібних їй. Прямий переклад програм, написаних на C++ або Java, на Go навряд чи дасть задовільний результат — програми на Java написані на Java, а не на Go. З іншого боку, обдумування проблеми з перспективи Go може призвести до створення успішної, але зовсім іншої програми. Іншими словами, щоб добре писати на Go, важливо розуміти її властивості та ідіоми. Також важливо знати встановлені конвенції для програмування на Go, такі як найменування, форматування, побудова програм і так далі, щоб програми, які ви пишете, були зрозумілими для інших програмістів на Go.

Цей документ містить поради щодо написання зрозумілого, ідіоматичного коду мовою Go. Він доповнює [специфікацію мови](https://go.dev/ref/spec) (англ.), [«Тур із Go»](https://go-tour-ua-translation.lm.r.appspot.com/welcome/1) (укр.) та [«Як писати код на Go»](https://go.dev/doc/code) (англ.), які вам слід прочитати першими.

**Примітка, додана у січні 2022 року:** Цей документ було написано до випуску Go у 2009 році, і відтоді він суттєво не оновлювався. Хоча це хороший посібник для розуміння того, як користуватися самою мовою, завдяки стабільності мови, в ньому мало сказано про бібліотеки і нічого про значні зміни в екосистемі Go з моменту написання, такі як система збірки, тестування, модулі та поліморфізм. Ми не плануємо її оновлювати, оскільки змін було багато, а велика кількість документів, блогів та книг, що постійно зростає, чудово описують сучасне використання Go. Цей документ продовжує бути корисним, але ви повинні розуміти, що тут викладено далеко не всю інформацію. Додатковий контекст дивіться у [питанні 28782](https://github.com/golang/go/issues/28782).

### Приклади
Вихідні коди пакетів Go призначені не лише для використання у якості основної бібліотеки, але й як приклади використання мови. Більше того, багато пакетів містять робочі, самодостатні виконувані приклади, які ви можете запустити безпосередньо з вебсайту [go.dev](https://go.dev), наприклад, [цей](https://go.dev/pkg/strings/#example-Map) (якщо потрібно, натисніть на слово «Приклад», щоб відкрити його). Якщо у вас є питання про те, як підійти до проблеми або як щось можна реалізувати, документація, код і приклади в бібліотеці можуть надати відповіді, ідеї та підказки.

## Форматування
Питання форматування є найбільш суперечливими, але водночас найменш значущими. Люди можуть адаптуватися до різних стилів форматування, але краще, якщо їм взагалі не доведеться цього робити, і менше часу приділяється темі, якщо всі дотримуються одного стилю. Проблема полягає в тому, як підійти до цієї утопії без необхідності в довгому керівництві по стилю.

У Go ми застосовуємо незвичний підхід і дозволяємо машині подбати про більшість проблем форматування. Програма `gofmt` (також доступна як `go fmt`, яка працює на рівні пакетів, а не на рівні вихідного файлу) читає програму на Go і видає вихідний текст у стандартному стилі з відступами і вертикальним вирівнюванням, зберігаючи і, за необхідності, переформатовуючи коментарі. Якщо ви хочете дізнатися, як впоратися з якоюсь новою стилістичною ситуацією, запустіть `gofmt`; якщо відповідь не здається вам правильною, переробіть вашу програму (або повідомте про ваду в `gofmt`), а не обходьте її стороною.

Наприклад, не потрібно витрачати час на вирівнювання коментарів до полів структури, адже `gofmt` зробить це за вас. У наступній декларації
```go
type T struct {
    name string // name of the object
    value int // its value
}
```
`gofmt` самостійно вирівняє колонки:
```go
type T struct {
    name    string // name of the object
    value   int    // its value
}
```
Весь код Go у стандартних пакетах було відформатовано за допомогою `gofmt`.

Дуже коротко про деякі деталі форматування:

**Відступи**

Ми використовуємо табуляцію для відступів і `gofmt` робить це за замовчуванням. Використовуйте пробіли лише за крайньої необхідності.

**Довжина рядка**

Go не має обмежень на довжину рядка. Не хвилюйтеся про його перевонення. Якщо рядок здається вам занадто довгим, загорніть його і зробіть відступ за допомогою додаткової табуляції.

**Дужки**

Go потребує менше круглих дужок, ніж C та Java: керуючі структури (`if`, `for`, `switch`) не мають круглих дужок у своєму синтаксисі. Крім того, ієрархія пріоритетів операторів коротша і зрозуміліша, тому
```go
x<<8 + y<<16
```
не потребує додавання пробілів, на відміну від інших мов.

## Коментарі
У Go передбачено блокові коментарі у стилі C `/* */` та рядкові коментарі у стилі C++ `//`. Рядкові коментарі є нормою; блокові коментарі з'являються здебільшого як коментарі до пакетів, але можуть бути корисними всередині виразів або для вимкнення великих ділянок коду.

Коментарі, які з'являються перед оголошеннями верхнього рівня, без проміжних нових рядків, вважаються такими, що документують саме оголошення. Ці «doc-коментарі» є основною документацією для певного пакета або команди Go. Докладнішу інформацію про них наведено у розділі [«Doc-коментарі в Go»](https://go.dev/doc/comment) (англ.).

## Найменування
Найменування є так само важливими у Go, як і в будь-якій іншій мові. Вони навіть мають семантичний ефект: видимість імені поза пакетом визначається тим, чи є його перший символ верхнім регістром. Тому варто витратити трохи часу на розмову про угоди щодо іменування у програмах на Go.

### Назви пакетів
Коли пакет імпортовано, його назва використовується для отримання доступу до його вмісту. Після того, як пакет імпортовано,
```go
import "bytes"
```
пакет, що в свою чергу імпортує, може використовувати `bytes.Buffer`. Добре, якщо всі користувачі пакету можуть використовувати те саме ім'я для посилання на його вміст, а це означає, що ім'я пакету повинно бути гарним: коротким, лаконічним, таким, що викликає асоціації. За домовленістю, пакети мають назву з одного слова, написаного малими літерами; не слід використовувати підкреслення або mixedCaps. Зробіть ставку на стислість, оскільки всі, хто користуватиметься вашим пакетом, будуть багаторазово набирати цю назву. Але не турбуйтеся про унікальність імені. Ім'я пакета тільки за замовчуванням використовується під час імпорту; воно не повинно бути унікальним, і в рідкісних випадках, під час імпорту може бути вказано інше ім'я. У будь-якому разі, плутанина трапляється рідко, оскільки ім'я файлу в імпорті визначає, який саме пакет використовується.

Іншою домовленістю є те, що ім'я пакету є базовим ім'ям його вихідного каталогу; пакет у `src/encoding/base64` імпортується як `"encoding/base64"`, але має ім'я `base64`, а не, скажімо, `encoding_base64` чи `encodingBase64`.

Імпортер пакету використовуватиме назву для посилання на його вміст, тому експортовані назви у пакеті можуть використовувати цей факт, щоб уникнути повторень. (Не використовуйте нотацію `import .`, хоч це й, звісно, може спростити тести, що мають виконуватися поза пакетом, який вони тестують, але в інших випадках її слід уникати). Наприклад, тип буферизованого читача у пакеті `bufio` називається `Reader`, а не `BufReader`, оскільки користувачі сприймають його як `bufio.Reader`, що є зрозумілим і лаконічним іменем. Крім того, оскільки імпортовані об'єкти завжди адресуються за назвою пакету, `bufio.Reader` не конфліктує зі, скажімо, `io.Reader`. Аналогічно, функція для створення нових екземплярів `ring.Ring`, яка є визначеною як конструктор у Go, зазвичай називається `NewRing`, але оскільки `Ring` є єдиним типом, що експортується пакетом, і оскільки пакет називається `ring`, вона називається просто `New`, і користувачі пакету бачать її як `ring.New`. Використовуйте структуру пакетів для вибору вдалих назв.

Інший короткий приклад — функція `once.Do`; `once.Do(setup)` читається добре, і водночас краще не стане, якщо її перейменувати в щось накшталт `once.DoOrWaitUntilDone(setup)`. Довгі імена не роблять назви більш читабельними. У той час як коментарі можуть бути ціннішими, ніж довгі імена.
