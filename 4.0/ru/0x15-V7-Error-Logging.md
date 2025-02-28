# V7 Обработка ошибок и ведение журнала

Основная цель обработки ошибок и ведения журнала — дать полезную информацию пользователям, администраторам и группам реагирования на инциденты. Цель журнала не в том, чтобы регистрировать в нем как можно больше записей, а в полезности каждой отдельной записи, и в улучшении отношения сигнал/шум.

Качественные журналы часто содержат конфиденциальную информацию и должны быть защищены в соответствии с местными законами о конфиденциальности. Меры защиты журнала должны включать:

* Не собирать и не регистрировать в журналах конфиденциальную информацию, если этого не требуется.
* Обеспечивать безопасную обработку и защиту регистрируемой в журналах информации в соответствии с ее категорией.
* Убедиться, что журналы не хранятся вечно, и имеют как можно более короткий срок хранения.

Если журналы содержат персональные или другие чувствительные данные, определение которых варьируется от страны к стране, то они становятся одной из наиболее привлекательных целей для злоумышленников в приложении.

Также важно убедиться, что и при сбоях приложение ведет себя безопасно, не раскрывая избыточной информации в тексте ошибок.

## V7.1 Содержимое журнала

Регистрация конфиденциальной информации в журнале опасна — журналы сами по себе становятся засекреченными, а это означает, что они должны быть зашифрованы, на них распространяются политики хранения и их необходимо раскрывать в ходе аудитов безопасности. Убедитесь, что в журналах хранится только необходимая информация, и, конечно, никаких платежных, учетных (включая сессионные токены), конфиденциальных или персональных данных.

V7.1 и V7.2 охватывают [OWASP Top 10 2017:A10](https://owasp.org/www-project-top-ten/2017/A10_2017-Insufficient_Logging%2526Monitoring). Поскольку 2017:A10 не поддаётся тестированию на проникновение, то необходимо:

* разработчикам — обеспечивать полное соответствие этому разделу, как если бы все требования были помечены как L1;
* пентестерам — обеспечивать контроль соответствия всем требованиям V7.1 с помощью интервью, снимков экрана и проверки утверждений.

| № | Описание | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---:| :---: | :---: |
| **7.1.1** | Убедитесь, что приложение не записывает в журнал учетные или платежные данные. Сессионные токены могут записываться в журнал только в необратимой хэшированной форме. ([C9, C10](https://owasp.org/www-project-proactive-controls/#div-numbering)) | ✓ | ✓ | ✓ | 532 |
| **7.1.2** | Убедитесь, что приложение не записывает в журнал другие конфиденциальные данные в соответствии с применимыми законами (ПДн, банковская, налоговая, коммерческая, врачебная и иные виды тайн) или действующей политике безопасности. ([C9](https://owasp.org/www-project-proactive-controls/#div-numbering)) | ✓ | ✓ | ✓ | 532 |
| **7.1.3** | Убедитесь, что приложение регистрирует в журнале события, относящиеся к безопасности, включая успешную и неудачную аутентификацию, события нарушения контроля доступа, десериализации и форматно-логического контроля входных данных. ([C5, C7](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 778 |
| **7.1.4** | Убедитесь, что каждое событие журнала включает необходимую и достаточную информацию, которая позволит провести его подробное исследование с учетом хронологических связей. ([C9](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 778 |

## V7.2 Обработка журнала

Своевременная регистрация событий имеет решающее значение для их аудита, сортировки и эскалации. Убедитесь, что журналы приложения понятны и могут анализироваться либо локально, либо в удаленной системе мониторинга.

| № | Описание | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---:| :---: | :---: |
| **7.2.1** | Убедитесь, что все решения по аутентификации регистрируются в журнале, без сохранения сессионных токенов, паролей и т.п., включая запросы с соответствующими метаданными, необходимыми для расследований событий безопасности. | | ✓ | ✓ | 778 |
| **7.2.2** | Убедитесь, что все решения по контролю доступа МОГУТ, а все неудачные попытки ДОЛЖНЫ быть занесены в журнал, включая запросы с соответствующими метаданными, необходимыми для расследований событий безопасности. | | ✓ | ✓ | 285 |

## V7.3 Защита журнала

Журналы, которые можно тривиально изменить или удалить, бесполезны для расследований и криминалистики. Раскрытие журнала может привести к разглашению внутренних сведений о приложении или содержащейся в нем информации. Необходимо соблюдать осторожность при защите журналов от несанкционированного раскрытия, изменения или удаления.

| № | Описание | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---:| :---: | :---: |
| **7.3.1** | Убедитесь, что все компоненты записывают события в журнал в нормализованной форме, указывая правильную кодировку, и используя экранирование символов, чтобы предотвратить инъекцию в журнал. ([C9](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 117 |
| **7.3.2** | [УДАЛЕНО, ДУБЛИРУЕТ 7.3.1] | | | | |
| **7.3.3** | Убедитесь, что журналы событий безопасности защищены от несанкционированного доступа и изменения. ([C9](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 200 |
| **7.3.4** | Убедитесь, что системное время синхронизируется с утвержденными источниками времени и в правильном часовом поясе. Для географически распределенных систем настоятельно рекомендуется вести журнал в формате UTC, чтобы облегчить криминалистический анализ после инцидента. ([C9](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | |

Примечание: Кодирование журнала (7.3.1) сложно протестировать и проверить с помощью автоматизированных динамических инструментов и тестов на проникновение, но архитекторы, разработчики и рецензенты исходного кода должны учитывать это требование как L1.

## V7.4 Обработка ошибок

Цель обработки ошибок — предоставлять важные для безопасности приложения события для мониторинга, сортировки и эскалации. Смысл не в том, чтобы создавать много записей. При регистрации событий, связанных с безопасностью, убедитесь, что в каждой записи есть смысл, который понятен SIEM или аналитической системе.

| № | Описание | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---:| :---: | :---: |
| **7.4.1** | Убедитесь, что при возникновении непредвиденной ошибки или ошибки, связанной с безопасностью, отображается универсальное сообщение с уникальным идентификатором, который персонал службы сопровождения может использовать для расследования. ([C10](https://owasp.org/www-project-proactive-controls/#div-numbering)) | ✓ | ✓ | ✓ | 210 |
| **7.4.2** | Убедитесь, что для учета ожидаемых и непредвиденных ошибок в кодовой базе используется обработка исключений (или ее функциональный эквивалент). ([C10](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 544 |
| **7.4.3** | Убедитесь, что определен обработчик ошибок «последней инстанции», который будет перехватывать все необработанные исключения. ([C10](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 431 |

Примечание. Некоторые языки, такие как Swift и Go, а также многие функциональные языки не поддерживают исключения или обработчики событий последней инстанции. В этом случае архитекторы и разработчики должны использовать такой шаблон, язык или фреймворк, которые обеспечат безопасную обработку исключений, а также неожиданных или связанных с безопасностью событий.

## Ссылки

Для дополнительной информации см. также:

* [OWASP Testing Guide 4.0: Testing for Error Handling](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/08-Testing_for_Error_Handling/README.html)
* [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html#authentication-and-error-messages)
