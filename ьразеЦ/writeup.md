<h1>ьразеЦ</h1>

<h2>Задание</h2>
<p>)еонреван( йынжолс ончотатсод сревер тотЭ</p>

<h2>Описание:</h2>
<p>Данное задание представляет собой исходный код и результат работы кода с флагом. Необходимо обратно декодировать сообщение</p>

<h2>Решение</h2>
<pre lang="python">
<code>
with open("output.txt", "r") as f:
    s = f.read()
    step1 = ''.join(c.lower() if c.isupper() else c.upper() for c in s)
    step1 = step1[::-1]
    flag = ""
    for i in step1:
        if i.isalpha():
            base = ord('A') if i.isupper() else ord('a')
            flag += chr((ord(i) - base - 6) % 26 + base)
        else:
            flag += i
print(flag)
</code>
</pre>
