.. _`POST SignReplyDocument`: https://developer.testkontur.ru/extern/post-v1-%7BaccountId%7D-docflows-%7BrelatedDocflowId%7D-documents-%7BrelatedDocumentId%7D-inventories-%7BinventoryId%7D-documents-%7BdocumentId%7D-replies-%7BreplyId%7D-cloud-sign
.. _`GET GetDocflowReplyDocumentTask`: https://developer.testkontur.ru/extern/get-v1-%7BaccountId%7D-docflows-%7BrelatedDocflowId%7D-documents-%7BrelatedDocumentId%7D-inventories-%7BinventoryId%7D-documents-%7BdocumentId%7D-tasks-%7BapiTaskId%7D
.. _`GET GetSignatureContent`: https://developer.testkontur.ru/extern/get-v1-%7BaccountId%7D-docflows-%7BrelatedDocflowId%7D-documents-%7BrelatedDocumentId%7D-inventories-%7BinventoryId%7D-documents-%7BdocumentId%7D-signatures-%7BsignatureId%7D-content
.. _`POST InitDecryptDocument`: https://developer.testkontur.ru/extern/post-v1-%7BaccountId%7D-docflows-%7BrelatedDocflowId%7D-documents-%7BrelatedDocumentId%7D-inventories-%7BinventoryId%7D-documents-%7BdocumentId%7D-decrypt-content

Подписание и дешифрование документов в ответе на требование
===========================================================

.. important:: Методы данного раздела позволяют работать только с DSS сертификатами электронной подписи, выпущенными Удостоверяющим центром АО "ПФ "СКБ Контур" (https://ca.kontur.ru).

Подробнее о технологии DSS читайте в разделе :ref:`Облачная подпись<rst-markup-сloud_dss>`

В этом разделе описан процесс подписания и дешифрования документов в документообороте типа ответ на требование (urn:docflow:fns534-inventory).

.. _rst-markup-сloud_inventory:

**Процесс работы с API для подписания ответного документа**

1. Подписание ответного документа `POST SignReplyDocument`_

В данном методе проверяется тип сертификата пользователя. Если пользователь использует DSS сертификат, то в результате метод вернет модель ``SignInitResult`` с заполненными полями ``TaskId``, ``ConfirmType = myDSS``. Это означает, что сервис переходит в режим ожидания ответа от сервера КриптоПро DSS с результатом операции.

2. Клиент на своем телефоне в приложении myDSS вводит ПИН-код от своей электронной подписи и подтверждает, что он действительно хочет подписать документ;

3. Проверка статуса задачи подписания документа методом `GET GetDocflowReplyDocumentTask`_

   * Если состояние ``task-state = failed``, это означает, что на любом этапе подписания возникла ошибка. Описание будет в модели ``Error``.
   * Если состояние ``task-state = running``, это означает, что подпись еще не подтверждена либо еще генерируется.
   * Если состояние ``task-state = succeed``, это означает, что подписание завершено. Файл подписи был успешно сформирован и сохранен в черновике.

4. Получить подпись `GET GetSignatureContent`_

.. note::
   Подпись будет приложена к ответному документу только при вызове метода `GET GetDocflowReplyDocumentTask`_ с результатом ``task-state = succeed``.

**Процесс работы с API для дешифрования контента документа**

1. Дешифрование содержимого документа `POST InitDecryptDocument`_
   
В данном методе проверяется тип сертификата пользователя. Если пользователь использует DSS сертификат, то в результате метод вернет модель ``DecryptionInitResult`` с заполненными полями ``TaskId``, ``ConfirmType = myDSS``. Это означает, что сервис переходит в режим ожидания ответа от сервера КриптоПро DSS с результатом операции.

2. Клиент на своем телефоне в приложении myDSS вводит ПИН-код от своей электронной подписи и подтверждает, что он действительно хочет подписать документ;

3. Проверка статуса задачи дешифрования `GET GetDocflowReplyDocumentTask`_

   * Если состояние task-state = failed, это означает, что на любом этапе дешифрования возникла ошибка. Описание будет в модели ``Error``.
   * Если состояние task-state = running, это означает, что дешифрование еще не подтверждено либо содержимое еще генерируется. 
   * Если состояние task-state = succeed, это означает, что дешифрование завершено. **В task-result будет лежать расшифрованный контент документа**.  