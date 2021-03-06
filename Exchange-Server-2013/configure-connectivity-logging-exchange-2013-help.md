﻿---
title: 'Настройка ведения журнала подключений: Exchange 2013 Help'
TOCTitle: Настройка ведения журнала подключений
ms:assetid: 24e46a79-33ea-44e9-b03c-549db1c86a6f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996827(v=EXCHG.150)
ms:contentKeyID: 50487680
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка ведения журнала подключений

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2013-02-18_

При ведении журнала подключения записываются данные об операциях подключения для доставки исходящих сообщений из службы транспорта на сервер Exchange. При ведении журнала подключения записываются данные об источнике, назначении, количестве переданных сообщений и байт, а также данные об ошибках подключений.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 15 минут.

  - Записи "Служба транспорта", "Внешняя служба транспорта" и "Служба транспорта почтовых ящиков" Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Чтобы включить или выключить ведение журнала подключения или указать путь журнала подключения только для службы транспорта, можно воспользоваться Центром администрирования Exchange (EAC). Для всех остальных параметров ведения журнала подключения в других службах транспорта следует использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Использование EAC для настройки ведения журнала подключения в службе транспорта

1.  В Центре администрирования Exchange перейдите к разделу **Серверы** \> **Серверы**.

2.  Выберите необходимый сервер почтовых ящиков и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств сервера щелкните **Журналы транспорта**.

4.  В разделе **Журнал подключения** выполните одно из указанных ниже действий.
    
      - Чтобы отключить ведение журнала подключения на сервере, снимите флажок **Включить ведение журнала подключения**. Чтобы включить ведение журнала подключения на сервере, установите флажок.
    
      - **Путь журнала подключения** Указанное значение должно находиться на локальном сервере Exchange. Если папка не существует, она будет создана после нажатия кнопки **Сохранить**.
    
    Завершив настройку, нажмите кнопку **Сохранить**.

## Использование командной консоли для настройки ведения журнала подключения

Чтобы настроить ведение журнала подключения, выполните следующую команду.

    <Set-TransportService | Set-MailboxTransportService | Set-FrontEndTransportService> <ServerIdentity> -ConnectivityLogEnabled <$true | $false> -ConnectivityLogMaxAge <dd.hh:mm:ss> -ConnectivityLogMaxDirectorySize <Size> -ConnectivityLogMaxFileSize <Size> -ConnectivityLogPath <LocalFilePath>

В этом примере показана установка следующих параметров журнала подключения в службе транспорта на сервере почтовых ящиков с именем Mailbox01.

  -  Задает местоположение файлов журнала подключения — D:\\Hub Connectivity Log. Обратите внимание, что если папка не существует, она будет создана.

  -  Задает максимальный размер файла журнала подключения — 20 МБ.

  -  Задает максимальный размер каталога журнала подключения — 1,5 ГБ.

  -  Задает максимальный срок хранения файла журнала подключения — 45 дней.

<!-- end list -->

    Set-TransportService Mailbox01 -ConnectivityLogPath "D:\Hub Connectivity Log" -ConnectivityLogMaxFileSize 20MB -ConnectivityLogMaxDirectorySize 1.5GB -ConnectivityLogMaxAge 45.00:00:00

> [!NOTE]  
> <ul><li><p>Чтобы настроить параметры журнала подключения в службе транспорта почтовых ящиков на сервере почтовых ящиков, воспользуйтесь командлетом <strong>Set-MailboxTransportService</strong>. Чтобы настроить параметры журнала подключения во внешней службе транспорта на сервере клиентского доступа, воспользуйтесь командлетом <strong>Set-FrontEndTransportService</strong>.</p></li>
> <li><p>Установка для параметра <em>ConnectivityLogPath</em> значения <code>$null</code> отключает ведение журнала подключения. Однако если параметру <em>ConnectivityLogEnabled</em> задано значение <code>$true</code>, возникают ошибки журнала событий.</p></li>
> <li><p>Если для параметра <em>ConnectivityLogMaxAge</em> задано значение <code>00:00:00</code>, автоматическое удаление файлов журнала подключения по истечении срока их хранения не выполняется.</p></li>
</ul>


## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно настроили ведение журнала подключения, выполните следующие действия.

1.  В командной консоли выполните следующую команду:
    
        <Get-TransportService | Get-FrontEndTransportService | Get-MailboxTransportService> <ServerIdentity> | Format-List ConnectivityLog*

2.  Убедитесь, что отображаются значения, которые вы настроили.

