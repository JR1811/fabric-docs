---
title: Собственные вкладки предметов
description: Вы узнаете как создавать собственные вкладки предметов и как в них добавлять предметы.
authors:
  - IMB11
---

# Собственные вкладки предметов {#custom-item-groups}

Вкладки предметов - это вкладки в творческом инвентаре в которых хранятся предметы. Вы можете создать собственную вкладку предметов, чтобы хранить предметы на отдельной вкладке. Это очень полезно, если ваш мод добавляет много предметов и вы хотите хранить их в одном месте, чтобы все игроки могли их легко получить.

## Создание вкладки с предметами {#creating-the-item-group}

Создавать вкладку с предметами очень легко. Просто создайте новое статическое конечное поле в классе с вашими предметами, чтобы хранить вкладку с предметами и ключа реестра для неё, затем вы можете использовать событие вкладки с предметами аналогично тому, как вы добавляете предметы в ванильную вкладку с предметами:

@[code transcludeWith=:::9](@/reference/latest/src/main/java/com/example/docs/item/ModItems.java)

@[code transcludeWith=:::_12](@/reference/latest/src/main/java/com/example/docs/item/ModItems.java)

<hr />

Теперь вы можете увидеть вкладку с предметами в меню творчества. Однако он не переведён - вам необходимо добавить ключ перевода в файл с переводами, так же как и вы перевели свой первый предмет.

![Вкладка с предметами без перевода в меню творчества](/assets/develop/items/itemgroups_0.png)

## Добавление ключа перевода {#adding-a-translation-key}

Если вы используете `Text.translatable` для конструктора метода `displayName` во вкладке с предмета, вам нужно добавить перевод в файл вашего языка.

```json
{
    "itemGroup.fabric_docs_reference": "Fabric Docs Reference"
}
```

Теперь как вы видите у вкладки с предметами правильное название:

![Полностью сделанная вкладка с предметами с переводом и предметами](/assets/develop/items/itemgroups_1.png)
