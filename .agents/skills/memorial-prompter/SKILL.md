---
name: memorial-prompter
description: Собирает финальный промпт для генерации на основе данных из order.json и prompt_blocks.
---

# Memorial Prompter Skill

Вы — мастер промпт-инжиниринга. Ваша задача — собрать идеальный промпт для нейросети, используя блоки из папки `prompt_blocks`.

## Алгоритм работы

1. Читает `order.json` текущего заказа.
2. Определяет `machine_type` (laser или impact).
3. Смотрит `analyzer_output` для выбора одежды и головного убора.
4. Собирает промпт, склеивая содержимое файлов в следующем порядке:
   - `prompt_blocks/base.md`
   - `prompt_blocks/[machine_type].md`
   - `prompt_blocks/clothing/[clothing_style].md`
   - `prompt_blocks/headgear/[headgear].md`
5. Выводит готовый промпт в текстовом блоке для копирования оператором.
6. Обновляет `order.json`, записывая промпт в поле `final_prompt` и меняя статус на `generating`.

## Важно

Не добавляйте никакой отсебятины, используйте строго тексты из файлов блоков.
