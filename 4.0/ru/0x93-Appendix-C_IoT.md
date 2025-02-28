# Приложение C: Требования к верификации Internet of Things

Эта глава изначально была в основной ветке, но с учётом работы, проделанной командой OWASP IoT, нет смысла поддерживать две разные ветки по этому вопросу. Для версии 4.0 мы переносим это в Приложение и призываем всех, кому это требуется, переходить в основной проект [OWASP IoT](https://owasp.org/www-project-internet-of-things/)

## Задачи контроля

Встраиваемые / IoT-устройства должны:

* Обеспечивать тот же уровень безопасности на устройстве, что и на сервере, применяя меры безопасности в доверенной среде.
* Конфиденциальные данные, хранящиеся на устройстве, должны храниться безопасным образом с использованием аппаратного хранилища, например, Secure Element.
* Все конфиденциальные данные, передаваемые с устройства, должны использовать безопасность транспортного уровня (TLS).

## Требования безопасности

| № | Описание | L1 | L2 | L3 | Версия |
| --- | --- | --- | --- | -- | -- |
| **C.1** | Убедитесь, что последовательные интерфейсы отладки прикладного уровня, такие как USB, UART и другие, отключены или защищены сложным паролем. | ✓ | ✓ | ✓ | 4.0 |
| **C.2** | Убедитесь, что криптографические ключи и сертификаты уникальны для каждого отдельного устройства. | ✓ | ✓ | ✓ | 4.0 |
| **C.3** | Убедитесь, что во встроенной операционной системе/IoT включены средства защиты памяти, такие как ASLR и DEP, если применимо. | ✓ | ✓ | ✓ | 4.0 |
| **C.4** | Убедитесь, что отключены встроенные интерфейсы отладки, такие как JTAG или SWD, или что имеющийся механизм защиты включен и настроен соответствующим образом. | ✓ | ✓ | ✓ | 4.0 |
| **C.5** | Убедитесь, что если на SoC или процессоре устройства реализовано доверенное выполнение, то оно включено. | ✓ | ✓ | ✓ | 4.0 |
| **C.6** | Убедитесь, что конфиденциальные данные, закрытые ключи и сертификаты безопасно хранятся в Secure Element, TPM, TEE (Trusted Execution Environment) или защищены с помощью стойкой криптографии. | ✓ | ✓ | ✓ | 4.0 |
| **C.7** | Убедитесь, что приложения встроенного ПО защищают передаваемые данные с помощью безопасности транспортного уровня (TLS). | ✓ | ✓ | ✓ | 4.0 |
| **C.8** | Убедитесь, что приложения встроенного ПО проверяют электронную подпись подключений к серверу. | ✓ | ✓ | ✓ | 4.0 |
| **C.9** | Убедитесь, что беспроводные подключения проходят взаимную аутентификацию. | ✓ | ✓ | ✓ | 4.0 |
| **C.10** | Убедитесь, что беспроводные подключения осуществляются по зашифрованному каналу.  | ✓ | ✓ | ✓ | 4.0 |
| **C.11** | Убедитесь, что любое использование запрещенных функций на языке C заменено их безопасными эквивалентами. | ✓ | ✓ | ✓ | 4.0 |
| **C.12** | Убедитесь, что каждая "прошивка" содержит спецификацию программного обеспечения с каталогом сторонних компонентов, версиями и опубликованными уязвимостями. | ✓ | ✓ | ✓ | 4.0 |
| **C.13** | Убедитесь, что весь код, включая сторонние бинарные файлы, библиотеки и фреймворки, проверяется на наличие в коде учётных данных (бэкдоров). | ✓ | ✓ | ✓ | 4.0 |
| **C.14** | Убедитесь, что компоненты приложения и встроенного ПО не подвержены инъекции команд операционной системы, вызывая команды оболочки ОС или скрипты, и что меры безопасности их предотвращают. | ✓ | ✓ | ✓ | 4.0 |
| **C.15** | Убедитесь, что приложения встроенного ПО закрепляют (pinning) электронную подпись на доверенных серверах. |  | ✓ | ✓ | 4.0 |
| **C.16** | Убедитесь в наличии средств защиты от несанкционированного доступа и/или его обнаружения. |  | ✓ | ✓ | 4.0 |
| **C.17** | Убедитесь, что включены все имеющиеся технологии защиты интеллектуальной собственности, предоставляемые производителем чипа. |  | ✓ | ✓ | 4.0 |
| **C.18** | Убедитесь, что меры безопасности препятствуют обратному инжинирингу встроенного ПО (например, удалению символов детализации отладки). |  | ✓ | ✓ | 4.0 |
| **C.19** | Убедитесь, что перед загрузкой устройство проверяет подпись загрузочного образа. |  | ✓ | ✓ | 4.0 |
| **C.20** | Убедитесь, что процесс обновления прошивки не подвержен атакам типа «момент проверки до момента использования». |  | ✓ | ✓ | 4.0 |
| **C.21** | Перед установкой убедитесь, что устройство использует подпись кода и проверяет файлы обновления прошивки. |  | ✓ | ✓ | 4.0 |
| **C.22** | Убедитесь, что версия прошивки устройство не может быть понижена до старых версий (анти-откат). |  | ✓ | ✓ | 4.0 |
| **C.23** | Проверьте использование криптографического генератора псевдослучайных чисел на встроенном устройстве (например, с использованием генераторов случайных чисел, предоставляемых чипом). |  | ✓ | ✓ | 4.0 |
| **C.24** | Убедитесь, что прошивка может выполнять автоматическое обновление по заданному расписанию. |  | ✓ | ✓ | 4.0 |
| **C.25** | Убедитесь, что устройство стирает прошивку и конфиденциальные данные при обнаружении несанкционированного доступа или получении недопустимого сообщения. |  |  | ✓ | 4.0 |
| **C.26** | Убедитесь, что используются только микроконтроллеры, поддерживающие отключение интерфейсов отладки (например, JTAG, SWD). |  |  | ✓ | 4.0 |
| **C.27** | Убедитесь, что используются только те микроконтроллеры, которые обеспечивают существенную защиту от декапинга (анг.: de-capping) и атак по побочным каналам. |  |  | ✓ | 4.0 |
| **C.28** | Убедитесь, что конфиденциальные дорожки не соприкасаются с внешними слоями печатной платы. |  |  | ✓ | 4.0 |
| **C.29** | Убедитесь, что канал связи между микросхемами зашифрован (например, между основной и дочерней платой). |  |  | ✓ | 4.0 |
| **C.30** | Убедитесь, что устройство использует подпись кода и проверяет код перед выполнением. |  |  | ✓ | 4.0 |
| **C.31** | Убедитесь, что конфиденциальная информация, хранящаяся в памяти, перезаписывается нулями, как только она больше не требуется. |  |  | ✓ | 4.0 |
| **C.32** | Убедитесь, что приложения встроенного ПО используют контейнеры ядра для изоляции между приложениями. |  |  | ✓ | 4.0 |
| **C.33** | Убедитесь, что для сборок микропрограмм настроены безопасные флаги компилятора, такие как `-fPIE`, `-fstack-protector-all`, `-Wl,-z,noexecstack`, `-Wl,-z,noexecheap`. |  |  | ✓ | 4.0 |
| **C.34** | Убедитесь, что в микроконтроллере настроена защита кода (если применимо).|  |  | ✓ | 4.0 |

## Ссылки

Для дополнительной информации см. также:

* [OWASP Internet of Things Top 10](https://owasp.org/www-pdf-archive/OWASP-IoT-Top-10-2018-final.pdf)
* [OWASP Embedded Application Security Project](https://owasp.org/www-project-embedded-application-security/)
* [OWASP Internet of Things Project](https://owasp.org/www-project-internet-of-things/)
* [Trudy TCP Proxy Tool](https://github.com/praetorian-inc/trudy)
