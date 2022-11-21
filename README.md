# Autoupdate Zimbra SSL certifcate script
Установка Let’s encrypt

Идем на сайт https://certbot.eff.org/instructions и устанавливаем certbot под нашу систему
```
sudo apt-get update
sudo apt-get install software-properties-common
sudo add-apt-repository universe
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install certbot
```
Генерация нового сертификата
Имя сервера Zimbra: test.my.domain
Домен должен быть куплен и доступен извне по имени по портам HTTP (80) и HTTPS (445)

Генерируем сертификат, можно добавить домен с www, если он не настроен, то его можно не генерировать
```
certbot certonly --standalone -d test.my.domain -d www.test.my.domain
```
Ставим скрипт на выполнение:
```
crontab -e
0 3 20 2,4,6,8,10,12 * /opt/zimbra/ssl/update_zimbra_ssl.sh
```
