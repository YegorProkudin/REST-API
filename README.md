Test Case № 1
Title: Successful creation of a pet (POST)
Description: Переконатися, що запит POST /pet створює нового улюбленця з усіма необхідними полями.

Preconditions: Немає (новий улюбленець ще не існує).

Steps:
Надіслати POST запит до {{host}}/pet з наступним JSON:
{
  "id": 123546,
  "category": {
    "id": 123546,
    "name": "Charlie"
  },
  "name": "Charlie",
  "photoUrls": ["string"]
}
Перевірити статус код 200 OK.
Перевірити, що Content-Type відповіді — application/json.
Переконатися, що поле id є ненульовим цілим числом.
Переконатися, що name є непорожнім рядком.
Переконатися, що photoUrls містить хоча б один елемент.

Expected Result:
Статус код 200 OK.
Content-Type: application/json.
Поле id — позитивне число.
Поле name — непорожній рядок.
photoUrls — масив із хоча б одним елементом.

Test Case № 2
Title: Retrieving an existing pet (GET)
Description: Переконатися, що GET /pet/{petId} повертає правильну інформацію про улюбленця.

Preconditions:
Існує улюбленець з id = 123546.

Steps:
Надіслати GET запит до {{host}}/pet/123546.
Перевірити, що статус код 200 OK.
Переконатися, що відповідь містить необхідні поля (id, category, name, photoUrls).
Переконатися, що category.name є непорожнім рядком.
Переконатися, що photoUrls містить хоча б один елемент.
Переконатися, що tags містить хоча б один тег із непорожнім ім’ям.

Expected Result:
Статус код 200 OK.
Відповідь містить всі необхідні поля.
category.name — непорожній рядок.
photoUrls — масив із хоча б одним елементом.
tags містить хоча б один тег із непорожнім ім’ям.

Test Case № 3
Title: Updating an existing pet (PUT)
Description: Переконатися, що запит PUT /pet оновлює дані улюбленця.

Preconditions:
Улюбленець із id = 123546 існує в системі.

Steps:
Надіслати PUT запит до {{host}}/pet з наступним JSON:
{
  "id": 123546,
  "category": {
    "id": 123546,
    "name": "Charlie Updated"
  },
  "name": "Charlie Updated",
  "photoUrls": ["updated_url"]
}
Перевірити статус код 200 OK.
Переконатися, що Content-Type відповіді — application/json.
Переконатися, що id є ненульовим позитивним числом.
Переконатися, що category.id є ненульовим позитивним числом.
Переконатися, що category.name є непорожнім рядком.
Переконатися, що name є непорожнім рядком.

Expected Result:
Статус код 200 OK.
Content-Type: application/json.
Поле id — позитивне число.
Поле category.name оновлено.
Поле name оновлено.

Test Case № 4
Title: Verifying changes after an update (GET)
Description: Переконатися, що після оновлення улюбленця дані дійсно змінилися.

Preconditions:
Було здійснено PUT запит, і дані улюбленця оновлені.

Steps:
Надіслати GET запит до {{host}}/pet/123546.
Перевірити, що статус код 200 OK.
Переконатися, що id, category, name, photoUrls, tags, status присутні у відповіді.
Переконатися, що category.name відповідає оновленому значенню ("Charlie Updated").
Переконатися, що name відповідає "Charlie Updated".
Переконатися, що photoUrls містить "updated_url".
Переконатися, що tags містить хоча б один елемент.
Переконатися, що status є непорожнім рядком.

Expected Result:
Статус код 200 OK.
Усі поля улюбленця оновлені згідно з PUT запитом.

