﻿---
title: 'Exchange 2013: настройка числа входящих вызовов на сервере почтовых ящиков'
TOCTitle: Настройте количество входящих вызовов на сервере почтовых ящиков
ms:assetid: 419e1de9-2bf8-48a8-824d-2a536b0a6d90
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997637(v=EXCHG.150)
ms:contentKeyID: 50556369
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Настройте количество входящих вызовов на сервере почтовых ящиков

 

_**Применимо к:** Exchange Server, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-02-23_

Вы можете настроить количество одновременных входящих подключений, которое может принять сервер почтовых ящиков с единой системой обмена сообщениями Microsoft Exchange. К таким подключениям относятся все входящие вызовы, в том числе голосовой доступ к Outlook, прием вызовов автоответчиком и автосекретарями, а также передача факсов. Увеличение количества одновременных подключений на сервере почтовых ящиков приводит к росту количества потребляемых системных ресурсов. Количество одновременных подключений особенно важно, если службы единой системы обмена сообщениями установлены на менее производительных компьютерах. Диапазон количества одновременных голосовых вызовов составляет от 0 до 200. Значением по умолчанию является 100.

Другие задачи, связанные с единой системой обмена сообщениями и серверами почтовых ящиков, см. в статье [Процедуры служб единой системы обмена СООБЩЕНИЯМИ](um-services-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Сервер почтовых ящиков (служба единой системы обмена сообщениями)" в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Убедитесь, что серверы клиентского доступа и почтовых ящиков установлены правильно.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что необходимо сделать?

## Настройка количества входящих вызовов на сервере почтовых ящиков с помощью Центра администрирования Exchange

1.  В Центре администрирования Exchange перейдите к разделу **Серверы** \> **Серверы**.

2.  Выберите из списка сервер Exchange, который необходимо изменить, и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Exchange Server** нажмите кнопку **Единая система обмена сообщениями**.

4.  В разделе **Параметры службы единой системы обмена сообщениями** в области **Максимально допустимое количество вызовов** введите число от 0 до 200 и нажмите **Сохранить**.

## Настройка количества входящих вызовов на сервере почтовых ящиков с помощью командной консоли

В этом примере показано, как установить значение 50 для количества входящих голосовых вызовов, вызовов голосового доступа к Outlook и передачи факсов, которое может принять сервер почтовых ящиков с именем `MyMailboxServer1`.

    Set-UMService -Identity MyMailboxServer1 -MaxCallsAllowed 50

