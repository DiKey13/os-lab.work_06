Попробуем почувствовать себя в роли защитника и попытаемся убрать программу созданную в задании 4.

<img width="608" height="584" alt="image" src="https://github.com/user-attachments/assets/22647d97-9c6f-440c-87ac-15a9c0e64869" />

При проверке мы можем увидеть подозрительную строчку (первая)

Попробуем это исправить и убрать значение s в ACL 

<img width="771" height="262" alt="image" src="https://github.com/user-attachments/assets/9435e342-e793-4b04-ad7e-cccc60bae630" />

Проведём проверку

<img width="596" height="586" alt="image" src="https://github.com/user-attachments/assets/5efecb8b-40c8-485a-a1d3-c4db65ae61bc" />

Как видим мы убрали строчку которая нам не нравилась.

Так почему же там не нравилась первая строка?
Потому что это demobash - классический бекдор, который должен находиться только в каталоге пользователя(root)
А строки sudo, su, passwd  являются штатными SUID программами и находятся в системном каталоге.

Доказательство опасности:

<img width="766" height="102" alt="image" src="https://github.com/user-attachments/assets/d2e7fdbf-90e7-4103-82a5-86e53dbf4490" />

имеется значение euid=0.

<img width="763" height="62" alt="image" src="https://github.com/user-attachments/assets/e462a363-1efb-492d-b9dc-48ff359fd906" />

После зачистки этого значения больше нет.

Вывод:Админ должен постоянно проверять SUID сравнивая его с эталонным список(с единственно верным) и удалять подозрительные
SUID особенно находящиеся вне каталогов.
