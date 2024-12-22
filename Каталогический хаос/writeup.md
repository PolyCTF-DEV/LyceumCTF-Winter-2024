<h1>Каталогический хаос</h1>

<h2>Задание</h2>
<p>Как можно работать в этом хаосе?!?!?!?!?</p>

<h2>Описание:</h2>
<p>Данное задание представляет собой набор каталогов, каждый из которых отвечает за определенную букву, индексы буквы находятся в текстовом файле внутри каталога.</p>

<h2>Решение</h2>
<span>Достаточно вручную обойти все каталоги и собрать по индексам флаг, чтобы ускорить процесс, можно написать простой алгоритм:</span><br><br>

<pre lang="python">
<code>
flag = [''] * 100
alphabet = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789{}_"
for i in alphabet:
    with open(f"task/{i}/{i}.txt", "r") as f:
        while True:
            line = f.readline()
            if not line:
                break
            flag[int(line)] = i
print(''.join(flag))
</code>
</pre>
