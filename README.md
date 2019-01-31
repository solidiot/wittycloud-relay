# SolidioT wittycloud-relay

1. [Монтаж  модуля реле в к соединительную коробку RJ11](#chapter-0)
2. [Подключение модуля реле к разъему RJ11](#chapter-1)
3. [Проблема с управлением реле от 3.3В и возможное решение](#chapter-2):
   + 3.1 [Недостаток альтернативы](#chapter-3)
   + 3.2 [Недостаток альтернативы ](#chapter-4)
4. [Схема подключения модуля реле к ESP8266](#chapter-5)
5. [Подключение модуля реле к вилке с розеткой](#chapter-6)
6. [Проверка модуля реле на точность срабатывания](#chapter-7)

<a id="chapter-0"></a>
## 1. Монтаж модуля
Без «хирургического вмешательства» обычное реле от Arduino из Китая (Arduino Relay Shield 5V 10A, если будете искать) не поместится в RJ11 коробочку. Как видно на фото, часть платы с иероглифами не позволяет закрыться коробочке.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay1.png)
Лично я лишнюю часть модуля реле стер о вращающийся диск угловой шлифмашинки («болгарка» в народе). Может у кого-то Dremel дома имеется, может другой инструмент. Я думаю, можно даже ножницами по металлу откусить лишнюю часть.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay2.png)
Теперь коробочка закрывается!

![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay3.png)

<a id="chapter-1"></a>
## 2. Подключение модуля реле к разъему RJ11
Займемся подключением модуля к разъему RJ11
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay4.png)
Нам нужно 3 провода: красный для +5V, черный для GND, и один провод для управляющего сигнала, предлагаю использовать зеленый провод. Откусываем лишний желтый провод.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay5.png)
У оставшихся 3-х проводов откусываем лишнюю часть наконечника.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay6.png)
С помощью паяльника, канифоли и припоя, готовим проводки к соединению с модулем.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay7.png)

<a id="chapter-2"></a>
## 3. Проблема с управлением реле от 3.3В и возможное решение
Но, к сожалению, если просто припаять 3 проводка, как на этом фото, реле корректно работать не будет. По питанию все верно получается, но по управляющему сигналу – не верно. Данное реле управляется GND сигналом, а Witty Cloud дает +3,3В. 
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay8.png)

<a id="chapter-3"></a>
### 3.1 Недостаток альтернативы
Вот такое реле сразу заработает от 3,3В. Для подключения даже не требуется пайки! Но есть два недостатка: 1. Такое реле рассчитано всего лишь на 2А силу тока. P = 2Ампер * 220Вольт = 440Вт. С такой мощностью сильно не разгуляешься.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay9.png)

<a id="chapter-4"></a>
### 3.2 Недостаток альтернативы
Такое реле не помещается в коробочку от RJ11! Я варварски выгрыз кусачками окошко для выпирающей части модуля реле. Эта сторона будет обращена к стене и приклеена к ней же двухсторонним скотчем, выглядеть все будет аккуратно. Так что решать Вам, какое реле использовать.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay10.png)

<a id="chapter-5"></a>
## 4 Схема подключения модуля реле к ESP8266
Вернемся к нашему 5-ти вольтовом модулю реле. Я радостно поспешил все заклеить с помощью клеевого пистолета, придется место пайки очищать от клея.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay11.png)

В интернете есть такая схема подключения похожего реле. Обратите внимание, что у модуля реле на схеме контакты +5V и GND расположены не так, как на нашем.

![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay12.png)

Вот так получилось реализовать эту схему навесным монтажом. На этот раз я не спешу заклеивать все клеем ☺

![](<https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay13.png>)

<a id="chapter-6"></a>
## 5 Подключение модуля реле к вилке с розеткой
Теперь можно подключить реле к 220В с помощью вилки и сделать розетку, управляемую реле. Фазу берем из вилки и подключаем к средней клемме. Клеммы слева и справа от средней «открываются» и «закрываются» в зависимости от состояния реле. Выбирайте левую или правую клемму по своим нуждам.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay14.png)
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay15.png)
Фазу я нашел в своей сети с помощью дешевого тестера-отвертки. Куда я подключил красный провод на вилке я пометил тонкой полоской красной изоляции. Если вы перепутаете фазу и ноль при подключении вилки к розетке 220В, ничего страшного не произойдет, все будет работать. Но желательно управлять фазой, а не нулем.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay16.png)
Ноль просто напрямую идет от вилки к розетке. Можно сделать подключение во внешней изоляции проводов, я же снял эту изоляцию для наглядности. Использован медный многожильный провод сечением 2,5мм, длинна провода 1,5м. 
220В – это уже не шутки! Будьте осторожны и проверьте соединения во избежание короткого замыкания!
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay17.png)

<a id="chapter-7"></a>
## 6 Проверка модуля реле на точность срабатывания
Для проверки работы реле я использовал вот такую лампу с вилкой на конце.
![](https://github.com/DmitriyPro/wittycloud-relay/blob/master/solidiot%20wittycloud-relay%D0%B5%20photo/solidiot%20wittycloud-relay18.png)
Я подключил лампу в управляемую розетку и долго-долго включал/выключал реле. Поставил на всю ночь на следующий цикл:
включить лампу → подождать 0.5 секунды → посмотреть встроенным сенсором освещенности, включилась ли лампа на самом деле → подождать 0.5 секунды →выключить лампу → подождать 1 секунду и повторить. 
Утром программа показала, что реле включилось более 6600 раз, все эти 6600 раз успешно. 
100% точность срабатывания!
Считаю тест на точность срабатывания пройденным успешно.
