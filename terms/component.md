# component

## Визначення (англ)

**Debian archive terminology**  
A component is a subdivision of a Debian distribution that groups packages based on licensing, dependency requirements, and compliance with Debian Free Software Guidelines (DFSG). Components appear in repository paths and define which packages are available to the user.

Common components: `main`, `contrib`, `non-free`, `non-free-firmware`.

## Визначення (укр)

**Загальне визначення**  
Компонент — це частина дистрибутива Debian, яка об’єднує пакунки за ліцензійними умовами та відповідністю принципам DFSG.

**Debian / APT**  
Компонент — це логічний розділ сховища Debian, який визначає, які пакунки доступні користувачу.  
Компоненти відображаються у шляху сховища, наприклад:

deb http://deb.debian.org/debian  stable main contrib non-free


Основні компоненти:

- **main** — повністю вільне ПЗ, яке відповідає DFSG;
- **contrib** — вільне ПЗ, що залежить від невільного;
- **non-free** — невільне ПЗ, яке не відповідає DFSG;
- **non-free-firmware** — невільні прошивки, виділені в окремий компонент починаючи з Debian 12.

## Контекст у APT

Компоненти визначають:

- які пакунки доступні для встановлення;
- які залежності можуть бути задоволені;
- чи дозволено встановлювати невільне ПЗ;
- які індекси (`Packages`, `Sources`) APT завантажує під час `apt update`.

APT читає компоненти з:

- `/etc/apt/sources.list`
- `/etc/apt/sources.list.d/*.list`

Приклад:

deb http://deb.debian.org/debian  bookworm main contrib non-free-firmware


Тут дистрибутив — *bookworm*, а компоненти — *main*, *contrib*, *non-free-firmware*.

## Можливі переклади

- **компонент**
- секція (небажано)
- розділ (може вводити в оману)
- частина (занадто загально)

## Аргументи за/проти

### «компонент»

**За:**
- усталений переклад у Debian/Ubuntu;
- відповідає англійському component;
- природно звучить у технічному контексті;
- не має омонімії;
- добре поєднується з іншими термінами:  
  - компонент сховища  
  - компонент дистрибутива  
  - компоненти main/contrib/non-free.

**Проти:**
- іншомовне походження, але це прийнятно для технічних термінів.

### «секція»

**Проти:**
- у Debian вже існує інший термін *section* (для класифікації пакунків: admin, utils, net, doc);
- може спричинити плутанину.

### «розділ»

**Проти:**
- надто загальне слово;
- не передає ліцензійної природи компонентів.

## Обраний переклад

**компонент**

## Примітки

- Компонент ≠ секція пакунка.  
  Секція — це класифікація пакунків (admin, utils, net), а компонент — це частина сховища (main, contrib, non-free).
- Компоненти визначають доступність пакунків, але не їхній стан у системі.
- Починаючи з Debian 12, прошивки винесені в окремий компонент `non-free-firmware`.

