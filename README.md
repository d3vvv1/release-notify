# release-notify

Переиспользуемый GitHub Actions workflow: присылает анонс релиза в Telegram.

- **Сайт:** проект передаёт заметки (раздел CHANGELOG) и ссылку — приходит сообщение «🚀 Проект X.Y.Z», список изменений и ссылка.
- **Приложение:** проект передаёт тег GitHub Release — приходят файлы релиза (по умолчанию `*.apk`, до 50 МБ) и сообщение с описанием релиза.

```yaml
jobs:
  notify:
    uses: d3vvv1/release-notify/.github/workflows/notify.yml@main
    with:
      project: Gym Tracker
      release_tag: v1.2.0        # или notes: ... и url: ...
      asset_pattern: '*.apk'
    secrets: inherit             # TELEGRAM_BOT_TOKEN, TELEGRAM_CHAT_ID
```

Секреты `TELEGRAM_BOT_TOKEN` и `TELEGRAM_CHAT_ID` задаются в каждом репозитории, который вызывает workflow. Без них шаг пропускается с предупреждением.
