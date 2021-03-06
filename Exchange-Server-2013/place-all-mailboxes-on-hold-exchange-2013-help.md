﻿---
title: 'Применение функции хранения ко всем почтовым ящикам: Exchange 2013 Help'
TOCTitle: Применение функции хранения ко всем почтовым ящикам
ms:assetid: 4c141604-3210-44cc-b98e-f3e0f15613b8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn767952(v=EXCHG.150)
ms:contentKeyID: 62486264
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Применение функции хранения ко всем почтовым ящикам

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2017-01-18_

> [!NOTE]  
> Мы перенесли дату, до которой можно создавать удержания на месте в Exchange Online (в Office 365 и автономных планах Exchange Online), с 1 июля 2017 г. на более поздний срок. Но до конца года или в начале следующего этой возможности в Exchange Online не станет. В качестве альтернативы можно использовать <a href="https://go.microsoft.com/fwlink/?linkid=780738">дела обнаружения электронных данных</a> или <a href="https://go.microsoft.com/fwlink/?linkid=827811">политики хранения</a> в Центре безопасности и соответствия требованиям Office 365. После этого вы по-прежнему сможете изменять существующие удержания на месте и создавать новые в гибридных развертываниях Exchange Server 2013 и Exchange. И вы по-прежнему сможете помещать почтовые ящики на хранение для судебного разбирательства.


В вашей организации может понадобиться сохранить все данные почтового ящика на определенный период. Чтобы сделать это, используйте хранение для судебного разбирательства или хранение на месте. Когда вы примените к почтовому ящику функцию хранения для судебного разбирательства или хранения на месте, элементы почтового ящика, которые изменяются или окончательно удаляются, будут сохранены в папке "Элементы с возможностью восстановления". Дополнительные сведения см. в статье [Хранение на месте и хранение для судебного разбирательства](in-place-hold-and-litigation-hold-exchange-2013-help.md).

Прежде чем применять ко всем почтовым ящикам в организации эти функции, обратите внимание на следующее:

  - Если применить к почтовому ящику функцию хранения, она будет действовать и для содержимого архивного почтового ящика пользователя (если он включен).

  - Применение функции хранения ко всем почтовым ящикам в организации может существенно увеличить их размер. Выполняя развертывание Exchange Server 2013, планируйте достаточно места для хранения, чтобы соблюдать соответствующие требования вашей организации. [Ограничения на размер хранилища почтовых ящиков](https://go.microsoft.com/fwlink/?linkid=403645), указанные для пользователей в службе Exchange Online, зависят от лицензии пользователей на подписку.

  - Длительное хранение данных почтового ящика приведет к увеличению размера папки "Элементы с возможностью восстановления" в основном и архивном почтовых ящиках пользователя. Для этой папки размер хранилища предусмотрен отдельно, и потому увеличение количества элементов в ней не может привести к превышению ограничения для хранилища почтовых ящиков. В Exchange Server 2013 и Exchange Online ограничение хранилища по умолчанию для папки "Элементы с возможностью восстановления" составляет 30 ГБ.
    
      - В Exchange Online квота для папки "Элементы с возможностью восстановления" автоматически увеличивается до 100 ГБ при применении к почтовому ящику функции хранения.
    
      - В Exchange Server 2013 рекомендуем периодически проверять размер этой папки, чтобы не допустить превышения ограничения. Дополнительные сведения см. в статье [Папка "Элементы для восстановления"](recoverable-items-folder-exchange-2013-help.md).

## Что выбрать: хранение для судебного разбирательства или хранение на месте?

Ниже приведены некоторые факторы, которые следует учитывать при выборе функции удержания, которая будет использоваться для всех почтовых ящиков в организации.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Требуется...</th>
<th>Применение хранения для судебного разбирательства</th>
<th>Применение хранения на месте</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Использование Центра администрирования Exchange</p></td>
<td><p>Да</p>
<p>При настройке хранения для судебного разбирательства Центр администрирования Exchange лучше всего подходит для быстрых одноразовых действий с небольшим количеством почтовых ящиков. Чтобы задать хранение для судебного разбирательства для всех пользователей в организации, мы рекомендуем использовать командную консоль.</p></td>
<td><p>Да</p>
<p>Однако в Центре администрирования Exchange невозможно выбрать более 500 исходных почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>Использование командной консоли</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Применение функции хранения к более 10 000 почтовых ящиков</p></td>
<td><p>Да</p>
<p>Хранение для судебного разбирательства — это свойство почтового ящика. Вы можете поместить все почтовые ящики в организации на удержание с помощью командлета <strong>Set-Mailbox</strong>.</p></td>
<td><p>Да, используйте несколько объектов хранения на месте.</p>
<p>Для одного объекта хранения на месте вы можете указать до 10 000 почтовых ящиков с помощью групп рассылки. Чтобы применить функцию хранения к дополнительным почтовым ящикам, создайте другие объекты хранения. Это потребует дополнительных затрат на управление. Хранение для судебного разбирательства упрощает удержание большого количества почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>Применение функции хранения к нескольким почтовым ящикам течение различных сроков.</p></td>
<td><p>Да</p>
<p>Хранение для судебного разбирательства — это свойство почтового ящика. К каждому почтовому ящику (или наборам почтовых ящиков) вы можете применять функцию хранения в течение различных сроков.</p>
<p>В разделе Дополнительные сведения приведены примеры того, как с помощью свойств получателей в фильтре можно применить хранение для судебного разбирательства к подмножеству почтовых ящиков.</p></td>
<td><p>Да</p>
<p>Если вы создаете отдельные объекты хранения для тысячи почтовых ящиков, мы рекомендуем использовать хранение для судебного разбирательства. Если вы применяете функцию хранения для определенных событий, связанных с несколькими пользователями, используйте один объект хранения на месте для группы пользователей.</p>
<p>Мы не рекомендуем создавать отдельные объекты хранения на месте для каждого почтового ящика. Это приведет к созданию множества запросов на хранение на месте, которыми управлять сложнее, чем хранением для судебного разбирательства. Большое количество объектов хранения на месте также может привести к снижению производительности Центра администрирования Exchange при их обновлении, создании или изменении.</p></td>
</tr>
<tr class="odd">
<td><p>Автоматическое применение функции хранения к новым почтовым ящикам</p></td>
<td><p>Нет</p>
<p>После создания нового почтового ящика его необходимо поместить на хранение для судебного разбирательства. Для этого вы также можете запланировать выполнение команды или сценария с необходимой частотой.</p></td>
<td><p>Нет</p>
<p>Новый почтовый ящик необходимо добавить в объект хранения на месте, даже если при создании этого объекта была указана группа рассылки. Для этого вы также можете запланировать выполнение команды или сценария с необходимой частотой. Мы рекомендуем проверять с помощью сценария, достигнуто ли ограничение в размере 10 000 почтовых ящиков для объекта хранения на месте, а затем при необходимости создавать новый.</p></td>
</tr>
<tr class="even">
<td><p>Поставить на удержание все общедоступные папки</p></td>
<td><p>Нет</p>
<p>В Exchange Online хранение для судебного разбирательства в почтовом ящике общедоступной папки не поддерживается. Необходимо использовать удержание на месте.</p></td>
<td><p>Да</p></td>
</tr>
</tbody>
</table>


## Применение ко всем почтовым ящикам хранения для судебного разбирательства

С помощью командной консоли вы можете легко и быстро поместить все почтовые ящики на удержание на неопределенное время или указанный период. Эта команда применит функцию хранения ко всем почтовым ящикам на 2555 дней (примерно 7 лет).

    Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Set-Mailbox -LitigationHoldEnabled $true -LitigationHoldDuration 2555

В этом примере с помощью командлета [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\)) и фильтра получателей считывается список всех почтовых ящиков пользователей в организации, который затем передается командлету [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)), чтобы включить хранение для судебного разбирательства и указать его продолжительность. Дополнительные сведения см. в статье [Перевод почтового ящика в режим хранения для судебного разбирательства](place-a-mailbox-on-litigation-hold-exchange-2013-help.md).

## Применение хранения на месте ко всем почтовым ящикам

С помощью Центра администрирования Exchange вы можете выбрать до 500 почтовых ящиков и применить к ним функцию хранения. Дополнительные сведения см. в статье [Создание или удаление инцидента хранения на месте](create-or-remove-an-in-place-hold-exchange-2013-help.md).

> [!TIP]  
> Чтобы применить функцию хранения на месте к более чем 500 пользователям, воспользуйтесь командной консолью. См. статью <a href="https://technet.microsoft.com/ru-ru/library/dd298064(v=exchg.150)">New-MailboxSearch</a>.


## Дополнительные сведения

  - Когда вы помещаете все почтовые ящики в организации на удержание, функция хранения применяется только к почтовым ящикам, существующим на момент выполнения команды. Чтобы применить функцию хранения к почтовым ящикам, созданным позднее, запустите команду еще раз. Если вы часто создаете новые почтовые ящики, можно запланировать выполнение команды с необходимой частотой.

  - Помещение почтовых ящиков на хранение позволяет сохранить данные путем предотвращения удаления до того, как наступит указанный интервал времени, и сохранения исходной версии сообщения перед его изменением. При этом сообщения не удаляются автоматически по истечении заданного интервала времени. Сочетание судебного или временного удержания с политикой сохранения позволяет автоматически удалять сообщения по истечении заданного интервала времени, чтобы обеспечить соответствие требованиям организации по хранению электронной почты. Дополнительные сведения см. в разделе [Теги хранения и политики хранения](retention-tags-and-retention-policies-exchange-2013-help.md).

  - Команда PowerShell, используемая в этой статье для применения функции хранения для судебного разбирательства ко всем почтовым ящикам, использует фильтр получателей, который возвращает все почтовые ящики пользователей. Вы можете использовать другие свойства получателей, чтобы получить список определенных почтовых ящиков, который можно передать командлету **Set-Mailbox**, чтобы применить функцию хранения для судебного разбирательства к этим почтовым ящикам.
    
    Вот несколько примеров использования командлетов **Get-Mailbox** и **Get-Recipient** для получения подмножества пользователей на основе общих свойств пользователей или почтовых ящиков. В этих примерах предполагается, что соответствующие свойства почтовых ящиков (например, *CustomAttributeN* или *Department*) заполнены.
    
```
        Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'CustomAttribute15 -eq "OneYearLitigationHold"'
```
```    
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'Department -eq "HR"'
```
```    
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'PostalCode -eq "98052"'
```
```    
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'StateOrProvince -eq "WA"'
```
```    
        Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -ne "DiscoveryMailbox"}
```    
Вы можете использовать в фильтре другие свойства, чтобы включать и исключать почтовые ящики. Подробные сведения см. в статье [Фильтруемые свойства для параметра -Filter](https://technet.microsoft.com/ru-ru/library/bb738155\(v=exchg.150\)).

