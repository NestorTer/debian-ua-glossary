# distribution

## Визначення (англ)

**General Linux terminology**  
A distribution is a complete operating system built from a curated collection of packages, configuration defaults, and release policies.

**Debian / APT**  
In APT, a distribution is a logical branch of the Debian archive (such as stable, testing, unstable), representing a moving or fixed set of package versions. Distributions are identified by suites (stable, testing, unstable) and codenames (bookworm, trixie, sid).

## Визначення (укр)

**Загальне визначення**  
Дистрибутив — це повноцінна операційна система, сформована з узгодженого набору пакунків, налаштувань і політик випуску.

**Debian / APT**  
У контексті APT дистрибутив — це логічна гілка архіву Debian, яка визначає набір доступних версій пакунків.  
Дистрибутиви мають:

- **suite** (гілку): stable, testing, unstable;
- **codename** (кодову назву): bookworm, trixie, sid;
- **release metadata**: файли `InRelease`, `Release`, `Release.gpg`.

Дистрибутив визначає, які версії пакунків будуть candidate version для встановлення.

## Контекст у APT

APT працює з дистрибутивами через:

- записи у `sources.list` (наприклад, `deb http://deb.debian.org/debian stable main`);
- файли релізу (`InRelease`, `Release`);
- механізм вибору candidate version.

Основні дистрибутиви Debian:

- **stable** — стабільний, фіксований набір версій;
- **testing** — майбутній stable, оновлюється регулярно;
- **unstable (sid)** — найсвіжіші пакунки, постійний рух;
- **oldstable**, **oldoldstable** — попередні стабільні релізи.

Дистрибутиви також поділяються на компоненти:

- **main** — вільне ПЗ;
- **contrib** — вільне ПЗ, що залежить від невільного;
- **non-free** — невільне ПЗ.

## Можливі переклади

- **дистрибутив**
- дистрибуція (небажано)
- дистрибутів (помилково)
- дистро (жаргон)

## Аргументи за/проти

### «дистрибутив»

**За:**

- усталений термін у Debian, Ubuntu, KDE, GNOME;
- відповідає міжнародній практиці;
- природно поєднується з іншими термінами:  
  - дистрибутив Debian  
  - дистрибутив stable  
  - дистрибутив testing  
- не має омонімії.

**Проти:**

- іншомовне походження, але це прийнятно для технічних термінів.

### «дистрибуція»

**Проти:**

- калька з англійської distribution у значенні “розповсюдження”;
- не усталене в Linux‑культурі;
- звучить неприродно у складених термінах.

## Обраний переклад

**дистрибутив**

## Примітки

- Дистрибутив ≠ реліз.  
  Реліз — це конкретний стан дистрибутива, описаний файлами `InRelease`/`Release`.
- Suite (stable/testing/unstable) ≠ codename (bookworm/trixie/sid).  
  Але обидва належать до поняття дистрибутива.
- У `sources.list` можна вказувати або suite, або codename — це впливає на поведінку оновлень.
