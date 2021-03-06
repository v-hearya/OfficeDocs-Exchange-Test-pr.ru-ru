﻿---
title: 'Политики почтовых ящиков единой системы обмена сообщениями: Exchange 2013 Help'
TOCTitle: Политики почтовых ящиков единой системы обмена сообщениями
ms:assetid: dfae629e-ee89-4494-a3ed-9655b67eb87e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124909(v=EXCHG.150)
ms:contentKeyID: 50556495
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Политики почтовых ящиков единой системы обмена сообщениями

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2012-11-15_

Политики почтовых ящиков единой системы обмена сообщениями необходимы при включении для пользователей поддержки единой системы обмена сообщениями. Политики почтовых ящиков единой системы обмена сообщениями создаются для применения стандартного набора политик или параметров безопасности к набору почтовых ящиков пользователей голосовой почты. Политики почтовых ящиков единой системы обмена сообщениями используются для указания следующих параметров единой системы обмена сообщениями:

  - политики ПИН-кодов

  - ограничения набора номеров

  - другие общие свойства политик почтовых ящиков единой системы обмена сообщениями

Например, можно создать политику почтового ящика единой системы обмена сообщениями, чтобы повысить уровень безопасности ПИН-кода за счет уменьшения максимального числа неудачных попыток входа в систему для определенной группы пользователей единой системы обмена сообщениями, таких как руководители.

## Политики почтовых ящиков единой системы обмена сообщениями

Хотя бы одну политику почтовых ящиков следует создать для того, чтобы можно было включить для пользователей поддержку единой системы обмена сообщениями. Можно создать дополнительные политики почтовых ящиков единой системы обмена сообщениями, чтобы применить общий набор параметров для группы пользователей.

Политики почтовых ящиков единой системы обмена сообщениями создаются с помощью командной консоли Exchange или центра администрирования Exchange (EAC). По умолчанию отдельная политика почтовых ящиков единой системы обмена сообщениями создается при каждом создании абонентской группы единой системы обмена сообщениями. Новая политика почтовых ящиков единой системы обмена сообщениями автоматически связывается с абонентской группой, и часть имени абонентской группы включается в отображаемое имя этой политики почтовых ящиков. Вы можете изменить эту политику почтовых ящиков единой системы обмена сообщениями по умолчанию.

С одной политикой почтовых ящиков единой системы обмена сообщениями можно связать нескольких пользователей, для которых включена поддержка единой системы обмена сообщениями. Каждый почтовый ящик пользователя с поддержкой единой системы обмена сообщениями должен быть сопоставлен с отдельной политикой почтовых ящиков системы. Это позволяет управлять параметрами безопасности ПИН-кода, такими как минимальное число цифр в ПИН-коде или максимальное число неудачных попыток входа в систему. Это касается пользователей с включенной поддержкой единой системы обмена сообщениями, сопоставленных с политикой почтовых ящиков системы. Можно также управлять параметрами текста сообщения или ограничениями набора номеров для тех же почтовых ящиков с включенной поддержкой единой системы обмена сообщениями.

