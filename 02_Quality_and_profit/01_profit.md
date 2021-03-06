@title Принцип расчета премий по проектам
@short Премии
@group qualityandprofit

Описание принципов премирования, и формуля расчета премии

= Формула расчета рентабельности проекта

== Термины
- **человекочасы** - часовая ставка себестоимости работы по проекту (отношения расходов по проекту к кол-ву часов потраченных на проект)
- **выручка** - кол-во денег, полученых по факту сдачи проекта и закрытию всех счетов
- **расходы** - расходы по проекту (издержки, оплата работы исполнителей и прочее).

== Сокращения
- **ЧЧ** = человекочасы

==Формула
```
Прибыль = Выручка - (ЧЧ факт * расходы план / ЧЧ план) - (выручка / 100 * % менеджера по продажам)
```

== На какие параметры формулы можно влиять
- ЧЧ - сокращая время на разработку проекта можно увеличивать прибыльность проекта, тем самым увеличивая премиальный фонд
IMPORTANT: Время это не единственный показатель который будет оцениваться, учитывается комбинация времени и показателей качества.

= Премиальный фонд и его распределение
Премиальный фонд составляет **45%** от прибыли до 01.06.2016 года
С 01.06.2016 г премиальный фонд будет равен **30%**

== Фонд распределяется следующим образом:
- **ПМ** - 66%
- **Ведущий программист по проекту** - 15%
- **Frontend** - 15%
- **Второй программист на проекте** - 4%

== Пример расчетов
На базе проекта gir.ua
Планируемая прибыль по проекту - 17108 грн
Премиальный фонд = 17108 / 100 * 45 = 7700 грн

=== Распределение
- ПМ - 7700 / 100 * 66 = 5082 грн
- Ведущий программист - 7700 / 100 * 15% = 1155 грн
- Frontend - 7700 / 100 * 15% = 1155 грн
- Второй программист - 7700 / 100 * 4 = 308 грн

= Навигация =
- Вперед: Метрики влияющие на размер премиального фонда: @{article: 2_quality}