# pr_4
**Реалізація нової сутності, створення CRUD-операцій та відповідного RESTful API**

Реалізовано нову сутність Post, створено зв’язок ManyToOne з User, додано поле user у Post. У User додано поле posts як OneToMany зв’язок. Створено відповідну міграцію для створення таблиці post. Перевірено структуру таблиці через інструмент у WebStorm (віджет БД).
Завдання реалізовано повністю, REST API працює коректно, перевірено через Postman.

## 1. Створимо сутність Post в src/orm/entities

![image](https://github.com/user-attachments/assets/ce72597e-6507-4ee2-bfbe-5de87219fa97)

## 2. Створимо та застосуємо міграцію 

```
npm run typeorm migration:generate -- -n CreatePost
npm run typeorm migration:run
```

![image](https://github.com/user-attachments/assets/29545262-8c3c-4114-9628-b4303af48e08)

Перевіримо стан БД

![image](https://github.com/user-attachments/assets/151244e9-f015-4a58-b013-f26510652169)

## 3. Реалізуємо RESTful API для CRUD-операцій

![image](https://github.com/user-attachments/assets/885c6192-880e-4ae4-b5af-cfd87477d88c)

![image](https://github.com/user-attachments/assets/75750eec-880d-4f2f-a875-42f729f0a06d)

![image](https://github.com/user-attachments/assets/c20168d9-028c-4cc3-8e7a-fbeb78e822ee)

```export default router;```

Підключимо його в index.ts

```
import postRoutes from './routes/v1/post';
app.use('/posts', postRoutes);
```

Додамо endpoints у Postman collection та протестуємо

![image](https://github.com/user-attachments/assets/33171e50-cae3-48ce-a626-4dcb3c365517)

Та інше: 

```
{
                "key": "Authorization",
                "value": "{{token}}",
                "type": "text"
              }
            ],
            "body": {
              "mode": "urlencoded",
              "urlencoded": []
            },
            "url": {
              "raw": "{{baseUrl}}/posts",
              "host": ["{{baseUrl}}"],
              "path": ["posts"]
            }
          },
          "response": []
        },
        {
          "name": "/:id",
          "protocolProfileBehavior": {
            "disableBodyPruning": true
          },
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Content-Type",
                "name": "Content-Type",
                "type": "text",
                "value": "application/x-www-form-urlencoded"
              },
              {
                "key": "Accept-Language",
                "type": "text",
                "value": "sl-SI"
              },
              {
                "key": "Authorization",
                "type": "text",
                "value": "{{token}}"
              }
            ],
            "body": {
              "mode": "urlencoded",
              "urlencoded": []
            },
            "url": {
              "raw": "{{baseUrl}}/posts/3",
              "host": ["{{baseUrl}}"],
              "path": ["posts", "3"]
            }
          },
          "response": []
        },
        {
          "name": "/:id",
          "request": {
            "method": "DELETE",
            "header": [
              {
                "key": "Content-Type",
                "name": "Content-Type",
                "type": "text",
                "value": "application/x-www-form-urlencoded"
              },
              {
                "key": "Accept-Language",
                "type": "text",
                "value": "sl-SI"
              },
              {
                "key": "Authorization",
                "type": "text",
                "value": "{{token}}"
              }
            ],
            "body": {
              "mode": "urlencoded",
              "urlencoded": []
            },
            "url": {
              "raw": "{{baseUrl}}/posts/9",
              "host": ["{{baseUrl}}"],
              "path": ["posts", "9"]
            }
          },
          "response": []
        },
        {
          "name": "/:id",
          "request": {
            "method": "PATCH",
            "header": [
              {
                "key": "Content-Type",
                "name": "Content-Type",
                "type": "text",
                "value": "application/x-www-form-urlencoded"
              },
              {
                "key": "Accept-Language",
                "type": "text",
                "value": "sl-SI"
              },
              {
                "key": "Authorization",
                "type": "text",
                "value": "{{token}}"
              }
            ],
            "body": {
              "mode": "urlencoded",
              "urlencoded": [
                {
                  "key": "postname",
                  "value": "Tyrion1",
                  "type": "text"
                },
                {
                  "key": "name",
                  "value": "test name",
                  "type": "text"
                }
              ]
            },
            "url": {
              "raw": "{{baseUrl}}/posts/5",

              "host": ["{{baseUrl}}"],
              "path": ["posts", "5"]
            }
          },
          "response": []
        }
      ],
      "protocolProfileBehavior": {}
    }
  ],
  "protocolProfileBehavior": {}
}
```

## 5. Протестуємо REST API через Postman

![image](https://github.com/user-attachments/assets/b9c7e2ab-d567-4061-a67f-195daafdeb65)

![image](https://github.com/user-attachments/assets/852e1d7d-f78a-410f-addf-02a3e81606ef)

