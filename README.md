# Курсовая работа "Проектирование корпоративной сети"

### Цель курсовой работы

Курсовая работа направлена на отработку знаний, полученных в ходе прохождения курса, и самостоятельное применение отдельных навыков при реализации комплексной задачи по проектированию и развертыванию сетевой инфраструктуры небольшой корпоративной сети. Данная работа позволит показать наличие практических навыков для решения комплексных задач, возникающих в реальной практике сетевого инженера.  

В результате выполнения этой работы вы:

1. Научитесь формировать адресный план предприятия;
2. Проектировать сетевую инфраструктуру на базе технического задания;
3. Разворачивать сеть на основании спроектированного решения;
4. Обосновывать выбранные технические решения, для их защиты перед внешними экспертами.

### Чек-лист готовности к выполнению работы
Для выполнения работ потребуется:

1. Packet Tracer;
2. Любой инструменты для рисования схем, например Draw.io;
3. Текстовый редактор для подготовки пояснительной записки.

------

### Задание

В курсовой работе необходимо спроектировать сеть среднего офиса, который включает пользовательских сегмент и внутренние инфраструктурные сервисы. Обеспечить офис подключением к сети интернет и к одному удаленному офису. Предусмотреть отказоустойчивость ключевых элементов сетевой инфраструктуры, возможность масштабирования офиса и филиальной сети, базовые средства обеспечения безопасности и шифрования данных там, где это необходимо.
Вы устроились работать в молодой и перспективный стартап по производству элексира доброты ЗАО "Доброта". Конъюнктура рынка такова, что руководство стартапа ожидает быстрое развитие бизнеса. Предполагается открытие одного офиса и производственного помещения, но в дальнейшем планируется развитие как существующих площадок, так и филиальной сети организации.

У вас есть следующие бизнес-требования к сети.
Проектируются две площадки - центральный офис и производство.

В центральном офисе планируется разместить 70 сотрудников, распределенные по отделам следующим образом:
производственный отдел - 45 человек,
отдел продаж - 15 человек,
ИТ отдел - 5 человек,
бухгалтерия и секретариат - 5 человек.
В офисе расположено 10 периферийных устройств, требующих подключения к сети.
Необходимо организовать беспроводное подключение к сети Wi-Fi для гостей компании.

Необходимо обеспечить резерв сетевой емкости при условии, что в пределах 3 лет ожидается двухкратный рост числа сотрудников.

На производстве будет размещено 10 сотрудников производственного отдела. Сотрудники производства должны иметь доступ к инфраструктуре центрального офиса. Отсутствие связи на производстве не оказывает критического воздействия на бизнес-процессы компании. 

В центральном офисе будут располагаться также общие внутренние и публичные сервисы компании:
- почтовый сервер (внутренний),
- веб сайт (публичный),
- ftp сервер (публичный),
- файловое хранилище (внутренний),
- котроллер домена (внутренний).
Внутренние и публичные сервисы компании должны иметь высокую доступность, выход из строя любого отдельного элемента сетевой инфраструктуры не должен приводить к их отказу.

Требования информационной безопасности.
1. Коммутаторы доступа должны быть настроены таким образом, чтобы минимизировать риски подключения неавторизированных устройств, неуправляемых коммутаторов, точек доступа. Использование технологии dot1x в данной работе не допустимо, хотя и может являться валидным решением данной задачи.
2. Доступ в интернет из центрального офиса разрешен для всех пользователей и сервисов компании за исключением периферийных устройств.
3. Производство должно выходить в интернет только через центральный офис.
4. Сегмент гостевого WiFi должен иметь возможность подключиться только к интернету и не должен подключаться к любым другим сегментам сети.
5. Веб сайт должен быть доступен из сети Интернет по протоколу https.
6. FTP сервер должен быть доступен из сети интернет только для клиента с IP 1.1.1.1/32.
7. Все пользователи сети (кроме гостевых) должны иметь возможность подключаться к корпоративным ресурсам.
8. Периферийные устройства должны быть доступны для пользователей, но сами не могут инициировать соединения ни к одному сегменту сети.
В реальной жизни подобных требований может быть значительно больше, а также могут возникать новые в ходе эксплуатации и развития сети. В учебных целях рассматривается ограниченный набор таких требований.

### Замечания к заданию
1. В рамках текущей работы вопрос подключения голосовой связи не рассматривается. Считаем, что на каждого пользователя приходится один порт, наличие голосового VLAN не требуется. 
2. Расположение сотрудников считаем произвольным, распределение пользователей по коммутаторам не имеет значения, ограничения на физическую длину кабеля не учитывается.
3. Считаем, что технологическая сеть производства полностью изолирована от ЛВС и не является объектом проектирования. 
4. БЛВС сегмент в рамках курсовой работы должен представлять собой одну точку доступа с гостевой SSID. В реальной жизни для подобной задачи целесообразно предусмотреть наличие БЛВС контроллера, провести радио планирование, расположить несколько точек доступа и организовать несколько SSID с разными требованиями к авторизации и правами на доступ. В рамках курсового проекта делать этого НЕ ТРЕБУЕТСЯ.
5. В данной работе отказоустойчивость рассматривается только в рамках сетевой инфраструктуры, проектирование конкретного сервиса, как отказоустойчивого решения, не требуется.
6. При эмуляции сети Интернет можно использовать отдельный хост с произвольным публичным IP адресом, подключенным к маршрутизатору условного оператора связи, а не напрямую к корпоративной сети. Необходимо, чтобы данный хост был доступен из сегментов, где требуется подключение к интернету, а от данного хоста были доступен условный веб сайт компании. 
7. При проектировании сети в PacketTracer не требуется подключение всех оконечных устройств (компьютеров пользователей, периферийных устройств и так далее). Подключение по одному устройству данного типа достаточно для проверки выполнения наличия связанности и выполнения требований информационной безопасности.
8. IPv6 адресация в работе не рассматривается.

------

### Этапы выполнения работы

1. Продумать критерии разбиения общей сети на подсети, если оно требуется. В случае, если разбиение на подсети необходимо, нужно составить таблицу следующего вида.

|  Сегмент сети  | Номер VLAN | Название VLAN | Адрес подсети | Маска подсети |
| -------------- | ---------- | ------------- | ------------- | ------------- |
| Гостевой WiFi  | 123        | GuestWiFi     | 192.168.1.0   |  /24          |

Обосновать необходимость/отсутствие необходимости в сегментировании. Обосновать выбранные размер подсети, учитывай требования по числу пользователей и планам по масштабированию, описанным в задании

2. Выбрать схему подключения центрального офиса к интернету с учетом требования по отказоустойчивости публичного сегмента. Компания не обладает PI адресами. В здании, где расположен центральный офис, присутствует только один оператор связи "МоноТел". Но оператор имеет два независимых кабельных и энерго-ввода и две различные точки присутствия в здании и готов реализовать любую предложенную схему.
- Описать выбранную схему.
- Обосновать требуемый размер публичной подсети/подсетей и описать ее/их в виде таблицы.

|   IP адрес  |    Назначение     | Зона ответственности |
| ----------- | ----------------- | -------------------- |
| 12.34.56.0  | Адрес сети        | Не используется      |
| 12.34.56.1  | ISP Router 1      | "МоноТел"            |
| 12.34.56.2  | ISP Router 2      | "МоноТел"            |
| 12.34.56.3  | VRRP шлюз         | "МоноТел"            |
| 12.34.56.4  | NAT для польз-ей  | ЗАО "Доброта"        |
| 12.34.56.5  | Веб сайт          | ЗАО "Доброта"        |
| 12.34.56.6  | Резерв            | ЗАО "Доброта"        |
| 12.34.56.7  | Широко-ный адрес  | Не используется      |

Адрес подсети приведен для примера и может быть выбран произвольно из диапазона публичных IPv4 адресов.

3. Выбрать и обосновать технологию подключения производства к центральному офису с учетом описанных в задании требований. Возможные варианты:
- интернет,
- L2VPN/L3VPN от оператора связи,
- арендованная ВОЛС.
Указать транспортные и/или туннельные адреса, необходимые для построения связанности, описать их в таблице по шаблону п.2. Если на производстве требуется подключение к интернету, описать его аналогично п. 2.

4. Описать выбранный протокол маршрутизации, если протокол необходим, или обосновать использование статических маршрутов. 
5. Продумать механизмы обеспечения отказоустойчивости сервисного сегмента. Указать выбранные технологии и обосновать их применение.
6. Нарисовать схему сети и собрать ее в Packet Tracer.
7. Настроить оборудование согласно выбранной схеме и требования по информационной безопасности.
8. Выполнить тесты, отражающие наличие требуемой связанности и выполнение требований информационной безопасности. ОПИШИ ОТДЕЛЬНО ТЕСТЫ.
------

### Правила приема работы
По результатам выполнения работы необходимо предоставить файлы, содержащие следующую информацию.
1. Пояснительную записку, которая содержит таблицы и описания к решениям, указанным в этапах 1-5 выполнения работ. Обоснование предполагает короткое описание (1-3 предложения) выбранного технического решения, которое должно ответить на вопрос, почему вы выбрали именно это решение, а не иное.
2. Схему L3 связанности, в которой должны быть отражены все подсети, точки терминации подсетей, связи между ними и используемые протоколы маршрутизации, если такие есть. Схему можно рисовать в любом редакторе и приложить в виде графического файла типа .jpeg. 
3. Собранную топологию в PacketTracer.
4. Конфигурационные файлы с оборудования.
5. Результаты тестирования, проведенного на 8 этапе выполнения работы, в виде отдельного текстового файла.  

------

### Критерии оценки

1. Разработанная сетевая архитектура, не противоречащая исходном заданию. Если какие-то вопросы по Вашему мнению не отражены в задании, и они мешают выполнению задания - можно делать так, как считаете нужным. Главное условие выполнение работы - соответствие тому, что написано в задании. 
2. На проверку предоставлены все данные, указанные в Правилах приема работы. 
3. Тесты, выполненные на 8 этапе выполнения работ, соответствуют требования задания.
