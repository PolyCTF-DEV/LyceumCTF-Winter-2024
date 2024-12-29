# Noxor

## Задание
Отправили мне зашифрованное сообщение, но кажется они напутали шифр

## Описание
Дана зашифрованная строка. Она зашифрована также как сделали бы это с помощью XOR для 7-битного текста, но использовали функцию NOT(XOR). Соответственно надо просто применить её ещё раз.

## Решение
Для простоты решения напишем функцию not(xor) на языке python и прочитав бинарно файл переведём сообщение:

```python
def noxor(a: int, b: int) -> int:
    a_b = bin(a).split('b')[-1]
    b_b = bin(b).split('b')[-1]
    a_b = a_b.zfill(7) # Чтобы использовать 7-битный алфавит
    b_b = b_b.zfill(7)
    c_b = [0] * 7
    for k in range(7):
        c_b[k] = int(not(int(a_b[k])^int(b_b[k])))
    return int(''.join(map(str, c_b)), 2)


def coder(s: bytes) -> bytes:
    output = b''
    for k, i in enumerate(s):
        c = chr(noxor(k, i)).encode()
        output += c
    return output

print(coder(open("flag.bin", "rb").read()))
```
