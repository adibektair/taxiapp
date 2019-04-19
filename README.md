# Почасовая тарификация
1. Запрос на получение цены чаосого тарифа: 
## 194.87.146.89/profile/account/get-hourly-price/
`
POST: {
  token
  duration - ДЛИТЕЛЬНОСТЬ В МИНУТАХ (1 час = 60 минут)
}
response:{
    "price": 2250,
    "state": "success"
}
`
2. Когда заказываете часовую тарификацию, запрос остается тот же `make-order/`, но latitude_to и longitude_to не отправляете, и отправляете 2 новых поля: 1. is_hourly - TRUE, и duration - длительность заказа в минутах(!)
3. Чтобы Ваше приложение не падало, как после хука от Тайсона, поставьте исключения, ведь теперь у водителя может прилететь заказ БЕЗ точки Б.
4. Отсчет времени начинается с момента, когда водитель нажимает на кнопку В ПУТИ. В этот момент с сервера придет уведомление и клиенту и водителю с кодом 204 а также полe "price_per_hour", чтобы Вы могли самостоятельно вывести и клиенту и водителю таймер со временем начала заказа и ценой. Продолжительность заказа может быть бесконечной. Хоть клиент и указал что он заказывает на час, они могут попасть в пробки и тд, в любом случае таймер работает до тех пор, пока водитель не завершит поездку.
