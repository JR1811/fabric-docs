---
title: Создание проекта
description: Пошаговое руководство по созданию нового проекта мода с использованием генератора шаблонов Fabric.
authors:
  - IMB11
  - Cactooz
---

Fabric предоставляет лёгкий путь создания новых проектов мода используя генератор шаблонов модов Fabric, если вы хотите, вы можете создать новый проект используя репозиторий примерного мода, вам следует перейти на [Создание проекта вручную](#manual-project-creation).

## Генерирование проекта {#generating-a-project}

Вы можете использовать [Генератор модов Fabric Template](https://fabricmc.net/develop/template/) для создания нового проекта для вашего мода. Вам следует заполнить обязательные поля, такие как имя мода, имя пакета и версию Minecraft, для которой вы хотите разрабатывать.

Имя пакета должно быть написано строчными буквами, разделено точками и быть уникальным, чтобы избежать конфликтов с пакетами других программистов. Обычно он форматируется как обратный интернет домен, например `com.example.modid`.

![Предварительный просмотр генератора](/assets/develop/getting-started/template-generator.png)

Если вы хотите использовать Kotlin, использовать официальные сопоставления Mojang вместо сопоставлений Yarn или хотите добавить генераторы данных, вы можете выбрать соответствующие параметры в разделе «Дополнительные параметры».

![Секция расширенных настроек](/assets/develop/getting-started/template-generator-advanced.png)

После того как вы заполнили обязательные поля, нажмите на кнопку `Generate`, и генератор для вас создадит новый проект в форме zip-файла.

Вам следует извлечь этот zip-файл в выбранное вами место, а затем открыть извлечённую папку в IntelliJ IDEA:

![Открытый интерпретатор проекта](/assets/develop/getting-started/open-project.png)

## Импортирование проекта {#importing-the-project}

После того как вы открыли проект в IntelliJ IDEA, IDE должен автоматически загрузить конфигурацию Gradle проекта и выполнит необходимые задачи по настройке.

Если вы получите уведомление, говорящее о скрипте сборки Gradle, вам следует нажать кнопку `Import Gradle Project`:

![Интерпретатор Gradle](/assets/develop/getting-started/gradle-prompt.png)

После того как ваш проект был импортирован, вы должны увидеть файлы проекта в проводнике проекта, и сможете начать разработку вашего мода.

## Создание проекта вручную {#manual-project-creation}

:::warning
Для клонирования репозитория примера мода вам потребуется установленный [Git](https://git-scm.com/).
:::

Если вы не можете использовать Fabric Template Mod Generator, вы можете создать новый проект вручную, следуя этим шагам.

Первое, клонируйте репозиторий примера мода используя Git:

```sh
клон git https://github.com/FabricMC/fabric-example-mod/ my-mod-project
```

Это клонирует репозиторий в новую папку под названием `my-mod-project`.

Затем, вы должны удалить папку `.git` из клонированного репозитория, и затем открыть проект в IntelliJ IDEA. Если папка `.git` не отображается, вам следует включить отображение скрытых элементов в вашем файловом менеджере.

После того как вы открыли проект в IntelliJ IDEA, оно должно автоматически загрузить конфигурацию Gradle проекта и должно выполнить необходимые задачи по настройке.

Опять же, как описывалось выше, если вы получите уведомление, говорящее о скрипте сборки Gradle, вам следует нажать кнопку `Import Gradle Project`.

### Изменение Шаблона {#modifying-the-template}

После импорта проекта вам следует изменить детали проекта, чтобы они соответствовали деталям вашего мода:

- Измените файл `gradle.properties` в вашем проекте, чтобы изменить свойства `maven_group` и `archive_base_name` чтобы соответствовать деталям вашего мода.
- Измените файл `fabric.mod.json`, чтобы изменить свойства `id`, `name`, и `description`, чтобы соответствовать деталям вашего мода.
- Убедитесь, что вы обновили версии Minecraft, маппингов, Loader и Loom — все из которых можно запросить через <https://fabricmc.net/develop/> — чтобы они соответствовали версиям, которые вы хотите поддерживать.

Вы конечно же можете изменить имя пакета и основной класс мода, чтобы соответствовать деталям вашего мода.
