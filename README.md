# Выращиваем гибрид

Нет, это не про монолит и микросервисы.

Мы взяли веб-приложение и сделали из него десктоп. Затем построили свой терминал и продаем клиентам. Все это меньше, чем за год. Не напрягаясь и не подключая сотни людей.

[Title Slide](slides/00.png)

__Место проведения:__ г. Владимир, ул. Гагарина 5, 4 этаж, [конф. зал Альтенара](https://yandex.ru/maps/-/CDQlNY~U).

8 Сентяря 2023 года. [Видео `VK`](https://vk.com/video-178974757_456239042) ▶ 00:51:00

## План

## Вопросы

`???` остались без ответа

## Hints

### WSL2 does not have an internet

Actualy, that is wrong nameserver.

```shell
sudo rm /etc/resolv.conf
sudo bash -c 'echo "nameserver 1.1.1.1" > /etc/resolv.conf'
sudo bash -c 'echo "[network]" > /etc/wsl.conf'
sudo bash -c 'echo "generateResolvConf = false" >> /etc/wsl.conf'
sudo chattr +i /etc/resolv.conf
```

### Get PNG slides with ImageMagick

> $ sudo apt-get install imagemagick

### ImageMagic PDF restrictions

> convert-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/408.

- Open `/etc/ImageMagick-6/policy.xml`
- Change policy for PDF: `<policy domain="coder" rights="read | write" pattern="PDF" />`

### HowTo get PNG slides

> convert -density 200 foo.pdf ./res/foo_%02d.png

Produces series of PNG files like: `foo_00.png`, `foo_01.png`, ...
