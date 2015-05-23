# Safecoin-запросы и правила
Существует три типа safecoin-запросов:
* PUT - используется для отправки монет (или данных) на определенный узел
* GET - используется для получения монет (или данных) с определенного узла
* EXCHANGE - используется для обмена монетами (или данными) между двумя определенными узлами

Safecoins - это иной вид данных, для которого тоже определены запросы PUT и GET. Однако, в отличии от обычных данных, для монет не реализована операция DELETE.

Запрос PUT имеет свойство "дублирование запрещено". Это означает, что если в сети уже имеется safecoin с таким же именем (первые 32 бита совпадают), то запрос отклоняется. Эта проверка проводится менеджером данных, которому приходит запрос PUT.

Запрос EXCHANGE позволяет обновить информацию о safecoin, но только при соблюдении следующих необходимых правил:


An EXCHANGE allows a requester to update the details of the safecoin but only if it follows the necessary rules.

* Owner is approved by the majority of 3rd party Vaults (escrow).
* Owner can (previous and current owners considered as approved themselves) update all fields.
* Each 3rd party Vaults (escrow) can only update their correspondent field once.
* Each time previous and current owner fields get updated, the safecoin version must be increased by one, and all escrow fields are erased.

The above rules are enforced by the Pmid manager holding the safecoin data. As the ownership field, together with the 3rd party Vaults (escrow) fields, are used as a 'transaction', the Pmid manager effectively becomes the Transaction manager. In this instance, the safecoin data can also be considered as a receipt object as well.
