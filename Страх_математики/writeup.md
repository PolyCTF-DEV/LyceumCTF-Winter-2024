<h1>Страх математики</h1>

<h2>Задание</h2>
<p> Цифры... Цифры ударили в голову... Я уже не могу все это считать...</p>

<h2>Описание:</h2>
<p>Данное задание представляет собой сайт, на котором необходимо решить 500 математических выражений.</p>

<h2>Решение</h2>
<span>Чисто теоретически можно решить все выражения вручную, но это крайне не эффективно. Проще сделать алгоритм, который будет автоматически решать все выражения</span><br><br>

<pre lang="python">
<code>
import requests

# URL вашего сайта
BASE_URL = "http://qookie.tech:30058/"

# Создаём сессию для сохранения cookie
session = requests.Session()

def solve_problem(problem):
    try:
        # Вычисление результата
        return eval(problem)
    except Exception as e:
        print(f"Ошибка вычисления: {e}")
        return None

def main():
    count = 0
    while count < 500:
        # Шаг 1: Получаем текущую задачу
        response = session.get(BASE_URL)
        if response.status_code != 200:
            print("Ошибка при получении страницы!")
            break

        s = response.text
        a = s.find("<p>")
        b = s.find("</p>")
        s = s[a + 18:b]
        print(s)
        print(f"Задача: {s}")

        # Шаг 2: Решаем задачу
        answer = solve_problem(s)
        if answer is None:
            print("Не удалось вычислить задачу. Пропускаем...")
            continue

        # Шаг 3: Отправляем результат
        response = session.post(BASE_URL, data={"answer": answer})
        if response.status_code != 200:
            print("Ошибка при отправке ответа!")
            break

        # Проверяем, достигли ли мы 500 задач
        if "PolyCTF" in response.text:
            print("Задачи завершены! Флаг найден:")
            print(response.text)
            break

        count += 1

if __name__ == "__main__":
    main()
</code>
</pre>

