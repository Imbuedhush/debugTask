# Задание 1 — найди ошибки

Самым сложным было перестать искать ошибки там где их нет.
Постепенно, по нарастающей...

1. Замена импорта в файле index.js, без него просто ничего не запускалось. В похожем стиле -> import { initMap } from "./map";
2. Карта на всю страницу: открытие дебаггера в браузере ->  height: 0 
    Нужно добавить стиль 'height: 100%;' для #map
3. После проблемы с пустой белой страницей(2), появилась проблема пустой карты, даже тестовые обьекты не рисовались, согласно офф. API нужно добавить 'myMap.geoObjects.add(objectManager);'
4. Все точки улетели куда то в Иран. После некоторой игры с коэффициентами(ничего не изменилось на мой взгляд, похоже просто страница не перезагружалась), было принято решение поменять местами долготу и широту.
5. В api.js функция loadDetails стала более похожего стиля
6. Кастомый Layout для Ballon. Не сразу было понятно в чем проблема, но то, что есть проблема именно в этом файле было выяснено просто после 'выключения' его в ObjectManager. Может быть, можно было догадаться по ошибке с 'null' в консоли браузера. Использование стрелочных функций которые теряют контекст. Замена на анонимные function.
7. Графики Chart.js не работали как надо, линий не рисовалось, либо рисовались не полностью и только у дефектных, отрицательные значения. Оно и понятно ведь у оси 'y' было максимальное значение 0, когда оно должно быть минимальным.(Да и кол-во соединений ведь не может в минус уйти);
8. Отображение того, что в кластере есть дефектная станиция. Сперва, хотелось добавить {preset:'islands#orangeClusterIcons'} для таких кластеров, но в глаза бросился pieChart у ObjectManager.