---
id: UP.MAP.001
name: Full Pack Navigation Map
scope: full-pack
summary: "Навигация по доменному Pack: distinctions, roles, methods, WP, FM и SoTA"
created: 2026-03-08
last_updated: 2026-03-08
generated: false
---

# [UP.MAP.001] Full Pack Navigation Map

## Purpose

Быстро пройти путь: `принцип -> метод -> рабочий продукт -> типовая ошибка -> решение`.

## Sections

### 1. Core Distinctions

| ID | Distinction | Notes |
|----|-------------|-------|
| [D.001](../01-domain-contract/01B-distinctions.md) | Целевая система vs. управляющие системы | Удерживает фокус на нефти как целевом продукте |
| [D.004](../01-domain-contract/01B-distinctions.md) | Локальное vs. системное | Основа против локальной оптимизации |
| [D.010](../01-domain-contract/01B-distinctions.md) | Состояние нефти vs. процесс добычи | Управление через состояние, а не через activity-only |
| [D.011](../01-domain-contract/01B-distinctions.md) | Физический vs. экономический регистр | Основа для Register Bridge и Work-Ledger |

### 2. Roles

| ID | Role | Primary Methods |
|----|------|-----------------|
| [R.001](../02-domain-entities/02A-roles.md) | Геолог / модельер | UP.M.001, UP.M.003 |
| [R.002](../02-domain-entities/02A-roles.md) | Разработчик | UP.M.002, UP.M.003, UP.M.004 |
| [R.003](../02-domain-entities/02A-roles.md) | Инженер-технолог | UP.M.005, UP.M.006 |
| [R.004](../02-domain-entities/02A-roles.md) | Инженер инноваций | UP.M.007, UP.M.008 |
| [R.005](../02-domain-entities/02A-roles.md) | Управляющий | UP.M.009 |
| [R.006](../02-domain-entities/02A-roles.md) | Владелец стыка | UP.M.005, UP.M.006 |

### 3. Methods

| ID | Method | Produces | Prerequisites |
|----|--------|----------|---------------|
| [UP.M.001](../03-methods/01-UP.M.001-heterogeneity-analysis.md) | Анализ гетерогенности | WP.Geo | - |
| [UP.M.002](../03-methods/02-UP.M.002-scenario-analysis.md) | Анализ сценариев | WP.Scenario | WP.Geo |
| [UP.M.003](../03-methods/03-UP.M.003-interference-matrix.md) | Матрица взаимовлияний | WP.Matrix | WP.Geo, WP.Scenario |
| [UP.M.004](../03-methods/04-UP.M.004-energy-balance.md) | Энергетический баланс | WP.Energy | WP.Geo |
| [UP.M.005](../03-methods/05-UP.M.005-effect-monitoring.md) | Мониторинг эффекта | WP.Monitor | UP.M.004 |
| [UP.M.006](../03-methods/06-UP.M.006-adaptive-management.md) | Адаптивное управление | WP.Adapt | UP.M.005 |
| [UP.M.007](../03-methods/07-UP.M.007-tech-vs-state.md) | Технология vs состояние | WP.TechMatrix | WP.Scenario, WP.Energy |
| [UP.M.008](../03-methods/08-UP.M.008-pilot-design.md) | Дизайн пилота | WP.Pilot | UP.M.007 |
| [UP.M.009](../03-methods/09-UP.M.009-kpi-impact.md) | Анализ KPI | WP.KPIAnalysis | WP.Scenario |
| [UP.M.010](../03-methods/10-UP.M.010-principle-verification.md) | Верификация принципа | WP.Verification | UP.M.005, UP.M.006 |

### 4. Work Products

| ID | Work Product | Produced By | Used By |
|----|--------------|-------------|---------|
| [WP.Innovation](../04-work-products/02-innovation-project-template.md) | Каркас инновационного проекта | UP.M.007, UP.M.008 | UP.M.006, UP.M.009 |
| [WP.ThreePipelines](../04-work-products/03-three-pipeline-model.md) | Операционная модель 3 конвейеров | UP.M.003, UP.M.006 | Governance / weekly review |
| [WP.WorkLedger](../04-work-products/04-work-ledger-template.md) | Учёт Work по переходам | UP.M.005 | UP.M.006, UP.M.010 |
| [BRG.Register](../01-domain-contract/01D-register-bridge.md) | Мост физика -> экономика | UP.M.005, UP.M.010 | WP.WorkLedger |

### 5. Failure Modes

| ID | Failure Mode | Related To |
|----|--------------|------------|
| [FM.PHYS.001](../05-failure-modes/01-failure-modes-catalog.md) | Игнорирование баланса энергии | UP.M.004, INV.003 |
| [FM.SYS.001](../05-failure-modes/01-failure-modes-catalog.md) | Локальное мышление | UP.M.003, INV.006 |
| [FM.IP.003](../05-failure-modes/01-failure-modes-catalog.md) | Масштабное внедрение провалилось | UP.M.008, INV.002 |
| [FM.EW.001](../05-failure-modes/01-failure-modes-catalog.md) | Смешение регистров | 01D, WP.WorkLedger, D.011 |

### 6. SoTA Annotations

| ID | Target | Status |
|----|--------|--------|
| [SOTA.PP.001](../06-sota/01-sota-annotations.md) | OA.PP.001 | deployed |
| [SOTA.PP.004](../06-sota/01-sota-annotations.md) | OA.PP.004 | emerging |
| [SOTA.IP.001](../06-sota/01-sota-annotations.md) | OA.IP.001 | emerging |
| [SOTA.OP.001](../06-sota/01-sota-annotations.md) | OA.OP.001 | theoretical/ignored mix |

## Navigation Hints

- Старт для архитектуры Pack: `01A -> 01B -> 01C -> 01D`.
- Старт для исполнения: `02C -> 03-methods -> 04-work-products`.
- Старт для риск-диагностики: `05-failure-modes -> matrix FM -> decision`.
