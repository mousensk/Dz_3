
# Отличия между `git pull` и `git fetch`

## `git fetch`

- **Что делает**: Загружает все изменения (коммиты, теги, ветки) из удалённого репозитория в ваш локальный репозиторий, но **не сливает** их с вашей текущей веткой. Эти изменения просто становятся доступными для локального просмотра и анализа.
  
  ```bash
  git fetch origin
  ```

- **Когда использовать**: 
  - Когда вы хотите увидеть, какие изменения произошли в удалённом репозитории, прежде чем сливать их со своей локальной веткой.
  - Это полезно для проверки обновлений и анализа, не затрагивая ваш текущий код.

- **Результат**:
  - Локальный репозиторий обновляется с новыми коммитами, но ваш рабочий каталог остаётся без изменений.
  - Вы можете увидеть эти изменения с помощью команд:
    ```bash
    git log origin/main
    ```

## `git pull`

- **Что делает**: Загружает изменения из удалённого репозитория и **автоматически сливает** их с вашей текущей веткой. Это объединение команд `git fetch` и `git merge` в одном действии.
  
  ```bash
  git pull origin main
  ```

- **Когда использовать**:
  - Когда вы хотите сразу обновить свою текущую ветку с последними изменениями из удалённого репозитория.
  - Используется для синхронизации локального репозитория с удалённым без необходимости выполнять дополнительные команды.

- **Результат**:
  - Изменения сливаются с вашей текущей локальной веткой.
  - Это может привести к конфликтам слияния, если изменения в удалённой ветке конфликтуют с вашим локальным кодом.

## Основные отличия:

- **`git fetch`**:
  - Только загружает изменения из удалённого репозитория без слияния с текущей веткой.
  - Позволяет вам анализировать и проверять изменения перед слиянием.
  
- **`git pull`**:
  - Загружает изменения и сразу сливает их с текущей веткой.
  - Может привести к конфликтам, если есть противоречия между локальными и удалёнными изменениями.

Таким образом, **`git fetch`** — это более безопасный способ обновить локальный репозиторий, когда вы хотите сначала посмотреть изменения, в то время как **`git pull`** используется для быстрой синхронизации и автоматического слияния.

----------------------------------------------------------------------------------------------------------------------
Чтобы присоединить новые изменения к **предыдущему коммиту**, в Git используется команда **`git commit --amend`**. Эта команда позволяет изменить последний коммит, добавив новые файлы или изменив сообщение коммита.

### Описание использования команды:

1. **Внесите новые изменения** в файлы, которые хотите присоединить к предыдущему коммиту.
   
2. **Добавьте изменения в индекс (staging area)**, чтобы подготовить их к коммиту:
   ```bash
   git add .
   ```

3. Выполните команду для изменения последнего коммита:
   ```bash
   git commit --amend
   ```

4. Откроется редактор, где вы сможете:
   - Либо изменить сообщение последнего коммита, если это необходимо.
   - Либо оставить его без изменений.

5. **Сохраните и закройте редактор**.

Теперь ваш последний коммит будет включать не только предыдущие изменения, но и новые, которые вы добавили. Это действие полезно, когда вы забыли добавить что-то в предыдущий коммит или хотите поправить сообщение.

### Пример:

1. Вы сделали коммит:
   ```bash
   git commit -m "Добавил файл README"
   ```

2. Затем обнаружили, что забыли добавить важный файл или сделать ещё одно изменение. Вы вносите изменения, добавляете их:
   ```bash
   git add important-file.txt
   ```

3. Присоединяете изменения к предыдущему коммиту:
   ```bash
   git commit --amend
   ```

4. Теперь последний коммит содержит оба изменения — изначальное и добавленное позже.

### Важно:
- Использовать **`git commit --amend`** рекомендуется только если коммит ещё не был отправлен на удалённый репозиторий. Если коммит уже "запушен", изменение коммита может привести к конфликтам с другими разработчиками.
