# HOMEWORK-SOLUTIONS-5-

Класс Image 
Этот интерфейс определяет контракт для работы с изображениями. В нём объявлены два метода:
displayThumbnail() — отображает миниатюру изображения.
displayFullImage() — загружает и отображает полное изображение.

Класс HighResolutionImage 
Этот класс представляет собой высококачественное изображение, которое загружается с диска при создании объекта.
В конструкторе происходит эмуляция загрузки изображения (loadImage()).
Метод displayThumbnail() имитирует отображение миниатюры.
Метод displayFullImage() отображает полное изображение.

Класс ImageProxy 
Этот класс реализует шаблон Proxy, позволяя загружать изображение только при необходимости.
В конструкторе сохраняется имя файла без загрузки изображения.
displayThumbnail() сразу отображает заглушку (миниатюру).
displayFullImage() при первом вызове создаёт объект HighResolutionImage и загружает изображение.

Класс MarkerStyle 
Этот класс представляет собой "легковесный" объект, содержащий стили для маркеров.
Содержит иконку (icon), цвет (color) и стиль текста (labelStyle).
Метод display(int x, int y) отображает маркер на заданных координатах.

Класс MarkerFactory 
Этот класс управляет кэшированием объектов MarkerStyle.
Метод getStyle(icon, color, labelStyle) проверяет, существует ли уже такой стиль.
Если стиль есть, он возвращает его; если нет — создаёт новый и сохраняет.

Класс MapMarker
Этот класс представляет собой маркер, который хранит координаты и использует MarkerStyle.
В конструкторе указываются координаты x, y и стиль маркера.
Метод display() выводит информацию о маркере.

Класс Main (главный метод в тестирование паттернов)
Этот класс объединяет тестирование Proxy и Flyweight.
Сначала проверяется работа Proxy на изображениях.
Затем создаются маркеры и стили для Flyweight.

При запуске кода в классе Main программа выведет следующее:
Testing Proxy Pattern:
Displaying cached thumbnail for: house1.jpg
Displaying cached thumbnail for: house2.jpg
Loading high-resolution image: house1.jpg
Displaying full image: house1.jpg
Displaying full image: house1.jpg

Testing Flyweight Pattern:
Marker at (10, 20) with icon: H, color: Red, label: Bold
Marker at (15, 25) with icon: H, color: Red, label: Bold
Marker at (30, 40) with icon: R, color: Blue, label: Italic

Этот пример показывает что в Proxy Pattern начала выводятся две строки с миниатюрами изображений для файлов house1.jpg и house2.jpg.
При вызове displayFullImage() для первого изображения происходит создание объекта HighResolutionImage, что приводит к выводу строки о загрузке изображения. После 
этого вызывается метод, который выводит строку об отображении полного изображения. При повторном вызове полного отображения для того же объекта изображение не 
перезагружается, а выводится снова сообщение об отображении полного изображения.
А в Flyweight Pattern Создаются два объекта стиля (hospital и restaurant). Далее создаются маркеры с координатами, и метод display() каждого маркера выводит 
информацию о маркере с использованием общего стиля.
Таким образом, весь вывод демонстрирует работу обоих паттернов в едином тестовом классе.
