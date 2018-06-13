﻿---
title: 'Маршрутизация транспорта в гибридных развертываниях Exchange 2013 и Exchange 2010: Exchange 2013 Help'
TOCTitle: Маршрутизация транспорта в гибридных развертываниях Exchange 2013 и Exchange 2010
ms:assetid: 7346bff7-41e0-401c-bd31-34498561f4c4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn393964(v=EXCHG.150)
ms:contentKeyID: 59636089
ms.date: 01/11/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Маршрутизация транспорта в гибридных развертываниях Exchange 2013 и Exchange 2010

 

_**Применимо к:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Последнее изменение раздела:**2016-07-29_

В этом разделе рассматриваются варианты маршрутизации для входящих сообщений из Интернета и исходящие сообщения в Интернет.

<table>
<thead>
<tr class="header">
<th><img src="images/Dn151301.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Не размещайте между локальными серверами Exchange и Office 365 серверы, службы или устройства, которые обрабатывают или изменяют SMTP-трафик. Безопасность потока обработки почты между локальной организацией Exchange и Office 365 зависит от информации, которая содержится в отправляемых сообщениях. Поддерживаются брандмауэры, пропускающие SMTP-трафик через TCP-порт 25 без изменений. Когда сервер, служба или устройство обрабатывает сообщение, отправленное из организации Exchange в Office 365 или наоборот, эта информация удаляется. В этом случае сообщение больше не считается внутренним, и на него распространяются правила фильтрации нежелательной почты, транспорта и журнала, а также другие политики.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dn986544.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В примерах этого раздела не показано, как добавлять пограничные транспортных серверы в гибридное развертывание. Маршрутизация сообщений между локальной организацией, организацией Exchange Online и Интернетом с добавлением пограничного транспортного сервера не меняется. Изменяется только маршрутизация внутри локальной организации. Дополнительные сведения о добавлении пограничных транспортных серверов в гибридное развертывание см. в разделе <a href="edge-transport-servers-in-exchange-2013-exchange-2010-hybrid-deployments-exchange-2013-help.md">Пограничные транспортные серверы в гибридных развертываниях Exchange 2013 и Exchange 2010</a>.</td>
</tr>
</tbody>
</table>


## Входящие сообщения из Интернета

В рамках планирования и настройки гибридного развертывания необходимо определить, следует ли направлять все сообщения от отправителей в Интернете через организацию Exchange Online или через локальную организацию. Все сообщения от отправителей из Интернета сначала будут доставляться в выбранную организацию. Затем будет выполняться маршрутизация в соответствии с расположением почтового ящика получателя. Выбор маршрутизации сообщений через организацию Exchange Online или через локальную организацию зависит от различных факторов, в том числе от необходимости применять политики соответствия требованиям ко всем сообщениям, направляемым в обе организации, от количества почтовых ящиков в каждой организации и т. д.

Пути сообщений, отправляемых получателям в локальной организации и организации Exchange Online зависят от настроек конфигурации записи MX в гибридном развертывании. Рекомендуемый способ — настроить запись MX таким образом, чтобы она указывала на Exchange Online Protection (EOP) в Office 365, так как эта конфигурация обеспечивает наиболее точную фильтрацию нежелательной почты. Мастер гибридной конфигурации не настраивает маршрутизацию для входящих сообщений из Интернет, как для локальной организации, так и для организации Exchange Online. Для изменения способа доставки входящей почты из Интернета необходимо вручную настроить запись MX.

  - **Если изменить запись MX таким образом, чтобы она указывала на службу защиты Microsoft Exchange Online (EOP) в Office 365:** это рекомендуемая конфигурация для гибридных развертываний. Все сообщения, отправленные любому получателю в любой организации будут маршрутизироваться в первую очередь через организацию Exchange Online. Сообщение, адресованное получателю в локальной организации, будет вначале маршрутизироваться через организацию Exchange Online и затем доставляться получателю в локальной организации. Такой маршрут рекомендуется в случаях, когда в организации Exchange Online больше получателей, чем в локальной организации, и необходимо выполнять фильтрацию сообщений с помощью EOP. Эта конфигурация обеспечивает проверку и блокировку нежелательной почты службой Exchange Online Protection.

  - **Если запись MX будет по-прежнему указывать на локальную организацию:** все сообщения, отправляемые любому получателю в любой организации, сначала будут маршрутизироваться через локальную организацию. Сообщение, адресованное получателю в Exchange Online, сначала будет маршрутизироваться через локальную организацию, а затем доставляться получателю в Exchange Online. Такой маршрут удобен для организаций, в которых существующие политики соответствия требованиям предусматривают проверку входящих и исходящих сообщений организации системой ведения журналов. Если выбрать этот вариант, служба Exchange Online Protection не сможет эффективно проверять наличие сообщений нежелательной почты.

Дополнительные сведения см. в статье [Рекомендации по потоку обработки почты для Exchange Online и Office 365 (обзор)](https://technet.microsoft.com/ru-ru/library/jj937232\(v=exchg.150\)).

Прочтите раздел ниже, соответствующий вашему варианту маршрутизации сообщений от получателей в Интернете для получателей в локальной организации и в организации Exchange Online.

## Маршрутизация входящих сообщений из Интернета через организацию Exchange Online

Указанные ниже шаги и схемы иллюстрируют путь входящих сообщений Интернета, который будет осуществлен в гибридном развертывании, если MX-запись указывает на службу EOP в организации Office 365. Путь сообщения отличается в зависимости от того, была ли включена централизованная транспортировка почты.

<table>
<thead>
<tr class="header">
<th><img src="images/Dn151301.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Необходимо будет приобрести лицензии EOP для каждого локального почтового ящика, получающего сообщения, которые вначале доставляются в EOP, а затем маршрутизируются через организацию Exchange Online. Для получения дополнительных сведений свяжитесь с торговым посредником корпорации Майкрософт.</td>
</tr>
</tbody>
</table>


Если функция централизованной транспортировки почты *отключена* (конфигурация по умолчанию), входящие сообщения из Интернета маршрутизируются как в гибридном развертывании:

1.  Входящее сообщение от отправителя из Интернета пересылается получателям alexey@contoso.com и ivan@contoso.com. Почтовый ящик Алексея расположен на сервере почтовых ящиков Exchange 2010 в локальной организации. Почтовый ящик Ивана расположен в ExchangeOnline.

2.  Так как оба получателя имеют адреса с почтовым доменом contoso.com, а MX-запись для contoso.com указывает на EOP, то сообщение доставляется в EOP.

3.  EOP направляет сообщения для обоих получателей в ExchangeOnline.

4.  Exchange Online сканирует сообщения на наличие вирусов и выполняет поиск каждого из получателей. В ходе поиска определено, что почтовый ящик пользователя Chris расположен в локальной организации, тогда как почтовый ящик пользователя David находится в организации Exchange Online.

5.  Exchange Online разбивает сообщение на две копии. Одна копия сообщения отправляется на ящик пользователя David.

6.  Вторая копия отправляется из Exchange Online обратно в EOP.

7.  EOP направляет сообщение на серверы клиентского доступа Exchange 2013 в локальной организации.

8.  Сервер клиентского доступа Exchange 2013 отправляет сообщение через соединитель групп маршрутизации, настроенный между сервером Exchange 2013 и транспортным сервером-концентратором Exchange 2010.

9.  Сервер почтовых ящиков Exchange 2010 получает сообщение и доставляет его в почтовый ящик Алексея. В этом примере роли сервера клиентского доступа и сервера почтовых ящиков устанавливаются на одном и том же сервере Exchange 2013.

**Маршрутизация почты через организацию Exchange Online для локальных организаций и организаций Exchange Online с отключенной функцией централизованной транспортировки почты (конфигурация по умолчанию)**

![Получение входящих сообщений через EXO без централизованного транспорта](images/Dn393964.23b8c817-1bf1-4a00-b722-a78548c39cb0(EXCHG.150).png "Получение входящих сообщений через EXO без централизованного транспорта")

Если функция централизованной транспортировки почты *включена*, входящие сообщения из Интернета маршрутизируются как в гибридном развертывании:

1.  Входящее сообщение от отправителя из Интернета пересылается получателям alexey@contoso.com и ivan@contoso.com. Почтовый ящик Алексея расположен на сервере почтовых ящиков Exchange 2010 в локальной организации. Почтовый ящик Ивана расположен в ExchangeOnline.

2.  Так как оба получателя имеют адреса с почтовым доменом contoso.com, а MX-запись для contoso.com указывает на EOP, то сообщение доставляется в EOP и проверяется на наличие вирусов.

3.  Поскольку централизованная транспортировка почты включена, EOP направляет сообщения обоим получателям на локальный сервер клиентского доступа Exchange 2013.

4.  Сервер Exchange 2013 выполняет поиск каждого получателя. В ходе поиска определено, что почтовый ящик пользователя Chris расположен в локальной организации, тогда как почтовый ящик пользователя David находится в организации Exchange Online.

5.  Сервер Exchange 2013 разбивает сообщение на две копии. Одна копия сообщения доставляется в почтовый ящик Алексея на локальном сервере почтовых ящиков Exchange 2010.

6.  Вторая копия отправляется с сервера Exchange 2013 обратно в EOP.

7.  EOP направляет сообщение в Exchange Online.

8.  Exchange доставляет сообщение в почтовый ящик пользователя David. В этом примере роли сервера клиентского доступа и сервера почтовых ящиков устанавливаются на одном и том же сервере Exchange 2013.

**Маршрутизация почты через организацию Exchange Online для локальных организаций и организаций Exchange Online с включенной функцией централизованной транспортировки почты**

![Получение входящих сообщений через EXO с централизованным транспортом](images/Dn393964.8b664544-60d5-4251-90aa-d0797963889f(EXCHG.150).png "Получение входящих сообщений через EXO с централизованным транспортом")

## Маршрутизация входящих сообщений из Интернета через локальную организацию

Указанные ниже шаги и схемы иллюстрируют путь входящих сообщений Интернета, который будет осуществлен в гибридном развертывании, если MX-запись указывает на локальную организацию.

1.  Входящее сообщение от отправителя из Интернета пересылается получателям alexey@contoso.com и ivan@contoso.com. Почтовый ящик Алексея расположен на сервере почтовых ящиков Exchange 2010 в локальной организации. Почтовый ящик Ивана расположен в Exchange Online.

2.  Поскольку оба получателя имеют адреса электронной почты contoso.com, а запись MX для contoso.com указывает на локальную организацию, сообщение доставляется на транспортный сервер-концентратор Exchange 2010.

3.  Сервер почтовых ящиков Exchange 2010 выполняет поиск каждого получателя, используя локальный сервер глобального каталога. Через поиск в глобальном каталоге устанавливается, что почтовый ящик Алексея расположен на сервере почтовых ящиков Exchange 2010, в то время как почтовый ящик Ивана находится в организации Exchange Online и имеет гибридный адрес маршрутизации ivan@contoso.mail.onmicrosoft.com.

4.  Сервер почтовых ящиков Exchange 2010 разбивает сообщение на две копии. Одна копия сообщения отправляется на ящик Алексея.

5.  Вторая копия сообщения отправляется через соединитель групп маршрутизации, настроенный между сервером Exchange 2013 и сервером Exchange 2010.

6.  Сервер почтовых ящиков Exchange 2013 отправляет сообщение в EOP, используя соединитель отправки, настроенный на использование протокола TLS. EOP получает сообщения, отправленные в организацию Exchange Online.

7.  EOP отправляет сообщение в организацию Exchange Online, где оно проверяется на наличие вирусов и контекстно-зависимой нежелательной почты, а затем доставляется в почтовый ящик Ивана. В этом примере роли сервера клиентского доступа и сервера почтовых ящиков устанавливаются на одном и том же сервере Exchange 2013.

**Маршрутизация почты через локальную организацию для локальных организаций и организаций Exchange Online**

![Получение входящих сообщений через локальную систему](images/Dn393964.6fa63ea0-65f5-473a-b0e7-51a2e315286d(EXCHG.150).png "Получение входящих сообщений через локальную систему")

## Исходящие сообщения в Интернет

Помимо выбора способа маршрутизации входящих сообщений, адресованных получателям в имеющихся организациях, можно также определить, как будут маршрутизироваться исходящие сообщения от пользователей Exchange. При запуске мастера управления гибридной конфигурацией можно выбрать один из двух вариантов:

  - **Не включать централизованную транспортировку почты**   При выборе этого параметра, установленного в мастере гибридной конфигурации по умолчанию, исходящие сообщения, отправляемые из организации Exchange Online, направляются непосредственно в Интернет. Этот параметр следует использовать, если не требуется применять локальные политики соответствия требованиям или другие правила обработки к сообщениям, которые отправляются от пользователей в организации Exchange Online.

  - **Включить централизованную транспортировку почты**   При выборе этого параметра исходящие сообщения, отправляемые из организации Exchange Online, будут маршрутизироваться через локальную организацию. За исключением сообщений, отправляемых другим получателям в той же организации Exchange Online, все исходящие сообщения от пользователей в организации Exchange Online отправляются через локальную организацию. Это позволяет применить правила соответствия требованиям к этим сообщениям и любым другим процессам или требованиям, которые должны применяться ко всем получателям независимо от того, расположены ли они в организации Exchange или в локальной организации.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dn986544.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Централизованный почтовый транспорт рекомендуется только для организаций с определенными требованиями соблюдения транспорта. Стандартным организациям Exchange централизованный почтовый транспорт не рекомендуется.</td>
    </tr>
    </tbody>
    </table>


Сообщения от локальных пользователей всегда отправляются непосредственно получателям в Интернете с использованием DNS, независимо от варианта, выбранного в мастере управления гибридной конфигурацией.

Следующие шаги и схема описывают путь исходящих сообщений, отправляемых локальными пользователями.

1.  Алексей, имеющий почтовый ящик на локальном сервере почтовых ящиков Exchange 2010, отправляет сообщение внешнему получателю в Интернете по адресу maksim@cpandl.com.

2.  Транспортный сервер-концентратор Exchange 2010 отправляет сообщение на сервер почтовых ящиков Exchange 2010.

3.  Транспортный сервер-концентратор Exchange 2010 выполняет поиск записи MX для адреса cpandl.com и отправляет сообщение на почтовые серверы thecpandl.com, расположенные в Интернете.

**Сообщения от локальных отправителей получателям в Интернете**

![Отправка исходящей почты из локальной системы](images/Dn393964.fdad1c2d-03a9-496b-9c4f-9d791a4adc80(EXCHG.150).png "Отправка исходящей почты из локальной системы")

Прочтите раздел ниже, соответствующий вашему варианту маршрутизации сообщений от получателей в организации Exchange Online получателям в Интернете.

## Доставка сообщений, отправляемых из Exchange Online в Интернет, с помощью DNS (централизованный почтовый транспорт отключен)

Указанные ниже шаги и схемы иллюстрируют путь исходящих сообщений, отправленных пользователями Exchange Online пользователям в сети Интернет, который будет осуществлен, если в мастере гибридной конфигурации не был выбран параметр **Включить централизованную транспортировку почты**, что является параметром по умолчанию.

1.  Пользователь David, имеющий почтовый ящик в организации Exchange Online, отправляет сообщение внешнему получателю в Интернете по адресу erin@cpandl.com.

2.  Exchange Online проверяет сообщение на наличие вирусов и отправляет его в службу EOP Exchange Online.

3.  Служба EOP ищет запись MX для домена cpandl.com и отправляет сообщение на почтовые серверы cpandl.com, расположенные в Интернете.

**Отправка почты пользователей Exchange Online непосредственно в Интернет при отключенной функции централизованной транспортировки почты (конфигурация по умолчанию)**

![Отправка исходящей почты напрямую из Exchange Online](images/Dn393964.1f7743de-94ef-4d03-a1ed-682739546ad0(EXCHG.150).png "Отправка исходящей почты напрямую из Exchange Online")

## Отправка Интернет-сообщений из Exchange Online через локальную организацию (при включенной функции централизованной транспортировки почты)

Указанные ниже шаги и схемы иллюстрируют путь исходящих сообщений, отправленных пользователями Exchange Online пользователям в сети Интернет, который будет осуществлен, если в мастере гибридной конфигурации был выбран параметр **Включить централизованную транспортировку почты**.

1.  Пользователь David, имеющий почтовый ящик в организации Exchange Online, отправляет сообщение внешнему получателю в Интернете по адресу erin@cpandl.com.

2.  Exchange Online сканирует сообщение на наличие вирусов и отправляет сообщение в EOP.

3.  В службе EOP настроена отправка всех адресованных в Интернет сообщений на локальный сервер, поэтому сообщение маршрутизируется на сервер клиентского доступа Exchange 2013. Сообщение отправляется с помощью TLS.

4.  Сервер клиентского доступа Exchange 2013 осуществляет проверку на соответствие требованиям, наличие вирусов и выполняет другие процессы, настроенные администратором, для сообщения пользователя David.

5.  Сервер клиентского доступа Exchange 2013 отправляет сообщение на транспортный сервер-концентратор Exchange 2010. В этом примере роли сервера клиентского доступа и сервера почтовых ящиков устанавливаются на одном и том же сервере Exchange 2013.

6.  Транспортный сервер-концентратор Exchange 2010 выполняет поиск записи MX для адреса cpandl.com и отправляет сообщение на почтовые серверы cpandl.com, расположенные в Интернете.

**Почта от отправителей в Exchange Online маршрутизируется через локальную организацию при включенной функции централизованной транспортировки почты**

![Отправка исходящей почты для Exchange Online через локальную систему](images/Dn393964.b60237c7-fc7a-472a-a7cd-f7b228cd64e2(EXCHG.150).png "Отправка исходящей почты для Exchange Online через локальную систему")
