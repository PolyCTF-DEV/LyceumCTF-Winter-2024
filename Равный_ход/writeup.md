<h1>Равный ход</h1>

<h2>Задание</h2>
<p>Зачем здесь так много знаков равно?</p>

<h2>Описание:</h2>
<p>Данное задание представляет собой исходный код и результат работы кода с флагом. Необходимо обратно декодировать сообщение</p>

<h2>Решение</h2>
<pre lang="python">
<code>
import base64
with open("output.txt", "r") as f:
    s = f.read()
    sp = []
    for i in range(0, len(s), 4):
        sp.append(s[i:i+4])
    flag = []
    for i in sp:
        flag.append(chr(ord(base64.b64decode(i).decode()) ^ 52))
print(''.join(flag))
</code>
</pre>
