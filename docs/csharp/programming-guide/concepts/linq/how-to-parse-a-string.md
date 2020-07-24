---
title: Postup analýzy řetězce (C#)
description: Naučte se analyzovat řetězec pro vytvoření stromu XML v jazyce C#. Naučte se, jak získat přístup ke konkrétním datům v analyzovaném kódu XML.
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: a4664e090b6a44c52c519e61b66ccdc5d59a71f1
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104806"
---
# <a name="how-to-parse-a-string-c"></a>Postup analýzy řetězce (C#)

Toto téma ukazuje, jak analyzovat řetězec pro vytvoření stromu XML v jazyce C#.

## <a name="example"></a>Příklad

Následující kód jazyka C# ukazuje, jak analyzovat řetězec XML:

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

Kořenový `Contacts` uzel má dva `Contact` uzly. Chcete-li získat přístup k určitým datům v analyzovaném kódu XML, použijte metodu [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , která v tomto případě vrátí podřízené prvky kořenového `Contacts` uzlu. Následující příklad vytiskne první `Contact` uzel do konzoly:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Viz také

- [Vyhledání elementu s konkrétním atributem (C#)](how-to-find-an-element-with-a-specific-attribute.md)
