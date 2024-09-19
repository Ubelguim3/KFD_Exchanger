# Обменник валют

from random import randint
 
user_cash = {'rub': 1000000, 'usd' : 0, 'usdt' : 0, 'eur' : 0, 'btc' : 0}
terminal_cash = {'rub': 10000, 'usd' : 1000, 'usdt' : 1000, 'eur' : 1000, 'btc' : 1.5}
currencies = {'rub/usd' : 90, 'rub/eur' : 104, 'usd/eur' : 1.11, 'usd/usdt' : 1, 'usd/btc': 60496 }

while True:
    print('выберите команду:\n (a) посмотреть Ваш баланс\n (b) посмотреть средства терминала  \n (c) обменять валюты \n (d) посмотреть курс валют \n (e) выход')
    command = input()
    if command == 'a':
        for key, value in user_cash.items():
            print(f'{key} : {value}')
    elif command == 'b':
        for key, value in terminal_cash.items():
            print(f'{key} : {value}')
    elif command == 'c':
         while True:
            print('выберите валютную пару: \n (1) rub/usd \n (2) rub/eur \n (3) usd/eur \n (4) usd/usdt \n (5) usd/btc \n (6) Выход')
            char = input()
            
            if char == '1':
                print('введите кол-во USD:')
                count_usd = float(input())
                count_rub = count_usd * currencies['rub/usd']
                if count_rub > user_cash['rub']:
                    print('Недостаточно средств')
                else:
                    user_cash['rub'] -= count_rub
                    user_cash['usd'] += count_usd
                    for k in currencies.keys():
                        currencies[k] += currencies[k] / 100*randint(0,5)
                    print('Обмен произведён')
                break
                
            if char == '2':
                print('введите кол-во EUR:')
                count_eur = float(input())
                count_rub = count_eur * currencies['rub/eur']
                if count_rub > user_cash['rub']:
                    print('Недостаточно средств')
                else:
                    user_cash['rub'] -= count_rub
                    user_cash['eur'] += count_eur
                    for k in currencies.keys():
                        currencies[k] += currencies[k] / 100*randint(0,5)
                    print('Обмен произведён')
                break
                
            if char == '3':
                print('введите кол-во eur:')
                count_eur = float(input())
                count_usd = count_eur * currencies['usd/eur']
                if count_usd > user_cash['usd']:
                    print('Недостаточно средств')
                else:
                    user_cash['usd'] -= count_usd
                    user_cash['eur'] += count_eur
                    for k in currencies.keys():
                        currencies[k] += currencies[k] / 100*randint(0,5)
                    print('Обмен произведён')
                break

            if char == '4':
                print('введите кол-во USDT:')
                count_usdt = float(input())
                count_usd = count_usdt * currencies['usd/usdt']
                if count_usd > user_cash['usd']:
                    print('Недостаточно средств')
                else:
                    user_cash['usd'] -= count_usd
                    user_cash['usdt'] += count_usdt
                    for k in currencies.keys():
                        currencies[k] += currencies[k] / 100*randint(0,5)
                    print('Обмен произведён')
                break

            if char == '5':
                print('введите кол-во BTC:')
                count_btc = float(input())
                count_usd = count_btc * currencies['usd/btc']
                if count_usd > user_cash['usd']:
                    print('Недостаточно средств')
                else:
                    user_cash['usd'] -= count_usd
                    user_cash['btc'] += count_btc
                    for k in currencies.keys():
                        currencies[k] += currencies[k] / 100*randint(0,5)
                    print('Обмен произведён')
                break
            if char == '6':
                print('Выход из обмена валют')
                break
            print("Неверный ввод")
    elif command == 'd':
        for key, value in currencies.items():
            print(f'{key} : {value}')                        
                

    elif command == 'e':
        print('Завершение работы программы')
        break
    else:
        print('Неверный ввод')
