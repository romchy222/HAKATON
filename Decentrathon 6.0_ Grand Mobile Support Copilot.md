ПАРТНЕРСКИЕ КЕЙСЫ · 30-31 ОКТЯБРЯ 2026

Grand Mobile × Decentrathon 6.0 рус

3 задачи от казахстанской игровой студии. Каждая выросла из реальной

боли продакшена с более чем 500 тыс. игроков в сутки. Решения не

требуют доступа к коду игры: вы строите отдельный сервис или модель на

наших данных, мы интегрируем.

с открытия задач до человек в команде кейса, один на языков игры,

дедлайна команду включая казахский

О Grand Mobile

Grand Mobile \- мобильная ролевая игра в открытом мире. Игрок создает персонажа,

устраивается на работу, вступает во фракцию или семью, покупает дом, машину и бизнес,

живет в городе вместе с тысячами других игроков на одном сервере. Можно быть таксистом,

полицейским, мэром или гангстером.

Игру делает студия из Казахстана, резидент Astana Hub. У игры более 55 млн установок и

более 500 тыс. игроков ежедневно. Серверы работают в СНГ, Казахстане, Узбекистане,

Европе и Латинской Америке. Клиент локализован на русский, казахский, узбекский,

английский, испанский и португальский.

Технически это собственный движок и клиент под Android и iOS, серверная игровая логика,

лаунчер и весь внутриигровой интерфейс на Flutter, бэкенд на Node.js с MariaDB и ClickHouse.

Каждое действие игрока с деньгами, каждая авторизация, каждое сообщение в чате и

каждое действие администратора пишутся в аналитические логи. На этих логах и построены

кейсы.

Как устроены кейсы

Мы не передаем исходный код игры, бинарники, протокол и доступ к серверам или API. Это

осознанное ограничение, и все кейсs спроектированы под него: вы получаете

анонимизированную выгрузку данных и четкий контракт входа и выхода, а сдаете

автономный сервис или модель. Интеграция в игру \- наша работа после хакатона.

| Что вы получаете | Что мы не даем |
| :---- | :---- |
| Анонимизированные датасеты вJSONL, CSV и ARB.Выборку для валидации, отобраннуюпо тому же рецепту, что скрытыйтест.Описание схем, таксономиикатегорий, правила игры. | Исходный код, сборки, протоколклиент-сервер.Доступ к боевым или тестовым API ибазам.Неанонимизированные данныеигроков.Скрытый тестовый набор дозавершения оценки. |

У каждого кейса есть обязательное ядро и бонусная часть. Ядро реально сделать за 36

часов командой из 3-4 человек. Бонус отличает хорошее решение от победного, но без ядра

не оценивается. Готового продакшен-решения никто не ждет: жюри смотрит на глубину

понимания задачи, качество MVP, честность метрик и ясность кода.

Команда выбирает один кейс. Стек свободный. Предобученные модели и открытые датасеты

разрешены при соблюдении лицензий. Внешние LLM-API разрешены везде, где в

ограничениях кейса не сказано иначе, но стоимость обработки нужно посчитать и указать в

отчете.

Данные и конфиденциальность

Все выгрузки анонимизированы до передачи. Идентификаторы аккаунтов, получателей и

групп заменены на соленые хэши, уникальные в пределах кейса. Время округлено до

минуты. В текстах чата и тикетов замаскированы телефоны, адреса электронной почты и

последовательности из 7 и более цифр. Никнеймы персонажей в чате заменены на токен

 \<nick\> , в обращениях на синтетические имена, одинаковые по всему набору.

Принимая данные, команда соглашается с условиями:

Использовать данные только для решения кейса в рамках Decentrathon 6.0.

Не пытаться деанонимизировать игроков, устройства или адреса.

Не публиковать данные и производные выборки, в том числе в публичных репозиториях.

Репозиторий решения может быть публичным, данные в нем лежать не должны.

Удалить данные в течение 14 дней после объявления победителей, если с Grand Mobile не

заключено отдельное соглашение.

КЕЙС 03 LLM RAG сложность: средняя

# Support Copilot: ассистент поддержки и разбора жалоб

Сервис, который сортирует обращения игроков, извлекает факты, пишет

черновик ответа на языке игрока со ссылками на пункты правил и честно

говорит, когда нужен человек.

ПРОФИЛЬ КОМАНДЫ ДАННЫЕ СДАЧА

   LLM-инженер, бэкенд, жалобы и репорты с HTTP-сервис \+ make

   продакт ответами админов, правила, predict \+ расчет стоимости

таксономия

ГЛАВНАЯ МЕТРИКА

слепая оценка черновиков

администраторами

Контекст

Обращения приходят по 2 каналам. Жалобы на игроков из лаунчера: ник, пункт правил,

скриншоты, иногда комментарий обвиняемого. Репорты из игры: короткие вопросы и

просьбы администраторам, от «застрял в текстурах» до «меня оскорбляют». 6 языков, но

большинство на русском. Разбирают администраторы прямо из игры, вручную. Большая

часть ответов однотипна и сводится к правилам и инструкциям из базы знаний, а серьезные

случаи тонут в потоке.

Задача

Построить сервис триажа: определить язык, категорию и приоритет, отсеять дубли и спам,

извлечь структурированные факты, подготовить черновик ответа с цитатами правил и

оценить, можно ли отвечать автоматически или нужен человек. Главное требование: не

выдумывать правила и не обещать того, чего сервис не может.

Что выдаем

| ФАЙЛ | СОДЕРЖАНИЕ |
| :---- | :---- |
| tickets\_train.jsonl.gz | Около 120 тыс. обращений: все жалобы и внутриигровые репорты 20%случайно выбранных заявителей за 3 месяца, с ответамиадминистраторов. Вердикт, наказание и пункт правил извлечены изответа. Категория и приоритет не размечены |
| tickets\_valid.jsonl | 1 000 обращений того же формата, выделенных для валидации.Категории и приоритета нет, вердикт и наказание из ответаадминистратора есть |
| rules.json | Правила игры на русском, 11 разделов с идентификаторами пунктов |
| taxonomy.json | Категории, приоритеты, критерии приоритета |
| tickets\_hidden.jsonl | Не выдается. 500 обращений для оценки |

Схема обращения

   {

     "ticket\_id": "5b2e…",

     "kind": "complaint", // complaint \| report

     "created\_at": "2026-03-14T19:02:00",

     "region": "kz", "server\_lang": "kk", // сервер, на котором подано

     "lang": "ru", // язык текста игрока по эвристике: ru \| kk \|

   uz \| en \| und

     "reporter\_hash": "a91c…",

     "reported\_hash": "7f3e…", // только complaint

     "reported\_nick": "Arman\_Petrov", // синтетический ник обвиняемого, одинаковый

   во всем наборе

     "rule\_refs\_raw": "2.1", // что игрок написал в поле «пункт правил»,

   как есть

     "images\_count": 2,

     "messages": \[

       { "role": "player", "ts": "…", "text": "оскорбил меня и семью, скрины

   есть" },

       { "role": "reported\_player", "ts": "…", "text": "это была игра по роли" },

       { "role": "admin", "ts": "…", "text": "Уважаемый Dias\_Volkov, … жалоба

   одобрена. Игрок Arman\_Petrov получит: мут на 30 минут за оскорбление." }

     \],

     "verdict": "approved", // approved \| rejected \| need\_evidence \|

   invalid\_format \| duplicate \| …, извлечено из ответа

     "punishment": "мут на 30 минут",

     "violation": "2.1 ОП",

     "category": null, // см. taxonomy.json; есть только в

   размеченной валидации

     "priority": null // p0 критично … p3 низкий

   }

Что сдаете

   HTTP-сервис POST /triage по контракту ниже и цель make predict IN=tickets.jsonl

   OUT=pred.jsonl .

Отчет: метрики на валидации, примеры черновиков, доля «нужен человек», стоимость на

тикет и латентность.

Контракт POST /triage

   // запрос

   { "kind": "complaint", "messages": \[ { "role": "player", "text": "Arman\_Petrov

   оскорблял меня и мою семью в чате, скрины есть, 2.1 ОП", "attachments": 2 } \] }

   // ответ

   {

     "lang": "ru",

     "category": "complaint.insult",

     "priority": "p2",

     "is\_spam\_or\_duplicate": false,

     "extracted": { "nickname": "Arman\_Petrov", "rule\_refs": \["2.1"\], "has\_evidence":

   true, "server": null },

     "draft\_reply": {

       "lang": "ru",

       "text": "Здравствуйте\! Жалоба рассмотрена. По скриншотам видно нарушение пункта

   2.1 общих правил: оскорбление игрока. Игрок Arman\_Petrov получит мут на 30 минут.",

       "cited": \["2.1"\]

     },

     "needs\_human": true,

     "confidence": 0.82,

     "reasons": \["решение о наказании подтверждает администратор"\]

   }

Критерии оценки

| КРИТЕРИЙ | КАК ИЗМЕРЯЕМ | ВЕС |
| :---- | :---- | :---- |
| Классификация | Accuracy по категории и macro-F1 по приоритету на скрытом тесте | 25% |
| Качество черновиков | Администраторы Grand Mobile слепо оценивают 100 черновиков пошкале 1-5 рядом с реальным ответом | 30% |
| Отсутствиегаллюцинаций | Каждая цитата правила должна существовать и быть релевантной.Выдуманный пункт правил обнуляет тикет | 20% |
| Казахский иузбекский | Качество черновиков на kk и uz по оценке носителей | 15% |
| Стоимость илатентность | Не дороже 0,002 \$ за обращение или локальная модель; p95 небольше 5 с | 10% |

Ограничения

RAG по правилам и базе знаний обязателен. Ответ без цитат допустим только для

категорий, где правила не нужны.

Черновик не может обещать разбан, возврат средств или наказание другого игрока. Такие

   темы помечаются needs\_human: true .

Платежи, апелляции банов и подозрения на взлом аккаунта всегда идут человеку.

Бонус

Дедупликация: 1 игрок, 1 проблема, 5 тикетов за час.

Автоматическое предложение новых шаблонов ответов по кластерам похожих

обращений.

Интерфейс админа: очередь, черновик, кнопки «отправить», «править», «эскалировать», с

сохранением правок как обучающего сигнала.

Подводные камни

Тексты короткие, с опечатками и смесью языков в одном сообщении.

Игра работает в cp1251, поэтому на kz-серверах казахские буквы набраны похожими

символами: ќ вместо қ, ґ вместо ғ, ѕ вместо ң, є вместо ә, ј вместо ө, ў вместо ұ, ї вместо ү.

Таблица замен есть в README данных, а в продакшене сервис получит текст в таком же

виде.

В жалобах игроки преувеличивают и ошибаются с пунктами правил. Факты из текста

нельзя принимать за истину.

Скриншотов в выгрузке нет, только их количество.

Частые вопросы

Можно взять 2 кейса?

Нет, 1 кейс на команду. Лучше 1 решение с ядром и бонусом, чем 2 без ядра.

Нужен ли опыт в играх?

Нет. Все кейсы сформулированы в терминах данных и контрактов.

Можно использовать внешние LLM-API?

Да, кроме инференса в кейсе 1, где требуется CPU-only. В остальных кейсах посчитайте

стоимость на единицу обработки и укажите ее в отчете. Это часть оценки.

Можно использовать готовые модели и датасеты?

Да, при соблюдении лицензий. Укажите источники в README.

Кому принадлежит решение?

Права на код остаются у команды. Grand Mobile может предложить победителям пилот,

контракт на доработку или работу в команде.

СЕРІКТЕСТЕР ҰСЫНҒАН КЕЙСТЕР · 2026 ЖЫЛҒЫ 30–31 ҚАЗАН

Grand Mobile × Decentrathon 6.0

Қазақстандық ойын студиясынан үш тапсырма. Әрқайсысы күніне 500 мыңнан астам

адам ойнайтын жобадағы нақты мәселеден туындаған. Ойынның бастапқы коды қажет

емес: біздің деректер негізінде жеке сервис немесе модель әзірлейсіздер, ал оны

ойынға енгізуді өзіміз атқарамыз.

Тапсырма жарияланған сәттен тапсыру мерзіміне дейін · Команда құрамы · Әр командаға бір кейс

· Ойын тілдері, соның ішінде қазақ тілі

Grand Mobile туралы

Grand Mobile — ашық әлемдегі мобильді рөлдік ойын. Ойыншы кейіпкер жасап,

жұмысқа орналасады, фракцияға немесе отбасына қосылады, үй, көлік және бизнес сатып

алады. Бір серверде мыңдаған ойыншымен бір қалада өмір сүреді. Такси жүргізушісі, полицей,

әкім немесе гангстер болуға болады.

Ойынды Astana Hub резиденті саналатын қазақстандық студия әзірлейді. Ойын 55 миллионнан астам рет

орнатылған, күн сайын 500 мыңнан астам адам ойнайды. Серверлер ТМД елдерінде, Қазақстанда,

Өзбекстанда, Еуропада және Латын Америкасында жұмыс істейді. Ойын клиенті орыс, қазақ, өзбек,

ағылшын, испан және португал тілдеріне бейімделген.

Жобаның өз ойын қозғалтқышы, Android пен iOS клиенттері және серверде орындалатын ойын логикасы

бар. Лаунчер мен ойын ішіндегі интерфейс Flutter арқылы жасалған, ал бэкенд Node.js, MariaDB және

ClickHouse негізінде жұмыс істейді. Ойыншының ақшаға қатысты әр әрекеті, жүйеге кіруі,

чаттағы әр хабарламасы және әкімшінің әр әрекеті аналитикалық журналдарға жазылады. Кейстер осы деректерге

негізделген.

Кейстер қалай ұйымдастырылған

Ойынның бастапқы коды, орындалатын файлдары, клиент пен сервер арасындағы хаттама, серверлер мен

API-ге қолжетімділік берілмейді. Бұл — барлық кейсте ескерілген шектеу. Сіздер

иесіздендірілген деректер мен кіріс-шығыс форматының нақты сипаттамасын алып, дербес сервис

немесе модель тапсырасыздар. Хакатоннан кейін оны ойынға енгізу — біздің міндетіміз.

| Сіздер алатын материалдар | Берілмейтін материалдар |
| :---- | :---- |
| JSONL, CSV және ARB форматтарындағы иесіздендірілген деректер.Жасырын тестпен бірдей тәсілмен таңдалған валидациялық іріктеме.Деректер схемаларының сипаттамасы, санаттар жіктемесі және ойын ережелері. | Бастапқы код, ойын құрастырылымдары және клиент-сервер хаттамасы.Өндірістік немесе тестілік API мен дерекқорларға қолжетімділік.Ойыншылардың иесіздендірілмеген деректері.Бағалау аяқталғанға дейін жасырын тест жиынтығы. |

Әр кейс міндетті негізгі бөлімнен және қосымша мүмкіндіктерден тұрады. Негізгі бөлімді 3–4

адамнан тұратын команда 36 сағатта орындай алады. Қосымша мүмкіндіктер жеңіске ықпал етеді, бірақ

негізгі бөлім орындалмаса, бағаланбайды. Толық дайын өнім талап етілмейді: қазылар мәселені қаншалықты

түсінгендеріңізге, MVP сапасына, метрикалардың адал көрсетілуіне және кодтың түсініктілігіне қарайды.

Команда бір кейсті таңдайды. Технологияларды еркін таңдауға болады. Лицензия талаптары сақталса, алдын ала

оқытылған модельдер мен ашық деректер жиынтықтарын пайдалануға рұқсат етіледі. Кейстің шектеулерінде

тыйым салынбаса, сыртқы LLM API-лерін де қолдануға болады. Дегенмен өңдеу құнын есептеп, есепте көрсету

қажет.

Деректер және құпиялылық

Барлық дерек берілмес бұрын иесіздендіріледі. Аккаунттардың, алушылардың және топтардың идентификаторлары әр

кейс шегінде бірегей, қосымша salt мәні қолданылған хэштермен алмастырылады. Уақыт минутқа

дейін дөңгелектенеді. Чат пен өтініш мәтіндеріндегі телефондар, электрондық пошта мекенжайлары және

жеті не одан көп цифрдан тұратын тізбектер бүркемеленеді. Чаттағы кейіпкер аттары \<nick\>

токенімен, ал өтініштерде бүкіл жиынтықта бірізді қолданылатын жасанды аттармен ауыстырылады.

Деректерді қабылдай отырып, команда мына талаптармен келіседі:

Деректерді тек Decentrathon 6.0 аясындағы кейсті шешу үшін пайдалану.

Ойыншылардың, құрылғылардың немесе мекенжайлардың кімге тиесілі екенін анықтауға тырыспау.

Деректерді және олардан алынған іріктемелерді, соның ішінде ашық репозиторийлерде жарияламау. Шешімнің

репозиторийі ашық болуы мүмкін, бірақ оның ішінде деректер болмауға тиіс.

Grand Mobile компаниясымен бөлек келісім жасалмаса, жеңімпаздар жарияланғаннан кейін 14

күн ішінде деректерді жою.

КЕЙС 03 · LLM · RAG · Күрделілігі: орташа

# Support Copilot: ойыншыларды қолдау және шағымдарды қарау көмекшісі

Ойыншылардың өтініштерін сұрыптап, деректерді бөліп алатын, ереже тармақтарына сілтеме жасап,

ойыншының тілінде жауап жобасын дайындайтын және қай кезде адам араласуы

қажет екенін көрсететін сервис.

КОМАНДА ҚҰРАМЫ · ДЕРЕКТЕР · ТАПСЫРЫЛАТЫН НӘТИЖЕ

Команда: LLM инженері, бэкенд әзірлеуші, өнім маманы. Деректер: әкімші жауаптары бар

шағымдар мен өтініштер, ережелер, санаттар жіктемесі. Нәтиже: HTTP сервисі, make predict және

шығын есебі.

НЕГІЗГІ КӨРСЕТКІШ

Әкімшілердің жауап жобаларын қайдан

алынғанын білмей бағалауы

Мәселенің мәні

Өтініштер екі арна арқылы келеді. Лаунчерден ойыншыларға қатысты шағымдар түседі: никнейм, ереже тармағы,

скриншоттар, кейде шағым түскен ойыншының түсініктемесі беріледі. Ойын ішіндегі өтініштер — әкімшіге

жолданған қысқа сұрақтар мен көмек сұраулары: «текстурада тұрып қалдым» дегеннен «мені қорлап жатыр» дегенге

дейін. Алты тіл қолданылады, бірақ өтініштердің көбі орысша. Әкімшілер оларды ойынның ішінен қолмен

қарайды. Жауаптардың көбі ережелер мен білім қорындағы нұсқауларға сүйенеді, ал маңызды жағдайлар жалпы

ағынның арасында елеусіз қалады.

Тапсырма

Өтініштерді бастапқы өңдеу сервисін жасаңыздар: тілін, санатын және басымдығын анықтау, қайталанатын өтініштер мен

спамды сүзу, деректерді құрылымдап шығару, ережелерден дәйексөз келтіріп жауап жобасын дайындау, автоматты жауап

беруге бола ма, әлде адам керек пе — соны бағалау. Негізгі талап: ережелерді

ойдан шығармау және сервис орындай алмайтын нәрсеге уәде бермеу.

Берілетін материалдар

| ФАЙЛ | МАЗМҰНЫ |
| :---- | :---- |
| tickets\_train.jsonl.gz | Шамамен 120 мың өтініш: кездейсоқ таңдалған өтініш берушілердің 20%-ы үш айда жіберген барлық шағым мен ойын ішіндегі өтініш, әкімшілердің жауаптарымен бірге. Шешім, жаза және ереже тармағы жауаптан алынған. Санат пен басымдық белгіленбеген. |
| tickets\_valid.jsonl | Валидацияға бөлінген осы форматтағы 1 000 өтініш. Санат пен басымдық жоқ; әкімші жауабынан алынған шешім мен жаза бар. |
| rules.json | Орыс тіліндегі ойын ережелері: тармақ идентификаторлары бар 11 бөлім. |
| taxonomy.json | Санаттар, басымдық деңгейлері және оларды белгілеу өлшемдері. |
| tickets\_hidden.jsonl | Берілмейді. Бағалауға арналған 500 өтініш. |

Өтініш жазбасының құрылымы

   {

     "ticket\_id": "5b2e…",

     "kind": "complaint", // complaint \| report

     "created\_at": "2026-03-14T19:02:00",

     "region": "kz", "server\_lang": "kk", // өтініш түскен сервер

"lang": "ru", // ойыншы мәтінінің эвристикамен анықталған тілі: ru \| kk \| uz \|

en \| und

     "reporter\_hash": "a91c…",

     "reported\_hash": "7f3e…", // тек complaint үшін

"reported\_nick": "Arman\_Petrov", // шағым түскен ойыншының жасанды никнеймі, бүкіл

жиынтықта бірдей

"rule\_refs\_raw": "2.1", // ойыншының «ереже тармағы» өрісіне жазғаны,

өзгеріссіз

     "images\_count": 2,

     "messages": \[

       { "role": "player", "ts": "…", "text": "оскорбил меня и семью, скрины

   есть" },

       { "role": "reported\_player", "ts": "…", "text": "это была игра по роли" },

       { "role": "admin", "ts": "…", "text": "Уважаемый Dias\_Volkov, … жалоба

   одобрена. Игрок Arman\_Petrov получит: мут на 30 минут за оскорбление." }

     \],

     "verdict": "approved", // approved \| rejected \| need\_evidence \|

   invalid\_format \| duplicate \| …, жауаптан алынған

     "punishment": "мут на 30 минут",

     "violation": "2.1 ОП",

"category": null, // taxonomy.json қараңыз; тек белгіленген

валидациялық жиынтықта бар

     "priority": null // p0 аса маңызды … p3 төмен

   }

Тапсырылатын нәтижелер

Төмендегі форматқа сай POST /triage HTTP сервисі және make нысанасы: make

predict IN=tickets.jsonl OUT=pred.jsonl.

Есеп: валидация метрикалары, жауап жобаларының мысалдары, адам араласуын қажет ететін өтініштер үлесі, бір өтініштің өңдеу құны

және жауап беру уақыты.

POST /triage кіріс-шығыс форматы

   // сұрау

   { "kind": "complaint", "messages": \[ { "role": "player", "text": "Arman\_Petrov

   оскорблял меня и мою семью в чате, скрины есть, 2.1 ОП", "attachments": 2 } \] }

   // жауап

   {

     "lang": "ru",

     "category": "complaint.insult",

     "priority": "p2",

     "is\_spam\_or\_duplicate": false,

     "extracted": { "nickname": "Arman\_Petrov", "rule\_refs": \["2.1"\], "has\_evidence":

   true, "server": null },

     "draft\_reply": {

       "lang": "ru",

       "text": "Здравствуйте\! Жалоба рассмотрена. По скриншотам видно нарушение пункта

   2.1 общих правил: оскорбление игрока. Игрок Arman\_Petrov получит мут на 30 минут.",

       "cited": \["2.1"\]

     },

     "needs\_human": true,

     "confidence": 0.82,

     "reasons": \["решение о наказании подтверждает администратор"\]

   }

Бағалау өлшемдері

| ӨЛШЕМ | БАҒАЛАУ ТӘСІЛІ | ҮЛЕСІ |
| :---- | :---- | :---- |
| Жіктеу | Жасырын тестте санат бойынша Accuracy және басымдық бойынша macro-F1 есептеледі. | 25% |
| Жауап жобаларының сапасы | Grand Mobile әкімшілері 100 жауап жобасын нақты жауаптармен қатар, қайдан алынғанын білмей, 1–5 шкаласымен бағалайды. | 30% |
| Ойдан қосылған мәліметтердің болмауы | Сілтеме жасалған әр ереже бар және жағдайға қатысты болуға тиіс. Ойдан шығарылған тармақ үшін өтінішке нөл балл беріледі. | 20% |
| Қазақ және өзбек тілдері | kk және uz тілдеріндегі жауап жобаларының сапасын сол тілдерді ана тілі ретінде меңгерген адамдар бағалайды. | 15% |
| Құны және жауап беру уақыты | Бір өтінішке 0,002 АҚШ долларынан аспау немесе жергілікті модельді қолдану; p95 уақыты 5 секундтан аспауға тиіс. | 10% |

Шектеулер

Ережелер мен білім қорына сүйенетін RAG міндетті. Ереже қажет емес санаттарда

ғана дәйексөзсіз жауап беруге болады.

Жауап жобасында банды алып тастауға, ақшаны қайтаруға немесе басқа ойыншыны жазалауға уәде беруге болмайды.

Мұндай жағдайлар needs\_human: true деп белгіленеді.

Төлемдер, банға шағымдану және аккаунттың бұзылуына қатысты күдіктер әрқашан адамға жіберіледі.

Қосымша мүмкіндіктер

Қайталанатын өтініштерді біріктіру: бір ойыншы бір мәселе бойынша бір сағатта бес өтініш жібереді.

Ұқсас өтініштер топтарына сүйеніп, жаңа жауап үлгілерін автоматты

ұсыну.

Әкімші интерфейсі: кезек, жауап жобасы, «жіберу», «өңдеу», «жоғары деңгейге жолдау» батырмалары. Түзетулер модельді

оқытуға арналған кері байланыс ретінде сақталады.

Ескеретін жайттар

Мәтіндер қысқа, қате теріледі және бір хабарламада бірнеше тіл араласуы мүмкін.

Ойын cp1251 кодтауын қолданады, сондықтан kz серверлерінде қазақ әріптерінің орнына ұқсас таңбалар жазылады: қ орнына ќ,

ғ орнына ґ, ң орнына ѕ, ә орнына є, ө орнына ј, ұ орнына ў, ү орнына ї.

Таңбаларды алмастыру кестесі деректердің README файлында бар. Нақты қолданыста да сервиске мәтін осы түрде

келеді.

Ойыншылар шағымдарда жағдайды асыра көрсетуі немесе ереже тармағын қате жазуы мүмкін. Мәтіндегі мәлімдемелерді

расталған факт деп қабылдауға болмайды.

Берілген деректерде скриншоттар жоқ, тек олардың саны көрсетілген.

Жиі қойылатын сұрақтар

Екі кейс алуға бола ма?

Жоқ, әр командаға бір кейс. Негізгі бөлігі аяқталмаған екі шешімнен негізгі және қосымша мүмкіндіктері бар бір шешім артық.

Ойын ойнау тәжірибесі қажет пе?

Жоқ. Барлық кейс деректер мен кіріс-шығыс форматтары арқылы сипатталған.

Сыртқы LLM API-лерін қолдануға бола ма?

Иә, тек 1-кейстегі инференс CPU арқылы ғана орындалуға тиіс. Қалған кейстерде бір

өңдеу бірлігінің құнын есептеп, есепте көрсетіңіздер. Бұл да бағалаудың бір бөлігі.

Дайын модельдер мен деректер жиынтықтарын қолдануға бола ма?

Иә, лицензия талаптары сақталса. Дереккөздерді README файлында көрсетіңіздер.

Шешімнің құқықтары кімге тиесілі?

Кодқа құқық командада қалады. Grand Mobile жеңімпаздарға пилоттық жоба, шешімді жетілдіру шарты

немесе командада жұмыс істеуді ұсынуы мүмкін.

PARTNER CHALLENGES · 30–31 OCTOBER 2026

Grand Mobile × Decentrathon 6.0

Three challenges from a game studio in Kazakhstan. Each addresses a real production problem

in a game with over 500,000 daily players. You do not need

access to the game’s source code: build a standalone service or model using our

data, and we will handle integration.

From challenge release to submission deadline · Team size · One challenge

per team · Game languages, including Kazakh

About Grand Mobile

Grand Mobile is an open-world mobile role-playing game. Players create a character, get a job, join

a faction or a family, buy a home, a car and a business, and share a

city with thousands of other players on the same server. You can be a taxi driver, a

police officer, a mayor or a gangster.

The game is developed by a Kazakhstan-based studio and Astana Hub resident. It has

over 55 million installs and more than 500,000 daily players. Servers operate across the

CIS, Kazakhstan, Uzbekistan, Europe and Latin America. The client is available in Russian,

Kazakh, Uzbek, English, Spanish and Portuguese.

The technology stack includes a proprietary engine, Android and iOS clients, and server-side game

logic. The launcher and all in-game interfaces use Flutter; the backend runs on Node.js

with MariaDB and ClickHouse. Every money-related player action, login, chat message and administrator

action is recorded in analytics logs. These logs form the basis of the

challenges.

How the challenges work

We do not provide the game’s source code, binaries, client-server protocol, or access to

servers or APIs. This is a deliberate constraint built into every challenge:

you receive anonymized data and a clear input/output contract, and deliver a standalone

service or model. We will integrate it into the game after the hackathon.

| What you receive | What we do not provide |
| :---- | :---- |
| Anonymized datasets in JSONL, CSV and ARB.A validation sample selected using the same approach as the hidden test set.Schema documentation, category taxonomy and game rules. | Source code, builds or the client-server protocol.Access to production or test APIs and databases.Non-anonymized player data.The hidden test set before evaluation is complete. |

Each challenge has a required core and optional bonus features. A team of 3–4 can realistically complete the

core in 36 hours. Bonus features can turn a good solution into a winning one, but are assessed

only if the core is complete. We do not expect a production-ready product: the judges will assess

your understanding of the problem, MVP quality, honest reporting of metrics and code clarity.

Each team chooses one challenge and may use any technology stack. Pretrained models and

open datasets are allowed, subject to their licenses. External LLM APIs are permitted

unless a challenge explicitly says otherwise; calculate the processing cost and include it in your

report.

Data and confidentiality

All exports are anonymized before delivery. Account, recipient and group identifiers are replaced

with salted hashes that are unique within each challenge. Timestamps are rounded to

the nearest minute. Phone numbers, email addresses and sequences of seven or more

digits are masked in chat and support messages. Character nicknames in chat are

replaced with \<nick\>; support requests use synthetic names consistently across the dataset.

By accepting the data, your team agrees to:

Use the data only to work on the challenge during Decentrathon 6.0.

Make no attempt to re-identify players, devices or addresses.

Do not publish the data or derived subsets, including in public repositories. Your

solution repository may be public, but it must not contain the data.

Delete the data within 14 days of the winners being announced, unless you have a

separate agreement with Grand Mobile.

CHALLENGE 03 · LLM · RAG · Difficulty: medium

# Support Copilot: an assistant for player support and complaint handling

A service that sorts player requests, extracts facts and drafts replies

in the player’s language with references to game rules, while clearly identifying

cases that need human review.

TEAM PROFILE · DATA · DELIVERABLES

Team: LLM engineer, backend developer, product specialist. Data: complaints and reports

with administrator replies, rules and taxonomy. Deliverables: HTTP service, make predict and

cost estimates.

PRIMARY METRIC

Blind evaluation of draft

replies by administrators

Background

Requests arrive through two channels. Complaints about players come from the launcher and include a

nickname, a rule reference, screenshots and sometimes a response from the accused player. In-game reports

are short questions or requests for administrators, from “I’m stuck in the scenery” to “someone is

insulting me.” Players use six languages, though most requests are in Russian. Administrators handle them

manually from within the game. Most replies repeat rules or knowledge-base instructions, while serious cases get

lost in the volume.

Your task

Build a triage service that identifies the language, category and priority; filters duplicates and spam;

extracts structured facts; drafts a reply with rule citations; and determines whether an

automatic reply is appropriate or a human is needed. The key requirement is to

avoid inventing rules or making promises the service cannot fulfill.

What we provide

| FILE | CONTENTS |
| :---- | :---- |
| tickets\_train.jsonl.gz | Around 120,000 tickets: all complaints and in-game reports submitted over three months by a randomly selected 20% of requesters, with administrator replies. Verdicts, penalties and rule references are extracted from replies. Categories and priorities are not labeled. |
| tickets\_valid.jsonl | 1,000 tickets in the same format, set aside for validation. Category and priority labels are absent; verdicts and penalties extracted from administrator replies are included. |
| rules.json | Game rules in Russian: 11 sections with rule identifiers. |
| taxonomy.json | Categories, priority levels and criteria for assigning priority. |
| tickets\_hidden.jsonl | Not provided. 500 tickets used for evaluation. |

Ticket schema

   {

     "ticket\_id": "5b2e…",

     "kind": "complaint", // complaint \| report

     "created\_at": "2026-03-14T19:02:00",

     "region": "kz", "server\_lang": "kk", // server where the ticket was submitted

"lang": "ru", // language of the player’s text, inferred heuristically: ru \| kk \| uz

\| en \| und

     "reporter\_hash": "a91c…",

     "reported\_hash": "7f3e…", // complaint only

"reported\_nick": "Arman\_Petrov", // synthetic nickname of the accused player, consistent across

the dataset

"rule\_refs\_raw": "2.1", // the player’s entry in the rule-reference field,

unchanged

     "images\_count": 2,

     "messages": \[

       { "role": "player", "ts": "…", "text": "оскорбил меня и семью, скрины

   есть" },

       { "role": "reported\_player", "ts": "…", "text": "это была игра по роли" },

       { "role": "admin", "ts": "…", "text": "Уважаемый Dias\_Volkov, … жалоба

   одобрена. Игрок Arman\_Petrov получит: мут на 30 минут за оскорбление." }

     \],

     "verdict": "approved", // approved \| rejected \| need\_evidence \|

   invalid\_format \| duplicate \| …, extracted from the reply

     "punishment": "мут на 30 минут",

     "violation": "2.1 ОП",

"category": null, // see taxonomy.json; available only in

the labeled validation set

     "priority": null // p0 critical … p3 low

   }

What to submit

HTTP service with POST /triage following the contract below, plus the make target: make

predict IN=tickets.jsonl OUT=pred.jsonl.

Report: validation metrics, sample draft replies, the share of tickets requiring human review, cost per

ticket and latency.

POST /triage contract

   // request

   { "kind": "complaint", "messages": \[ { "role": "player", "text": "Arman\_Petrov

   оскорблял меня и мою семью в чате, скрины есть, 2.1 ОП", "attachments": 2 } \] }

   // response

   {

     "lang": "ru",

     "category": "complaint.insult",

     "priority": "p2",

     "is\_spam\_or\_duplicate": false,

     "extracted": { "nickname": "Arman\_Petrov", "rule\_refs": \["2.1"\], "has\_evidence":

   true, "server": null },

     "draft\_reply": {

       "lang": "ru",

       "text": "Здравствуйте\! Жалоба рассмотрена. По скриншотам видно нарушение пункта

   2.1 общих правил: оскорбление игрока. Игрок Arman\_Petrov получит мут на 30 минут.",

       "cited": \["2.1"\]

     },

     "needs\_human": true,

     "confidence": 0.82,

     "reasons": \["решение о наказании подтверждает администратор"\]

   }

Evaluation criteria

| CRITERION | HOW IT IS MEASURED | Weight |
| :---- | :---- | :---- |
| Classification | Category accuracy and priority macro-F1 on the hidden test set. | 25% |
| Draft quality | Grand Mobile administrators blindly rate 100 drafts on a 1–5 scale alongside the actual replies. | 30% |
| No hallucinations | Every cited rule must exist and be relevant. An invented rule gives that ticket a score of zero. | 20% |
| Kazakh and Uzbek | Native speakers assess draft quality in kk and uz. | 15% |
| Cost and latency | No more than \$0.002 per ticket, or use a local model; p95 latency must not exceed 5 seconds. | 10% |

Constraints

RAG over the rules and knowledge base is required. Replies without citations are allowed only in

categories that do not require rules.

Drafts must not promise to lift a ban, issue a refund or punish another

player. Mark these cases needs\_human: true.

Payments, ban appeals and suspected account compromises must always go to a human.

Bonus features

Deduplication: one player submits five tickets about the same issue within an hour.

Automatically suggest new reply templates from clusters of similar

requests.

Administrator interface: a queue, draft replies and Send, Edit and Escalate buttons,

with edits saved as training feedback.

Pitfalls to watch for

Messages are short, contain typos and may mix languages within a single message.

The game uses cp1251, so Kazakh letters on kz servers are represented by similar characters: ќ for

қ, ґ for ғ, ѕ for ң, є for ә, ј for ө, ў for ұ and ї for ү.

The data README includes a character-mapping table. The production service will receive text in the same

format.

Players may exaggerate or cite the wrong rules in complaints. Claims in the text must not

be treated as verified facts.

The export contains no screenshots, only the number attached.

Frequently asked questions

Can we take on two challenges?

No, one challenge per team. One complete solution with bonus features is better than two with incomplete cores.

Do we need gaming experience?

No. Every challenge is defined in terms of data and input/output contracts.

Can we use external LLM APIs?

Yes, except for inference in Challenge 1, which must run on CPU only. For the other challenges, calculate the

cost per processing unit and include it in your report. This is part of the evaluation.

Can we use existing models and datasets?

Yes, provided you comply with their licenses. List your sources in the README.

Who owns the solution?

Your team retains the rights to the code. Grand Mobile may offer the winners a pilot project,

a development contract or a role on the team.

