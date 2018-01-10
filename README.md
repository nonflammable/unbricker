# unbricker
Universal Atmel Unbricker 

Inspiracja:<br>
Zdarza się, że podczas zabawy Arduino (i nie tylko) uszkodzeniu ulega bootloader. Pierwotnym przypadkiem który natchnął mnie do budowy urządzenia to dość często spotykany problem przy wgrywaniu oprogramowania do drukarki Anet A6/A8. Większość użytkowników nie ma pod ręką programatora typu USBasp, a samo wgranie bootloadera to dla nich czarna magia. Myślę, że urządzenie sprawdzi się również u tych bardziej doświadczonych poprzez przyspieszenie i uproszczenie samego procesu odceglania lub (masowego?) programowania nowych układów.

Koncepcja:<br>
Przygotowanie uniwersalnego "unbrickera" w formie wtyczki która po podłączeniu automatycznie wgra bootloader. Ponieważ bootloadery dla mikrokontrolerów różnią się między sobą, trzeba wykryć typ układu lub rozważyć dołożenie zworek / DIP switcha umożliwiającego wybór "ratowanego" układu (szykowanie urządzenia dla jednego typu to marnotrawienie możliwości). Dodanie paru LED sygnalizujących przebieg operacji wydaje się potrzebne, a w przyszłości można pokusić się o przygotowanie wersji z małym wyświetlaczem OLED i joystickiem.

Budowa:<br>
Arduino Nano (lub klon) ... a może coś prostszego (attiny?) + SPI Flash (jeżeli wymagane bootloadery nie zmieszczą się w pamięci mikrokontrolera) + DIP Switch + 6-cio pinowe gniazdo IDC + kilka LED.

Oprogramowanie:<br>
Skecz który przy starcie sprawdza typ wybranego układu na podstawie DIP Switcha lub sam odczytuje go z "ofiary". Następnie wybiera i "wypluwa" bootloader przez piny D11/D12/D13 (MISO/MOSI/SCK) + reset 5V GND  na 6-cio pinowe złącze spotykane na większości płytek typu Arduino (sygnalizacja przebiegu - LED), odczytanie poprawności zaprogramowania (kolejny LED) ... (operacja nieudana = jeszcze jeden LED).

Licencje: open source, open hardware, etc.<br>
Do zrobienia: Przedyskutowanie i zdecydowanie o ostatecznym kształcie urządzenia (mikroprocesor, ilość ledów, SPI Flash itd.), Schemat + PCB, napisanie kodu, zebranie bootloaderów w jedno miejsce, przygotowanie wersji angielskiej tego wpisu i zaproszenie świata do współpracy.
