# Написание свёрточной нейронной сети для распознавания дорожных знаков, аугментация данных, обучение сети / Convolutional neural network creation for traffic sign recognition, data augmentation, neural network training

*Разработчик/Developer*

1. [Андрей Недов](https://github.com/Andrey-Nedov-is-a-human)

## Задача

*Разработать алгоритм классификации стандартизованных изображений с помощью свёрточной нейронной сети.*

- Подготовить приложение для генерации обучающей выборки из исходного набора изображений;
- Разработать функцию расчета свёрточной карты для выбранного ядра;
- Разработать класс, реализующий функциональность свёрточной сети для
- классификации изображений;
- Разработать функцию обучения с учителем для нейтронной сети по подготовленной ранее обучающей выборке.

__Задание выполняетя на языке С# с использованием только стандартных библиотек.__

_Изображения для распознавания:_

<img src="imgs/img1.png" width="400"/>

[Полный текст задания/Full issue text](https://github.com/Andrey-Nedov-is-a-human/Convolutional-Neural-Network-Hand-Made/tree/main/materials/Task_NN_2019_L3_CNN.pdf)

## Данные

Датасет был получен из исходных шаблонов путём аугментации данных с добавления шума, сдвигов, изменения яркости и угла поворота изображения.

<p>
<img src="/imgs/d1.png" width="400"/>
<img src="/imgs/d2.png" width="400"/>
<img src="/imgs/d3.png" width="400"/>
<img src="/imgs/d4.png" width="400"/>
</p>

В качестве свёрточных ядер опытным путём были подобраны следующие четрые ядра с разрешением 5x5 пикселей:

<img src="/imgs/kernel.png" width="400"/>

## Архитектура сети

<img src="imgs/nn.png" width="800"/>

Сеть получает на вход биноризованное по цвету изображение размером 64х64 пикселя, и сжимае его до 20х20. Далее следует операция свёртки. Дополнительная граница изображению не дорисовывается, поэтому после свёртки результатом является двумерный вектор размером 16x16. Далее вектор подаётся на сенсорный слой нейронной сети, откуда, проходя через скрытый слой, попадает на четыре результирующие нейрона, по одному на каждый шаблон.

## Обучение сети

### Алгоритм обучения сети:
100 раз:
  берём по небольшому набору (например 20) изображений каждого знака из соответствующей директории (по разу из каждой директории получается 4 набора) когда изображения в директории заканчиваются алгоритм обнуляет счётчик изображений для каждой директории и берёт изображения с первого.

### Время обучения
Примерно 3 минуты
