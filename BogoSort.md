# Тестовый отчет - Команда BogoSort

## 1. Общая информация
**Проект:** Эмпориум  
**Команда:** BogoSort  
**Состав команды:**
- Агеева Ксения 
- Чупраков Сергей 
- Санин Фёдор 
- Куренков Дмитрий

**Ментор:**
- Денис

**Дата начала тестирования:** 25 февраля 2025  
**Дата завершения тестирования:** 12 марта 2025

## 2. Описание тестирования
**Цель тестирования:** Проверка функциональности и нефункциональных характеристик проекта Эмпориум.

> ***Комментарий:***  
> Позитивные и негативные кейсы

> [!IMPORTANT]  
> Проверка производится в браузере Google Chrome, если не написано иное напрямую

## 3. Структура отчета
4. [Тестирование](#тестирование)
5. [Баги](#баги)
6. [Выводы](#выводы)

---

## 4. Тестирование <a name="тестирование"></a>

### 4.1 Добавление объявления (товара)

#### Создание объявления

##### Позитивные сценарии

**$${\color{darkorange}БАГ.}$$**

- [ ] **Успешное добавление товара** <a name="bug-4.1-001"></a>
  - **Ввод:**
    - Категория: _Спорт и отдых_
    - Название товара: _Jogel Мяч баскетбольный JB-100_
    - Цена: _999_
    - Описание: 
    ```md
    Топовый мяч, хорошо отскакивает от большинства поверхностей. Хорошо подходит для стритбола и как для начала занятий баскетболом, так и для профессиональной деятельности.
    ```
    - Фотография: _Файл изображения см. ниже_
    - Адрес: _Москва, ул. Тверская, 12_  
  - **Действие:** Нажатие на кнопку "Разместить объявление"

    ![img.png](./img/4.1/Создание%20объявления/Позитивный%20сценарий/img.png)

  - **Ожидание:**
    - Объявление успешно создано и отображается в каталоге.
    - Фотография корректно загружена и отображается в карточке товара.

    ![img_1.png](./img/4.1/Создание%20объявления/Позитивный%20сценарий/img_1.png)
  
    ![img_2.png](./img/4.1/Создание%20объявления/Позитивный%20сценарий/img_2.png)
  
  - **Фактический результат:**
    - [x] Объявление создано, отображается в каталоге.
    - [ ] Изображение не отображается (отсутствует или сломанный значок).

Добавленное изображение:

![basketball-white-background-ai-generated.jpg](./img/4.1/Создание%20объявления/Позитивный%20сценарий/basketball-white-background-ai-generated.jpg)

- [x] **Цена равная 0**
  - **Ввод:** `0`
  - **Ожидание:** Система пропустила создав объявление с нулевой ценой
  - **Фактический результат:** Система пропустила создав объявление с нулевой ценой

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Нулевая%20цена/img.png)

##### Негативные сценарии

###### Категория

**$${\color{gold}БАГ.}$$**

- [ ] **Изменить в html значение value на несуществующее**  <a name="bug-4.1-006"></a>
  - **Ввод:** Категория `Женский гардероб` // Перед этим поменять значение value с `d4d10f10-4f9a-4bd5-ab1e-d2fc3ed35748` на `d4d10f10-4f9a-4bd5-ab1e-d2fc3ed35700`.
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Категория/Изменить%20value/img.png)

  - **Ожидание:** Не пропустит, вернет ошибку
  - **Фактический результат:** Не пропустило, вернуло ошибку, но с бекенда.

  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Категория/Изменить%20value/img_1.png)

  ![img_2.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Категория/Изменить%20value/img_2.png)

###### Название товара

- [x] **Название не заполнено**
  - **Ввод:** Пустое поле
  - **Ожидание:** Подсветить поле ввода: "Название".
  - **Фактический результат:** Выделилось красным поле "Название".

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Название%20товара/Пустое%20поле/img.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Название слишком длинное (> 45 символов)** <a name="bug-4.1-002"></a>
  - **Ввод:**
  ```md
  оооооооооооооооооооооооооооооооооооооооооооооооооо
  ```
  - **Ожидание:** Ошибка "Название не должно превышать 45 символов"
  - **Фактический результат:** Система не обработала ошибку, объявление разместилось.
    
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Название%20товара/Название%20слишком%20длинное/img.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Название содержит код** <a name="bug-4.1-005"></a>
  - **Ввод:**
  ```js
  <script>alert("Hello")</script>
  ```
  - **Ожидание:** Создание объявления без выведения на экран фразы "Hello"
  - **Фактический результат:** Создание объявления без выведения на экран фразы "Hello", но с пустым названием

**$${\color{gold}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.1-003"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Название%20товара/Введены%20битые%20символы/img.png)
  
  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Объявление удалось создать
  
    ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Название%20товара/Введены%20битые%20символы/img_1.png)

- [x] **Эмодзи в названии**
  - **Ввод:** `🙂`
  - **Ожидание:** Создание объявления с таким названием.
  - **Фактический результат:** Создание объявления с таким названием.
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Название%20товара/Эмодзи/img.png)

###### Цена

**$${\color{gold}БАГ.}$$**

- [ ] **Ввод символов после изменения типа (html)** <a name="bug-4.1-004"></a>
  - **Ввод:** `test` // Перед этим изменить type поля на `text`.

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Ввод%20символов/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Система пропустила создав объявление с нулевой ценой
  
  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Ввод%20символов/img_1.png)

- [x] **Отрицательная цена**
  - **Ввод:** `-2`
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Отрицательная%20цена/img.png)

  - **Ожидание:** Выделилось красным поле "Цена".
  - **Фактический результат:** Выделилось красным поле "Цена".
  
  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Отрицательная%20цена/img_1.png)

- [x] **Битые цифры (html)**
  - **Ввод:** `1` // обработать через https://zalgo.org/ и перед этим изменить type поля на `text`.
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Битая%20цифра/img.png)

  - **Ожидание:** Выделилось красным поле "Цена".
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Битая%20цифра/img_1.png)

- [x] **Дробные числа**
  - **Ввод:** `0.55555`
  - **Ожидание:** Вывод соответствующего уведомления о невозможности дробной цены
  - **Фактический результат:** Вывод соответствующего уведомления о невозможности дробной цены
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Дробные%20числа/img.png)

- [x] **Дробные числа (html)**
  - **Ввод:** `0.55555` // Перед этим изменить type поля на `text`.

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Дробные%20числа%20html/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности дробной цены
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Дробные%20числа%20html/img_1.png)

- [x] **Пустое поле**
  - **Ввод:** Пустое поле
  - **Ожидание:** Вывод соответствующего уведомления о невозможности пустой цены
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Цена/Пустое%20поле/img.png)

###### Описание

- [x] **Пустое поле**
  - **Ввод:** Пустое поле
  
  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Пустое%20поле/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия описания
  - **Фактический результат:** Выделилось красным поле "Описание".

  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Пустое%20поле/img_1.png)

- [x] **Длинное описание (html)**
  - **Ввод:** 
  ```md
  ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss
  ```

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Длинное%20описание%20(html)/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия описания
  - **Фактический результат:** Выделилось красным поле "Описание".

  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Длинное%20описание%20(html)/img_1.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Описание содержит код** <a name="bug-4.1-007"></a>
  - **Ввод:**
  ```js
  <script>alert("Hello")</script>
  ```
  - **Ожидание:** Создание объявления без выведения на экран фразы "Hello"
  - **Фактический результат:** Создание объявления без выведения на экран фразы "Hello", но с пустым описанием

**$${\color{gold}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.1-008"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Битые%20символы/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Объявление удалось создать

    ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Битые%20символы/img_1.png)

**$${\color{red}БАГ.}$$**

- [ ] **Введены сильно битые символы** <a name="bug-4.1-009"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img_2.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Сильно%20битые%20символы/img_2.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Несколько ошибок с бекенда, ошибка открытия объявления, хотя на фронте отрабатывает как для созданного

    ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Сильно%20битые%20символы/img.png)

    ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Описание/Сильно%20битые%20символы/img_1.png)

###### Фотография

**$${\color{red}БАГ.}$$**

- [ ] **Попытка добавить png** <a name="bug-4.1-010"></a>
  - **Ввод:** png и zip (адрес - `img/4.1/Создание объявления/Негативные сценарии/Фотография/png-zip/test.zip`)

    ![portal.png](img/4.1/Создание%20объявления/Негативные%20сценарии/Фотография/png-zip/portal.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобного типа
  - **Фактический результат:** Объявление удалось создать

###### Адрес

- [x] **Пустое поле**
  - **Ввод:** Пустое поле
  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия адреса
  - **Фактический результат:** Выделилось красным поле "Адрес".

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Пустое%20поле/img.png)

- [x] **Длинный адрес (html)**
  - **Ввод:**
  ```md
  ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss
  ```

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Длинный%20адрес%20(html)/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия адреса
  - **Фактический результат:** Выделилось красным поле "Адрес".

  ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Длинный%20адрес%20(html)/img_1.png)

- [x] **Адрес содержит код**
  - **Ввод:**
  ```js
  <script>alert("Hello")</script>
  ```
  - **Ожидание:** Создание объявления без выведения на экран фразы "Hello"
  - **Фактический результат:** Создание объявления без выведения на экран фразы "Hello"

  ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Код/img.png)

**$${\color{red}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.1-011"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Битые%20символы/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Несколько ошибок с бекенда, ошибка открытия объявления, хотя на фронте отрабатывает как для созданного

    ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Битые%20символы/img_1.png)

    ![img_2.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Битые%20символы/img_2.png)

**$${\color{red}БАГ.}$$**

- [ ] **Введен эмодзи** <a name="bug-4.1-016"></a>
  - **Ввод:** `😀`

    ![img.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Эмодзи/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Объявление создалось

    ![img_1.png](./img/4.1/Создание%20объявления/Негативные%20сценарии/Адрес/Эмодзи/img_1.png)

##### Визуальные

###### Категория

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.1-012"></a>
  - **Фактический результат:** Выход за границы экрана

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Категория/img.png)

###### Название

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.1-013"></a>
  - **Фактический результат:** Выход за границы экрана (поля ввода и комментария по ограничению размера)

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Название/img.png)

###### Описание

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.1-014"></a>
  - **Фактический результат:** Выход за границы экрана (поля ввода и комментария по ограничению размера)

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Описание/img.png)

###### Адрес

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.1-015"></a>
  - **Фактический результат:** Выход за границы экрана (поля ввода и комментария по ограничению размера)

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Адрес/img.png)

###### Кнопка

**$${\color{red}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.1-017"></a>
  - **Фактический результат:** Кнопка переход на страницу создания уезжает вниз и загораживает кнопку, благодаря которой можем разместить объявление

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Кнопка/img.png)

###### Форма

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 1000px и меньше** <a name="bug-4.1-018"></a>
  - **Фактический результат:** Форма не помещается, появляется горизонтальный ползунок

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Форма/img.png)

###### Оглавление

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.1-019"></a>
  - **Фактический результат:** Оглавление прижато к левому краю

  ![img.png](./img/4.1/Создание%20объявления/Визуальные/Оглавление/img.png)

##### Визуальные в других браузерах

###### Safari

- [x] **Новых ошибок визуала нет (не считая поля выбора категории)**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Safari/img.png)
  
  ![img_2.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Safari/img_2.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Поле выбора категории** <a name="bug-4.1-020"></a>
  - **Фактический результат:** Нет окантовки (обводка поля выбора)

  ![img_1.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Safari/img_1.png)

###### FireFox

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img.png)

  ![img_1.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img_1.png)
  
  ![img_2.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img_2.png)
  
  ![img_3.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img_3.png)

###### Opera

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Opera/img.png)

  ![img_1.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Opera/img_1.png)

  ![img_2.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Opera/img_2.png)

  ![img_3.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Opera/img_3.png)

###### Microsoft Edge

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img.png)

  ![img_1.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_1.png)

  ![img_2.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_2.png)

  ![img_3.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_3.png)

###### Yandex

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img.png)

  ![img_1.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img_1.png)

  ![img_2.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img_2.png)

  ![img_3.png](img/4.1/Создание%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img_3.png)

<br/><br/><br/>

### 4.2 Редактирование объявления

#### Редактирование объявления

##### Позитивные сценарии

**$${\color{darkorange}БАГ.}$$**

- [ ] **Успешное редактирование объявления** <a name="bug-4.2-001"></a>
  - **Ввод:**
    - Категория: _Спорт и отдых_
    - Название товара: _Jogel Мяч баскетбольный JB-100_
    - Цена: _999_
    - Описание:
    ```md
    Топовый мяч, хорошо отскакивает от большинства поверхностей. Хорошо подходит для стритбола и как для начала занятий баскетболом, так и для профессиональной деятельности.
    ```
    - Фотография: _Файл изображения см. ниже_
    - Адрес: _Москва, ул. Тверская, 12_
  - **Действие:** Нажатие на кнопку "Сохранить изменения"

    ![img.png](./img/4.2/Редактирование%20объявления/Позитивный%20сценарий/img.png)

  - **Ожидание:**
    - Объявление успешно изменено и отображается в каталоге.
    - Фотография корректно загружена и отображается в карточке товара.

    ![img_1.png](./img/4.2/Редактирование%20объявления/Позитивный%20сценарий/img_1.png)

    ![img_2.png](./img/4.2/Редактирование%20объявления/Позитивный%20сценарий/img_2.png)

  - **Фактический результат:**
    - [x] Объявление изменено, отображается в каталоге.
    - [ ] Изображение не отображается (отсутствует или сломанный значок).

Добавленное изображение:

![basketball-white-background-ai-generated.jpg](./img/4.2/Редактирование%20объявления/Позитивный%20сценарий/basketball-white-background-ai-generated.jpg)

##### Негативные сценарии

###### Категория

**$${\color{gold}БАГ.}$$**

- [ ] **Изменить в html значение value на несуществующее**  <a name="bug-4.2-006"></a>
  - **Ввод:** Категория `Женский гардероб` // Перед этим поменять значение value с `d4d10f10-4f9a-4bd5-ab1e-d2fc3ed35748` на `d4d10f10-4f9a-4bd5-ab1e-d2fc3ed35700`.

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Категория/Изменить%20value/img.png)

  - **Ожидание:** Не пропустит, вернет ошибку
  - **Фактический результат:** Не пропустило, вернуло ошибку, но с бекенда.

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Категория/Изменить%20value/img_1.png)

  ![img_2.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Категория/Изменить%20value/img_2.png)

###### Название товара

- [x] **Название не заполнено**
  - **Ввод:** Пустое поле
  - **Ожидание:** Подсветить поле ввода: "Название".
  - **Фактический результат:** Выделилось красным поле "Название".

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Пустое%20поле/img.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Название слишком длинное (> 45 символов)** <a name="bug-4.2-002"></a>
  - **Ввод:**
  ```md
  ssssssssssssssssssssssssssssssssssssssssssssssssss
  ```
  - **Ожидание:** Ошибка "Название не должно превышать 45 символов"
  - **Фактический результат:** Система не обработала ошибку, объявление изменилось.

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Название%20слишком%20длинное/img.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Название содержит код** <a name="bug-4.2-005"></a>
  - **Ввод:**
  ```js
  <script>alert("Hello")</script>
  ```
  
  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Содержит%20код/img.png)

  - **Ожидание:** Изменилось объявления без выведения на экран фразы "Hello"
  - **Фактический результат:** Изменение объявления без выведения на экран фразы "Hello", но название сменилось на пустое

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Содержит%20код/img_1.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.2-003"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Введены%20битые%20символы/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Объявление удалось изменить

    ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Введены%20битые%20символы/img_1.png)

- [x] **Эмодзи в названии**
  - **Ввод:** `🙂`
  - **Ожидание:** Изменение объявления с таким названием.
  - **Фактический результат:** Изменение объявления с таким названием.

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Название%20товара/Эмодзи/img.png)

###### Цена

**$${\color{gold}БАГ.}$$**

- [ ] **Ввод символов после изменения типа (html)** <a name="bug-4.2-004"></a>
  - **Ввод:** `test` // Перед этим изменить type поля на `text`.

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Ввод%20символов/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Система пропустила, изменив объявление на нулевую цену

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Ввод%20символов/img_1.png)

- [x] **Цена равная 0**
  - **Ввод:** `0`
  - **Ожидание:** Система пропустила создав объявление с нулевой ценой
  - **Фактический результат:** Система пропустила, изменив в объявлении цену на ноль

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Нулевая%20цена/img.png)

- [x] **Отрицательная цена**
  - **Ввод:** `-2`

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Отрицательная%20цена/img.png)

  - **Ожидание:** Выделилось красным поле "Цена".
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Отрицательная%20цена/img_1.png)

- [x] **Битые цифры (html)**
  - **Ввод:** `1` // обработать через https://zalgo.org/ и перед этим изменить type поля на `text`.

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Битая%20цифра/img.png)

  - **Ожидание:** Выделилось красным поле "Цена".
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Битая%20цифра/img_1.png)

- [x] **Дробные числа**
  - **Ввод:** `0.55555`
  - **Ожидание:** Вывод соответствующего уведомления о невозможности дробной цены
  - **Фактический результат:** Вывод соответствующего уведомления о невозможности дробной цены

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Дробные%20числа/img.png)

- [x] **Дробные числа (html)**
  - **Ввод:** `0.55555` // Перед этим изменить type поля на `text`.

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Дробные%20числа%20html/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности дробной цены
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Дробные%20числа%20html/img_1.png)

- [x] **Пустое поле**
  - **Ввод:** Пустое поле
  - **Ожидание:** Вывод соответствующего уведомления о невозможности пустой цены
  - **Фактический результат:** Выделилось красным поле "Цена".

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Цена/Пустое%20поле/img.png)

###### Описание

- [x] **Пустое поле**
  - **Ввод:** Пустое поле

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Пустое%20поле/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия описания
  - **Фактический результат:** Выделилось красным поле "Описание".

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Пустое%20поле/img_1.png)

- [x] **Длинное описание (html)**
  - **Ввод:** // Сначала убрать атрибут `maxlength`
  ```md
  ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss
  ```

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Длинное%20описание/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия описания
  - **Фактический результат:** Выделилось красным поле "Описание".

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Длинное%20описание/img_1.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Описание содержит код** <a name="bug-4.2-007"></a>
  - **Ввод:**
  ```js
  <script>alert("Hello")</script>
  ```
  - **Ожидание:** Изменение объявления без выведения на экран фразы "Hello"
  - **Фактический результат:** Изменение объявления без выведения на экран фразы "Hello", но на пустое значение

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Код/img.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.2-008"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Битые%20символы/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Объявление удалось изменить

    ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Битые%20символы/img_1.png)

**$${\color{darkorange}БАГ.}$$**

- [ ] **Введены сильно битые символы** <a name="bug-4.2-009"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Сильно%20битые%20символы/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Ошибка с бекенда, открывает со старым описанием

    ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Описание/Сильно%20битые%20символы/img_1.png)

###### Фотография

**$${\color{red}БАГ.}$$**

- [ ] **Попытка добавить png** <a name="bug-4.2-010"></a>
  - **Ввод:** png и zip (адрес - `img/4.2/Редактирование объявления/Негативные сценарии/Фотография/png-zip/test.zip`)

    ![portal.png](img/4.2/Редактирование%20объявления/Негативные%20сценарии/Фотография/png-zip/portal.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобного типа
  - **Фактический результат:** Объявление не удалось изменить, но ответ с бекенда, а не фронта

    ![img.png](img/4.2/Редактирование%20объявления/Негативные%20сценарии/Фотография/png-zip/img.png)
  
    ![img_1.png](img/4.2/Редактирование%20объявления/Негативные%20сценарии/Фотография/png-zip/img_1.png)

###### Адрес

- [x] **Пустое поле**
  - **Ввод:** Пустое поле
  - **Ожидание:** Вывод соответствующего уведомления о невозможности отсутствия адреса
  - **Фактический результат:** Выделилось красным поле "Адрес".

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Пустое%20поле/img.png)

- [x] **Длинный адрес (html)**
  - **Ввод:**
  ```md
  ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss
  ```

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Длинный%20адрес%20(html)/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности такого адреса
  - **Фактический результат:** Выделилось красным поле "Адрес".

  ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Длинный%20адрес%20(html)/img_1.png)

- [x] **Адрес содержит код**
  - **Ввод:**
  ```js
  <script>alert("Hello")</script>
  ```
  - **Ожидание:** Изменение объявления без выведения на экран фразы "Hello"
  - **Фактический результат:** Изменение объявления без выведения на экран фразы "Hello"

  ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Код/img.png)

**$${\color{red}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.2-011"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Битые%20символы/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Ошибка с бекенда, открывает со старым описанием

    ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Битые%20символы/img_1.png)

**$${\color{red}БАГ.}$$**

- [ ] **Введен эмодзи** <a name="bug-4.2-016"></a>
  - **Ввод:** `😀`

    ![img.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Эмодзи/img.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Объявление изменилось

    ![img_1.png](./img/4.2/Редактирование%20объявления/Негативные%20сценарии/Адрес/Эмодзи/img_1.png)

##### Визуальные

###### Категория

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.2-012"></a>
  - **Фактический результат:** Выход за границы экрана

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Категория/img.png)

###### Название

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.2-013"></a>
  - **Фактический результат:** Выход за границы экрана (поля ввода и комментария по ограничению размера)

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Название/img.png)

###### Описание

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.2-014"></a>
  - **Фактический результат:** Выход за границы экрана (поля ввода и комментария по ограничению размера)

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Описание/img.png)

###### Адрес

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.2-015"></a>
  - **Фактический результат:** Выход за границы экрана (поля ввода и комментария по ограничению размера)

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Адрес/img.png)

###### Кнопка

**$${\color{red}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.2-017"></a>
  - **Фактический результат:** Выход за границы экрана

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Кнопка/img.png)

###### Форма

**$${\color{darkorange}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 1000px и меньше** <a name="bug-4.2-018"></a>
  - **Фактический результат:** Форма не помещается, появляется горизонтальный ползунок

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Форма/img.png)

###### Оглавление

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.2-019"></a>
  - **Фактический результат:** Оглавление прижато к левому краю

  ![img.png](./img/4.2/Редактирование%20объявления/Визуальные/Оглавление/img.png)

##### Визуальные в других браузерах

###### Safari

- [x] **Новых ошибок визуала нет (не считая поля выбора категории)**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Safari/img.png)

  ![img_2.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Safari/img_2.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Поле выбора категории** <a name="bug-4.2-020"></a>
  - **Фактический результат:** Нет окантовки (обводка поля выбора)

  ![img_1.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Safari/img_1.png)

###### FireFox

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img.png)

  ![img_1.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img_1.png)

  ![img_2.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img_2.png)

  ![img_3.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/FireFox/img_3.png)

###### Opera

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Opera/img.png)

  ![img_1.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Opera/img_1.png)

  ![img_2.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Opera/img_2.png)

  ![img_3.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Opera/img_3.png)

###### Microsoft Edge

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img.png)

  ![img_1.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_1.png)

  ![img_2.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_2.png)

  ![img_3.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_3.png)

###### Yandex

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img.png)

  ![img_1.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img_1.png)

  ![img_2.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img_2.png)

  ![img_3.png](img/4.2/Редактирование%20объявления/Визуальные%20в%20других%20браузерах/Yandex/img_3.png)

<br/><br/><br/>

### 4.3 Страница своего товара

##### Визуальные

###### Описание

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.3-001"></a>
  - **Фактический результат:** Выход за границы экрана

  ![img.png](./img/4.3/Визуальные/image_01.png)

#### Оплата

- [x] **Уменьшение экрана до ширины 300px** <a name="bug-4.3-002"></a>
  - **Фактический результат:** Выход за границы экрана

  ![img.png](./img/4.3/Визуальные/image_02.png)

<br/><br/><br/>

### 4.4 Поиск

##### Позитивные сценарии

- [x] **Успешный поиск товара по полному названию**
  - **Ввод:** `Настольная игра`
  - **Действие:** Нажатие на кнопку поиска

    ![img.png](./img/4.4/Поиск/Позитивные%20сценарии/Поиск%20при%20полном%20названии/img.png)

  - **Ожидание:** Удалось успешно найти товар
  - **Фактический результат:** Удалось успешно найти товар

    ![img_1.png](./img/4.4/Поиск/Позитивные%20сценарии/Поиск%20при%20полном%20названии/img_1.png)

- [x] **Успешный поиск товара по неполному названию**
  - **Ввод:** `Настольная игр`
  - **Действие:** Нажатие на кнопку поиска

    ![img.png](./img/4.4/Поиск/Позитивные%20сценарии/Поиск%20при%20неполном%20названии/img.png)

  - **Ожидание:** Удалось успешно найти товар
  - **Фактический результат:** Удалось успешно найти товар

    ![img_1.png](./img/4.4/Поиск/Позитивные%20сценарии/Поиск%20при%20неполном%20названии/img_1.png)

**$${\color{darkorange}БАГ.}$$**

- [ ] **Возврат к прошлому запросу** <a name="bug-4.4-001"></a>
  - **Ввод:** `Настольная игр`
  - **Действие:** Нажатие на кнопку поиска

    ![img.png](./img/4.4/Поиск/Позитивные%20сценарии/Возврат%20к%20прошлому%20запросу/img.png)

  - **Ввод:** `Настольная игра`
  - **Действие:** Нажатие на кнопку поиска

    ![img_1.png](./img/4.4/Поиск/Позитивные%20сценарии/Возврат%20к%20прошлому%20запросу/img_1.png)

  - **Действие:** Нажатие на кнопку вернуться

    ![img_2.png](./img/4.4/Поиск/Позитивные%20сценарии/Возврат%20к%20прошлому%20запросу/img_2.png)

  - **Ожидание:** Видно предыдущий запрос
  - **Фактический результат:** Поломалась верстка

    ![img_3.png](./img/4.4/Поиск/Позитивные%20сценарии/Возврат%20к%20прошлому%20запросу/img_3.png)

##### Негативные сценарии

**$${\color{gold}БАГ.}$$**

- [ ] **Поиск пустоты**  <a name="bug-4.4-002"></a>
  - **Ввод:** Пустая строка

    ![img.png](./img/4.4/Поиск/Негативные%20сценарии/Пустая%20строка/img.png)

  - **Действие:** Нажатие на кнопку поиска
  - **Ожидание:** Должно подсказать, что ничего не введено
  - **Фактический результат:** Ничего не произошло

**$${\color{gold}БАГ.}$$**

- [ ] **Поиск несуществующего товара**  <a name="bug-4.4-003"></a>
  - **Ввод:** `что-то непонятное`

    ![img.png](./img/4.4/Поиск/Негативные%20сценарии/Несуществующий%20товар/img.png)

  - **Действие:** Нажатие на кнопку поиска
  - **Ожидание:** Должно подсказать, что таких товаров нет
  - **Фактический результат:** Пустая страница

    ![img_1.png](./img/4.4/Поиск/Негативные%20сценарии/Несуществующий%20товар/img_1.png)

**$${\color{darkorange}БАГ.}$$**

- [ ] **Битые символы**  <a name="bug-4.4-004"></a>
  - **Ввод:** `Настольная игра` // обработанное через https://zalgo.org/

    ![img.png](./img/4.4/Поиск/Негативные%20сценарии/Битые%20символы/img.png)

  - **Действие:** Нажатие на кнопку поиска
  - **Ожидание:** Должно подсказать, что таких товаров нет
  - **Фактический результат:** Ошибка с бекенда

    ![img_1.png](./img/4.4/Поиск/Негативные%20сценарии/Битые%20символы/img_1.png)

**$${\color{darkorange}БАГ.}$$**

- [ ] **Большой запрос**  <a name="bug-4.4-005"></a>
  - **Ввод:** 
  ```md
  ssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss
  ```
  ![img.png](./img/4.4/Поиск/Негативные%20сценарии/Длинный%20запрос/img.png) 

  - **Действие:** Нажатие на кнопку поиска
  - **Ожидание:** Должно подсказать, что таких товаров нет
  - **Фактический результат:** Ошибка с бекенда

    ![img_1.png](./img/4.4/Поиск/Негативные%20сценарии/Длинный%20запрос/img_1.png)

##### Визуальные

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 1200px** <a name="bug-4.4-006"></a>
  - **Фактический результат:** Пустая кнопка поиска

  ![img.png](./img/4.4/Поиск/Визуальные/img.png)

##### Визуальные в других браузерах

###### Safari

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Safari/img.png)

  ![img_1.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Safari/img_1.png)

###### FireFox

**$${\color{gold}БАГ.}$$**

- [ ] **Поломанный адаптив** <a name="bug-4.4-007"></a>
  - **Фактический результат:** Неверное расположения поля при изменении размера экрана, не всегда занимает все доступное место

  ![img.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/FireFox/img.png)

  ![img_1.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/FireFox/img_1.png)

  ![img_2.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/FireFox/img_2.png)

  ![img_3.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/FireFox/img_3.png)

  ![img_4.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/FireFox/img_4.png)

###### Opera

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Opera/img.png)

  ![img_1.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Opera/img_1.png)

  ![img_2.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Opera/img_2.png)

  ![img_3.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Opera/img_3.png)

###### Microsoft Edge

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img.png)

  ![img_1.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_1.png)

  ![img_2.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_2.png)

  ![img_3.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Microsoft%20Edge/img_3.png)

###### Yandex

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

  ![img.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Yandex/img.png)

  ![img_1.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Yandex/img_1.png)

  ![img_2.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Yandex/img_2.png)

  ![img_3.png](img/4.4/Поиск/Визуальные%20в%20других%20браузерах/Yandex/img_3.png)

<br/><br/><br/>

### 4.5 Оформление заказа

##### Позитивные сценарии

  - [x] **Успешное оформление заказа**
    - **Ввод:**
      - Вид дотсавки: _Доставка_
      - ФИО получателя: _Иванов Иван Иванович_
      - Адрес доставки: _г.Москва, ул.Пушкина, д.15 к.1_
    - **Действие:** Нажатие на кнопку "Оформить заказ"

      ![img_0.png](./img/4.5/Позитивные%20сценарии/img_0.png)

    - **Ожидание:**
      - Заказ успешно оформлен
      - Произошел редирект на страницу с заказами

        ![img_1.png](./img/4.5/Позитивные%20сценарии/img_1.png)

    - **Фактический результат:**
      - [x] Заказ успешно оформлен
      - [x] Произошел редирект на страницу с заказами

##### Негативные сценарии

###### Вид доставки

**$${\color{gold}БАГ.}$$**

  - [ ]  **Изменить в html значение value на несуществующее** <a name="bug-4.5-001"></a>
    - **Ввод:** Вид доставки `Доставка` // Перед этим поменять значение value c `delivery` на `delivery111` 

      ![img_0.png](./img/4.5/Негативные%20сценарии/img_0.png)

    - **Ожидание:** Не пропустит, вернет ошибку
    - **Фактический результат:** Не пропустило, вернуло ошибку, но с бекенда

      ![img_1.png](./img/4.5/Негативные%20сценарии/img_1.png)

###### ФИО получателя

  - [x] **Поле не заполнено**
    - **Вввод:** пустое поле
    - **Ожидние:** Подсветить поле ввода: "ФИО получателя"
    - **Фактический результат:** Появилась подсказка `Заполните это поле.` для поля "ФИО получателя".

      ![img_2.png](./img/4.5/Негативные%20сценарии/img_2.png)

  - [x] **Убрать в html аттрибут required для поля**
    - **Вввод:** пустое поле // Перед этим убрать аттрибут `required`

      ![img_3.png](./img/4.5/Негативные%20сценарии/img_3.png)

    - **Ожидние:** Подсветить поле ввода "ФИО получателя"
    - **Фактический результат:** Подсветилось красным поле "ФИО получателя".

      ![img_4.png](./img/4.5/Негативные%20сценарии/img_4.png)

**$${\color{gold}БАГ.}$$**

  - [ ] **Ввод слишком длинный (250 символов)** <a name="bug-4.5-002"></a>
    - **Ввод:**
    ```md
    оооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооо
    ```
    - **Ожидание:** Ошибка "Длина ФИО не должна превышать N символов"
    - **Фактический результат:** Вернулась ошибка с бэкенда

      ![img_5.png](./img/4.5/Негативные%20сценарии/img_5.png)

**$${\color{gold}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.5-003"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img_6.png](./img/4.5/Негативные%20сценарии/img_6.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Заказ успешно создался

    ![img_7.png](./img/4.5/Негативные%20сценарии/img_7.png)

- [x] **Эмодзи в поле ввода**
  - **Ввод:** `🙂`

    ![img_8.png](./img/4.5/Негативные%20сценарии/img_8.png)

  - **Ожидание:** Создание заказа с таким ФИО
  - **Фактический результат:** Создание заказа с таким ФИО

    ![img_9.png](./img/4.5/Негативные%20сценарии/img_9.png)

###### Адрес доставки

  - [x] **Поле не заполнено**
    - **Вввод:** пустое поле
    - **Ожидние:** Подсветить поле ввода: "Адрес доставки"
    - **Фактический результат:** Появилась подсказка `Заполните это поле.` для поля "Адрес доставки".

      ![img_10.png](./img/4.5/Негативные%20сценарии/img_10.png)

  - [x] **Убрать в html аттрибут required для поля**
    - **Вввод:** пустое поле // Перед этим убрать аттрибут `required`

      ![img_11.png](./img/4.5/Негативные%20сценарии/img_11.png)

    - **Ожидние:** Подсветить поле ввода "Адрес доставки"
    - **Фактический результат:** Подсветилось красным поле "Адрес доставки".

      ![img_12.png](./img/4.5/Негативные%20сценарии/img_12.png)

**$${\color{gold}БАГ.}$$**

  - [ ] **Ввод слишком длинный (250 символов)** <a name="bug-4.5-004"></a>
    - **Ввод:**
    ```md
    оооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооооо
    ```
    - **Ожидание:** Ошибка "Длина адреса не должна превышать N символов"
    - **Фактический результат:** Вернулась ошибка с бэкенда

      ![img_13.png](./img/4.5/Негативные%20сценарии/img_13.png)

**$${\color{red}БАГ.}$$**

- [ ] **Введены битые символы** <a name="bug-4.5-005"></a>
  - **Ввод:** `Hello` // обработанное через https://zalgo.org/

    ![img_14.png](./img/4.5/Негативные%20сценарии/img_14.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Вернулась ошибка с бэкенда

    ![img_15.png](./img/4.5/Негативные%20сценарии/img_15.png)

**$${\color{red}БАГ.}$$**

- [ ] **Эмодзи в поле ввода** <a name="bug-4.5-006"></a>
  - **Ввод:** `🙂`

    ![img_16.png](./img/4.5/Негативные%20сценарии/img_16.png)

  - **Ожидание:** Вывод соответствующего уведомления о невозможности использования подобных символов
  - **Фактический результат:** Создание заказа с таким адресом

    ![img_17.png](./img/4.5/Негативные%20сценарии/img_17.png)

##### Визуальные

**$${\color{gold}БАГ.}$$**

  - [ ] **Уменьшение ширины экрана до 380px** <a name="bug-4.5-007"></a>
     - **Фактический результат:** Выход кнопки за границы блока 

      ![img_0.png](./img/4.5/Визуальные/img_0.png)

##### Визуальные в других браузерах

###### FireFox

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_1.png](./img/4.5/Визуальные/img_1.png)
    ![img_2.png](./img/4.5/Визуальные/img_2.png)

###### Opera

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_3.png](./img/4.5/Визуальные/img_3.png)
    ![img_4.png](./img/4.5/Визуальные/img_4.png)

###### Edge

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_5.png](./img/4.5/Визуальные/img_5.png)
    ![img_6.png](./img/4.5/Визуальные/img_6.png)

### 4.6 Заказы

##### Позитивные сценарии

---

##### Негативные сценарии

---

##### Визуальные

**$${\color{gold}БАГ.}$$**

  - [ ] **Уменьшение ширины экрана до 280px** <a name="bug-4.6-001"></a>
     - **Фактический результат:** Выход номера телефона за границы блока 

        ![img_0.png](./img/4.6/Визуальные/img_0.png)

##### Визуальные в других браузерах

###### FireFox

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_1.png](./img/4.6/Визуальные/img_1.png)
    ![img_2.png](./img/4.6/Визуальные/img_2.png)

###### Opera

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_3.png](./img/4.6/Визуальные/img_3.png)
    ![img_4.png](./img/4.6/Визуальные/img_4.png)

###### Edge

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_5.png](./img/4.6/Визуальные/img_5.png)
    ![img_6.png](./img/4.6/Визуальные/img_6.png)

### 4.7 Каталог и главная страница

##### Позитивные сценарии

- [x] **Подгрузка новых объявлений при скролле главной страницы**
  - **Действие:** Скролл главной страницы
  - **Ожидание:** Подгрузка новых объявлений
  - **Фактический результат:** Подгрузка новых объявлений

    ![img_0.png](./img/4.7/Позитивные%20сценарии/img_0.png)
    ![img_1.png](./img/4.7/Позитивные%20сценарии/img_1.png)

- [x] **Переход к товарам выбранной категории**
  - **Действие:** Нажатие на ссылку категории

    ![img_0.png](./img/4.7/Позитивные%20сценарии/img_2.png)

  - **Ожидание:** Редирект на старницу категории
  - **Фактический результат:** Редирект на старницу категории

    ![img_0.png](./img/4.7/Позитивные%20сценарии/img_3.png)

##### Негативные сценарии

- [x]  **Изменить в html значение href на несуществующее**
    - **Действие:** Нажатие на ссылку категории // Перед этим поменять значение href c `/category/d4d10f10-4f9a-4bd5-ab1e-d2fc3ed35748` на `/category/11` 

      ![img_0.png](./img/4.7/Негативные%20сценарии/img_0.png)

    - **Ожидание:** Появится сообщение о том, что такой категории не существует
    - **Фактический результат:** Появилось сообщение о том, что такой категории не существует

      ![img_1.png](./img/4.7/Негативные%20сценарии/img_1.png)

##### Визуальные

---

##### Визуальные в других браузерах

###### FireFox

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_1.png](./img/4.7/Визуальные/img_1.png)
    ![img_2.png](./img/4.7/Визуальные/img_2.png)

###### Opera

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_3.png](./img/4.7/Визуальные/img_3.png)
    ![img_4.png](./img/4.7/Визуальные/img_4.png)

###### Edge

- [x] **Новых ошибок визуала нет**
  - **Фактический результат:** Новые ошибки не появилось (в сравнении с Google Chrome)

    ![img_5.png](./img/4.7/Визуальные/img_5.png)
    ![img_6.png](./img/4.7/Визуальные/img_6.png)

### 4.8 Страница товара (чужая)

##### Визуальные

###### Описание

**$${\color{gold}БАГ.}$$**

- [ ] **Уменьшение экрана до ширины 300px** <a name="bug-4.8-001"></a>
  - **Фактический результат:** Выход за границы экрана

  ![img.png](./img/4.8/Визуальные/image.png)

<br/><br/><br/>

### 4.9 Корзина

##### Позитивные сценарии

- [x] **Успешное добавление товара в корзину для авторизованного пользователя**
  - **Действие:** Нажатие на кнопку "В корзину"

    ![img.png](./img/4.9/Позитивные%20сценарии/img_0.png)

  - **Ожидание:** Удалось успешно добавить товар в корзину
  - **Фактический результат:** Удалось успешно добавить товар в корзину

    ![img_1.png](./img/4.9/Позитивные%20сценарии/img_1.png)
    ![img_2.png](./img/4.9/Позитивные%20сценарии/img_2.png)

- [x] **Добавление товара в корзину для неавторизованного пользователя**
  - **Действие:** Нажатие на кнопку "В корзину"

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_3.png)
    
  - **Ожидание:** Появление модального окна для авторизации
  - **Фактический результат:** Появление модального окна для авторизации

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_4.png)

- [x] **Переход в корзину с главной страницы**
  - **Действие:** Нажатие на значок "корзина" в правом верхнем углу

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_17.png)

  - **Ожидание:** Отображение страницы корзины. Так как корзина пустая - отображение пустой корзины и кнопки "За покупками"
  - **Фактический результат:** Отображение страницы корзины. Так как корзина пустая - отображение пустой корзины и кнопки "За покупками"

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_18.png)

  - **Ожидание:** Отображение страницы корзины. Так как в корзине есть товары - отображение моей корзины
  - **Фактический результат:** Отображение страницы корзины. Так как в корзине есть товары - отображение моей корзины

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_19.png)

- [x] **Переход со страницы корзины на главную**
  - **Действие:** Нажатие на кнопку "За покупками"

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_18.png)

  - **Ожидание:** Отображение главной страницы с объявлениями
  - **Фактический результат:** Отображение главной страницы с объявлениями

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_17.png)

- [x] **Оформление покупки для одного товара**
  - **Действие:** Нажатие на кнопку "Перейти к оформлению"

    ![img_8.png](./img/4.9/Позитивные%20сценарии/img_8.png)
    
  - **Ожидание:** Появление модального окна для заполнения данных о доставке
  - **Фактический результат:** Появление модального окна для заполнения данных о доставке

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_7.png)
  
  - **Действие:** Заполнение данных корректными данными

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_9.png)
    
  - **Ожидание:** Переход на страницу заказы, где отображается заказ с присвоенным ему номером
  - **Фактический результат:** Переход на страницу заказы, где отображается заказ с присвоенным ему номером
  
    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_10.png)

- [x] **Выбор варианта получения с доставкой**
  - **Действие:** Выбор в выпадающем списке варианта "доставка"

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_11.png)
    
  - **Ожидание:** Появление поля для ввода адреса
  - **Фактический результат:** Появление поля для ввода адреса

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_8.png)

- [x] **Выбор варианта получения у продавца**
  - **Действие:** Выбор в выпадающем списке варианта "заберу у продавца"

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_11.png)
    
  - **Ожидание:** Поля для ввода адреса нет
  - **Фактический результат:** Поля для ввода адреса нет

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_12.png)

- [x] **Оформление покупки для нескольких товаров от разных продавцов**
  - **Действие:** Нажатие на кнопку "Перейти к оформлению"

    ![img_8.png](./img/4.9/Позитивные%20сценарии/img_13.png)
    
  - **Ожидание:** Появление модального окна для заполнения данных о доставке
  - **Фактический результат:** Появление модального окна для заполнения данных о доставке

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_7.png)
  
  - **Действие:** Заполнение данных корректными данными

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_9.png)
    
  - **Ожидание:** Переход на страницу заказы, где отображается заказ с присвоенным ему номером. Так как товары принадлежат разным продавцам - для каждого товара каждого продавца создается отдельный заказ. 
  - **Фактический результат:** Переход на страницу заказы, где отображается заказ с присвоенным ему номером. Так как товары принадлежат разным продавцам - для каждого товара каждого продавца создается отдельный заказ. 
  
    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_14.png)

- [x] **Оформление покупки для нескольких товаров от одного продавца**
**$${\color{red}БАГ.}$$** <a name="bug-4.9-001"></a>

  - **Действие:** Нажатие на кнопку "Перейти к оформлению" 

    ![img_8.png](./img/4.9/Позитивные%20сценарии/img_15.png)
    
  - **Ожидание:** Появление модального окна для заполнения данных о доставке
  - **Фактический результат:** Появление модального окна для заполнения данных о доставке

    ![img_4.png](./img/4.9/Позитивные%20сценарии/img_7.png)
  
  - **Действие:** Заполнение данных корректными данными

    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_9.png)
    
  - **Ожидание:** Переход на страницу заказы, где отображается заказ с присвоенным ему номером. Так как товары принадлежат одному продавцу - создается общий заказ для этих двух товаров. 
  - **Фактический результат:** Переход на страницу заказы, где отображается заказ с присвоенным ему номером. В заказ попал только один из товаров. Второй товар не учитывается.
  
    ![img_3.png](./img/4.9/Позитивные%20сценарии/img_16.png)

##### Негативные сценарии

- [ ] **Попытка повторно добавить товар в корзину**
  - **Действие:** Нажатие на кнопку "В корзину"

    ![img_5.png](./img/4.9/Негативные%20сценарии/img_5.png)

  - **Ожидание:** После добавления товара в корзину текст кнопки меняется на "Товар уже в корзине", по кнопке осуществляется переход в корзину
  - **Фактический результат:** После добавления товара в корзину текст кнопки меняется на "Товар уже в корзине", по кнопке осуществляется переход в корзину

    ![img_4.png](./img/4.9/Негативные%20сценарии/img_5.png)
    ![img_4.png](./img/4.9/Негативные%20сценарии/img_6.png)

#### Визуальные

- [ ] **Уменьшение экрана до ширины 1000px** **$${\color{red}БАГ.}$$**  <a name="bug-4.9-001"></a>
  - **Фактический результат:** Пропадает кнопка "корзина" 

  ![img.png](./img/4.9/Визуальные/img_1.png)


### 4.10 Избранное

##### Позитивные сценарии

- [x] **Успешное добавление товара в избранное с главной страницы**
  - **Действие:** Нажатие на кнопку со значком "лайка"

    ![img.png](./img/4.10/Позитивные%20сценарии/img_1.png)

  - **Ожидание:** Кнопка лайка окрасилась в красный цвет, товар добавлен в избранное
  - **Фактический результат:** Кнопка лайка окрасилась в красный цвет, товар добавлен в избранное

    ![img_1.png](./img/4.10/Позитивные%20сценарии/img_1_1.png)
    ![img_2.png](./img/4.10/Позитивные%20сценарии/img_2.png)

- [x] **Успешное добавление товара в корзину со страницы товара**
  - **Действие:** Нажатие на кнопку со значком "лайка"

    ![img_3.png](./img/4.10/Позитивные%20сценарии/img_3.png)
    
  - **Ожидание:** Кнопка лайка окрасилась в красный цвет, товар добавлен в избранное
  - **Фактический результат:** Кнопка лайка окрасилась в красный цвет, товар добавлен в избранное

    ![img_4.png](./img/4.10/Позитивные%20сценарии/img_4.png)
    ![img_2.png](./img/4.10/Позитивные%20сценарии/img_2.png)

- [x] **Обновление количества добавления товара в избранное**
  - **Действие:** Добавление товара в избранное с аккаунта "А"
  - **Действие:** Вход с аккаунта "Б"
  - **Действие:** Добавление товара в избранное с аккаунта "Б"
    
  - **Ожидание:** Счетчик избранного увеличился на 1. После лайка с аккаунта "Б" счетчик лайка увеличился еще на один.
  - **Фактический результат:** Счетчик избранного увеличился на 1. После лайка с аккаунта "Б" счетчик лайка увеличился еще на один.

    ![img_4.png](./img/4.10/Позитивные%20сценарии/img_5.png)
    ![img_2.png](./img/4.10/Позитивные%20сценарии/img_6.png)

#### Негативные сценарии

----

#### Визуальные

- [ ] **Уменьшение экрана до ширины 300px** **$${\color{red}БАГ.}$$**  <a name="bug-4.10-001"></a>
  - **Фактический результат:** Поломалась верстка - кнопка лайка не на одном уровне с ценой

  ![img.png](./img/4.10/Визуальные/img.png)


---

## 5. Баги <a name="баги"></a>

| ID                                         | Описание бага                                                                                                                                                                             | Шаги для воспроизведения                                                                                                                                                       | Ожидаемый результат                                                        | Фактический результат                                           | Приоритет                          |
|--------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|
| **Раздел 4.1: Размещение объявлений**      | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.1-001](#bug-4.1-001)                    | Не отображается изображение после размещение объявления                                                                                                                                   | 1. Открыть размещение объявления  <br/>2. Заполнить все поля обязательно добавив изображение  <br/>3. Нажать на кнопку "Разместить объявление"                                 | Товар добавляется                                                          | Картинка не отображается после добавления                       | 🟠 $${\color{darkorange}Средний}$$ |
| [4.1-002](#bug-4.1-002)                    | Удаётся разместить объявление с названием длиннее чем 45 символов                                                                                                                         | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, название сделать длинной больше 45 символов  <br/>3. Нажать на кнопку "Разместить объявление"                    | Вывод соответствующей ошибки                                               | Объявление разместилось                                         | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-003](#bug-4.1-003)                    | Введены битые символы в названии объявления и они системой никак не запрещены                                                                                                             | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, название заполнить битыми символами  <br/>3. Нажать на кнопку "Разместить объявление"                            | Вывод соответствующей ошибки                                               | Объявление разместилось                                         | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-004](#bug-4.1-004)                    | Введены символы в поле цены (изменение html), а должна вывестись ошибка                                                                                                                   | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, цену заполнить символами, перед этим сменив тип поля на `text`  <br/>3. Нажать на кнопку "Разместить объявление" | Вывод соответствующей ошибки                                               | Объявление разместилось с ценой равной 0                        | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-005](#bug-4.1-005)                    | Удалось создать товар с пустым названием                                                                                                                                                  | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, название заполнить скриптом `<script>alert("Hello")</script>`  <br/>3. Нажать на кнопку "Разместить объявление"  | Создание объявления с таким названием                                      | Объявление разместилось с пустым названием                      | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-006](#bug-4.1-006)                    | Изменено значение value у категории                                                                                                                                                       | 1. Открыть размещение объявления  <br/>2. Через код страницы поменять значение value и выбрать измененное значение  <br/>3. Нажать на кнопку "Разместить объявление"           | Вывод соответствующей ошибки                                               | Ошибка пришла с бекенда                                         | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-007](#bug-4.1-007)                    | Удалось создать товар с пустым описанием                                                                                                                                                  | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, описание заполнить скриптом `<script>alert("Hello")</script>`  <br/>3. Нажать на кнопку "Разместить объявление"  | Создание объявления с таким названием                                      | Объявление разместилось с пустым названием                      | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-008](#bug-4.1-008)                    | Введены битые символы в описании объявления и они системой никак не запрещены                                                                                                             | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, описание заполнить битыми символами  <br/>3. Нажать на кнопку "Разместить объявление"                            | Вывод соответствующей ошибки                                               | Объявление разместилось                                         | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-009](#bug-4.1-009)                    | Введены сильно битые символы в описании объявления и они системой никак не запрещены, ошибки со стороны бекенда, возможная высокая уязвимость, проходит далеко                            | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, описание заполнить сильно битыми символами  <br/>3. Нажать на кнопку "Разместить объявление"                     | Вывод соответствующей ошибки                                               | Несколько ошибок со стороны бекенда                             | 🔴 $${\color{red}Высокий}$$        |
| [4.1-010](#bug-4.1-010)                    | Прокидываются картинки других типов до бекенда, возможная уязвимость (zip-бомба, Path Traversal (архив с путями вне разрешенной директории), прокидывание скриптов (майнер, червь...) ... | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, добавить png картинку  <br/>3. Нажать на кнопку "Разместить объявление"                                          | Вывод соответствующей ошибки                                               | Объявление разместилось, картинка заблочилась на уровне бекенда | 🔴 $${\color{red}Высокий}$$        |
| [4.1-011](#bug-4.1-011)                    | Введены битые символы в адресе объявления и они системой никак не запрещены, ошибки со стороны бекенда, возможная высокая уязвимость, проходит далеко                                     | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, адрес заполнить битыми символами  <br/>3. Нажать на кнопку "Разместить объявление"                               | Вывод соответствующей ошибки                                               | Несколько ошибок со стороны бекенда                             | 🔴 $${\color{red}Высокий}$$        |
| [4.1-012](#bug-4.1-012)                    | Поле категория выходит за границы видимого экрана                                                                                                                                         | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 300px                                                                                                             | Поле ввода видно полностью                                                 | Часть поля ввода не видно                                       | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-013](#bug-4.1-013)                    | Поле название и подсказка выходят за границы видимого экрана                                                                                                                              | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 300px                                                                                                             | Поле ввода и подсказку видно полностью                                     | Часть поля ввода и подсказки не видно                           | 🟠 $${\color{darkorange}Средний}$$ |
| [4.1-014](#bug-4.1-014)                    | Поле описание и подсказка выходят за границы видимого экрана                                                                                                                              | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 300px                                                                                                             | Поле ввода и подсказку видно полностью                                     | Часть поля ввода и подсказки не видно                           | 🟠 $${\color{darkorange}Средний}$$ |
| [4.1-015](#bug-4.1-015)                    | Поле адрес и подсказка выходят за границы видимого экрана                                                                                                                                 | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 300px                                                                                                             | Поле ввода и подсказку видно полностью                                     | Часть поля ввода и подсказки не видно                           | 🟠 $${\color{darkorange}Средний}$$ |
| [4.1-016](#bug-4.1-016)                    | Введено эмодзи в адресе объявления и они системой никак не запрещены, показывает, что нет проверки адреса на действительность                                                             | 1. Открыть размещение объявления  <br/>2. Заполнить все поля, адрес заполнить эмодзи `😀`  <br/>3. Нажать на кнопку "Разместить объявление"                                    | Вывод соответствующей ошибки                                               | Объявление разместилось                                         | 🔴 $${\color{red}Высокий}$$        |
| [4.1-017](#bug-4.1-017)                    | Кнопка перехода на страницу создания объявления загораживает кнопку создания объявления                                                                                                   | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 300px                                                                                                             | Кнопку создания объявления видно полностью                                 | Другая кнопка загородила необходимую кнопку                     | 🔴 $${\color{red}Высокий}$$        |
| [4.1-018](#bug-4.1-018)                    | При размере экрана меньше 1000px содержимое экрана не помещается и появляется горизонтальный ползунок                                                                                     | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 1000px и меньше                                                                                                   | Все видно, ничто не выходит за пределы экрана                              | Не поместилось содержимое, появился горизонтальный ползунок     | 🟠 $${\color{darkorange}Средний}$$ |
| [4.1-019](#bug-4.1-019)                    | При размере экрана 300px оглавление прижато к левому краю                                                                                                                                 | 1. Открыть размещение объявления  <br/>2. Уменьшить экран до 300px                                                                                                             | Между оглавлением и левым краем есть небольшой отступ                      | Отступ отсутствует                                              | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-020](#bug-4.1-020)                    | Открыть страницу создания объявления в браузере Safari (нет окантовки поля выбора "Категория")                                                                                            | 1. Открыть сайт в браузере Safari  <br/>2. Открыть размещение объявления                                                                                                       | У поля выбора категории есть окантовка                                     | Окантовка отсутствует                                           | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.2: Редактирование объявлений**  | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.2-001](#bug-4.2-001)                    | Не отображается изображение после изменения объявления                                                                                                                                    | 1. Открыть изменение объявления  <br/>2. Изменить/добавить изображение  <br/>3. Нажать на кнопку "Сохранить изменения"                                                         | Товар измелися                                                             | Картинка не отображается после изменения                        | 🟠 $${\color{darkorange}Средний}$$ |
| [4.2-002](#bug-4.2-002)                    | Удаётся изменить объявление с названием длиннее чем 45 символов                                                                                                                           | 1. Открыть изменение объявления  <br/>2. Название сделать длинной больше 45 символов  <br/>3. Нажать на кнопку "Сохранить изменения"                                           | Вывод соответствующей ошибки                                               | Объявление изменилось                                           | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-003](#bug-4.2-003)                    | Введены битые символы в названии объявления и они системой никак не запрещены                                                                                                             | 1. Открыть изменение объявления  <br/>2. Название заполнить битыми символами  <br/>3. Нажать на кнопку "Сохранить изменения"                                                   | Вывод соответствующей ошибки                                               | Объявление изменилось                                           | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-004](#bug-4.2-004)                    | Введены символы в поле цены (изменение html), а должна вывестись ошибка                                                                                                                   | 1. Открыть изменение объявления  <br/>2. Цену заполнить символами, перед этим сменив тип поля на `text`  <br/>3. Нажать на кнопку "Сохранить изменения"                        | Вывод соответствующей ошибки                                               | Объявление изменилось, цена стала равной 0                      | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-005](#bug-4.2-005)                    | Удалось изменить название товара на пустое                                                                                                                                                | 1. Открыть изменение объявления  <br/>2. Название заполнить скриптом `<script>alert("Hello")</script>`  <br/>3. Нажать на кнопку "Сохранить изменения"                         | Изменение объявления, название изменилось на переданное                    | Объявление изменилось, название стало пустым                    | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-006](#bug-4.2-006)                    | Изменено значение value у категории, это вызывает ошибку с бекенда, а не на уровне фронта                                                                                                 | 1. Открыть изменение объявления  <br/>2. Через код страницы поменять значение value и выбрать измененное значение  <br/>3. Нажать на кнопку "Сохранить изменения"              | Вывод соответствующей ошибки                                               | Ошибка пришла с бекенда                                         | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-007](#bug-4.2-007)                    | Удалось изменить описание товара на пустое                                                                                                                                                | 1. Открыть изменение объявления  <br/>2. Описание заполнить скриптом `<script>alert("Hello")</script>`  <br/>3. Нажать на кнопку "Сохранить изменения"                         | Изменение объявления, название изменилось на переданное                    | Объявление изменилось, название стало пустым                    | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-008](#bug-4.2-008)                    | Введены битые символы в описании объявления и они системой никак не запрещены                                                                                                             | 1. Открыть изменение объявления  <br/>2. Описание заполнить битыми символами  <br/>3. Нажать на кнопку "Сохранить изменения"                                                   | Вывод соответствующей ошибки                                               | Объявление изменилось                                           | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-009](#bug-4.2-009)                    | Введены сильно битые символы в описании объявления и они системой никак не запрещены, ошибка со стороны бекенда                                                                           | 1. Открыть изменение объявления  <br/>2. Описание заполнить сильно битыми символами  <br/>3. Нажать на кнопку "Сохранить изменения"                                            | Вывод соответствующей ошибки                                               | Ошибка со стороны бекенда                                       | 🟠 $${\color{darkorange}Средний}$$ |
| [4.2-010](#bug-4.2-010)                    | Прокидываются картинки других типов до бекенда, возможная уязвимость (zip-бомба, Path Traversal (архив с путями вне разрешенной директории), прокидывание скриптов (майнер, червь...) ... | 1. Открыть изменение объявления  <br/>2. Добавить png картинку  <br/>3. Нажать на кнопку "Сохранить изменения"                                                                 | Вывод соответствующей ошибки                                               | Объявление дошло до бекенда                                     | 🔴 $${\color{red}Высокий}$$        |
| [4.2-011](#bug-4.2-011)                    | Введены битые символы в адресе объявления и они системой никак не запрещены, ошибки со стороны бекенда, возможная высокая уязвимость, проходит далеко                                     | 1. Открыть изменение объявления  <br/>2. Адрес заполнить битыми символами  <br/>3. Нажать на кнопку "Сохранить изменения"                                                      | Вывод соответствующей ошибки                                               | Несколько ошибок со стороны бекенда                             | 🔴 $${\color{red}Высокий}$$        |
| [4.2-012](#bug-4.2-012)                    | Поле категория выходит за границы видимого экрана                                                                                                                                         | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 300px                                                                                                              | Поле ввода видно полностью                                                 | Часть поля ввода не видно                                       | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-013](#bug-4.2-013)                    | Поле название и подсказка выходят за границы видимого экрана                                                                                                                              | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 300px                                                                                                              | Поле ввода и подсказку видно полностью                                     | Часть поля ввода и подсказки не видно                           | 🟠 $${\color{darkorange}Средний}$$ |
| [4.2-014](#bug-4.2-014)                    | Поле описание и подсказка выходят за границы видимого экрана                                                                                                                              | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 300px                                                                                                              | Поле ввода и подсказку видно полностью                                     | Часть поля ввода и подсказки не видно                           | 🟠 $${\color{darkorange}Средний}$$ |
| [4.2-015](#bug-4.2-015)                    | Поле адрес и подсказка выходят за границы видимого экрана                                                                                                                                 | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 300px                                                                                                              | Поле ввода и подсказку видно полностью                                     | Часть поля ввода и подсказки не видно                           | 🟠 $${\color{darkorange}Средний}$$ |
| [4.2-016](#bug-4.2-016)                    | Введено эмодзи в адресе объявления и они системой никак не запрещены, показывает, что нет проверки адреса на действительность                                                             | 1. Открыть изменение объявления  <br/>2. Адрес заполнить эмодзи `😀`  <br/>3. Нажать на кнопку "Разместить объявление"                                                         | Вывод соответствующей ошибки                                               | Объявление изменилось                                           | 🔴 $${\color{red}Высокий}$$        |
| [4.2-017](#bug-4.2-017)                    | Кнопка перехода на страницу создания объявления загораживает кнопку изменения объявления                                                                                                  | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 300px                                                                                                              | Кнопку изменения объявления видно полностью                                | Другая кнопка загородила необходимую кнопку                     | 🔴 $${\color{red}Высокий}$$        |
| [4.2-018](#bug-4.2-018)                    | При размере экрана меньше 1000px содержимое экрана не помещается и появляется горизонтальный ползунок                                                                                     | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 1000px и меньше                                                                                                    | Все видно, ничто не выходит за пределы экрана                              | Не поместилось содержимое, появился горизонтальный ползунок     | 🟠 $${\color{darkorange}Средний}$$ |
| [4.2-019](#bug-4.2-019)                    | При размере экрана 300px оглавление прижато к левому краю                                                                                                                                 | 1. Открыть изменение объявления  <br/>2. Уменьшить экран до 300px                                                                                                              | Между оглавлением и левым краем есть небольшой отступ                      | Отступ отсутствует                                              | 🟡 $${\color{gold}Низкий}$$        |
| [4.2-020](#bug-4.2-020)                    | Открыть страницу изменения объявления в браузере Safari (нет окантовки поля выбора "Категория")                                                                                           | 1. Открыть сайт в браузере Safari  <br/>2. Открыть изменение объявления                                                                                                        | У поля выбора категории есть окантовка                                     | Окантовка отсутствует                                           | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.3: Страница своего товара**     | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |    
| [4.3-001](#bug-4.3-001)                    | Поломалась верстка описание объявления при уменьшении количества пикселей                                                                                                                 | Уменьшить экран до 300px                                                                                                                                                       | Между оглавлением и левым краем есть небольшой отступ                      | Поломалась верстка                                              | 🟡 $${\color{gold}Низкий}$$        |
| [4.3-002](#bug-4.3-002)                    | Поломалась верстка оплаты при уменьшении количества пикселей                                                                                                                              | Уменьшить экран до 300px                                                                                                                                                       | Блок покупки продвижения полностью помещается на экране                    | Поломалась верстка                                              | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.4: Поиск**                      | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.4-001](#bug-4.4-001)                    | Поломалась верстка при возврате к предыдущему запросу                                                                                                                                     | 1. Ввести запрос `Настольная игр` <br/>2. Нажать на кнопку поиска <br/>3. Ввести запрос `Настольная игра` <br/>4. Нажать на кнопку поиска <br/>5. Нажать на кнопку вернуться   | Видно предыдущий запрос                                                    | Поломалась верстка                                              | 🟠 $${\color{darkorange}Средний}$$ |
| [4.4-002](#bug-4.4-002)                    | Нет подсказки что в поиск надо что-то ввести перед тем как искать                                                                                                                         | 1. Ввести запрос - пустая строка <br/>2. Нажать на кнопку поиска                                                                                                               | Появляется подсказка, что ничего не введено                                | Подсказка не вывелась                                           | 🟡 $${\color{gold}Низкий}$$        |
| [4.4-003](#bug-4.4-003)                    | Нет подсказки что нет того что ищем, непонятно оно ещё подгружает или подгружать нечего                                                                                                   | 1. Ввести запрос `что-то непонятное` <br/>2. Нажать на кнопку поиска                                                                                                           | Появляется подсказка, что нет того, что ищем                               | Подсказка не вывелась                                           | 🟡 $${\color{gold}Низкий}$$        |
| [4.4-004](#bug-4.4-004)                    | Благодаря zalgo получилось нагрузить размер передаваемого на бекенд запроса (превысить допустимый размер)                                                                                 | 1. Ввести запрос `Настольная игра` битыми символами (zalgo) <br/>2. Нажать на кнопку поиска                                                                                    | Появляется подсказка, что нельзя использовать такие символы                | Подсказка не вывелась, запрос ушел на бекенд                    | 🟠 $${\color{darkorange}Средний}$$ |
| [4.4-005](#bug-4.4-005)                    | Благодаря большому количеству символов удалось нагрузить размер передаваемого на бекенд запроса (превысить допустимый размер), нет ограничения на максимальное количество символов        | 1. Ввести запрос очень большой длинны <br/>2. Нажать на кнопку поиска                                                                                                          | Появляется подсказка, что нельзя использовать такой длинный запрос         | Подсказка не вывелась, запрос ушел на бекенд                    | 🟠 $${\color{darkorange}Средний}$$ |
| [4.1-006](#bug-4.4-006)                    | При уменьшении экрана визуально кнопка пропала, но навестись можно                                                                                                                        | 1. Уменьшить экран до 1200px                                                                                                                                                   | Кнопка с иконкой поиска либо словом "Поиск", либо отсутствием кнопки вовсе | Кнопка есть, пустая                                             | 🟡 $${\color{gold}Низкий}$$        |
| [4.1-007](#bug-4.4-007)                    | При уменьшении экрана визуал не совпадает с тем, что в браузере Google Chrome (FireFox)                                                                                                   | 1. Уменьшить экран                                                                                                                                                             | Совпадает с визуалом в Google Chrome                                       | Не совпало                                                      | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.5: Оформление заказа**          | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.5-001](#bug-4.5-001)                    | Изменено значение value у вида доставки, это вызывает ошибку с бекенда, а не на уровне фронта                                                                                             | 1. Открыть оформление заказа </br> 2. Через код страницы поменять значение value и выбрать измененное значение </br> 3. Нажать на кнопку "Оформить заказ"                      | Вывод соответствующей ошибки                                               | Ошибка пришла с бекенда                                         | 🟡 $${\color{gold}Низкий}$$        |
| [4.5-002](#bug-4.5-002)                    | Введена длинная строка в поле "ФИО получателя", длина ввода никак не ограничена                                                                                                           | 1. Открыть оформление заказа </br> 2. Ввести 250 символов в поле "ФИО получателя" </br> 3. Нажать на кнопку "Оформить заказ"                                                   | Ошибка "Длина ФИО не должна превышать N символов"                          | Вернулась ошибка с бэкенда                                      | 🟡 $${\color{gold}Низкий}$$        |
| [4.5-003](#bug-4.5-003)                    | Введены битые символы, которые не запрещаются системой                                                                                                                                    | 1. Открыть оформление заказа </br> 2. Ввести битые символы в поле "ФИО получателя" </br> 3. Нажать на кнопку "Оформить заказ"                                                  | Вывод соответствующей ошибки                                               | Заказ создался                                                  | 🟡 $${\color{gold}Низкий}$$        |
| [4.5-004](#bug-4.5-004)                    | Введена длинная строка в поле "Адрес", длина ввода никак не ограничена                                                                                                                    | 1. Открыть оформление заказа </br> 2. Ввести 250 символов в поле "Адрес" </br> 3. Нажать на кнопку "Оформить заказ"                                                            | Ошибка "Длина адреса не должна превышать N символов"                       | Вернулась ошибка с бэкенда                                      | 🟡 $${\color{gold}Низкий}$$        |
| [4.5-005](#bug-4.5-005)                    | Введены битые символы, которые не запрещаются системой, ошибки со стороны бекенда, возможная высокая уязвимость, проходит далеко                                                          | 1. Открыть оформление заказа </br> 2. Ввести битые символы в поле "Адрес" </br> 3. Нажать на кнопку "Оформить заказ"                                                           | Вывод соответствующей ошибки                                               | Вернулась ошибка с бэкенда                                      | 🔴 $${\color{red}Высокий}$$        |
| [4.5-006](#bug-4.5-006)                    | Введено эмодзи в адресе доставки и они системой никак не запрещены, показывает, что нет проверки адреса на действительность                                                               | 1. Открыть оформление заказа </br> 2. Ввести `😀` в поле "Адрес" </br> 3. Нажать на кнопку "Оформить заказ"                                                                    | Вывод соответствующей ошибки                                               | Заказ создался                                                  | 🔴 $${\color{red}Высокий}$$        |
| [4.5-007](#bug-4.5-007)                    | Выход кнопки за границы блока при ширине экрана, меньшей 380px                                                                                                                            | 1. Открыть оформление заказа </br> 2. Уменьшить широту экрана до 380px                                                                                                         | Кнопка не выходит за границы блока                                         | Кнопка выходит за границы блока                                 | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.6: Заказы**                     | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.6-001](#bug-4.6-001)                    | Выход номера телефона за границы блока при ширине экрана, меньшей 280px                                                                                                                   | 1. Открыть страницу заказов </br> 2. Уменьшить широту экрана до 280px                                                                                                          | Номер телефона не выходит за границы блока                                 | Номер телефона выходит за границы блока                         | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.7: Каталог и главная страница** | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| **Раздел 4.8: Страница товара (чужая)**    | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.8-001](#bug-4.8-001)                    | Поломалась верстка при уменьшении количества пикселей                                                                                                                                     | Уменьшить экран до 300px                                                                                                                                                       | Между оглавлением и левым краем есть небольшой отступ                      | Поломалась верстка                                              | 🟡 $${\color{gold}Низкий}$$        |
| **Раздел 4.9: Корзина**                    | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.9-001](#bug-4.9-001)                    | Пропала кнопка "корзина" при уменьшении экрана до 1000 px                                                                                                                                 | 1. Уменьшить экран                                                                                                                                                             | Кнопка корзина не пропала                                                  | Кнопка корзина пропала                                          | 🟠 $${\color{darkorange}Средний}$$ |
| **Раздел 4.10: Избранное**                 | **—**                                                                                                                                                                                     | **—**                                                                                                                                                                          | **—**                                                                      | **—**                                                           | **—**                              |
| [4.10-001](#bug-4.10-001)                  | Поломалась верстка при уменьшении экрана до 300px                                                                                                                                         | 1. Уменьшить экран                                                                                                                                                             | Кнопки лайка и цена на одном уровне                                        | Кнопка лайка и цена на разных уровнях                           | 🟡 $${\color{gold}Низкий}$$        |


> ***Комментарий:***  
> Шаблон -  
> | 001 | Ошибка при добавлении товара в корзину | 1. Открыть каталог  <br/>2. Нажать «Добавить в корзину» | Товар добавляется   | Ошибка 500            | Высокий   |

---

## 6. Выводы <a name="выводы"></a>
- Основные функциональности протестированы
- Обнаружены 60 багов, которые необходимо исправить

**Дата составления отчета:** 12.03.2025
