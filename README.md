# Token

На странице - одна кнопка "Войти", по ней вызывается стандартная oauth-авторизация. 
1. страница авторизации https://testing.e-id.cards/oauth/user
s.deal@ukr.net/EiG3oobe
test1/EiG3oobe
- Параметры (Обязательно регистро-зависимые!):
response_type=code
redirect_uri = "????" (пользователь на него вернется с кодом для получения токена, это адрес на нашем сервере)
client_id = "test-task"
client_secret = "soHievJa"
scope = "firstname,surname,email,phone,pwhash,viber,skype,wechat,trust_level,otp,totp_secret"

2. token_url = "https://testing.e-id.cards/oauth/client" для получения access_token
Также для получения токена добавляем сюда же параметры client_id, client_secret, grant_type=authorization_code и redirect_uri	

3. Полученный access_token отправляем по адресу
DATA_URL = "https://testing.e-id.cards/oauth/data"
3. В ответ получаем json со всеми данными пользователя и отправляем его без изменений по адресу
https://testing.bb.yttm.work:5000/v1/oauth_auth
4. В ответ получаем json, в котором нас интересует только sid (ну и чтобы result=="ok")
5. Используя этот sid получаем список валют и курсы валют, выводим его пользователю в виде сворачиваемого списка accordion, в котором верхний уровень - валюты, нижний - курсы
https://testing.bb.yttm.work:5000/v1/get_currencies
https://testing.bb.yttm.work:5000/v1/get_currency_rates
в реальности для выполнения именно этих методов sid не нужен, его надо просто отобразить в тестовом виде
6. Дизайнер в разработке не участвует, но результат должен быть визуально приемлимым 
