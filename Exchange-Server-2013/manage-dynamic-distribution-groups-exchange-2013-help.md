﻿---
title: 'Управление динамическими группами рассылки: Exchange 2013 Help'
TOCTitle: Управление динамическими группами рассылки
ms:assetid: 8ef85d0a-41df-4b5c-b8e7-ca8d09c048ca
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb123722(v=EXCHG.150)
ms:contentKeyID: 50487230
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.CreateDynamicGroupWizardForm.CreateDynamicGroupInformationWizardPage
ms.translationtype: HT
---

# Управление динамическими группами рассылки

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Динамические группы рассылки — это объекты групп Active Directory с включенной поддержкой почты, которые создаются для упрощения массовой отправки сообщений электронной почты и другой информации в пределах организации Exchange.

В отличие от обычных групп рассылки, которые содержат определенный набор членов, список членов для динамических групп рассылки рассчитывается при каждой отправке сообщения в группу в соответствии с определяемыми пользователем фильтрами и условиями. Если электронное сообщение отправляется динамической группе рассылки, оно доставляется всем получателям, соответствующим заданным для группы критериям, в организации.

> [!IMPORTANT]  
> В динамическую группу рассылки включается любой получатель из Active Directory, имеющий атрибуты, соответствующие применяемому фильтру. Если после изменения свойств получателя они начинают отвечать критериям фильтра, такой получатель может случайно стать членом группы и начать получать сообщения, отправляемые группе рассылки. Строгая и последовательная процедура подготовки учетной записи позволяет снизить вероятность возникновения такой ситуации.


## Что нужно знать перед началом работы?

  - Осталось времени до завершения: от 2 до 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Динамические группы рассылки" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что необходимо сделать?

## Создание динамической группы рассылки

## Использование EAC для создания динамической группы рассылки

1.  В EAC перейдите в раздел **Получатели** \> **Группы** \> **Создать** \> **Динамическая группа рассылки**.

2.  На странице **новой динамической группы рассылки** заполните следующие поля:
    
      - \* **Краткое имя**   Это поле используется для ввода краткого имени. Это имя отображается в общей адресной книге в строке "Кому" при отправке в эту группу электронного сообщения и в списке "Группы" в центре администрирования Exchange. Отображаемое имя обязательно и должно быть понятным, чтобы пользователи могли понять его назначение. Это имя также должно быть уникальным в лесу.
        
        > [!NOTE]  
        > Политика именования групп не применяется к динамической группе рассылки.
    
      - \* **Псевдоним**   Это поле используется для ввода псевдонима группы. Длина псевдонима не должна превышать 64 знака, и он должен быть уникальным в данном лесу. Когда пользователь вводит псевдоним в строку "Кому" электронного сообщения, он сопоставляется с кратким именем группы.
    
      - **Описание**   Это поле используется для описания группы, чтобы пользователи могли представить ее назначение. Это описание отображается в общей адресной книге.
    
      - **Подразделение**   Можно выбрать другое подразделение, кроме указанного по умолчанию (которое расположено в области получателя). Если область получателей установлена на уровне леса, то значение по умолчанию настроено в контейнере пользователей в домене Active Directory, содержащем компьютер под управлением центра администрирования Exchange. Если область получателей настроена на определенный домен, то контейнер пользователей в этом домене выбирается по умолчанию. Если в качестве области получателей задано определенное подразделение организации, то оно выбирается по умолчанию.
        
        Нажмите кнопку **Обзор**, чтобы выбрать другое подразделение. В этом диалоговом окне отображаются все подразделения в лесу, которые находятся внутри определенной области. Выберите нужное подразделение и нажмите кнопку **ОК**.
    
      - **Владелец**   Владельца для динамической группы рассылки указывать необязательно. В число владельцев можно добавлять других пользователей, нажав **Обзор** и выбрав пользователей из списка.

3.  Раздел **Участники** используется для указания типов получателей группы и задания правил, которые будут определять членство. Выберите одно из приведенных ниже значений.
    
      - **Все типы получателей**   Выберите этот параметр для отправки сообщений, которые соответствуют условиям, определенным для этой группы, всем типам получателей.
    
      - **Только следующие типы получателей**   Сообщения, которые соответствуют условиям, определенным для данной группы, будут отправляться следующим типам получателей:
        
          - **Пользователи с почтовыми ящиками Exchange**   Установите этот флажок, чтобы включить пользователей, которые имеют почтовые ящики Exchange. К пользователям с почтовыми ящиками Exchange относятся пользователи, имеющие учетную запись домена пользователя и почтовый ящик в организации Exchange.
        
          - **Пользователи с внешними адресами электронной почты**   Установите этот флажок, чтобы добавить пользователей с внешними адресами электронной почты. Пользователи с внешними учетными записями электронной почты имеют учетные записи домена Active Directory, но используют учетные записи электронной почты, которые являются внешними для организации. Это позволяет включать их в глобальный список адресов (GAL) и добавлять в списки рассылки.
        
          - **Почтовые ящики ресурса**   Установите этот флажок, чтобы добавить почтовые ящики ресурса Exchange. Почтовые ящики ресурсов позволяют администрировать ресурсы компании, например, конференц-зал или транспортное средство компании, через почтовый ящик.
        
          - **Контакты с внешними адресами электронной почты**   Установите этот флажок, чтобы добавить пользователей с внешними адресами электронной почты. Контакты с внешними адресами электронной почты не имеют учетных записей домена Active Directory, но используют внешние адреса электронной почты, доступные в глобальном списке адресов.
        
          - **Группы с включенной поддержкой почты**   Установите этот флажок, чтобы добавить группы безопасности или группы рассылки с включенной поддержкой почты. Группы с включенной поддержкой почты подобны группам рассылки. Сообщения электронной почты, отправленные на учетную запись группы с включенной поддержкой почты, будут доставлены нескольким получателям.

4.  Щелкните **Добавить правило**, чтобы определить условия членства в этой группе.

5.  Выберите один из следующих атрибутов получателя из раскрывающегося списка и введите соответствующее значение. Если значение для выбранного атрибута соответствует заданному значению, получатель получает сообщение, отправленное в эту группу.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Атрибут</th>
    <th>Отправить сообщение получателю, если...</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Контейнер получателей</strong></p></td>
    <td><p>Объект получателя находится в указанном домене или подразделении.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Область, край;</strong></p></td>
    <td><p>Указанное значение соответствует свойству области или краю получателя.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Company</strong></p></td>
    <td><p>Указанное значение соответствует свойству организации получателя.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Department</strong></p></td>
    <td><p>Указанное значение соответствует свойству отдела получателя.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Пользовательский атрибут N</strong> (где N — это число от 1 до 15)</p></td>
    <td><p>Указанное значение соответствует свойству CustomAttributeN получателя.</p></td>
    </tr>
    </tbody>
    </table>
    
    > [!IMPORTANT]  
    > Значения, вводимые для выбранного атрибута, должны точно совпадать со значениями, отображаемыми в свойствах получателя. Например, если ввести <strong>Вашингтон</strong> в поле <strong>Область или край</strong>, но значение свойства получателя равно <strong>WA</strong>, условие не будет соблюдаться. Кроме того, в текстовых задаваемых значениях не учитывается регистр. Например, если указать <strong>Contoso</strong> для атрибута <strong>Организация</strong>, сообщения будут отправлены получателю и в том случае, если задано значение <strong>contoso</strong>.


6.  В окне **Укажите слова или фразы** введите значение в текстовом поле. Нажмите кнопку **Добавить**, а затем — кнопку **ОК**.

7.  Чтобы добавить правило для определения условий членства, щелкните **Добавить правило** под предыдущим правилом.
    
    > [!IMPORTANT]  
    > Если добавлено несколько правил, определяющих членство, получатель должны соответствовать условиям каждого правила для получения сообщений, отправляемых группе. Другими словами, правила связаны логическим оператором <strong>И</strong>.


8.  Закончив, щелкните **Сохранить** для создания динамической группы рассылки.

> [!NOTE]  
> Если требуется задать правила для атрибутов, недоступных в EAC, необходимо использовать командную консоль Exchange для создания динамической группы рассылки. Необходимо учитывать, что управление параметрами фильтра и условий для динамических групп рассылки с настраиваемыми фильтрами получателей выполняется только с помощью командной консоли Exchange. Пример создания динамической группы рассылки с пользовательским запросом см. в следующем разделе по использованию командной консоли Exchange для создания динамической группы рассылки.


## Использование консоли для создания динамической группы рассылки

В этом примере создается динамическая группа рассылки "Mailbox Users DDG", в которую входят только пользователи почтовых ящиков.

    New-DynamicDistributionGroup -IncludedRecipients MailboxUsers -Name "Mailbox Users DDG" -OrganizationalUnit Users

В этом примере создается динамическая группа рассылки с настраиваемым фильтром получателей. Динамическая группа рассылки включает в себя всех пользователей почтовых ящиков на сервере Server1:

    New-DynamicDistributionGroup -Name "Mailbox Users on Server1" -OrganizationalUnit Users -RecipientFilter {((RecipientTypeDetails -eq 'UserMailbox' -and ServerName -eq 'Server1'))}

В этом примере создается динамическая группа рассылки с настраиваемым фильтром получателей. Динамическая группа рассылки включает в себя всех пользователей почтовых ящиков, которые имеют значение"FullTimeEmployee"в свойстве **CustomAttribute10**.

    New-DynamicDistributionGroup -Name "Full Time Employees" -RecipientFilter {(RecipientTypeDetails -eq 'UserMailbox') -and (CustomAttribute10 -eq 'FullTimeEmployee')}

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-DynamicDistributionGroup](https://technet.microsoft.com/ru-ru/library/bb125127\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в успешном создании динамической группы рассылки, выполните одно из следующих действий:

  - В центре администрирования Exchange последовательно выберите пункты **Получатели** \> **Группы**. В списке групп отображается новая динамическая группа рассылки. В разделе **Тип группы** указано **Динамическая группа рассылки**.

  - В командной консоли Exchange выполните следующую команду, чтобы отобразить информацию о новой динамической группе рассылки.
    
        Get-DynamicDistributionGroup | FL Name,RecipientTypeDetails,RecipientFilter,PrimarySmtpAddress

## Изменение свойств динамической группы рассылки

## Использование EAC для изменения свойств динамической группы рассылки

1.  В центре администрирования Exchange последовательно выберите пункты **Получатели** \> **Группы**.

2.  В списке групп выберите динамическую группу рассылки, которую нужно просмотреть или изменить, а затем нажмите **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств группы щелкните один из следующих разделов, чтобы просмотреть или изменить свойства.
    
      - Общие
    
      - Владение
    
      - Членство
    
      - Управление доставкой
    
      - Утверждение сообщения
    
      - Параметры электронной почты
    
      - Подсказка
    
      - Делегирование группы

## Общие

Этот раздел используется для просмотра или изменения базовых сведений о группе.

  - \* **Отображаемое имя**.   Это имя будет отображаться в адресной книге, в полях электронного письма "Кому", при отправке в эту группу электронного сообщения и в списке "Группы". Отображаемое имя обязательно и должно быть понятным, чтобы пользователи могли понять его назначение. Кроме того, оно должно быть уникальным в пределах домена.

  - \* **Псевдоним**   Это часть адреса электронной почты слева от знака @. Если изменить псевдоним, основной адрес SMTP группы также изменится и будет содержать новый псевдоним. Кроме того, адрес электронной почты с предыдущим псевдонимом сохранится в качестве прокси-адреса группы.

  - **Описание**   Это поле используется для описания группы, чтобы пользователи могли представить ее назначение. Это описание отображается в адресной книге на панели подробностей в центре администрирования Exchange.

  - **Скрыть эту группу в списках адресов**   Установите этот флажок, если пользователи не должны видеть эту группу в адресной книге. Чтобы отправить электронное сообщение этой группе, отправитель должен ввести псевдоним группы или адрес электронной почты в строки "Кому" или "Копия" .

  - **Подразделение**   В этом поле только для чтения указано подразделение, в состав которого входит группа рассылки. Необходимо использовать оснастку "Пользователи и компьютеры Active Directory", чтобы переместить группу в другое подразделение.

## Собственность

Этот раздел используется для назначения владельцев группы. Динамическая группа рассылки может иметь только одного владельца. Владелец группы отображается на вкладке **Управляется** объекта в разделе "Active Directory — пользователи и компьютеры".

В число владельцев можно добавлять других пользователей, нажав **Обзор** и выбрав пользователей из списка. Чтобы удалить владельца, выберите команду **Очистить**, а затем — **Сохранить**![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\"").

## Членство

Используйте этот раздел, чтобы изменить условия, определяющие состав группы. Можно удалить или изменить существующие правила членства и добавить новые правила. Процедур, рассказывающие о том, как это сделать, см. в разделе Использование EAC для создания динамической группы рассылки в описании настройки членства при использовании EAC для создания новой динамической группы рассылки.

## Управление доставкой

В этом разделе можно определить, кто может отправлять почту в эту группу.

  - **Отправители только в этой организации**.   Выберите этот параметр, чтобы разрешить отправлять сообщения в данную группу только отправителям внутри организации. Это означает, что если кто-то снаружи организации отправляет сообщение электронной почты в эту группу рассылки, оно отклоняется. Это настройка по умолчанию.

  - **Отправители из этой организации и за ее пределами**.   Выберите этот параметр, чтобы разрешить всем отправлять сообщения в данную группу.
    
    Можно дополнительно ограничить круг пользователей, имеющих право отправлять сообщения в эту группу, указав только определенных отправителей. Нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"), а затем выберите одного или нескольких получателей. Если в этот список будут добавлены отправители, они станут единственными пользователями, которые будут иметь право на отправку сообщений в эту группу. Сообщения электронной почты, отправленные кем-либо, не содержащимся в этом списке, будут отклоняться.
    
    Чтобы удалить пользователя или группу из этого списка, выберите их в списке и нажмите кнопку **Удалить**![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\"").
    
    > [!IMPORTANT]  
    > Если настроить эту группу так, чтобы разрешить отправлять сообщения в эту группу только для отправителей внутри организации, письмо, отправленное от почтового контакта, будет отклонено, даже если он добавлен в этот список.


## Утверждение сообщений

В этом разделе можно установить параметры изменения группы. Модераторы утверждают или отклоняют отправленные в группу сообщения перед их доставкой членам группы.

  - **Сообщения, отправляемые этой группе, должны быть подтверждены модератором.** По умолчанию этот флажок не установлен. Если установить этот флажок, входящие сообщения перед доставкой будут проверяться модераторами группы. Модераторы группы могут утвердить или отклонить входящее сообщение.

  - **Модераторы группы.** Чтобы добавить модераторов группы, нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"). Чтобы удалить модератора, выберите его и нажмите кнопку **Удалить**![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\""). Если установлен флажок "Сообщения, отправляемые в эту группу, должны утверждаться модератором", а модератор не выбран, то сообщения будут отправляться на утверждение владельцам группы.

  - **Отправители, чьи сообщения не требуют утверждения**    Чтобы добавить пользователей или группы, чьи сообщения не требуют утверждения в данной группе, нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"). Чтобы удалить пользователя или группу, выберите соответствующий элемент и нажмите кнопку **Удалить**![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\"").

  - **Выберите уведомления модерирования.** В этом разделе можно указать, каким образом уведомлять пользователей об утверждении сообщений.
    
      - **Уведомлять всех отправителей о том, что их сообщения не утверждены**   Это значение по умолчанию. Все отправители, которые находятся внутри и вне организации, будут уведомляться в том случае, если их сообщения не были утверждены.
    
      - **Оповестите отправителей организации в том случае, если их сообщения не одобрены**   Если выбран этот параметр, уведомление о том, что отправленное в группу сообщение не утверждено модератором, получают только пользователи и группы в организации.
    
      - **Не уведомлять о неутвержденных сообщениях**   Если выбран этот параметр, то уведомления о том, что сообщение не утверждено модераторами группы, не отправляются.

## Параметры электронной почты

Этот раздел используется для просмотра и изменения адресов электронной почты, связанных с группой. Он включает основные адреса SMTP группы и любые связанные прокси-адреса. Основной адрес SMTP (также известный как *адрес ответа*) отображается жирным шрифтом в списке адресов и прописными буквами **SMTP** в столбце **Тип**.

  - **Добавить.** Нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"), чтобы добавить новый адрес электронной почты для данного почтового ящика. Выберите один из следующих типов адресов:
    
      - **SMTP.** Это тип адреса по умолчанию. Нажмите эту кнопку, а затем введите новый адрес SMTP в поле **\*Адрес электронной почты**.
        
        > [!NOTE]  
        > Чтобы новый адрес был основным адресом SMTP группы, установите флажок в поле <strong>Сделать этот адрес адресом ответа</strong>.
    
      - **Настраиваемый тип адреса**   Нажмите эту кнопку и введите один из поддерживаемых типов адреса электронной почты, не являющихся адресом SMTP, в поле \* **Адрес электронной почты**.
        
        > [!NOTE]  
        > В системе Exchange не выполняется проверка правильности формата настраиваемых адресов (за исключением адресов X.400). Убедитесь, что указанный настраиваемый адрес соответствует требованиям формата для этого типа адреса.


  - **Изменить**   Чтобы изменить адрес электронной почты, связанный с группой, выберите его в списке и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").
    
    > [!NOTE]  
    > Чтобы сделать существующий адрес основным адресом SMTP группы, установите флажок в поле <strong>Сделать этот адрес адресом ответа</strong>.


  - **Удалить**   Чтобы удалить адрес электронной почты, связанный с группой, выберите его в списке и нажмите кнопку **Удалить**![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\"").

  - **Автоматически обновлять адреса электронной почты на основе политики адресов электронной почты, которая применяется к этому получателю**   Установите этот флажок, чтобы адреса электронной почты получателей автоматически обновлялись на основе изменений политики адресов электронной почты организации. По умолчанию этот флажок установлен.

## Подсказка

Используйте этот раздел для добавления подсказок, предупреждающих пользователей о возможных проблемах перед отправкой сообщения определенной группе. Подсказка — это текст, который отображается на панели информации при добавлении этой группы в строки "Кому", "Копия" и "СК" нового сообщения электронной почты. Например, можно добавить подсказку для больших аудиторий, чтобы предупредить возможных отправителей о том, что сообщение отправится большому числу получателей.

> [!NOTE]  
> Подсказки могут содержать HTML-теги, но сценарии не допускаются. Длина пользовательской подсказки не должна превышать 175 отображаемых символов. HTML-теги при этом не учитываются.


## Делегирование группы

Этот раздел используется для назначения разрешений пользователю (известному как *представитель* ), чтобы разрешить ему отправлять сообщения в качестве группы или от ее имени. Можно назначать следующие разрешения:

  - **Отправить как**   Это разрешение позволяет представителю отправлять сообщения в качестве группы. После того, как разрешение будет назначено, представитель сможет добавить группу в строку **От**, чтобы указать, что сообщение было отправлено группой.

  - **Отправить от имени**   Это разрешение также позволяет представителю отправлять сообщения от имени группы. После назначения этого разрешения делегат может добавить группу в строку **От**. Это сообщение отобразится как отправленное группой, и в нем будет сообщаться, что оно было отправлено представителем от имени группы.

Для назначения разрешений представителям нажмите кнопку **Добавить** под соответствующим разрешением, чтобы открыть страницу **Выбрать получателя**, в которой отображается список всех получателей в организации Exchange, которым можно назначить разрешение. Выберите нужных получателей, добавьте их в список и нажмите кнопку **OK**. Чтобы найти определенного получателя, введите имя получателя в поле поиска и нажмите кнопку **Поиск**.

## Использование командной консоли для настройки свойств динамической группы рассылки

Используйте командлеты **Get-DynamicDistributionGroup** и **Set-DynamicDistributionGroup** для просмотра и изменения свойств динамических групп рассылки. Преимущества использования командной консоли — возможность изменения свойств, которые отсутствуют в EAC, и возможность изменять свойства для нескольких групп. Дополнительные сведения о том, какие параметры соответствуют свойствам групп рассылки, см. в следующих разделах:

  - [Get-DynamicDistributionGroup](https://technet.microsoft.com/ru-ru/library/bb124762\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/ru-ru/library/bb123796\(v=exchg.150\))

Ниже приведено несколько примеров использования командной консоли Exchange для изменения свойств динамической группы рассылки.

В этом примере изменяются следующие параметры для всех динамических групп рассылки в организации:

  - Скрыть все динамические группы рассылки из адресной книги

  - Задать максимальный размер сообщений, отправляемых в группу, как 5 МБ

  - Включить модерацию

  - Назначить администратора модератором группы

<!-- end list -->

    Get-DynamicDistributionGroup -ResultSize unlimited | Set-DynamicDistributionGroup -HiddenFromAddressListsEnabled $true -MaxReceiveSize 5MB -ModerationEnabled $true -ModeratedBy administrator

Этот пример добавляет адрес электронной почты SMTP-прокси, Seattle.Employees@contoso.com, в группу всех сотрудников.

    Set-DynamicDistributionGroup -Identity "All Employees" -EmailAddresses SMTP:All.Employees@contoso.com, smtp:Seattle.Employees@contoso.com

## Как проверить, что все получилось?

Чтобы убедиться в том, что свойства динамической группы рассылки успешно изменены, выполните следующие действия:

  - Чтобы просмотреть изменения свойств или функций, в центре администрирования Exchange выберите группу и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования"). В зависимости от свойства, которое было изменено, оно может отображаться в панели подробностей выбранной группы.

  - Используйте командлет **Get-DynamicDistributionGroup** в консоли для проверки изменений. Одним из преимуществ использования командной консоли является возможность просмотреть несколько свойств для нескольких групп. В первом примере следует выполнить следующую команду, чтобы проверить новые значения.
    
        Get-DynamicDistributionGroup -ResultSize unlimited | fl Name,HiddenFromAddressListsEnabled,MaxReceiveSize,ModerationEnabled,ModeratedBy
    
    Чтобы увидеть указанный выше пример, в котором изменяются пределы сообщения, выполните эту команду.
    
        Get-Mailbox -OrganizationalUnit "Marketing" | fl Name,IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults

