# Курсовая работа "Проектирование корпоративной сети"

### Цель курсовой работы

Курсовая работа направлена на отработку знаний, полученных в ходе прохождения курса, и самостоятельное применение отдельных навыков при реализации комплексной задачи по проектированию и развертыванию сетевой инфраструктуры небольшой компании. Данная работа позволит показать наличие практических навыков для решения комплексных задач, возникающих в практике сетевого инженера.  

В результате выполнения этой работы вы:

1. Научитесь формировать адресный план предприятия;
2. Проектировать сетевую инфраструктуру на базе технического задания;
3. Разворачивать сеть на основании спроектированного решения;
4. Обосновывать выбранные технические решения, для их защиты перед внешними экспертами.

### Чек-лист готовности к выполнению работы
Для выполнения работ потребуется:

1. Packet Tracer 8.1.1;
2. Текстовый редактор для подготовки пояснительной записки.

------

### Задание

Вы устроились работать в молодой и перспективный стартап по производству элексира доброты ЗАО "Доброта". Конъюнктура рынка такова, что руководство стартапа ожидает быстрое развитие бизнеса. Предполагается открытие одного офиса и производственного помещения, но в дальнейшем планируется развитие как существующих площадок, так и филиальной сети организации.

У вас есть следующие бизнес-требования к сети.
Проектируются две площадки - центральный офис и производство.

В центральном офисе планируется разместить 70 сотрудников, распределенных по отделам следующим образом:
производственный отдел - 45 человек,
отдел продаж - 15 человек,
ИТ отдел - 5 человек,
бухгалтерия и секретариат - 5 человек.
В офисе расположено 10 периферийных устройств (принтеров и т.д.), требующих подключения к сети.
Необходимо организовать беспроводное подключение к сети Wi-Fi для гостей компании.

Необходимо обеспечить резерв сетевой емкости при условии, что в пределах 3 лет ожидается двухкратный рост числа сотрудников.

На производстве будет размещено 10 сотрудников производственного отдела. Сотрудники производства должны иметь доступ к инфраструктуре центрального офиса. Отсутствие связи на производстве не оказывает критического воздействия на бизнес-процессы компании. 

Требования информационной безопасности.
1. Коммутаторы доступа должны быть настроены таким образом, чтобы минимизировать риски подключения неавторизированных устройств, неуправляемых коммутаторов, точек доступа. Использование технологии dot1x в данной работе не допустимо, хотя и может являться валидным решением данной задачи.
2. Доступ в интернет из центрального офиса разрешен для всех пользователей и сервисов компании за исключением периферийных устройств.
3. Производство должно выходить в интернет локально через свой канал доступа в интернет.
4. Сегмент гостевого Wi-Fi должен иметь возможность подключиться только к интернету и не должен подключаться к любым другим сегментам сети.
5. Каждый отдел не имеет доступа к ПК из других отделов. Так, например, пользовель ПК производственного отдела не может взаимодействовать с ПК из отдела продаж, ИТ отдела и бухгалтерии. Все отделы должны иметь доступ к подсети с принтерами.
В реальной жизни подобных требований может быть значительно больше, а также могут возникать новые в ходе эксплуатации и развития сети. В учебных целях рассматривается ограниченный набор таких требований.

### Замечания к заданию
1. В рамках текущей работы вопрос подключения голосовой связи не рассматривается. Считаем, что на каждого пользователя приходится один порт, наличие голосового VLAN не требуется. 
2. Расположение сотрудников считаем произвольным, распределение пользователей по коммутаторам не имеет значения, ограничения на физическую длину кабеля не учитывается.
3. БЛВС сегмент в рамках курсовой работы должен представлять собой одну точку доступа с гостевой SSID и ПК, подключенным к ней. В реальной жизни для подобной задачи целесообразно предусмотреть наличие БЛВС контроллера, провести радио планирование, расположить несколько точек доступа и организовать несколько SSID с разными требованиями к авторизации и правами на доступ. В рамках курсового проекта делать этого НЕ ТРЕБУЕТСЯ.
4. При проектировании сети в Packet Tracer не требуется подключение всех оконечных устройств (компьютеров пользователей, периферийных устройств и так далее). Подключение по одному устройству каждого типа достаточно для проверки выполнения наличия связанности и выполнения требований информационной безопасности.
5. IPv6 адресация в работе не рассматривается.
------

### Этапы выполнения работы

1. Продумать критерии разбиения общей сети на подсети, если оно требуется. В случае, если разбиение на подсети необходимо, нужно составить таблицу, содержащую все внутренние подсети, используемые в работе (включая транзитные, которые используются для стыка между оборудованием). В таблице должны быть указаны следующие столбцы:
Название подсети;
Номер VLAN;
Адрес подсети;
Минимально возможная маска подсети для удовлетворения требования задания без учета масштабирования;
Минимально возможная маска подсети с учетом резерва под рост числа пользователей;
Выбранная маска подсети для реализации.
Обосновать необходимость/отсутствие необходимости в сегментировании. 

2. Настроить подключение офиса и филиала к интернету.
К заданию прилагается [файл](https://github.com/usipovtt/crpnt-diplom/blob/main/internet.pkt). В нем выполнены настройки для эмуляции доступа в интернет.
В центральном офисе есть два оператора связи.
Первый оператор отдает услуги с порта Gi0/0 оборудования ISP1 со следующими настройками:
IP 1.0.0.2
MASK 255.255.255.252
GW 1.0.0.1
Второй оператор отдает услуги с порта Gi0/0 оборудования ISP2 со следующими настройками:
IP 1.0.1.2
MASK 255.255.255.252
GW 1.0.1.1
Оператор связи на производстве отдает услуги с порта Gi0/0 оборудования ISP3 со следующими настройками:
IP 1.0.2.2
MASK 255.255.255.252
GW 1.0.2.1
Других возможностей подключения к интернету или организации связи между производством и офисом не предусмотрено. 
IP адрес ПК для проверки доступа из офиса в интернет – 3.0.0.2.
Для подключения центрального офиса и производства к интернету у вас есть три маршрутизатора Cisco 2901.

3. Спроектировать и настроить инфраструктуру центрального офиса согласно условиям задания.
Для этого у вас есть два L3 коммутатора Cisco 3650. Число и функционал коммутаторов доступа вы определяете самостоятельно.
Все элементы сетевой инфраструктуры центрального офиса, кроме коммутаторов для подключения оконечных устройств, должны быть зарезервированы. 
В качестве протокола маршрутизации рекомендуется выбрать EIGRP, в качестве протокола обеспечения отказоустойчивости шлюза – HSRP (в силу ограничений платформы Packet Tracer)
При настройке коммутаторов доступа учесть требование информационной безопасности №1. Так же предусмотреть, чтобы подключение оконечного устройства к коммутатору доступа не вызывало перестроение STP дерева.
При использовании протокола xSTP предусмотреть защиту от подключения не валидного root коммутатора, а также подключения неавторизированных коммутаторов в порты доступа.
Протоколы обеспечения отказоустойчивости должны быть настроены таким образом, чтобы, когда сеть исправна, трафик ходил наиболее оптимальными путями.
3. Спроектировать и настроить подключение производства к центральному офису через имеющиеся каналы доступа в интернет, а также сетевую инфраструктуру производства.
Необходимо обеспечить обмен маршрутной информацией между офисом и производством путем распространения домена маршрутизации центрального офиса на производство. 
Предусмотреть возможность подключения к маршрутизатору на производстве более одного VLAN.
Указать транспортные и/или туннельные адреса, необходимые для построения связанности, указать их в таблице из п.1. 
4. Настроить NAT на маршрутизаторах 2901 согласно заданию и требованиям по информационной безопасности 2 и 3. Публичный IP адрес пользователей в центральном офисе должен быть неизменным, за исключением случая неисправности основного канала доступа в интернет (ISP1) или неисправности маршрутизатора, к которому он подключен. 
5. Настроить правила доступа для удовлетворения требованиям информационной безопасности 4 и 5 с использованием списков доступа (использование statefull фильтрации на текущем этапе не предусмотрено, поскольку межсетевые экраны не заложены в проект).
6. Настроить сеть гостевого WiFi согласно замечанию к заданию 3 и требованиям по информационной безопасности для этой сети.
7. По условиям договора о предоставлении услуг оператора ISP2 исходящая полоса пропускания емкостью более 10 Мбит/c тарифицируется дополнительно. Для снижения расходов необходимо настроить ограничение исходящей полосы пропускания для интерфейса в сторону ISP2.
8. Выполнить тесты, отражающие наличие требуемой связанности и выполнение требований информационной безопасности.

### Тестирование
Результаты тестов собрать в ОДИН общий файл и предоставить вместе с результатами курсовой работы. 

Необходимо провести и зафиксировать (в виде скриншота из PacketTracer) следующие тесты. Если не указано дополнительно - тестирование производить командой ping.
- ПК сегмента производственного отдела, гостевого Wi-Fi и веб сервер имеют доступ в сеть интернет.
- ПК на производстве имеет доступ в интернет и выходит в него через ISP3 (дополнительно приложить вывод traceroute).
- ПК на производстве имеет доступ к принтерам центрального офиса и сети производства центрального офиса, однако не имеют доступа к сегменту бухгалтерии.
- ПК в сегменте гостевого Wi-Fi не имеет доступа к сегменту производственного отдела.
- ПК в сегменте бухгалтерии имеют доступ к принтерам.
- ПК производственного отдела не может взаимодействовать с ПК из отдела продаж, ИТ отдела и бухгалтерии.
- ПК, подключенное в сегмент периферийных устройств, не имеет доступа в интернет. 

Провести тестирование используемых механизмов обеспечения отказоустойчивости. Для каждого их следующих пунктов снять трассировки из точки А в точку Б до начала теста и после отключения одного из элементов сети. 

- Точка А – ПК в бухгалтерии, точка Б – интернет (3.0.0.2). Отключение ISP1, проверка, что центральный офис перешел на ISP2. 
- Точка А – ПК в производственном отделе, точка Б – пользователь на производстве. Отключение ISP1, проверка, что связь между офисом и производством не прервалась.
- Точка А – ПК в отделе продаж, точка Б – интернет (3.0.0.2). Полное отключение маршрутизатора, к которому подключен ISP1, проверка того, что центральный офис перешел на второй маршрутизатор. 
- Точка А – ПК в производственном отделе, точка Б – пользователь на производстве. Полное отключение маршрутизатора, к которому подключен ISP1, проверка того, что связь до производства перешла на второй маршрутизатор. 
- Точка А – ПК в бухгалтерии, точка Б – интернет (3.0.0.2). Отключение устройства, на котором расположены адреса шлюзов по умолчанию для внутренних сетей в центральном офисе. Проверка того, что адрес шлюза стал доступен через резервное устройство.
- Точка А – ПК в бухгалтерии, точка Б – интернет (3.0.0.2). Поочередное отключение каждого из линков, подключенных к коммутатору доступа, где расположена точка А. Проверка того, что выход из строя одного из линков не нарушает связанность.

ПРИМЕЧАНИЕ. В связи с особенностью эмулятора Packet Tracer, часто бывает так, что для того, чтобы тест заработал, нужно перезагрузить устройства. 

------

### Правила приема работы
По результатам выполнения работы необходимо предоставить файлы, содержащие следующую информацию.
1. Пояснительную записку, которая содержит таблицы и описания к решениям, указанным в этапах 1-5 выполнения работ. Обоснование предполагает короткое описание (1-3 предложения) выбранного технического решения, которое должно ответить на вопрос, почему вы выбрали именно это решение, а не иное.
2. Собранную топологию в PacketTracer в виде. pkt файла.
4. Конфигурационные файлы с оборудования.
5. Результаты тестирования, проведенного на 8 этапе выполнения работы, в виде отдельного текстового файла с вложенными в него скриншотами и трассировками.  

------

### Критерии оценки

1. Разработанная сетевая архитектура, не противоречащая исходному заданию. Если какие-то вопросы по Вашему мнению не отражены в задании, и они мешают выполнению задания - можно делать так, как считаете нужным. Главное условие выполнение работы - соответствие тому, что написано в задании. 
2. На проверку предоставлены все данные, указанные в Правилах приема работы. 
3. Тесты, выполненные на 8 этапе выполнения работ, соответствуют требованиям задания.
