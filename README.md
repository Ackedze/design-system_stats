# design-system_stats

Единое хранилище JSON-отчётов Apollo.

Репозиторий предназначен только для статистики проверок, которую Apollo
передаёт через Supabase Edge Function. Каталоги дизайн-системы, индексы,
паттерны и agentic-контракты здесь не хранятся.

## Структура

```text
apollo/
  stats/
    <figma-user>/
      dd-mm-yyyy/
        <figma-user>_dd-mm-yyyy_hh-mm-ss.json
        <figma-user>_dd-mm-yyyy_hh-mm-ss_agent.json
```

## Типы отчётов

- `*.json` — полный технический отчёт Apollo для отладки аудита.
- `*_agent.json` — компактный отчёт для отправки в корпоративного агента.

## Публикация

Production-сборка Apollo не пишет в репозиторий напрямую. Плагин отправляет
отчёт в Supabase Edge Function `apollo-stats`, а функция уже публикует JSON в
этот репозиторий.

При переезде с `design-system_ab` нужно обновить настройки Edge Function:

- целевой GitHub repo: `Ackedze/design-system_stats`;
- целевая ветка: `main`;
- путь внутри repo: `apollo/stats`.

## Что не хранить здесь

- raw-каталоги Figma;
- `referenceSourcesMVP.json`;
- `componentContractIndex.json`;
- `agent-context.json`, `rules.json`, `contract.generated.json` и другие
  agentic-файлы компонентов;
- markdown-паттерны дизайн-системы.

