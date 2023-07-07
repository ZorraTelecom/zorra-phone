# Zorra phone SDK

![zorra telecom](./image.png)

## Quick Start

При подключении скрипта создаётся глобальная переменная zorra

### self-host

```
<script src="build/index.js"></script>
...
zorra.connect(sipLogin, sipPassword, sipHost);
```

### es-6 module

```
import Dialer from "build";

const zorra = new Dialer()
zorra.connect(sipLogin, sipPassword, sipHost);
```
