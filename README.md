# Видеохостинг

## Описание проекта

Проект видеохостинга представляет собой платформу, на которой пользователи могут загружать, просматривать и монетизировать видео. Основными источниками дохода для видеохостинга являются реклама, подписка, а также платные функции для создателей контента и рекламодателей.

## Как проект генерирует прибыль

1. **Реклама** — Показ рекламы перед, во время или после видео.
2. **Подписка** — Премиум-подписка для просмотра видео без рекламы и доступ к эксклюзивному контенту.
3. **Продажа данных и аналитики** — Аналитические услуги для рекламодателей и создателей контента.
4. **Платные функции для создателей контента** — Продвижение видео, расширенная аналитика и прочие инструменты.

## Основные пользователи

- **Зрители** — Пользователи, которые просматривают видео на платформе.
- **Создатели контента** — Пользователи, загружающие и монетизирующие свои видео.
- **Рекламодатели** — Компании, размещающие рекламу на платформе.

## User Stories

1. **Зритель просматривает бесплатные видео с рекламой** — Просмотры рекламы во время видео приносят доход платформе.
2. **Создатель контента загружает и монетизирует видео** — Популярные видео генерируют доход для платформы и создателя.
3. **Зритель оформляет премиум-подписку** — Платформа получает доход за счёт подписок.
4. **Рекламодатель запускает рекламную кампанию с таргетингом** — Рекламодатели платят за доступ к целевой аудитории.
5. **Создатель контента продвигает своё видео** — Это платная функция, обеспечивающая доход платформе и увеличивающая охват видео.

## Архитектура системы

### Основные компоненты

1. **Фронтенд интерфейс** — Для зрителей, создателей контента и рекламодателей.
2. **API для видеообработки** — Загрузка, обработка и публикация видео.
3. **Система рекламы** — Показ рекламы на основе предпочтений пользователей.
4. **Платежная система** — Обработка транзакций по подпискам и рекламным кампаниям.
5. **Система аналитики** — Сбор данных о просмотрах, рекламных показах и действиях пользователей.

### Сервисы и взаимодействия

#### Сервис загрузки и обработки видео

- **Методы**: `uploadVideo`, `processVideo`, `publishVideo`
- **Описание**: Позволяет загружать файлы, которые затем кодируются и оптимизируются для потокового воспроизведения.
- **Точки взаимодействия**: Принимает запросы от фронтенда, передает данные в систему хранения.

#### Рекламный сервис

- **Методы**: `serveAd`, `targetAd`, `trackAdPerformance`
- **Описание**: Таргетирует рекламу на основе предпочтений пользователей, используя данные аналитики.
- **Точки взаимодействия**: Использует данные из аналитического сервиса для таргетинга, обновляет рекламные отчеты.

#### Сервис подписок и платежей

- **Методы**: `createSubscription`, `processPayment`, `manageSubscription`
- **Описание**: Обрабатывает транзакции для подписок и других услуг.
- **Точки взаимодействия**: Принимает запросы от фронтенда, обновляет данные в базе подписчиков.

#### Сервис аналитики

- **Методы**: `trackView`, `generateReport`, `analyzeUserBehavior`
- **Описание**: Собирает и анализирует данные о просмотрах и рекламных кампаниях.
- **Точки взаимодействия**: Отправляет данные рекламному сервису и создателям контента.

#### Сервис рекомендаций

- **Методы**: `generateRecommendation`, `updateRecommendationModel`
- **Описание**: Генерирует рекомендации на основе поведения пользователей.
- **Точки взаимодействия**: Использует данные из аналитической базы, отправляет результаты на фронтенд.

### Протоколы и базы данных

- **Протоколы**: REST API для взаимодействия сервисов, gRPC для обработки видео, WebSocket для обновлений в реальном времени.
- **Базы данных**:
  - **Видео и метаданные** — NoSQL (например, MongoDB или S3 для хранения файлов)
  - **Аналитика и статистика** — ClickHouse или BigQuery
  - **Рекламные кампании** — PostgreSQL
  - **Подписчики и платежи** — PostgreSQL


