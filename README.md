# Marketing
Техническое задание Маркетинг

**Описание

Интернет-магазин собирает историю покупателей, проводит рассылки предложений и планирует будущие продажи. Для оптимизации процессов надо выделить пользователей, которые готовы совершить покупку в ближайшее время.

**Цель

Предсказать вероятность покупки в течение 90 дней

Для анализа данных и обучения моделей даны три датафрейма: apparel-purchases с историей покупок, apparel-messages с историей рекламных рассылок и apparel-target_binary с информацией от том, совершит ли клиент покупку в течение следующих 90 дней.

Для решения задачи в датафреймы были добавлены новые признаки: три признака, определяющие категорию покупки, признак, определяющий сколько дней прошло со дня покупки до самой поздней даты рекламной рассылки (соответствует примерной дате выгрузки данных), суммарная стоимость чека, суммарное количество покупок, число уникальных рекламных сообщений, а также  количество каждого вида событий (сообщений), связанных с рекламной рассылкой.

В датафреймах apparel-purchases и apparel-messages была проведена группировка по уникальному идентификатору клиента. После чего эти две таблицы были объединены с третьей таблицей apparel-target_binary. Объединение проводилось по уникальному идентификатору клиента.

Для обучения использовались различные модели: DecisionTreeClassifier, KNeighborsClassifier, LogisticRegression, CatBoostClassifier и SVC.

Для подбора гиперпараметров моделей использовался рандомизированный (случайный) поиск гиперпараметров с помощью RandomizedSearchCV.
В качестве метрики будем использовалась метрика ROC-AUC.

В результате подбора модели и параметров оказалось, что лучшее значение показала модель CatBoostClassifier ('preprocessor__num': MinMaxScaler(), 'models__learning_rate': 0.008, 'models__iterations': 853, 'models__depth': 6). Метрика ROC-AUC на кросс-валидации равна 0.75, на тестовой - 0.74.
