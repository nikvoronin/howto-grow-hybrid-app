# Выращиваем гибрид

Нет, это не про монолит и микросервисы.

Мы взяли веб-приложение и сделали из него десктоп. Затем построили свой терминал и продаем клиентам. Все это меньше, чем за год. Не напрягаясь и не подключая сотни людей.

![Title Slide](slides/00.png)

__Место проведения:__ Vladimir Tech Talks #19, г. Владимир, ул. Гагарина 5, этаж 4, [конф. зал Альтенара](https://yandex.ru/maps/-/CDQlNY~U).

8 Сентября 2023 года. ▶ [Видео `VK`](https://vk.com/video-178974757_456239042?t=51m)

## План

- Об авторе и почему он делал гибридный проект - десктоп плюс веб.
- Зачем в 2023 году нужны терминалы?
- Режим киоска.
- Переписать веб-фронт на десктоп.
- Chromium Embdedded Framework + sharp.
- Встраиваем браузер в десктоп приложение.
- Общение между браузером и десктоп приложением.
- Гибридный результат в среде обитания.
- Некоторое железо: принтер, купюро- и монето- приемники.
- Упрощаем жизнь разработчика.
- Сборка и доставка приложения.
- Визитка + альтернативы и [пример приложения на гитхабе](https://github.com/nikvoronin/GenericBrowser).

### Доп. секция

- Преимущества веб-браузеров.
- Контроль состояния принтера.
- Контроль долгих операций.

## Вопросы

▶ [Видео `VK`](https://vk.com/video-178974757_456239042?t=1h15m20s)

- `???` Защита веб-приложения от инъекций постороннего кода мошенниками?
- Почему нет поддержки пластиковых карт?
- Рассматривался ли как вариант [Tauri](https://tauri.app/)?
- Первый ли такого типа проект у автора?
- Контролируется ли состояние оборудования?

`???` остались без ответа

## Hints

### WSL2 does not have an internet

Actualy, that is a wrong configuration of nameserver.

```shell
sudo rm /etc/resolv.conf
sudo bash -c 'echo "nameserver 1.1.1.1" > /etc/resolv.conf'
sudo bash -c 'echo "[network]" > /etc/wsl.conf'
sudo bash -c 'echo "generateResolvConf = false" >> /etc/wsl.conf'
sudo chattr +i /etc/resolv.conf
```

### Get PNG slides with ImageMagick

> sudo apt-get install imagemagick

### ImageMagic PDF restrictions

> convert-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/408.

- Open `/etc/ImageMagick-6/policy.xml`
- Change policy for PDF: `<policy domain="coder" rights="read | write" pattern="PDF" />`

### HowTo get PNG slides

> convert -density 200 foo.pdf ./res/foo_%02d.png

Produces series of PNG files like: `foo_00.png`, `foo_01.png`, ...
