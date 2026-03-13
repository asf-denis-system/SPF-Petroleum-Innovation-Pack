# Ontology: Upstream Petroleum Development

> Domain ontology per SPF.SPEC.002.  
> Реестр типов сущностей, ключевых терминов и связей для `upstream-petroleum`.

---

## 1. Entity Types

| Code | Type | FPF/SPF Concept | Definition | Not this | Source |
|------|------|-----------------|------------|----------|--------|
| `OA` | Object of Attention | U.System / U.State / U.Characteristic | Второй принцип или ключевой объект наблюдения в домене (физика, системность, инновации, орг-контур, Work) | Не метод, не KPI-отчёт | SPF pack |
| `M` | Method | U.Method | Повторяемый способ анализа/управления, который производит рабочий продукт | Не инструмент, не роль | SPF base |
| `WP` | Work Product | U.Work + U.Episteme | Артефакт-доказательство результата метода | Не сам метод | SPF base |
| `FM` | Failure Mode | SPF-specific | Типовая ошибка интерпретации/применения принципов | Не баг кода | SPF pack |
| `D` | Distinction | A.7 Strict Distinction | Жёсткое различение для правильной инженерной интерпретации | Не факт измерения | SPF base |
| `R` | Role | U.RoleAssignment | Функциональная роль агента в конвейере решений | Не конкретный человек | SPF base |
| `SOTA` | SoTA Annotation | SPF-specific | Аннотация зрелости знания и практики по принципу | Не обзор литературы в полном объёме | SPF pack |
| `MAP` | Navigation Map | U.Episteme | Навигационный слой по структуре Pack и связям сущностей | Не источник доменного знания | SPF pack |
| `BRG` | Register Bridge | U.Episteme + U.Work | Формальная связь физического и экономического регистров (`SW -> OpEx`) | Не финансовая модель компании | Pack extension |

---

## 2. Domain Glossary

| Term | Definition | Parent Concept (SPF) | Related entity |
|------|-----------|---------------------|----------------|
| Состояние нефти | Измеримый факт о стадии целевого продукта в конвейере | U.State | `D.010`, `OA.PP.*` |
| Переход | Смена состояния нефти между узлами цепочки с явным DoD | U.Dynamics | `WP.ThreePipelines` |
| Стык | Граница перехода, где концентрируются потери и неопределённость | U.System boundary | `R.006`, `INV.006` |
| Baseline | Исходные потери/метрики до вмешательства для GO/NO-GO | U.Episteme | `INV.005`, `WP.Pilot` |
| Gate-решение | Формализованное `GO / NO-GO / PIVOT` | U.Control | `UP.M.008`, `UP.M.006` |
| Problem-first приоритезация | Сначала оценка приоритета проблемного поля, затем оценка конкретного проекта | U.Control + U.Episteme | `UP.M.013`, `WP.PriorityPortfolio` |
| Горизонт эффекта | Временной горизонт получения эффекта (`H1/H2/H3`) | U.Dynamics | `UP.M.013`, `WP.PriorityPortfolio` |
| Корзина приоритета | Управленческая категория `P1..P4` по итоговому score | U.Control | `UP.M.013`, `WP.PriorityPortfolio` |
| Ключевой разрыв | Локализованный сбой в цепочке `проблема -> технология -> испытание -> внедрение -> эффект` | U.Dynamics + U.Episteme | `UP.M.011`, `WP.RetroProject` |
| Архитектура программы | Логика покрытия темы, состав подпроектов, очередность и интерфейсы между ними | U.System + U.Dynamics | `UP.M.012`, `WP.RetroProgram` |
| Ретроспектива | Формализованный разбор завершенного цикла для получения повторно используемого знания и решений следующего цикла | U.Episteme + U.Control | `UP.M.011`, `UP.M.012` |
| Work-регистр (физический) | Удельные физические затраты перехода (`SW`, `eta`, `WC`) | U.Work | `OA.EW.001`, `OA.EW.002` |
| Экономический регистр | Денежная интерпретация Work через bridge-параметры | U.Work + U.Episteme | `01D-register-bridge.md` |

---

## 3. Relationships Between Types

| Subject | Relationship | Object | Example |
|---------|-------------|--------|---------|
| Role (`R`) | performs -> | Method (`M`) | `R.002` performs `UP.M.002/003/004` |
| Method (`M`) | produces -> | Work Product (`WP`) | `UP.M.003` produces `WP.Matrix` |
| Method (`M`) | evaluates -> | Object of Attention (`OA`) | `UP.M.007` evaluates `OA.IP.001..003` |
| Failure Mode (`FM`) | violates -> | Invariant (`INV`) | `FM.IP.003` violates `INV.002` |
| Distinction (`D`) | constrains interpretation of -> | Method (`M`) | `D.011` constrains `UP.M.005` and bridge interpretation |
| Work Product (`WP`) | proves transition in -> | Oil pipeline stage | `WP.Monitor` + `WP.Pilot` support gate decision |
| Work Product (`WP`) | prioritizes -> | Project pipeline stage | `WP.PriorityPortfolio` supports stage `Приоритизация` |
| Bridge (`BRG`) | transforms -> | Physical -> Economic register | `SW_lift -> OpEx_lift` in `01D` |

---

## 4. Type Hierarchy (Domain View)

```text
OA
|- OA.PP (Physical Principles)
|- OA.SP (System Principles)
|- OA.IP (Innovation Principles)
|- OA.OP (Organizational Principles)
`- OA.EW (Economic Work Principles)
```

---

## 5. Cross-Pack Terms

| This Pack term | Related Pack | Term there |
|----------------|--------------|------------|
| Production Layer | FPF/SPF | SPF over FPF (DRR.003) |
| Boundary Ledger | FPF | CC-B1.6.1 |
| Delta_work additivity | FPF | B.1.6 |
| Strict Distinction | FPF | A.7 |

---

_Ontology per SPF.SPEC.002. Pack ID: upstream-petroleum_
