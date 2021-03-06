﻿---
title: 'Справка по Exchange 2013: импорт или экспорт сертификатов для UM'
TOCTitle: Импорт или экспорт сертификатов для единой системы обмена СООБЩЕНИЯМИ
ms:assetid: ee688c33-2e08-47e7-95fc-04ba10238341
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn205143(v=EXCHG.150)
ms:contentKeyID: 54652141
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Импорт или экспорт сертификатов для единой системы обмена СООБЩЕНИЯМИ

 

_**Применимо к:** Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-12-18_

С помощью Центра администрирования Exchange (EAC) или командной консоли можно импортировать и экспортировать самозаверяющие сертификаты, сертификаты внутренней инфраструктуры открытых ключей (PKI) или коммерческие сертификаты сторонних поставщиков. Для единой системы обмена сообщениями можно использовать один из этих сертификатов для служб единой системы обмена сообщениями Microsoft Exchange и маршрутизатора вызовов этой системы. Можно использовать один сертификат для обеих служб или различные сертификаты для каждой из них.

Импорт сертификатов для Exchange может быть полезным, если необходимо:

  - импортировать сертификат, экспортированный в файл;

  - импортировать сертификат инфраструктуры открытых ключей (PKI), созданный внутренним центром сертификации;

  - импортировать сторонний коммерческий сертификат.

Экспорт существующего сертификата из хранилища сертификатов на локальном сервере Exchange может быть полезным, если необходимо:

  - экспортировать его для импорта на другой сервер Exchange;

  - экспортировать его для импорта на шлюз VoIP, IP-УАТС или УАТС с поддержкой протокола SIP;

  - экспортировать сертификат для резервного копирования самого сертификата и его закрытого ключа.

Дополнительные сведения о задачах, связанных с управлением сертификатами для единой системы обмена сообщениями, см. в разделе [Развертывание сертификатов для единой системы обмена СООБЩЕНИЯМИ процедур](deploying-certificates-for-um-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Пункт "Управление сертификатами" в статье [Разрешения инфраструктуры Exchange и командной консоли](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md) и пункт "Служба единой системы обмена сообщениями" в статье [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md). Также необходимо войти в систему с помощью учетной записи домена, являющейся членом локальной группы "Администраторы" данного компьютера.

  - Прежде чем экспортировать сертификат, с помощью командлета **Get-ExchangeCertificate** убедитесь, что для атрибута *PrivateKeyExportable* сертификата задано значение `$true`.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что необходимо сделать?

## Использование Центра администрирования Exchange для экспорта сертификата

1.  В Центре администрирования Exchange последовательно выберите пункты **Серверы** \> **Сертификаты** \> **Дополнительные параметры**![Значок дополнительных параметров](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Значок дополнительных параметров"), а затем нажмите кнопку **Экспортировать сертификат Exchange**.

2.  На странице **Экспорт сертификата Exchange** в поле **Файл для экспорта** введите имя файла сертификата.

3.  В поле **Пароль** введите пароль, который необходимо использовать для защиты закрытого ключа, а затем нажмите кнопку **ОК**.

## Использование командной консоли для экспорта сертификата

В этом примере сертификат с отпечатком A36DE2B9B62980A717EBD0C3052F5F0B08FBFFCC экспортируется в файл после запроса имени пользователя и пароля.

    $file = Export-ExchangeCertificate -Thumbprint A36DE2B9B62980A717EBD0C3052F5F0B08FBFFCC -BinaryEncoded:$true -Password (Get-Credential).password

В данном примере выполняется следующее:

1.  Командлет **Get-ExchangeCertificate** используется для поиска сертификата, который необходимо экспортировать.

2.  Командлет **Export-ExchangeCertificate** используется для установки пароля для сертификата.

3.  Сертификат экспортируется в файл после ввода имени пользователя и пароля.

<!-- end list -->

```
    $file = Get-ExchangeCertificate -DomainName umcorp.northwindtraders.com | Export-ExchangeCertificate -BinaryEncoded:$true -Password (Get-Credential).password
```
```
    Set-Content -Path "d:\umcerts\selfsigned.pfx" -Value $file.FileData =Encoding Byte
```

## Использование Центра администрирования Exchange для импорта сертификата

1.  В Центре администрирования Exchange последовательно выберите пункты **Серверы** \> **Сертификаты** \> **Дополнительные параметры**![Значок дополнительных параметров](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Значок дополнительных параметров"), а затем нажмите кнопку **Импортировать сертификат Exchange**.

2.  На странице **Импорт сертификата Exchange** в поле **Файл для импорта** введите путь к общей папке и имя файла сертификата. Если сертификат защищен паролем, введите его в поле **Пароль** и нажмите кнопку **Далее**.

3.  Нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"), чтобы выбрать серверы, к которым необходимо применить сертификат, и нажмите кнопку **ОК**. Чтобы удалить сервер из списка, последовательно нажмите кнопки **Удалить**![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\"") и **Готово**.

## Использование командной консоли для импорта сертификата

В этом примере после ввода имени пользователя и пароля импортируется сертификат из файла сертификата d:\\certificates\\exchange\\SelfSignedUMCert.pfx.

    Import-ExchangeCertificate -FileData ([Byte[]]$(Get-Content -Path d:\certificates\exchange\SelfSignedUMCert.pfx -Encoding Byte -ReadCount 0)) -Password:(Get-Credential).password

