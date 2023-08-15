# Zorra phone SDK

![zorra telecom](./image.png)

## Quick Start

При подключении скрипта создаётся глобальная переменная zorra

### self-host

```html
<script src="build/index.js"></script>
...
zorra.connect(sipLogin, sipPassword, sipHost);
```

### es-6 module

```js
import Dialer from "build";

const zorra = new Dialer()
zorra.connect(sipLogin, sipPassword, sipHost);
```

 **Убедитесь, что включены настройки WebRTC в браузере.** 

#### Предиктив

Укажите вариант использования SDK Предиктив
```
zorra.predictive = true;
```

Подключение (выход оператора на линию)
```js
zorra.online(sipLogin, sipPassword, sipHost);
```

Отключение (уход с линии)
```js
zorra.offline();
```
Подпись на события подключения и отключения:
```js
zorra.on("connection", (event) => {
    // your code
});
```


Подпись на события статуса звонка:
```js
zorra.on("call", (event) => {
    // your code
});
```

Пример использования
```js
zorra.on("connection", (event) => {
    if(result.message === "registered") {
        toggleStatusColor()
    }
});
```

| статусы подключения|
|--------------------|
| connected       |
| disconnected       |
| registered         |
| unregistered       |
| registrationFailed |

```js
zorra.on("call", (result) => {
    ...
    p.innerHTML = `
    Статус звонка: ${result.status} <br>
        ${
          result.cause
            ? `Причина ошибки/отмены звонка: ${result.cause}  <br>`
            : ""
        }
        ${result.direction ? `Направление: ${result.direction}  <br>` : ""}
        taskId: ${result.from?.taskId}`;
});
```
