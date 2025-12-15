# package

## Визначення (англ)

**Merriam-Webster**

as in *bundle*

a wrapped or sealed case containing an item or set of items "got a job sorting *packages* in the mail room"

as in *batch*

a number of things considered as a unitate "a whole *package* of cookies at once"

**Computerhope**

With software, a **package** is a module that can be added to any program to add additional options, features, or functionality. A package is often added to program using an "include" or "import" type of statement, as in the below Java code.

**Dev.to**

A collection of files, metadata, and scripts bundled together to be installed, upgraded, or removed as a single unit by a package management system.

**Debian Glossary**

(In Debian) See [binary package](https://wiki.debian.org/Glossary#binary-package) or [source package](https://wiki.debian.org/Glossary#source-package).

*Binary package*

An installable [.deb](https://wiki.debian.org/Glossary#dotdeb) file as opposed to the [source package](https://wiki.debian.org/Glossary#source-package) it's built from. The idea is that this is the "binary" compiled in the package building process (regardless of whether the output .deb contains a [binary](https://wiki.debian.org/Glossary#binary) executable, documentation, or indeed Linux kernel [source](https://wiki.debian.org/Glossary#source) code). See also [virtual package](https://wiki.debian.org/Glossary#virtual-package).

*Source package*

Can mean:

- A unit of upstream software (with a single build system), which may correspond to several separate [binary package](https://wiki.debian.org/Glossary#binary-package)s within Debian.

- The bundle of files ([.dsc](https://wiki.debian.org/Glossary#dotdsc) file, upstream tarball, etc) used as input to the package-building process.

## Визначення (укр)

*Варіанти перекладу: ПАКЕТ і ПАКУНОК*

**СУМ-20**

***Пакет:***

- Конверт із документом, перев. офіційного змісту

- Паперовий, поліетиленовий мішок або обгортка для пакування речей, продуктів і т. ін.

- Те саме, що **паку́нок**

- перен. Комплект взаємопов'язаних документів, пропозицій, що пропонуються до розгляду або затверджені одночасно

- спец. Стос. однорідних (перев. будівельних) матеріалів

- Індивідуа́льний (саніта́рний, перев'я́зувальний *і т. ін.)* паке́т – особливим чином упакований набір перев'язувального матеріалу для надання першої медичної допомоги

- Контро́льний паке́т а́кцій – частка від загальної кількості акцій, яка забезпечує її власникові вирішальний вплив на діяльність акціонерного товариства

- Паке́т [прикладни́х] програ́м, інформ. –  набір програм, признач. для розв'язання задач певного класу

***Пакунок:***

- Що-небудь, упаковане в паперову чи якусь іншу обгортку для транспортування, перенесення, перевезення або зберігання; пака (у 1, 2 знач.)

- чого, рідко. Купка зв'язаних предметів

**Словник термінів ДСТУ**

Набір файлів, метаданих і службових скриптів, об’єднаних у єдину одиницю для встановлення, оновлення або видалення за допомогою системи керування пакунками.

## Контекст у APT

У APT «package» — це базова одиниця, з якою працює менеджер пакунків.  
APT:

- завантажує пакунки,
- перевіряє залежності,
- встановлює або оновлює їх,
- видаляє або очищує,
- визначає їхній стан (broken, held, essential тощо).

## Можливі переклади

- **пакунок**
- пакет

## Аргументи за/проти

### «пакунок»

**За:**

- використовується в офіційних перекладах Debian, Ubuntu, KDE, GNOME;
- уникає омонімії зі словом «пакет» (пакет документів, пакет акцій);
- усталений у спільноті українських перекладачів FLOSS.

**Проти:**

- менш звичний для новачків, які переходять з російської.

### «пакет»

**За:**

- звичне слово для широкої аудиторії.

**Проти:**

- створює плутанину з «пакет документів», «пакет оновлень» (update bundle ≠ package);
- у Debian‑спільноті вважається некоректним.

## Обраний переклад

**пакунок**

## Примітки

- У всіх повідомленнях APT слід використовувати «пакунок» у називному відмінку та відповідні відмінки за контекстом.
- Уникаємо кальок типу «пакетний менеджер» → «менеджер пакунків».

# ✅ 1. Package у Debian — це НЕ “обгортка”, а **логічна одиниця ПЗ**

У Debian package — це:

- набір файлів,

- метадані,

- залежності,

- контрольні скрипти,

- версія,

- ім’я,

- архітектура,

- статус у системі.

І головне:

### ✅ Package існує навіть після встановлення.

Після встановлення:

- файли розпаковуються,

- але **метадані пакунка залишаються в системі**,

- dpkg продовжує знати, що це *пакунок*,

- APT може його оновити, видалити, перевірити залежності.

Тобто package не “зникає” після розпакування.

# ✅ 2. Package — це не архів, а **об’єкт керування**

У Debian:

- `.deb` — це архів

- але **package ≠ архів**

Package — це:

- ім’я: `bash`

- версія: `5.2.15-2`

- залежності: `libc6`, `libtinfo6`

- статус: installed, unpacked, half-configured, removed

- файли: `/bin/bash`, `/usr/share/doc/bash/*`

- скрипти: `postinst`, `prerm`, `postrm`

Тобто package — це **сутність**, яка має життєвий цикл.

# ✅ 3. Чому аналогія “пакунок = обгортка” не працює

Тому що:

### ❌ Пакунок не зникає після встановлення

У dpkg база `/var/lib/dpkg/status` містить записи про всі пакунки.

### ❌ Пакунок — це не просто набір файлів

Це набір файлів + метадані + залежності + скрипти.

### ❌ Пакунок — це не “обгортка”, а **одиниця керування**

APT працює з пакунками навіть після встановлення.

### ❌ Пакунок може бути встановлений, але не розпакований

Статус `unpacked`, `half-installed`, `half-configured` — це все стани пакунка.

### ❌ Пакунок може бути “пошкоджений” (broken)

Це не про архів, а про логічний стан залежностей.

# ✅ 4. Чому “пакунок” — правильне слово

Тому що в українській мові:

- **пакунок** — це компактна одиниця, що містить набір речей

- **пакет** — це або конверт, або пакет документів, або пакет акцій, або пакет послуг

У Debian:

- package — це **одиниця**, а не “пакет документів”

- package — це **цілісний об’єкт**, а не “набір окремих файлів”

Тобто “пакунок” ближче до концепту “unit”.

# ✅ 5. Найважливіше: package — це **не фізичний об’єкт**, а логічний

Пакунок залишається пакунком, бо dpkg/apt продовжують ним керувати.

Це як:

- автомобіль залишається автомобілем, навіть якщо ти зняв колеса

- користувач залишається користувачем, навіть якщо він не залогінений

- файл залишається файлом, навіть якщо він відкритий у пам’яті

# ✅ 6. Найкраща аналогія

Package у Debian — це **об’єкт**, який має:

- ім’я

- версію

- залежності

- файли

- статус

- життєвий цикл

Це **не архів**, а **сутність**, яку система знає, відстежує й керує.



**Уточнення:**

- **бінарний пакунок** (binary package)

- **вихідний пакунок** або **пакунок вихідних кодів** (source package)
  
  див окремі картки
