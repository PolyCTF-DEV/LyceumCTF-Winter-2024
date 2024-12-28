
<h1>Многогранная личность</h1>

<h2>Задание</h2>
<p>Я прошел тест на определение личности а он выдал это изображение. Что мне с ним делать? </p>

<h2>Описание:</h2>
<p>Данное задание представляет собой изображение, на котором изображен штрих-код, сжатый по высоте до 1 пикселя</p>


<h2>Решение</h2>
<b>Шаг 1:</b> <span>На изображении находиться набор черных пикселей в линию, сначала можно подумать, что это фраза в бинарном виде, но теория опровергается, так как есть 1 и 2 подряд идущих пикселя, но еще и 3.</span><br><br>
<b>Шаг 2:</b> <span>Создаеем код, который растягивает пиксели по высоте.</span><br><br>

<pre lang="python">
<code>
from PIL import Image

source_image = Image.open("task.png")
width, height = source_image.size
copied_image = Image.new("RGB", (width, height))

for x in range(width):
    for y in range(height):
        pixel_color = source_image.getpixel((x, y))
        copied_image.putpixel((x, y), pixel_color)
source_image1 = Image.open("task.png")
for x in range(width):
    pixel_color = source_image1.getpixel((x, 300))
    if pixel_color[0] == 0:
        for i in range(100, 500):
            copied_image.putpixel((x, i), pixel_color)

copied_image.save("output.png")
</code>
</pre>
<b>Шаг 3:</b> <span>Из полученного изображения мы получаем штрих-код, который сканируем через онлайн сервисы, по итогу которых получаем флаг.</span>

