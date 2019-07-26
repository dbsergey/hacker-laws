# 💻📖 hacker-laws
[![All Contributors](https://img.shields.io/badge/all_contributors-5-purple.svg?style=flat-square)](#они-внесли-свой-вклад)

Законы, теории, принципы и модели, которые полезно знать разработчику.

- 🇺🇸 [English Version / Версия на Английском](https://github.com/dwmkerr/hacker-laws) - оригинальная версия о [Dave Kerr](https://github.com/dwmkerr).
- 🇨🇳 [中文 / Версия на Китайском](https://github.com/nusr/hacker-laws-zh) - спасибо [Steve Xu](https://github.com/nusr)!
- 🇰🇷 [한국어 / Версия на Корейском](https://github.com/codeanddonuts/hacker-laws-kr) - спасибо [Doughnut](https://github.com/codeanddonuts)!

---

<!-- vim-markdown-toc GFM -->

* [Вступление](#вступление)
* [Законы](#законы)
    * [Закон Амдала](#закон-амдала)
    * [Закон Брукса](#закон-брукса)
    * [Закон Конвея](#закон-конвея)
    * [Число Данбара](#число-данбара)
    * [Бритва Хэнлона](#бритва-хэнлона)
    * [Закон Хофштадтера](#закон-хофштадтера)
    * [Цикл хайпа и закон Амара](#цикл-хайпа-и-закон-амара)
    * [Закон Хайрама (Закон неявных интерфейсов)](#закон-хайрама-закон-неявных-интерфейсов)
    * [Закон Мура](#закон-мура)
    * [Закон Паркинсона](#закон-паркинсона)
    * [Закон Путта](#закон-путта)
    * [Закон сохранения сложности (закон Теслера)](#закон-сохранения-сложности-закон-теслера)
    * [Закон негерметичных абстракций](#закон-негерметичных-абстракций)
    * [Закон тривиальности](#закон-тривиальности)
    * [Философия Unix](#философия-unix)
    * [Модель Спотифай](#модель-спотифай)
    * [Закон Вадлера](#закон-вадлера)
* [Принципы](#принципы)
    * [Принцип Парето (Правило 80/20)](#принцип-парето-правило-8020)
    * [Принцип устойчивости (Закон Постела)](#принцип-устойчивости-закон-постела)
    * [SOLID](#solid)
    * [Принцип единственной ответственности](#принцип-единственной-ответственности)
    * [Принцип открытости/закрытости](#принцип-открытостизакрытости)
    * [Принцип подстановки Лисков](#принцип-подстановки-лисков)
    * [Принцип разделения интерфейса](#принцип-разделения-интерфейса)
    * [Принцип инверсии зависимостей](#принцип-инверсии-зависимостей)
    * [Принцип DRY](#принцип-dry)
    * [Принцип YAGNI](#принцип-yagni)
* [Список литературы](#список-литературы)
* [TODO](#todo)

<!-- vim-markdown-toc -->

---

## Вступление

Существует много законов, которые люди обсуждают, говоря о разработке. Этот репозиторий собрал в себе ссылки и обзоры наиболее распространённых. Пожалуйста, делитесь им и присылайте PR'ы!

❗: Этот репозиторий содержит объяснения некоторых законов, принципов и паттернов, но не _агитирует_ ни за один из них. Вопрос о том, стоит ли их применять, всегда будет предметом споров, и ответ на него в значительной степени зависит от того, над чем вы работаете.

## Законы

Ну, поехали!

### Закон Амдала

[Закон Амдала в Википедии](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%90%D0%BC%D0%B4%D0%B0%D0%BB%D0%B0)

> Закон Амдала - это формула, показывающая потенциал увеличения скорости вычислительных задач, которого можно достичь путём увеличения ресурсов системы. Обычно используется в параллельных вычислениях. Он может предсказать реальную выгоду от увеличения числа процессоров, учитывая ограничения распараллеливания программы.

Давайте для наглядности приведём пример. Если программа состоит из двух частей: части А, которая должна выполняться одним процессором, и части Б, которая может выполняться параллельно, тогда мы увидим, что добавление нескольких процессоров в систему может иметь ограниченное преимущество. Это потенциально может ускорить выполнение части Б, но скорость выполнения части А останется неизменной.

Диаграмма ниже показывает несколько примеров потенциального увеличения скорости:

![Диаграмма: Закон Амдала](./images/amdahls_law.png)

**(Источник изображения: авторство Daniels220, взято из Английской Википедии, Creative Commons Attribution-Share Alike 3.0 Unported, [https://en.wikipedia.org/wiki/File:AmdahlsLaw.svg](https://en.wikipedia.org/wiki/File:AmdahlsLaw.svg))**

Как можно видеть, программа с возможностью распараллеливания на 50% принесет очень мало пользы, всего 10 процессорных единиц, тогда как программа с возможностью распараллеливания на 95% может привести к значительному улучшению скорости на более чем тысячу процессорных единиц.

В то время как [Закон Мура](#закон-мура) замедляется, а скорость отдельных процессоров уменьшается, распараллеливание является ключом к повышению производительности. Этому можно считать отличным примером графическое программирование. C современными вычислениями на основе шейдеров отдельные пиксели или фрагменты могут отображаться параллельно — вот почему современные графические карты часто имеют много тысяч процессорных ядер (графических процессоров или шейдерных блоков).

Читайте также:
- [Закон Брукса](#закон-брукса)
- [Закон Мура](#закон-мура)

-----

### Закон Брукса

[Закон Брукса в Википедии](https://ru.wikipedia.org/wiki/%D0%9C%D0%B8%D1%84%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9_%D1%87%D0%B5%D0%BB%D0%BE%D0%B2%D0%B5%D0%BA%D0%BE-%D0%BC%D0%B5%D1%81%D1%8F%D1%86#%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%91%D1%80%D1%83%D0%BA%D1%81%D0%B0)

> Если проект не укладывается в сроки, то добавление рабочей силы задержит его ещё больше.

Считается, что часто попытка ускорить сдачу проекта, не укладывающегося в сроки, за счёт добавления людей в команду, приведёт к ещё более позднему сроку сдачи. Брукс поясняет, что это излишнее упрощение. Тем не менее, основная мысль заключается в том, что, с учетом роста рабочего времени программистов и издержек коммуникации, в краткосрочной перспективе скорость значительно снижается.

Распространённое выражение «Девять женщин не могут выносить ребёнка за один месяц» отсылает нас как раз к закону Брука. В частности, к тому факту, что некоторые виды работ нельзя поделить на части и запараллелить.

Эта мысль является центральной темой книги «[The Mythical Man Month](#список-литературы)».

Читайте также:

- [Death March](#todo)
- [Список литературы: The Mythical Man Month](#список-литературы)

---

### Закон Конвея

[Закон Конвея в Википедии](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%9A%D0%BE%D0%BD%D0%B2%D0%B5%D1%8F)

Этот закон предполагает, что технические рамки системы будут отражать структуру организации. Обычно его упоминают в контексте улучшения организации. В законе Конвея говорится, что, если организация разделена на небольшие отдельные команды, то и программное обеспечение будет разделено подобным образом. Если организация выстроена вокруг «вертикалей», которые ориентированы на улучшение и сервис, то система программного обеспечения будет отражать это.

Читайте также:

- [модель Спотифай](#модель-спотифай)

---

### Число Данбара

[Число Данбара в Википедии](https://ru.wikipedia.org/wiki/%D0%A7%D0%B8%D1%81%D0%BB%D0%BE_%D0%94%D0%B0%D0%BD%D0%B1%D0%B0%D1%80%D0%B0)

> Число Данбара — ограничение на количество постоянных социальных связей, которые человек может поддерживать. О каждом человеке, включённом в это число связей, вы точно можете сказать, кто это и как он связан с другими людьми. 
> Есть разногласия с точным числом.

Данбар предполагал, что человек может комфортно поддерживать только 150 стабильных связей. Он описал жизненную ситуацию, которая поможет определить число таких связей в вашей жизни: количество людей, которые не смутят вас своим появлением и кому вы будете рады в качестве собутыльника, если случайно столкнётесь в баре. Это число будет лежать где-то между 100 и 250.

Подобно отношениям между людьми, отношения разработчика с кодовой базой требуют усилий для поддержания. Когда мы сталкиваемся с большим проектом или занимаемся ведением нескольких проектов, мы опираемся на соглашения, политику и смоделированную процедуру масштабирования. Число Данбара важно принимать во внимание не только в вопросах роста офиса, но и при определении размера команды или для принятия решения о том, в какой момент структура должна инвестировать в инструментарий для поддержки и автоматизации логистических издержек. В контексте работы инженера число указывает на количество проектов (или на усреднённую сложность одного проекта), которые вы можете уверенно поддерживать единовременно.

Читайте также:

- [Закон Конвея](#закон-конвея)

### Бритва Хэнлона

[Бритва Хэнлона в Википедии](https://ru.wikipedia.org/wiki/%D0%91%D1%80%D0%B8%D1%82%D0%B2%D0%B0_%D0%A5%D1%8D%D0%BD%D0%BB%D0%BE%D0%BD%D0%B0)

> Никогда не приписывайте злому умыслу то, что адекватно объясняется глупостью.
>
> Роберт Джей Хэнлон

Этот принцип предполагает, что действие, приведшее к негативному результату, не является результатом злого умысла. Скорее, негативный результат связан с тем, что это действие и/или его последствия были не до конца ясны.

---

### Закон Хофштадтера

[Закон Хофштадтера в Википедии](https://ru.wikipedia.org/wiki/%D0%A5%D0%BE%D1%84%D1%88%D1%82%D0%B0%D0%B4%D1%82%D0%B5%D1%80,_%D0%94%D1%83%D0%B3%D0%BB%D0%B0%D1%81#%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%A5%D0%BE%D1%84%D1%88%D1%82%D0%B0%D0%B4%D1%82%D0%B5%D1%80%D0%B0)

> Любое дело всегда длится дольше, чем ожидается, даже если учесть закон Хофштадтера.
>
> Дуглас Хофштадтер

Кто-нибудь мог ссылаться на этот закон, глядя на оценку сроков выполнения чего-либо. Кажется очевидным, что мы не очень хороши в оценке сроков разработки. 

Из книги «[Gödel, Escher, Bach: An Eternal Golden Braid](#список-литературы)».

Читайте также:

- [Список литературы: Gödel, Escher, Bach: An Eternal Golden Braid](#список-литературы)

---

### Цикл хайпа и закон Амара

[Цикл хайпа в Википедии](https://ru.wikipedia.org/wiki/Gartner#%D0%A6%D0%B8%D0%BA%D0%BB_%D1%85%D0%B0%D0%B9%D0%BF%D0%B0)

> Мы склонны переоценивать эффект от технологии в краткосрочной перспективе и недооценивать эффект в долгосрочной перспективе.
>
> Рой Амара

Цикл хайпа является визуализацией кривых волнения и развития технологии во времени. Впервые был представлен компанией Gartner. Лучше показать на примере:

![Цикл хайпа](./images/gartner_hype_cycle.png)

**(Источник изображения: авторство Jeremykemp, взято из Английской Википедии, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=10547051)**

Если коротко, этот цикл показывает, что вокруг новой технологии обычно наблюдается взрыв ажиотажа относительно её потенциального воздействия. Команды часто поспешно _прыгают с головой_ в эту новую технологию, но в итоге разочаровываются результатом. Это может быть связано с тем, что технология ещё недостаточно развита или приложения в реальном мире ещё не до конца реализованы. По прошествии времени возможности технологии возрастают, и практическая польза от неё увеличивается. Что позволяет командам продуктивно использовать эту технологию. Рой Амара сформулировал это наиболее ёмко: «Мы склонны переоценивать эффект от технологии в краткосрочной перспективе и недооценивать эффект в долгосрочной перспективе».

---

### Закон Хайрама (Закон неявных интерфейсов)

[Закон Хайрама онлайн](http://www.hyrumslaw.com/)

> При достаточном количестве пользователей API
> не имеет особого значения, что вы пишите в документации:
> любые наблюдаемые варианты поведения вашей системы
> будут на кого-то влиять.
>
> Хайрам Райт

Закон Хайрама гласит, что, когда у вас есть _достаточно большое количество пользователей_ API, любое действия этого API (даже неопределённые в рамках публичной документации) в конечном итоге повлияют на кого-то. Тривиальный пример: нефункциональный элемент, такой, как время ответа API. Менее значительный пример: пользователи, которые опираются на использование регулярных выражений при определении **типа** ошибки API. Даже если публичная документация API не говорит ничего о тексте сообщения ошибки, явно указывая, что нужно смотреть на код ошибки, _некоторые_ пользователи могут использовать текст сообщения, и изменение этого текста приводит к поломке API у таких юзеров.

Читайте также:

- [Закон дырявых абстракций](#закон-дырявых-абстракций)
- [XKCD 1172](https://xkcd.com/1172/)

---

### Закон Мура

[Закон Мура в Википедии](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%9C%D1%83%D1%80%D0%B0)

> Количество транзисторов в интегральной схеме удваивается примерно каждые два года.

Часто используемый для иллюстрации скорости, с которой улучшаются технологии производства полупроводников и чипов, прогноз Мура был очень точным с 1970-х и до 2000-х годов. В последние годы эта тенденция немного изменилась, в частности из-за [физических ограничений на степень миниатюризации компонентов](https://ru.wikipedia.org/wiki/%D0%A2%D1%83%D0%BD%D0%BD%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D1%8D%D1%84%D1%84%D0%B5%D0%BA%D1%82). И тем не менее, достижения в области распараллеливания и потенциальные революционные изменения в технологии полупроводников, а также квантовые компьютеры могут означать, что закон Мура останется актуальным на протяжении следующих десятилетий.

---

### Закон Паркинсона

[Закон Паркинсона в Википедии](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%9F%D0%B0%D1%80%D0%BA%D0%B8%D0%BD%D1%81%D0%BE%D0%BD%D0%B0)

> Работа заполняет всё время, отпущенное на неё.

В оригинальном контексте этот закон был сформулирован в ходе изучения бюрократии. Это может иметь пессимистичный подтекст в случае применения к области разработки программного обеспечения. Теория заключается в том, что команда будет неэффективна вплоть до близкого дедлайна. Затем будет стремиться закончить работу к крайнему сроку. 

Если этот закон совместить с [законом Хофштадтера](#закон-хофштадтера), то картина окажется ещё более пессимистичной — работа заполнит всё отведённое на неё время и **всё равно займёт больше времени, чем ожидалось**.

Читайте также:

- [Законом Хофштадтера](#закон-хофштадтера)

---

### Закон Путта

[Закон Путта в Википедии](https://en.wikipedia.org/wiki/Putt%27s_Law_and_the_Successful_Technocrat)

> В технологиях доминируют два типа людей: те, кто понимает, что им не удается, и те, кто управляет тем, что они не понимают.

Закон Путта часто сопровождается следствием Путта:

> Каждая техническая иерархия со временем развивает инверсию компетенций.

Из этого закона следует, что из-за разницы в критериях отбора и тенденциях в процессах организации групп, на разных рабочих уровнях технических организаций будет некоторое число высококвалифицированных людей и людей, занимающих руководящие позиции, которые не будут понимать сложности и проблемы той работы, которой занимаются. Это можно связать с [Принципом Парето](#принцип-парето-правило-8020) и [Законом Дилберта](#TODO).

Впрочем, стоит подчеркнуть, что подобные законы являются обобщениями и могут применяться лишь к организациям _некоторых_ типов и не применяться к другим.

Читайте также:

- [Принцип Парето](#принцип-парето-правило-8020)
- [Закон Дилберта](#TODO).

---


### Закон сохранения сложности (закон Теслера)

[Закон сохранения сложности в Википедии](https://en.wikipedia.org/wiki/Law_of_conservation_of_complexity)

Закон гласит, что в системе существует определённый уровень сложности, который невозможно уменьшить.

В системе изначально существует «непреднамеренная» сложность. Это следствие плохой структуры, ошибок или плохого моделирования решения проблемы. Непреднамеренная сложность может быть уменьшена (или полностью устранена). Однако определённая сложность является «естественной» и связана со сложностью решаемой проблемы. Этот вид сложности может перемещаться, но её нельзя устранить полностью. 

Одна интересная особенность этого закона: предполагается, что даже при упрощении всей системы целиком, естественная сложность не уменьшается, а _перекладывается на плечи пользователя_. Из-за этого усложняется поведение, ожидаемое от пользователя.

---

### Закон негерметичных абстракций

[Закон негерметичных абстракций в Википедии](https://en.wikipedia.org/wiki/Leaky_abstraction)

> Все нетривиальные абстракции, в какой-то степени, негерметичны.
> 
>  Джоэл Спольски

Этот закон гласит, что абстракции, используемые в некоторых случаях для упрощения сложных систем, могут «вытекать» из элементов базовой системы. Это заставляет абстракцию вести себя неожиданным образом.

Примером может служить процесс загрузки файла и чтение его содержимого. API файловой системы является _абстракцией_ низкоуровневых систем ядра, которые, в свою очередь, являются абстракциями над физическими процессами изменения данных на диске (или флеш-памяти SSD). В большинстве случаев абстракция обработки файла в виде потока двоичных данных будет работать. Однако для магнитного накопителя последовательное чтение данных будет *значительно* быстрее чем рандомный доступ (из-за увеличения количества служебных ошибок). Но в случае с SSD-диском такие издержки отсутствуют. Для понимания этого примера потребуется разобраться с основами. Например, каталоги файлов в базе данных структурированы таким образом, чтобы снизить издержки при рандомном доступе. «Утечки» абстракций должны быть предусмотренным разработчиком при реализации.

Пример выше становится тем сложнее, чем _больше_ абстракций вводится. Операционная система Linux позволяет получать доступ к файлам по сети, но локально представлена в виде «нормальных» файлов. Эта абстракция «протечёт», если в сети произойдёт сбой. Если разработчик будет рассматривать файлы как «нормальные» при работе через сеть, не предусмотрев возможность сбоев и задержек, его решения будут в корне неверны.

В статье, описывающей данный закон, говорится, что исходная проблема потенциально _усложняется_ в случаях чрезмерной зависимости от абстракций и плохого понимания основных процессов.

Читайте также:

- [Закон Хайрама (Закон неявных интерфейсов)](#закон-хайрама-закон-неявных-интерфейсов)

Реальный пример:

- [Медленный запуск Photoshop](https://forums.adobe.com/thread/376152) - проблема, с которой я столкнулся. Photoshop медленно запускался, иногда это занимало несколько минут. Похоже, проблема была в том, что программа при запуске считывала информацию о дефолтном принтере. Если принтер был сетевым, то этот процесс мог занимать неприлично много времени. Абстракция работы с сетевым принтером была той же, что для работы с локальным принтером. Не был предусмотрен сценарий ситуации с плохим качеством подключения у клиента.  

---

### Закон тривиальности

[Закон тривиальности в Википедии](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D1%82%D1%80%D0%B8%D0%B2%D0%B8%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D1%81%D1%82%D0%B8)

Этот закон предполагает, что группы будут тратить больше времени на тривиальные или косметические задачи, нежели на серьёзные и существенные.

В качестве примера приводится вымышленный комитет, работа которого заключалась в согласовании проекта атомной электростанции. Члены комитета проводят большую часть своего времени за обсуждением структуры велосипедного навеса, а не гораздо более важного проекта самой электростанции. Бывает трудно внести ценный вклад в дискуссию на очень большие и сложные темы без высокой степени предметной экспертизы или подготовки. Тем не менее, люди хотят вносить ценный вклад. Отсюда возникает тенденция уделять слишком много времени мелким деталям, которые легко обосновываются, но не обязательно имеют особое значение.

Вымышленный пример, рассмотренный выше, привел к использованию термина «Bike Shedding» (_если переводить дословно, то получится что-то вроде «сарая для велосипедов»_) в качестве выражения для траты времени на тривиальные детали.

---

### Философия Unix

[Философия Unix в Википедии](https://ru.wikipedia.org/wiki/%D0%A4%D0%B8%D0%BB%D0%BE%D1%81%D0%BE%D1%84%D0%B8%D1%8F_Unix)

Философия Unix заключается в том, что компонент программного обеспечения должен быть небольшого размера и сфокусирован на идеальном исполнении одной специфичной задачи. Это может упростить создание систем путем компоновки небольших, простых, четко определенных модулей, а не путём использования больших, сложных, многоцелевых программ.

Современные практики, такие как «Архитектура Микросервисов», могут рассматриваться как применение этого закона. Сервисы небольшие, сфокусированы на одной специфичной задаче, что позволяет создать сложное поведение путём составления простых строительных блоков.

---

### Модель Спотифай

[Модель Спотифай в Википедии](https://ru.wikipedia.org/wiki/Spotify_Model)

Модель Спотифай — подход к организации команды и структуре компании, которая была популяризирована компанией-разработчиком Spotify. В этой модели команды организованы вокруг функций, а не технологий.

Модель Спотифай также популяризирует концепты «Отрядов», «Племён», «Отделов» и «Гильдий», которые являются компонентами их организационной структуры: каждый из «отрядов» сфокусирован на отдельной части функциональности продукта, как то поиск или плейлисты, что позволяет им становиться экспертами в своих областях. На следующем уровне взаимодействия «отряды» Спотифай с общей или схожей миссией объединяются в «племена», проводя периодические (порой даже спонтанные) собрания чтобы скорректировать общие цели. «Отделы» состоят из сотрудников одного профиля (например, разработчики или тестировщики), которые регулярно встречаются, чтобы убедиться в использовании новейших трендов и технологий, обмениваться знаниями и эффективно переиспользовать существующие решения. «Гильдия» же представляет собой менее формальную и включающую в себя большее количество людей группу: так, гильдия тестировщиков состоит не только из широкого круга тестировщиков (включая и автоматизаторов, и специалистов по мануальному тестированию), но и из программистов, которые хотят лучше понимать процессы тестирования и вносить свой вклад в деятельность в этом направлении.

![Модель Спотифай](./images/spotify.jpg)

- __Squad__ — отряд, эквивалент скрам-команды; автономен на столько, на сколько это возможно;
- __Tribe__ — племя, организованы по принципу минимальной взаимозависимости, чаще всего организуется на уровне офиса до 100 человек;
- __Chapter__ — отдел, объединяет людей по опыту или профилю;
- __Guild__ — гильдия, сообщество с обищим интересами; не зависит от струтуры «племён»;
- __PO__ — руководитель проекта (product owner).

Читайте также:

- [Список литературы: Spotify engineering culture](#список-литературы)

---

### Закон Вадлера

[Закон Вадлера на wiki.haskell.org](https://wiki.haskell.org/Wadler's_Law)

> В любой конструкции языка время, затрачиваемое на обсуждение функции из этого списка, пропорционально двойке, возведённой в степень позиции в списке.
> 
> 0. Семантика
> 1. Синтаксис
> 2. Лексический синтаксис
> 3. Лексический синтаксис комментариев
> 
> (Короче говоря, на каждый час, потраченный на семантику, придётся 8 часов обсуждения синтаксиса комментариев).

Аналогично [Закону тривиальности](#закон-тривиальности) закон Вадлера гласит, что при проектировании языка время, потраченное на структурные особенности, непропорционально велико в сравнении с важностью этих функций. 

Читайте также:

- [Закон тривиальности](#закон-тривиальности)

---

## Принципы

Принципы больше похожи на гайдлайны для дизайна системы.

### Принцип Парето (Правило 80/20)

[Принцип Парето в Википедии](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%BA%D0%BE%D0%BD_%D0%9F%D0%B0%D1%80%D0%B5%D1%82%D0%BE)

> Большинство вещей в жизни распределяются неравномерно.

В некоторых случаях основной результат достигается небольшими ресурсами:

- 80% от общего объёма кода при разработке программного обеспечения пишется за 20% от выделяемого времени (и напротив, самые сложные 20% кода отнимают 80% времени)
- 20% усилий дают 80% результата
- 20% работы обеспечивают 80% дохода
- 20% багов приводят к 80% поломок

В 1940-х американо-румынский инженер доктор Джозеф Юран, которому приписывают создание контроля качества, [начал применять принцип Парето в вопросах качества](https://en.wikipedia.org/wiki/Joseph_M._Juran).

Этот принцип также известен как правило 80/20.  

Примеры из реальной жизни:

- В 2002 г. Майкрософт сообщила, что после исправления 20% багов, о которых сообщалось чаще всего, 80% связанных ошибок и поломок в Windows и MS Office просто пропадёт ([Источник](https://www.crn.com/news/security/18821726/microsofts-ceo-80-20-rule-applies-to-bugs-not-just-features.htm)).

---

### Принцип устойчивости (Закон Постела)

[Принцип устойчивости в Википедии](https://en.wikipedia.org/wiki/Robustness_principle)

> Будьте консервативны в том, что вы делаете и либеральны в том, что принимаете от других.

Этот принцип часто применяется при разработке серверных приложений. То, что вы посылаете другим, должно быть минималистичным и совместимым насколько это возможно. Но вы должны предусмотреть обработку несовместимого ввода. 

Целью этого принципа является построение прочных систем, которые могут обработать плохо форматированный ввод, если смысл этого ввода понятен. Впрочем, приём неправильного ввода имеет потенциальные последствия для безопасности. Особенно если процесс обработки такого ввода плохо протестирован.  

---

### SOLID

Это акроним, который расшифровывается следующим образом:

* S: [Принцип единственной ответственности](#принцип-единственной-ответственности)
* O: [Принцип открытости/закрытости](#принцип-открытостизакрытости)
* L: [Принцип подстановки Барбары Лисков](#принцип-подстановки-барбары-лисков)
* I: [Принцип разделения интерфейса](#принцип-разделения-интерфейса)
* D: [Принцип инверсии зависимостей](#принцип-инверсии-зависимостей)

Это ключевые принципы [Объектно-ориентированного программирования](#todo). Такие принципы проектирования должны помочь разработчикам создавать более простые в поддержке и обслуживании системы.

### Принцип единственной ответственности

[Принцип единственной ответственности в Википедии](https://ru.wikipedia.org/wiki/%D0%9F%D1%80%D0%B8%D0%BD%D1%86%D0%B8%D0%BF_%D0%B5%D0%B4%D0%B8%D0%BD%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D0%BE%D0%B9_%D0%BE%D1%82%D0%B2%D0%B5%D1%82%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D0%BE%D1%81%D1%82%D0%B8)

> Каждый модуль или класс должен иметь одну единственную ответственность. 

Первый из пяти принципов [SOLID](#solid). Этот принцип гласит, что модуль или класс должен делать всего одну вещь. В практическом смысле это означает, что одно маленькое изменение при доработке программы должно требовать изменения только в одном компоненте. Например, изменение в механизме проверки сложности пароля должно потребовать изменения только в одной части программы.

Теоретически это должно делать код более надёжным и простым для изменений. Знание, что изменённый компонент несёт на себе единственную ответственность, означает, что _тестирование_ этого изменения будет простым. Возвращаясь к предыдущему примеру, изменения в компоненте проверки сложности пароля должны повлиять только на часть программы, отвечающую за проверку пароля. Гораздо сложнее рассуждать о влиянии изменения в компоненте, у которого сразу несколько функций.

Читайте также: 

- [Объектно-ориентированное программирование](#todo)
- [SOLID](#solid)

---

### Принцип открытости/закрытости

[Принцип открытости/закрытости в Википедии](https://ru.wikipedia.org/wiki/%D0%9F%D1%80%D0%B8%D0%BD%D1%86%D0%B8%D0%BF_%D0%BE%D1%82%D0%BA%D1%80%D1%8B%D1%82%D0%BE%D1%81%D1%82%D0%B8/%D0%B7%D0%B0%D0%BA%D1%80%D1%8B%D1%82%D0%BE%D1%81%D1%82%D0%B8)

> Сущности должны быть открыты для расширения, но закрыты для изменения.

Второй из пяти принципов [SOLID](#solid). Этот принцип говорит, что сущности (классы, модули, функции и прочее) должны иметь возможность _расширять_ своё поведение, но их существующее поведение не должно _изменяться_.

В качестве гипотетического примера представьте модуль, который превращает разметку Markdown в HTML-документ. Если можно добавить в модуль обработку новых возможностей Markdown без изменения основного поведения модуля, то он будет считаться открытым для расширения. Если пользователь _не_ может изменить в модуле стандартную обработку синтаксиса Markdown, то такой модуль будет считаться _закрытым_ для изменений.

Этот принцип имеет особое значение для объектно-ориентированного программирования, в рамках которого мы можем создавать модули, простые в расширении, но должны избегать создания объектов, поведение которых меняется неожиданным образом.

Читайте также: 

- [Объектно-ориентированное программирование](#todo)
- [SOLID](#solid)

---

### Принцип подстановки Барбары Лисков

[Принцип подстановки Барбары Лисков в Википедии](https://ru.wikipedia.org/wiki/%D0%9F%D1%80%D0%B8%D0%BD%D1%86%D0%B8%D0%BF_%D0%BF%D0%BE%D0%B4%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B8_%D0%91%D0%B0%D1%80%D0%B1%D0%B0%D1%80%D1%8B_%D0%9B%D0%B8%D1%81%D0%BA%D0%BE%D0%B2)

> Должна быть возможность заменить тип на подтип без поломки системы.

_(от редактора)_
> Наследующий класс должен дополнять, а не замещать поведение базового класса.

Третий из пяти принципов [SOLID](#solid). Этот принцип указывает, что, если компонент зависит от определённого типа, то должна быть возможность использовать подтип этого типа (производную от типа) без поломки всей системы или необходимости знать детали того, что это за подтип.

В качестве примера представьте, что у нас есть метод, который читает XML-документ из файла. Если метод использует в качестве основы тип 'file', то мы должны иметь возможность использовать в функции и любое производное от 'file'. Если 'file' поддерживает поиск в обратном порядке, а парсер XML использует эту возможность, и при этом подтип 'network file' выдаёт ошибку при попытке поиска в обратном порядке, тогда подтип 'network file' нарушает описываемый принцип.

Этот принцип имеет особое значение для объектно-ориентированного программирования, где иерархия типов должна проектироваться аккуратно, чтобы не запутать пользователей системы.

Читайте также: 

- [Объектно-ориентированное программирование](#todo)
- [SOLID](#solid)

---

### Принцип разделения интерфейса

[Принцип разделения интерфейса в Википедии](https://ru.wikipedia.org/wiki/%D0%9F%D1%80%D0%B8%D0%BD%D1%86%D0%B8%D0%BF_%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F_%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D1%84%D0%B5%D0%B9%D1%81%D0%B0)

> Программные сущности не должны зависеть от методов, которые они не используют.

Четвёртый из пяти принципов [SOLID](#solid). Этот принцип говорит, что клиенты компонента не должны зависеть от функций этого компонента, если они не используют их непосредственно.

Представьте, например, что у нас есть компонент, читающий XML из файла. Он должен только читать байты, двигаясь вперёд или назад по файлу. Если этот метод потребуется изменить потому, что в файловую структуру внесены несвязанные с ним изменения (например, обновление системы безопасности для доступа к файлу), тогда принцип будет нарушен. 

Этот принцип особо актуален для объектно-ориентированного программирования, где интерфейсы, иерархии и абстрактные типы должны стремиться к минимизации [зацепления](#todo) между разными компонентами. [Утиная типизация](#todo) — методология, которая обеспечивает соблюдение этого принципа при помощи исключения явных интерфейсов.

Читайте также:

- [Объектно-ориентированное программирование](#todo)
- [SOLID](#solid)
- [Утиная типизация](#todo)
- [Зацепление](#todo)

---

### Принцип инверсии зависимостей

[Принцип инверсии зависимостей в Википедии](https://ru.wikipedia.org/wiki/%D0%9F%D1%80%D0%B8%D0%BD%D1%86%D0%B8%D0%BF_%D0%B8%D0%BD%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B8_%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D0%B5%D0%B9)

> Высокоуровневые модули не должны зависеть от низкоуровневой реализации.

Пятый из принципов [SOLID](#solid). Из этого принципа следует, что высший уровень управляющих компонентов не должен знать о деталях реализации зависимостей.

В качестве примера представьте, что у нас есть программа, которая считывает мета-данные с сайта. Мы предполагаем, что главный компонент должен знать о компоненте, занимающимся скачиванием контента с сайта, а затем и о компоненте, считывающем мета-данные. Если мы примем во внимание инверсию зависимостей, то основной компонент будет зависеть только от абстрактного компонента, который может извлекать байтовые данные, а затем от абстрактного компонента, который мог бы считывать метаданные из байтового потока. Основной компонент не будет знать о TCP/IP, HTTP, HTML и прочем.

Этот принцип сложный. Может показаться, что он «инвертирует» вероятные зависимости системы (отсюда и название). На практике это также означает, что отдельный управляющий компонент должен гарантировать, что используются правильные реализации абстрактных типов (например, в предыдущем примере _нечто_ должно по-прежнему предоставлять компоненту чтения метаданных загрузчик файлов HTTP и средство чтения метатегов HTML). Это также касается таких шаблонов, как [Инверсия управления](#todo) и [Внедрение зависимости](#todo).

Читайте также:

- [Объектно-ориентированное программирование](#todo)
- [SOLID](#solid)
- [Inversion of Control](#todo)
- [Dependency Injection](#todo)

---

### Принцип DRY

[Принцип DRY в Википедии](https://ru.wikipedia.org/wiki/Don%E2%80%99t_repeat_yourself)

> Каждая часть знания должна иметь единственное, непротиворечивое и авторитетное представление в рамках системы.

DRY это акроним от фразы _Don't Repeat Yourself_ («Не повторяй себя»). Этот принцип призван помочь разработчикам избежать повторений в коде и хранить информацию в одном месте. Был впервые описан в 1999 году в книге [The Pragmatic Developer](https://en.wikipedia.org/wiki/The_Pragmatic_Programmer) Эндрю Ханта и Дейва Томаса.

> Принципу DRY полностью противоположен принцип _WET_ — Write Everything Twice или We Enjoy Typing (Пиши всё дважды или Мы любим печатать).

На практике, если у вас есть два одинаковых куска кода в двух или более местах, то вы можете воспользоваться принципом DRY и объединить их в один, переиспользуя там, где он необходим.

Читайте также:

- [Список литературы: The Pragmatic Developer](https://en.wikipedia.org/wiki/The_Pragmatic_Programmer)

---

### Принцип YAGNI

[Принцип YAGNI в Википедии](https://ru.wikipedia.org/wiki/YAGNI)

Акроним _**Y**ou **A**ren't **G**onna **N**eed **I**t_ (англ. Вам это не понадобится).

> Всегда имплементируйте функционал, когда он вам действительно нужен, и не делайте этого, когда лишь предвидите необходимость в нем.
>
> ([Рон Джеффриз](https://twitter.com/RonJeffries)) (Соавтор методологии экстремального программирования и автор книги "Extreme Programming Installed")

Данный принцип _Экстремального Программирования_ предполагает, что разработчики имплементируют лишь тот функционал, который необходим для выполнения текущих требований, и стремятся не предсказывать будущие требования, имплементируя то, что может понадобиться позже.

Соблюдение принципа должно уменьшить количество неиспользуемого кода и избежать затрат усилий и времени на функционал, который не имеет ценности.

Читайте также:

- [Список литературы: Extreme Programming Installed](#список-литературы)


---

## Список литературы

Если вас заинтересовали перечисленные концепции, то вам могут понравиться следующие материалы:

- [Закон Амдала](http://ssd.sscc.ru/en/content/%D0%B7%D0%B0%D0%BA%D0%BE%D0%BD-%D0%B0%D0%BC%D0%B4%D0%B0%D0%BB%D0%B0), Supercomputer Software Department
- [Закон Амдала](https://medium.com/german-gorelkin/amdahls-law-79a8edb040e2), Герман Горелкин, 11 декабря 2018
- [The Mythical Man Month - Frederick P. Brooks Jr.](https://www.goodreads.com/book/show/13629.The_Mythical_Man_Month) - Классический труд о разработке ПО. [Закон Брукса](#закон-брукса) в центре повествования.
- [Gödel, Escher, Bach: An Eternal Golden Braid - Douglas R. Hofstadter.](https://www.goodreads.com/book/show/24113.G_del_Escher_Bach) - Эту книгу сложно классифицировать. [Закон Хофштадтера](#закон-хофштадтера) описан именно в этой книге.
- [Spotify engineering culture](https://labs.spotify.com/2014/03/27/spotify-engineering-culture-part-1/)
- [How to Build Your Own “Spotify Model”](https://medium.com/the-ready/how-to-build-your-own-spotify-model-dce98025d32f)
- [The Pragmatic Developer](https://en.wikipedia.org/wiki/The_Pragmatic_Programmer)
- [Extreme Programming Installed - Ron Jeffries, Ann Anderson, Chet Hendrikson](https://www.goodreads.com/en/book/show/67834) - Покрывает ключевые принципы методологии экстремального программирования.

## TODO

Привет! Если вы это читаете, то вы перешли по ссылке на статью, которая ещё не написана. Простите за это! Я работаю над этим.

Не стесняйтесь [заводить issue](https://github.com/solarrust/hacker-laws/issues) с пожеланиями или [присылайте Pull Request](https://github.com/solarrust/hacker-laws/pulls) со своими правками или новыми темами. 

---

## Они внесли свой вклад

Большое спасибо этим прекрасным людям ([что значат emoji?](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
<table><tr><td align="center"><a href="https://aceof.github.io/"><img src="https://avatars2.githubusercontent.com/u/16652418?v=4" width="100px;" alt="Alexandr Kizilow"/><br /><sub><b>Alexandr Kizilow</b></sub></a><br /><a href="#content-ACEof" title="Content">🖋</a></td><td align="center"><a href="https://github.com/natashta"><img src="https://avatars1.githubusercontent.com/u/15847929?v=4" width="100px;" alt="Natalia Ryzhova"/><br /><sub><b>Natalia Ryzhova</b></sub></a><br /><a href="#content-natashta" title="Content">🖋</a></td><td align="center"><a href="https://github.com/rikkalo"><img src="https://avatars1.githubusercontent.com/u/3524991?v=4" width="100px;" alt="Anastasia Lopatina"/><br /><sub><b>Anastasia Lopatina</b></sub></a><br /><a href="#content-rikkalo" title="Content">🖋</a></td><td align="center"><a href="https://github.com/nksoff"><img src="https://avatars2.githubusercontent.com/u/1710024?v=4" width="100px;" alt="Nikita Slimov"/><br /><sub><b>Nikita Slimov</b></sub></a><br /><a href="#content-nksoff" title="Content">🖋</a></td><td align="center"><a href="https://github.com/Realetive"><img src="https://avatars1.githubusercontent.com/u/2073959?v=4" width="100px;" alt="Realetive"/><br /><sub><b>Realetive</b></sub></a><br /><a href="#content-Realetive" title="Content">🖋</a></td></tr></table>

<!-- ALL-CONTRIBUTORS-LIST:END -->
