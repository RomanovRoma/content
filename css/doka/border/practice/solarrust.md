---
tags:
  - practice
permalink: false
---

🛠 При помощи `border` можно рисовать различные геометрические фигуры. Например, треугольник. Для этого потребуется задать прозрачную рамку с двух сторон и непрозрачную рамку с третьей стороны.

```html
<div class="top"></div>
```

```css
.top {
  width: 0;
  height: 0;
  border-left: 50px solid transparent; /* прозрачная рамка слева, ширина х */
  border-right: 50px solid transparent; /* прозрачная рамка справа, ширина х */
  border-bottom: 100px solid red; /* цветная рамка снизу, ширина х * 2 */
}
```

Такое поведение достигается из-за того, что прозрачные рамки перекрывают часть цветной рамки.

Наглядно видно наложение рамок на следующей картинке:

![Внешний вид наложения рамок](../images/1.png)

В итоге можно создать треугольники, смотрящие в любую сторону. Этот приём можно использовать чтобы не тянуть в проект мелкие иконки треугольников или стрелок.

<iframe title="Треугольники" src="../demos/triangles.html"></iframe>

🛠 Ещё немного про треугольники. А точнее стрелки. Их тоже можно создать при помощи `border`, но тут понадобиться подключить свойство `transform` ([transform](/css/doka/transform/)), чтобы повернуть элемент с рамками на 45 градусов в нужную сторону:

```html
<div class="arrows">
  <div class="arrow _prev"></div>
  <div class="arrow _next"></div>
</div>
```

```css
.arrows {
  max-width: 1200px;
  height: 250px;
  margin: 0 auto;
  background-color: #f1f1f1;
}

.arrow {
  /* Рисуем квадрат */
  width: 50px;
  height: 50px;

  border-left: 5px solid #ff0001; /* Задаём левую рамку */
  border-bottom: 5px solid #ff0001; /* Задаём нижнюю рамку */
}

.arrow._prev {
  transform: rotate(45deg); /* Поворачиваем квадрат нижним левым углом влево */
}

.arrow._next {
  transform: rotate(
    -135deg
  ); /* Поворачиваем квадрат нижним левым углом вправо */
}
```

<iframe title="Стрелки для слайдера" src="../demos/arrows.html"></iframe>

Чем не стрелки для слайдера? 🤗

🛠 Часто встречающийся дизайнерский приём — появление рамки вокруг элемента при наведении на него курсора мыши.

Если просто добавлять рамку для селектора `:hover`, то элемент будет дёргаться. Причина в том, что размер элемента увеличивается на ширину рамки. Чтобы подобных подёргиваний не происходило, изначально задай рамку нужной толщины, но задай для неё прозрачный цвет (`transparent`). А по наведению курсора просто меняй цвет на нужны. Profit! Вы прекрасны 😄