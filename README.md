#  Проект: извлечения телефонных номеров и адресов электронной почты
## Collector of :phone: phone numbers and :email: e-mails
----------
Проект помогает если необходимо заняться рутинной работой — найти все телефонные номера и адреса электронной почты, которые содержатся на длинной веб-странице или в документе большого размера. Программа, способна выполнять поиск телефонных номеров и электронных адресов в буфере обмена, с ее помощью можно просто нажать комбинацию клавиш <Ctrl+A> для выделения всего текста и комбинацию клавиши <Ctrl+C> для копирования выделенного текста в буфер, а затем выполнить программу. Эта программа может заменить находящийся в буфере текст найденными телефонными номерами и адресами электронной почты.

### План программы, что должна делать программа:
+ получать текст из буфера обмена;
+ находить в тексте все телефонные номера и адреса электронной почты;
+ переносить найденный текст в буфер обмена.


### Реализация всего вышеуказанного в виде кода. Код выполняет следующие операции:
+ использует модуль pyperclip для копирования и вставки строк;
+ создаёт два регулярных выражения, первое из которых соответствует телефонным номерам, а второе — адресам электронной почты;
+ находит все совпадения, а не только первое, для обоих регулярных выражений;
+ аккуратно форматирует найденные строки, преобразуя их в одну строку для вставки в буфер;
+ отображает соответствующее сообщение, если искомые соответствия в тексте не были обнаружены.


#### Регулярное выражение для поиска телефонных номеров

Телефонный номер начинается с кода страны в котором одна цифра со знаком плюс либо без знака плюс `(\d{1} | \+\d{1})` 
В качестве разделителя групп цифр в телефонном номере могут использоваться пробел (\s), дефис (-) или точка (.), поэтому данные компоненты регулярного выражения также должны быть соединены символами канала, вот так `(\s | - | \.)?`
Поскольку территориальный код может иметь ровно три цифры `(\d{3})`. Снова  может идти разделитель `(\s | - | \.)?`
В следующих трех компонентах нет ничего сложного: три цифры `(\d{3})`, за которыми следует другой разделитель `(\s | - | \.)?`, а затем еще четыре цифры `(\d{4})`.

#### Регулярное выражение для поиска адресов электронной почты