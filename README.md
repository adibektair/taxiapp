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
