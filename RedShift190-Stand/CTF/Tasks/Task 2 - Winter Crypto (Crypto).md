***Описание***: ﻿Вам предоставлено зашифрованное сообщение, а также код, с помощью которого было выполнено шифрование. Попробуйте понять работу кода и расшифровать сообщение. Формат флага: Shift{decrypt_text}

---

***Решение***:

Шифротекст: 

```sh
# code_text.txt

ФйкзхьШкпхжуакфадрокпию
```

Код, которым зашифровано исходное сообщение:

```python
# py.py

from struct import *

FILEIN = 'text.txt'
FILEOUT = 'code_text.txt'
KEY = 113

f1 = open(FILEIN, 'rb')
f2 = open(FILEOUT, 'wb')

b_st = f1.read()

for x in b_st:
    x = int(x)
    y = (x + KEY) % 255
    b_y = pack('B', y)
    f2.write(b_y)

f1.close()
f2.close()
```

У нас есть файл code_text.txt с закодированным текстом и файл py.py с кодом, с помощью которого зашифрован текст. Код нужно немного изменить. 

```python
# solve.py

from struct import *

FILEIN = 'text.txt'
FILEOUT = 'code_text.txt'
KEY = 113

f1 = open(FILEIN, 'wb')
f2 = open(FILEOUT, 'rb')

b_st = f2.read()

for x in b_st:
    x = int(x)
    y = (x - KEY) % 255
    b_y = pack('B', y)
    f1.write(b_y)

f1.close()
f2.close()
```

И расшифрованный текст будет сохранен в файл text.txt

---

***Флаг***: Shift{Winter_is_coming}