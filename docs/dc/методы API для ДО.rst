.. _`GET Docflows`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows
.. _`GET Docflow`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}
.. _`GET Documents`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents
.. _`GET Document`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}
.. _`GET DocumentDescription`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-description
.. _`GET EncryptedDocumentContent`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-encrypted-content
.. _`GET DecryptedDocumentContent`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-decrypted-content
.. _`GET DocumentSignatures`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-signatures
.. _`GET DocumentSignature`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-signatures-{signatureId}
.. _`GET DocumentSignatureContent`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-signatures-{signatureId}-content
.. _`POST DocumentPrint`: https://developer.testkontur.ru/extern/post-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-print
.. _`POST RecognizeDocument`: https://developer.testkontur.ru/extern/post-v1-{accountId}-docflows-{docflowId}-documents-{documentId}-recognize
.. _`GET RelatedDocflows`: https://developer.testkontur.ru/extern/get-v1-{accountId}-docflows-{relatedDocflowId}-documents-{relatedDocumentId}-related

Методы для работы с документооборотами
======================================

Подробная спецификация методов показана в сваггере в разделе **Документообороты**.

Список доступных методов:

* `Получение списка документооборотов`_
* `Получение документооборота`_
* `Получение списка документов документооборота`_
* `Получение документа`_
* `Получение описания документа`_
* `Получение зашифрованного контента документа`_
* `Получение расшифрованного контента документа`_
* `Получение подписей под документом`_
* `Получение конкретной подписи под документом`_
* `Получение контента конкретной подписи под документом`_
* `Печать документов`_
* `Распознавание входящего требования`_
* `Получение связанных документооборотов`_

.. _rst-markup-get-dcs:

Получение списка документооборотов 
----------------------------------

Метод: `GET Docflows`_

С помощью этого метода можно получить список всех документооборотов учетной записи, при этом можно применить различные фильтры, чтобы получить необходимую выборку интересных на данный момент документооборотов. В ответе получает список документооборотов с необходимой мета-информацией по ним.

Сценарии, в которых можно использовать списки документооборотов:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* узнавать о входящих документооборотах;
* следить за статусом исходящих документооборотов;
* отображать пользователю списки его документооборотов, применяя различные фильтры.

.. _rst-markup-get-dc:

Получение документооборота
--------------------------

Метод: `GET Docflow`_

С помощью этого метода можно получить всю информацию о документообороте, такую как:

* его текущий статус;
* мета-информацию документооборота;
* перечень всех документов, созданных в ходе документооборота, на данный момент;
* и многое другое, полный ответ можно посмотреть в сваггере.

Если текущий статус документооборота подразумевает необходимость отправки ответного документа в контролирующий орган, среди ссылок в ответе этого метода будет ссылка на методы для работы с ответными документами :doc:`→ </dc/ответный документ>`.

**Пример запроса GET Docflow**

.. code-block::

    GET /v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9 HTTP/1.1
    X-Kontur-Apikey: ****
    Authorization: auth.sid ****
    Accept: application/json
    Content-Type: application/json

.. container:: toggle

    .. container:: header

        **Пример ответа GET Docflow**. 

    .. code-block:: http

        HTTP/1.1 200 OK
        Content-Type: application/json; charset=utf-8
        
        {
            "id": "a9bc74bd-311b-43f0-aff7-faba24ce35d9",
            "organization-id": "988b38f1-5580-4ba9-b9f8-3215e7f392ea",
            "type": "urn:docflow:fns534-report",
            "status": "urn:docflow-common-status:finished",
            "success-state": "urn:docflow-state:successful",
            "description": {
                "form-version": {
                "knd": "1110018",
                "version": "100501",
                "form-fullname": "Сведения о среднесписочной численности работников за предшествующий календарный год",
                "form-shortname": "Сведения о среднесписочной численности"
                },
                "recipient": "0087",
                "final-recipient": "0087",
                "correction-number": 0,
                "period-begin": "2012-01-01T00:00:00.0000000",
                "period-end": "2012-12-31T00:00:00.0000000",
                "period-code": "34",
                "payer-inn": "7757424860-680345565",
                "original-draft-id": "74b6e8b9-290a-4d12-b874-c7fb35cad54f"
            },
            "documents": [
                {
                "id": "008d30c8-b1b4-4b61-b726-cf32f2103ef4",
                "description": {
                    "type": "urn:document:fns534-report-receipt",
                    "filename": "IZ_IVNOSRCHIS_0087_0087_7757424860680345565_20200331_d66b5737fd3b40c889809975d4bfc1b3.xml",
                    "content-type": "application/xml",
                    "decrypted-content-size": 2736,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": []
                },
                "content": {
                    "decrypted": {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/008d30c8-b1b4-4b61-b726-cf32f2103ef4/decrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "ece675b1-73f8-4bef-a9e3-864101e46d63",
                        "encrypted": false,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-03-31T15:07:27.2873280Z",
                "signatures": [
                    {
                    "id": "cab34903-d98a-42eb-89f0-4dfb353e58ce",
                    "title": "ООО 'Баланс Плюс' (Марков Георгий Эльдарович)",
                    "signature-certificate-thumbprint": "20AACA440F33D0C90FBC052108012D3062D44873",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/008d30c8-b1b4-4b61-b726-cf32f2103ef4/signatures/cab34903-d98a-42eb-89f0-4dfb353e58ce/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/008d30c8-b1b4-4b61-b726-cf32f2103ef4/signatures/cab34903-d98a-42eb-89f0-4dfb353e58ce/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/008d30c8-b1b4-4b61-b726-cf32f2103ef4"
                    },
                    {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/008d30c8-b1b4-4b61-b726-cf32f2103ef4/decrypted-content"
                    }
                ]
                },
                {
                "id": "4a6abad8-ba68-4015-992e-03dade655fc6",
                "description": {
                    "type": "urn:document:fns534-report-receipt",
                    "filename": "IZ_KVNOSRCHIS_0087_0087_7757424860680345565_20200331_39c7347a61824287bc2a05ae1759d0c8.xml",
                    "content-type": "application/xml",
                    "decrypted-content-size": 2735,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": []
                },
                "content": {
                    "decrypted": {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4a6abad8-ba68-4015-992e-03dade655fc6/decrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "4badf4a5-8971-401e-bfce-4911933bd671",
                        "encrypted": false,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-03-31T15:07:26.1935268Z",
                "signatures": [
                    {
                    "id": "736af099-9d8b-449d-8336-57781d6773e5",
                    "title": "ООО 'Баланс Плюс' (Марков Георгий Эльдарович)",
                    "signature-certificate-thumbprint": "20AACA440F33D0C90FBC052108012D3062D44873",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4a6abad8-ba68-4015-992e-03dade655fc6/signatures/736af099-9d8b-449d-8336-57781d6773e5/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4a6abad8-ba68-4015-992e-03dade655fc6/signatures/736af099-9d8b-449d-8336-57781d6773e5/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4a6abad8-ba68-4015-992e-03dade655fc6"
                    },
                    {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4a6abad8-ba68-4015-992e-03dade655fc6/decrypted-content"
                    }
                ]
                },
                {
                "id": "9314a815-e1ee-43e6-ad33-c403677be863",
                "description": {
                    "type": "urn:document:fns534-report-receipt",
                    "filename": "IZ_PDNOSRCHIS_1BM_1BM_7757424860680345565_20200331_105c57ec3e6f4ef4b9088d525dfb0da1.xml",
                    "content-type": "application/xml",
                    "decrypted-content-size": 2832,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": []
                },
                "content": {
                    "decrypted": {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/9314a815-e1ee-43e6-ad33-c403677be863/decrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "33717561-de57-4700-9d2d-f424afe73fb7",
                        "encrypted": false,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-03-31T15:07:24.6927347Z",
                "signatures": [
                    {
                    "id": "16913d40-ad37-4ce6-a97f-27d35eb8674c",
                    "title": "ООО 'Баланс Плюс' (Марков Георгий Эльдарович)",
                    "signature-certificate-thumbprint": "20AACA440F33D0C90FBC052108012D3062D44873",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/9314a815-e1ee-43e6-ad33-c403677be863/signatures/16913d40-ad37-4ce6-a97f-27d35eb8674c/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/9314a815-e1ee-43e6-ad33-c403677be863/signatures/16913d40-ad37-4ce6-a97f-27d35eb8674c/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/9314a815-e1ee-43e6-ad33-c403677be863"
                    },
                    {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/9314a815-e1ee-43e6-ad33-c403677be863/decrypted-content"
                    }
                ]
                },
                {
                "id": "ea59dd5e-221b-48cc-bfc6-47f6f20e8247",
                "description": {
                    "type": "urn:document:fns534-report-processing-result-ok",
                    "filename": "IV_NOSRCHIS_7757424860_7757424860_0087_20200226_55fbe1c82c5e4a9c8d30b9e4fa3c4942.xml",
                    "content-type": "application/xml",
                    "encrypted-content-size": 1649,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": [
                    {
                        "serial-number": "01D0850043AB3C924A605B8D8661E43E"
                    }
                    ]
                },
                "content": {
                    "encrypted": {
                    "rel": "encrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/ea59dd5e-221b-48cc-bfc6-47f6f20e8247/encrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "d1a36e4f-7fed-4242-b2b2-c19c6d59e57f",
                        "encrypted": true,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-02-26T06:51:55.8084140Z",
                "signatures": [
                    {
                    "id": "f0a91da5-a190-483c-bb72-fa017df0cd8f",
                    "title": "Корионов  Илья Валерьянович",
                    "signature-certificate-thumbprint": "344AAD7111FC77ADE2A98FFB5E35F039BC4DD650",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/ea59dd5e-221b-48cc-bfc6-47f6f20e8247/signatures/f0a91da5-a190-483c-bb72-fa017df0cd8f/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/ea59dd5e-221b-48cc-bfc6-47f6f20e8247/signatures/f0a91da5-a190-483c-bb72-fa017df0cd8f/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/ea59dd5e-221b-48cc-bfc6-47f6f20e8247"
                    },
                    {
                    "rel": "encrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/ea59dd5e-221b-48cc-bfc6-47f6f20e8247/encrypted-content"
                    },
                    {
                    "rel": "decrypt-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/ea59dd5e-221b-48cc-bfc6-47f6f20e8247/decrypt-content"
                    }
                ]
                },
                {
                "id": "33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f",
                "description": {
                    "type": "urn:document:fns534-report-acceptance-result-positive",
                    "filename": "KV_NOSRCHIS_7757424860_7757424860_0087_20200226_16b4c2e212fb42a0a856dda5fdce51d3.xml",
                    "content-type": "application/xml",
                    "encrypted-content-size": 1827,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": [
                    {
                        "serial-number": "01D0850043AB3C924A605B8D8661E43E"
                    }
                    ]
                },
                "content": {
                    "encrypted": {
                    "rel": "encrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f/encrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "2640ead1-0ff3-43f2-b846-16e94f5a42cb",
                        "encrypted": true,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-02-26T06:51:55.6365313Z",
                "signatures": [
                    {
                    "id": "a8bccaac-38a8-467e-a3e0-894060b4a385",
                    "title": "Корионов  Илья Валерьянович",
                    "signature-certificate-thumbprint": "344AAD7111FC77ADE2A98FFB5E35F039BC4DD650",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f/signatures/a8bccaac-38a8-467e-a3e0-894060b4a385/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f/signatures/a8bccaac-38a8-467e-a3e0-894060b4a385/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f"
                    },
                    {
                    "rel": "encrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f/encrypted-content"
                    },
                    {
                    "rel": "decrypt-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/33eb6e4a-13d1-4b8a-82f3-01c61ec0e72f/decrypt-content"
                    }
                ]
                },
                {
                "id": "eb5dab2c-2bc7-45cb-bbbc-110bf9f105b1",
                "description": {
                    "type": "urn:document:fns534-report-receipt",
                    "filename": "IZ_NOSRCHIS_7757424860_7757424860_0087_20200226_ba3dd2e3a79a49bea6bf46fa1229bb77.xml",
                    "content-type": "application/xml",
                    "decrypted-content-size": 4968,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": []
                },
                "content": {
                    "decrypted": {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/eb5dab2c-2bc7-45cb-bbbc-110bf9f105b1/decrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "de6b5719-4e06-4aa0-88fd-c2052e55f411",
                        "encrypted": false,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-02-26T06:51:24.8363467Z",
                "signatures": [
                    {
                    "id": "cf092947-5795-484a-b55d-5230046146f7",
                    "title": "Корионов  Илья Валерьянович",
                    "signature-certificate-thumbprint": "344AAD7111FC77ADE2A98FFB5E35F039BC4DD650",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/eb5dab2c-2bc7-45cb-bbbc-110bf9f105b1/signatures/cf092947-5795-484a-b55d-5230046146f7/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/eb5dab2c-2bc7-45cb-bbbc-110bf9f105b1/signatures/cf092947-5795-484a-b55d-5230046146f7/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/eb5dab2c-2bc7-45cb-bbbc-110bf9f105b1"
                    },
                    {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/eb5dab2c-2bc7-45cb-bbbc-110bf9f105b1/decrypted-content"
                    }
                ]
                },
                {
                "id": "75d929b9-08a9-4692-961d-111cc87dc2e8",
                "description": {
                    "type": "urn:document:fns534-report",
                    "filename": "NO_SRCHIS_0007_0007_7757424860680345565_20200129_92425a70-4ac9-4680-bada-3666f0c0514n.xml",
                    "content-type": "application/xml",
                    "encrypted-content-size": 2237,
                    "compressed": true,
                    "requisites": {},
                    "related-docflows-count": 0,
                    "support-recognition": false,
                    "encrypted-certificates": [
                    {
                        "serial-number": "01D0850043AB3C924A605B8D8661E43E"
                    },
                    {
                        "serial-number": "33AC7500C3AAAE924839AA8AE6C459FE"
                    },
                    {
                        "serial-number": "19CCC7C800010000215D"
                    }
                    ]
                },
                "content": {
                    "encrypted": {
                    "rel": "encrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/encrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "f1facbc3-5d74-498f-a8af-dbfd57f82f1f",
                        "encrypted": true,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-02-26T06:51:08.4636938Z",
                "signatures": [
                    {
                    "id": "82d5457d-5297-49fb-949a-f9865a1491b1",
                    "title": "ООО 'Баланс Плюс' (Марков Георгий Эльдарович)",
                    "signature-certificate-thumbprint": "20AACA440F33D0C90FBC052108012D3062D44873",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/signatures/82d5457d-5297-49fb-949a-f9865a1491b1/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/signatures/82d5457d-5297-49fb-949a-f9865a1491b1/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    },
                    {
                    "id": "045d9beb-7748-4789-a539-4416fa7969b9",
                    "title": "ООО 'Баланс Плюс' (Марков Георгий Эльдарович)",
                    "signature-certificate-thumbprint": "20AACA440F33D0C90FBC052108012D3062D44873",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/signatures/045d9beb-7748-4789-a539-4416fa7969b9/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/signatures/045d9beb-7748-4789-a539-4416fa7969b9/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    },
                    {
                    "id": "565164bb-c9d5-4805-8250-7f6a4ac9d4aa",
                    "title": "Корионов  Илья Валерьянович",
                    "signature-certificate-thumbprint": "344AAD7111FC77ADE2A98FFB5E35F039BC4DD650",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/signatures/565164bb-c9d5-4805-8250-7f6a4ac9d4aa/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/signatures/565164bb-c9d5-4805-8250-7f6a4ac9d4aa/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8"
                    },
                    {
                    "rel": "related-docflow",
                    "href": "https://extern-api.testkontur.ru//v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/related"
                    },
                    {
                    "rel": "encrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/encrypted-content"
                    },
                    {
                    "rel": "decrypt-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/75d929b9-08a9-4692-961d-111cc87dc2e8/decrypt-content"
                    }
                ]
                },
                {
                "id": "4007e30b-0fb4-4acf-ba11-9ac513f51ca0",
                "description": {
                    "type": "urn:document:fns534-report-date-confirmation",
                    "filename": "PD_NOSRCHIS_7757424860680345565_7757424860680345565_1BM_20200226_af133042-f8c5-490c-ac5a-54b0e5e0fa9a.xml",
                    "content-type": "application/xml",
                    "decrypted-content-size": 3024,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": []
                },
                "content": {
                    "decrypted": {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4007e30b-0fb4-4acf-ba11-9ac513f51ca0/decrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "8df55933-2cbd-42b2-945c-2a1aa4386ee6",
                        "encrypted": false,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-02-26T06:51:08.4636938Z",
                "signatures": [
                    {
                    "id": "f506582c-f228-415b-844e-a78fbb7e645f",
                    "title": "АО \"ПФ \"СКБ Контур\"",
                    "signature-certificate-thumbprint": "A875B626A7D182CDCA85164FC0EF15068487A6EF",
                    "content-link": {
                        "rel": "content",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4007e30b-0fb4-4acf-ba11-9ac513f51ca0/signatures/f506582c-f228-415b-844e-a78fbb7e645f/content"
                    },
                    "links": [
                        {
                        "rel": "self",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4007e30b-0fb4-4acf-ba11-9ac513f51ca0/signatures/f506582c-f228-415b-844e-a78fbb7e645f/content"
                        },
                        {
                        "rel": "docflow",
                        "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                        }
                    ]
                    }
                ],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4007e30b-0fb4-4acf-ba11-9ac513f51ca0"
                    },
                    {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/4007e30b-0fb4-4acf-ba11-9ac513f51ca0/decrypted-content"
                    }
                ]
                },
                {
                "id": "2ad464ce-5348-444b-a1c2-d96c73aa1100",
                "description": {
                    "type": "urn:document:fns534-report-description",
                    "filename": "TR_DEKL.xml",
                    "content-type": "application/xml",
                    "decrypted-content-size": 366,
                    "compressed": true,
                    "requisites": {},
                    "support-recognition": false,
                    "encrypted-certificates": []
                },
                "content": {
                    "decrypted": {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/2ad464ce-5348-444b-a1c2-d96c73aa1100/decrypted-content"
                    },
                    "docflow-document-contents": [
                    {
                        "content-id": "6a6adf01-c138-48c8-b1fa-432fce4e5c03",
                        "encrypted": false,
                        "compressed": true
                    }
                    ]
                },
                "send-date": "2020-02-26T06:51:08.4636938Z",
                "signatures": [],
                "links": [
                    {
                    "rel": "docflow",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                    },
                    {
                    "rel": "self",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/2ad464ce-5348-444b-a1c2-d96c73aa1100"
                    },
                    {
                    "rel": "decrypted-content",
                    "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9/documents/2ad464ce-5348-444b-a1c2-d96c73aa1100/decrypted-content"
                    }
                ]
                }
            ],
            "links": [
                {
                "rel": "self",
                "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/docflows/a9bc74bd-311b-43f0-aff7-faba24ce35d9"
                },
                {
                "rel": "organization",
                "href": "https://extern-api.testkontur.ru/v1/bd0cd3f6-315d-4f03-a9cc-3507f63265ed/organizations/988b38f1-5580-4ba9-b9f8-3215e7f392ea"
                },
                {
                "rel": "web-docflow",
                "href": "https://setter.testkontur.ru/?inn=662909960905&forward_to_rel=/ft/transmission/state.aspx?key=cfOOHYSO4USxIIRIMEKAL%2fE4i5iAValLufgyFefzkuqKJpsKOwY6TorTSpphojA7vXS8qRsx8EOv9%2fq6JM412Q%3d%3d"
                }
            ],
            "send-date": "2020-02-26T09:51:08.4636938",
            "last-change-date": "2020-03-31T15:07:27.2873280Z"
        }

Получение списка документов документооборота 
--------------------------------------------

Метод: `GET Documents`_

С помощью этого метода можно получить данные всех документов, созданных и полученных в ходе документооборота.

Получение документа 
-------------------

Метод: `GET Document`_

C помощью этого метода можно получить отдельный документ, созданный или полученный в ходе документооборота, с его описанием и контентами. У каждого документа будет ссылка на контенты (зашифрованный или расшифрованный, либо оба) в текущем состоянии в соответствии с требованиями контролирующих органов.

Получение описания документа 
----------------------------

Метод: `GET DocumentDescription`_

Данный метод позволяет отдельно получить описание документа, входящего в документооборот.

Получение зашифрованного контента документа 
-------------------------------------------

Метод: `GET EncryptedDocumentContent`_

Зашифрованный контент возвращается в формате base64. Чтобы получить контент, его нужно конвертировать, дешифровать при помощи закрытого ключа, на который он был зашифрован. В результате вы получите архив, который нужно разархивировать.

Получение расшифрованного контента документа 
--------------------------------------------

Метод: `GET DecryptedDocumentContent`_

Наличие расшифрованного контента возможно не для всех документов.

Получение подписей под документом 
---------------------------------

Метод: `GET DocumentSignatures`_

В некоторых случаях у документа может быть несколько подписей. В ответе будут возвращены все подписи под запрашиваемым документом.

Получение конкретной подписи под документом 
-------------------------------------------

Метод: `GET DocumentSignature`_

В ответе будет мета-информация подписи и ссылка на её контент.

Получение контента конкретной подписи под документом 
----------------------------------------------------

Метод: `GET DocumentSignatureContent`_

Печать документов 
-----------------

Метод: `POST DocumentPrint`_

Можно получить печатную форму любого формализованного документа в документообороте. Печать документов происходит только после проверки подписей под печатаемыми документами, тем самым подтверждается валидность и неизменность печатаемых документов.

.. _rst-markup-document-recognize:

Распознавание входящего требования
----------------------------------

Метод:  `POST RecognizeDocument`_

Данный метод позволяет распознать номер и дату требования, список ИНН из требования. Данные возвращаются в ответ на переданные идентификаторы входящего требования. Само требование передается в теле запроса в формате файла. Результат запроса запишется в мета-информацию документа. 

Получение связанных документооборотов
-------------------------------------

Метод: `GET RelatedDocflows`_

Метод позволяет получить документообороты типа ответ на требование и письмо, которые могут быть связаны с входящим документооборотом и документом в нем. 
