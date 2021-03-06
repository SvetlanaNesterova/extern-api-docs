.. _`шлюз ФСС`: http://f4.fss.ru/fss/office
.. _`инструкции`: https://www.kontur-extern.ru/support/faq/31/157
.. _`POST AddDocument`: https://developer.testkontur.ru/extern/post-v1-%7BaccountId%7D-drafts-%7BdraftId%7D-documents
.. _`PUT PutDocumentSignature`: https://developer.testkontur.ru/extern/put-v1-%7BaccountId%7D-drafts-%7BdraftId%7D-documents-%7BdocumentId%7D-signatures-%7BsignatureId%7D
.. _`POST Check`: https://developer.testkontur.ru/extern/post-v1-%7BaccountId%7D-drafts-%7BdraftId%7D-check
.. _`POST Prepare`: https://developer.testkontur.ru/extern/post-v1-%7BaccountId%7D-drafts-%7BdraftId%7D-prepare
.. _`POST Send`: https://developer.testkontur.ru/extern/post-v1-%7BaccountId%7D-drafts-%7BdraftId%7D-send

Документооборот с ФСС
=====================

.. _rst-marckup-dc-fss:

Через API Контур.Экстерна в Фонд социального страхования можно отправить только форму 4-ФСС (тип документооборота urn:docflow:fss-report).

**Особенности документооборота с ФСС**:

* подпись документа передается вместе с содержимым документа;
* в данном виде документооборота нет ответных документов;
* помимо статусов важную роль имеют стадии. Подробное описание представлено в разделе :ref:`спецификация<rst-markup_4fss>`;
* со стороны контролирующего органа отчетность принимает `шлюз ФСС`_, на котором вы можете найти отправленный отчет по его идентификатору.

Порядок документооборота по форме 4-ФСС
---------------------------------------

1. Создаем и наполняем черновик. 
2. Добавляем документ в черновик. Для документооборота с ФСС он всегда будет один для файла отчета по форме 4-ФСС. 
  
  В методе `POST AddDocument`_ подпись можно приложить вместе с содержимым документа в виде ``base64-content`` либо отдельным параметром ``signature``. Также допускается добавить только содержимое документа, а подпись подложить отдельно в методе `PUT PutDocumentSignature`_.

3. Когда черновик готов, запускаем последовательность методов: `POST Check`_ -> `POST Prepare`_ -> `POST Send`_. Если подпись и содержимое документа лежали отдельно, то метод ``Prepare`` объединит их в одном параметре ``base64-content`` модели ``documentContents``. 

После отправки отчета требуется дождаться получения квитанции или протокола обработки. Подробное описание документов доступно в `инструкции`_. 