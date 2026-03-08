# WORKPLAN: SPF-Petroleum-Innovation-Pack

> Рабочие продукты для Pack по нефтегазовым инновациям.
> Сегодня: 2026-03-08.
> Недельный горизонт: W11 (2026-03-09..2026-03-15).

## План на неделю (W11: 2026-03-09..2026-03-15)

| # | РП | Статус | Критерий готовности |
|---|-----|--------|---------------------|
| SPI-W11-001 | Ревизия `pack/01-domain-contract` | done | `01A..01D` взаимно согласованы; нет противоречий между контекстом, distinctions и rationale |
| SPI-W11-002 | Сверка `pack/02-domain-entities` с `pack/03-methods` | done | `02C-methods-index.md` покрывает UP.M.001..010; у каждого метода есть валидные роли/объекты |
| SPI-W11-003 | Обновление `pack/04-work-products` под цикл внедрения | done | Актуализированы шаблоны 01..04; добавлены явные шаги контроля и отчётности |
| SPI-W11-004 | Доработка `pack/05-failure-modes` и связка с методами | done | Для ключевых failure modes есть привязка к методам и управленческим решениям |
| SPI-W11-005 | Недельная интеграционная проверка Pack | done | `00-pack-manifest.md`, `ontology.md` и разделы 01..07 согласованы по терминам и ссылкам |

## План на сегодня (2026-03-08)

| # | Задача | Статус | Результат сегодня |
|---|--------|--------|-------------------|
| SPI-DAY-001 | Быстрый аудит структуры `pack/01..07` | done | Найдены и приоритизированы несогласованности (P1/P2); добавлен список правок |
| SPI-DAY-002 | Зафиксировать backlog ревизии domain-contract | done | Сформирован исполнимый backlog `DC-001..DC-007` по `01A..01D` с порядком выполнения |
| SPI-DAY-003 | Проверить покрытие методов в `02C-methods-index.md` | done | Покрытие `UP.M.001..010` подтверждено; выявлены пробелы в агрегированной WP-матрице и ролях |
| SPI-DAY-004 | Определить минимальный объём обновлений `04-work-products` | done | Зафиксирован минимальный скоуп W11 (must-fix + defer) для 01..04 WP-артефактов |
| SPI-DAY-005 | Подготовить стартовый чеклист на понедельник (2026-03-09) | done | Сформирован стартовый execution checklist первого дня W11 с контрольными точками |

## Результат SPI-DAY-001 (аудит структуры `pack/01..07`)

### Что подтверждено
- Индекс методов и файлы методов согласованы по покрытию `UP.M.001..010`.

### Несогласованности и приоритеты правки

| Приоритет | Проблема | Доказательство | Что править |
|---|---|---|---|
| P1 | `pack/ontology.md` остаётся шаблоном (`[Domain Name]`, `_TBD_`) | `pack/ontology.md:1`, `pack/ontology.md:16-24` | Заполнить типы, глоссарий и связи на основе фактических сущностей Pack |
| P1 | `02D-tools-index.md` не заполнен (template placeholders) | `pack/02-domain-entities/02D-tools-index.md:20`, `:26` | Сформировать реальный индекс инструментов и связать с `UP.M.001..010` |
| P1 | В `07-map` отсутствует рабочая карта навигации | `pack/07-map/_map-template.md:11`; в каталоге нет map-файлов кроме шаблона | Создать минимум 1 рабочую карту (`full-pack`) с ссылками на 01..06 |
| P1 | Конфликт схем ID: `UP.*` в manifest vs `OA.*` в сущностях/ошибках/SoTA | `pack/00-pack-manifest.md:200-216`, `pack/01-domain-contract/01C-design-rationale.md:134`, `pack/02-domain-entities/02B-objects-of-attention.md` | Зафиксировать каноническую схему ID и добавить явный mapping/alias |
| P1 | Невалидные ссылки на сущности: `OA.SP.005`, `OA.D.002`, `UP.PP.008..010` | `pack/03-methods/03-UP.M.003-interference-matrix.md:146`, `pack/05-failure-modes/01-failure-modes-catalog.md:165`, `pack/03-methods/07-UP.M.007-tech-vs-state.md:11` | Привести ссылки к существующим OA/UP ID |
| P1 | Есть ссылки на FM, которых нет в каталоге | Отсутствуют в индексе: `FM.G.001`, `FM.TECH.001`, `FM.INN.001..004`, `FM.IP.004`, `FM.ORG.003..005` | Либо добавить карточки/записи в каталог, либо заменить на существующие FM ID |
| P1 | Frontmatter метода `UP.M.005` нарушен (`follows` вне `related`; self-reference в `uses`) | `pack/03-methods/05-UP.M.005-effect-monitoring.md:11`, `:15` | Исправить структуру YAML и убрать циклическую зависимость |
| P2 | Сводка в manifest устарела по количествам | `pack/00-pack-manifest.md:184-185` vs фактически: `FM=14`, `SOTA=9` | Обновить `Content Summary` под фактическое состояние |

## Результат SPI-DAY-002 (backlog ревизии `01A..01D`)

### Порядок выполнения

| Порядок | ID | Файл(ы) | Приоритет | Статус | Что исправить | Доказательство |
|---|---|---|---|---|---|---|
| 1 | DC-001 | `01C-design-rationale.md` + `01B-distinctions.md` | P1 | done | Зафиксировать каноническую ID-схему (`OA.*` vs `UP.*`) и добавить явный alias/mapping в DRR.003 | `01C-design-rationale.md:134`, `01B-distinctions.md:294` |
| 2 | DC-002 | `01B-distinctions.md` | P1 | done | Убрать/заменить неразрешимые ссылки: `FM.G.001`, `SOTA.M.001` на существующие сущности | `01B-distinctions.md:59-60`; `FM.G.001_in_catalog=0`, `SOTA.M.001_in_sota=0` |
| 3 | DC-003 | `01B-distinctions.md` | P1 | done | Исправить неверную привязку метода для гетерогенности: `UP.M.005` -> `UP.M.001` | `01B-distinctions.md:209`; `02B-objects-of-attention.md:80` |
| 4 | DC-004 | `01B-distinctions.md` (+ при необходимости `04-work-products/*`) | P2 | done | Формализовать `Work Product: Матрица "Вмешательство vs. Наблюдение"`: ссылка на существующий WP или создание отдельного WP-артефакта | `01B-distinctions.md:135`; в `04-work-products` отдельного WP нет |
| 5 | DC-005 | `01D-register-bridge.md` | P1 | done | Устранить конфликт ресурсного кода `RES.AM` (привести к объявленному базису или добавить явное объявление) | `01D-register-bridge.md:126` |
| 6 | DC-006 | `01C-design-rationale.md` + `05-failure-modes/*` | P1 | done | Синхронизировать утверждение о трассировке FM к инвариантам с фактическим каталогом (обновить формулировку или довести покрытие) | `01C-design-rationale.md:162`; аудит FM показал пропуски |
| 7 | DC-007 | `01A-bounded-context.md` + `01B-distinctions.md` | P2 | done | Техническая правка качества: обновить метаданные ревизии и исправить опечатки/терминоединообразие | `01A-bounded-context.md:161`; `01B-distinctions.md:152` |

### Критерий завершения SPI-W11-001
- `01A..01D` проходят ссылочную проверку без несуществующих ID.
- DRR.003 не конфликтует с фактической ID-схемой Pack.
- Distinctions ссылаются только на существующие FM/SoTA/Methods/WP.
- Register Bridge использует согласованный ресурсный базис без конфликтующих кодов.

## Результат SPI-DAY-003 (проверка `02C-methods-index.md`)

### Что подтверждено
- Полное покрытие методов `UP.M.001..010` в индексе и в `03-methods/*UP.M.*.md` (пропусков по ID нет).

### Таблица пробелов

| Приоритет | Пробел | Доказательство | Что исправить |
|---|---|---|---|
| P1 | Секция `Methods by Work Product Produced` неполная и содержит лишний `WP.Plan` | `02C-methods-index.md:73-77`; фактически у методов `produces`: `WP.Geo`, `WP.Scenario`, `WP.Matrix`, `WP.Energy`, `WP.Monitor`, `WP.Adapt`, `WP.TechMatrix`, `WP.Pilot`, `WP.KPIAnalysis`, `WP.Verification` | Пересобрать WP-матрицу из фактических `produces` и удалить `WP.Plan` |
| P1 | Недоописаны роли исполнителей для ряда методов | Индекс: `02C-methods-index.md:25,33,41,48`; карточки методов: `02-UP.M.002-*.md:13`, `05-UP.M.005-*.md:13`, `08-UP.M.008-*.md:13`, `10-UP.M.010-*.md:13` | Синхронизировать колонку `Выполняет роль` с `requires_role` (учесть `R.Modeler`, `R.Technologist`, и конкретизировать `UP.M.010`) |
| P2 | Опечатка в названии метода `UP.M.003` | `02C-methods-index.md:26` (`вздействия`) | Исправить орфографию (`воздействия`) |
| P2 | Внизу индекса остался шаблонный checklist `DOMAIN.M.<NNN>` | `02C-methods-index.md:102-105` | Удалить служебный шаблонный хвост из финального индекса |

## Результат SPI-DAY-004 (минимальный объём обновлений `04-work-products`)

### Must-fix в W11 (минимум)

| Приоритет | Файл | Что правим | Доказательство |
|---|---|---|---|
| P1 | `04-work-products/04-work-ledger-template.md` | Исправить ссылку проверки квалификации `UP.M.007-008` на валидные ссылки методов (`07-UP.M.007...`, `08-UP.M.008...`) | `04-work-ledger-template.md:147` |
| P1 | `04-work-products/02-innovation-project-template.md` | Техническая редактура шаблона (ошибки формулировок, опечатки) без изменения структуры блоков | `02-innovation-project-template.md:17,72,127,152` |
| P2 | `04-work-products/01-innovation-implementation-methodology.md` | Убрать маркеры-заглушки `ВСТАВИТЬ Рис.` (заменить на нейтральные подписи/ссылки или удалить) | `01-innovation-implementation-methodology.md:89,145` |
| P2 | `04-work-products/04-work-ledger-template.md` | Обновить метаданные версии/даты после правок | `04-work-ledger-template.md:160` |

### Откладываем (defer)

| Приоритет | Что откладываем | Почему |
|---|---|---|
| P3 | Полный редизайн содержательной методологии (`01-*`) | Не блокирует текущую консистентность Pack; можно делать отдельным редакционным циклом |
| P3 | Декомпозицию `WP.Innovation` на несколько узкоспециализированных шаблонов | Сначала нужен стабильный базовый шаблон и единая терминология |

## Результат SPI-DAY-005 (execution checklist на 2026-03-09)

### Старт дня (09:00-09:30)

1. Проверить рабочее дерево и актуальность ветки.
2. Открыть `WORKPLAN.md`, зафиксировать цель дня: закрыть `SPI-W11-002` и must-fix из `SPI-DAY-004`.
3. Подготовить список файлов к правке: `02C-methods-index.md`, `04-work-ledger-template.md`, `02-innovation-project-template.md`, `01-innovation-implementation-methodology.md`.

### Основной цикл (09:30-14:00)

1. Исправить `02C-methods-index.md` по результатам `SPI-DAY-003`:
   - Пересобрать `Methods by Work Product Produced`.
   - Синхронизировать роли с `requires_role`.
   - Исправить опечатку `вздействия`.
   - Удалить шаблонный хвост `DOMAIN.M.<NNN>`.
2. Выполнить must-fix в `04-work-products` по `SPI-DAY-004`:
   - Починить ссылку `UP.M.007-008` в `04-work-ledger-template.md`.
   - Внести техническую редактуру в `02-innovation-project-template.md`.
   - Убрать `ВСТАВИТЬ Рис.` в `01-innovation-implementation-methodology.md`.
3. Обновить версионные метаданные в затронутых `04-*` файлах.

### Контроль качества (14:00-15:00)

1. Прогнать ссылочную/ID-проверку:
   - Нет ссылок на несуществующие `FM.*`, `SOTA.*`, `OA.*`, `UP.*`.
   - Нет template-маркеров `_TBD_`, `DOMAIN.*` в рабочих файлах.
2. Проверить, что `00-pack-manifest.md` соответствует фактическим количествам после правок.
3. Обновить статусы `SPI-W11-*` в `WORKPLAN.md` по факту.

### Завершение дня (15:00-16:00)

1. Сформировать краткий changelog дня (что исправлено, что осталось).
2. Зафиксировать остаточные риски и перенос на следующий день (если есть).
3. Подготовить commit-пакет по логическим блокам (`02C`, `04-work-products`, `manifest/workplan`).

## Close Capture (2026-03-08)

### Что закрыто

| РП | Статус | Основание |
|---|---|---|
| SPI-W11-002 | done | Синхронизированы роли/produces в `pack/02-domain-entities/02C-methods-index.md`; удалён template-tail `DOMAIN.M.<NNN>` |
| SPI-W11-003 | done | Помимо must-fix, в `01..04` добавлен обязательный контур контроля/отчётности: недельный ритм, gate-решения `GO/NO-GO/PIVOT`, минимальный формат отчётов |

### Артефакты (capture)

1. `pack/02-domain-entities/02C-methods-index.md` — валидная матрица `Methods by Work Product Produced` по фактическим `produces` из `03-methods`.
2. `pack/04-work-products/04-work-ledger-template.md` — квалификационная ссылка переведена на `UP.M.007` и `UP.M.008`.
3. `pack/04-work-products/02-innovation-project-template.md` — устранены критичные опечатки и формулировки в полях шаблона.
4. `pack/04-work-products/01-innovation-implementation-methodology.md` — удалены placeholder-маркеры рисунков.
5. `pack/04-work-products/03-three-pipeline-model.md` — добавлен единый операционный цикл контроля и отчётности по трём конвейерам.
6. `pack/04-work-products/02-innovation-project-template.md`, `01-innovation-implementation-methodology.md`, `04-work-ledger-template.md` — добавлены явные шаги контроля, частота отчётности и минимальная структура отчётов.

### Git фиксация

- Commit: `29df760`
- Message: `close SPI-W11-002 and must-fix for SPI-W11-003`
- Branch: `main`
- Push: `origin/main`

## Close Capture (2026-03-08, SPI-W11-004)

### Что закрыто

| РП | Статус | Основание |
|---|---|---|
| SPI-W11-004 | done | В `pack/05-failure-modes/01-failure-modes-catalog.md` добавлена явная матрица `FM -> UP.M -> управленческое решение`; индекс FM расширен колонками методов и управленческих решений |

### Артефакты (capture)

1. `pack/05-failure-modes/01-failure-modes-catalog.md` — добавлена секция `Матрица связки ключевых failure modes с методами и управленческими решениями (SPI-W11-004)`.
2. `pack/05-failure-modes/01-failure-modes-catalog.md` — расширен `Failure Modes Index`: добавлены колонки `Метод(ы)` и `Управленческое решение` для всех текущих FM.
3. `pack/05-failure-modes/01-failure-modes-catalog.md` — исправлена ссылка `OA.D.002` -> `D.002` в FM.MOD.001.

## Close Capture (2026-03-08, SPI-W11-001)

### Что закрыто

| РП | Статус | Основание |
|---|---|---|
| SPI-W11-001 | done | В `01A..01D` устранены конфликтные/невалидные ссылки и зафиксирована согласованная схема ID (`OA.*` + alias `UP.*`), обновлён ресурсный базис и метаданные ревизии |

### Артефакты (capture)

1. `pack/01-domain-contract/01A-bounded-context.md` — обновлены метаданные ревизии.
2. `pack/01-domain-contract/01B-distinctions.md` — исправлены ссылки на актуальные FM/SoTA, уточнены связи методов и WP, устранены опечатки.
3. `pack/01-domain-contract/01C-design-rationale.md` — формализована эквивалентность `OA.* <-> UP.*`, уточнён статус покрытия FM по инвариантам.
4. `pack/01-domain-contract/01D-register-bridge.md` — устранён конфликт ресурсного кода (`RES.AM` -> `RES.DG`), обновлена версия.

## Close Capture (2026-03-08, SPI-W11-005)

### Что закрыто

| РП | Статус | Основание |
|---|---|---|
| SPI-W11-005 | done | Проведена интеграционная синхронизация Pack: заполнены `ontology.md` и `02D-tools-index.md`, добавлена рабочая map, выровнены manifest/ID-ссылки/индексы |

### Артефакты (capture)

1. `pack/ontology.md` — заменён шаблон на рабочую онтологию домена (`entity types`, glossary, relations, cross-pack terms).
2. `pack/02-domain-entities/02D-tools-index.md` — заполнен реальный индекс инструментов по методам `UP.M.001..010`.
3. `pack/07-map/01-upstream-full-pack-map.md` — добавлена рабочая навигационная карта Pack (full-pack scope).
4. `pack/00-pack-manifest.md` — обновлены `last_updated`, `Content Summary`, `Extended Kinds`, `Entity Index`, `Change Log`.
5. `pack/02-domain-entities/02B-objects-of-attention.md` — добавлен `OA.PP.005` в `Objects of Attention Index`.
6. `pack/03-methods/05..08,10` — исправлены невалидные `FM.*` и `UP.PP.*` ссылки на актуальные ID.

## Бэклог из W10 (источник задач)

| # | РП | Статус | Описание |
|---|-----|--------|----------|
| SPI-W10-001 | Ревизия `pack/01-domain-contract` после последних правок | carry-over | Проверить целостность bounded context, distinctions и design rationale |
| SPI-W10-002 | Проверить связность индексов и методов в `pack/02-03-*` | carry-over | Убедиться, что роли/объекты/индексы согласованы с методами UP.M.001..010 |
| SPI-W10-003 | Обновить операционные шаблоны в `pack/04-work-products` | carry-over | Подготовить шаблоны под ближайший цикл внедрения и отчётности |
