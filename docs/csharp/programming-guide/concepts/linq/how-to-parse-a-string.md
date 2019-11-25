---
title: 'Postupy: Analýza řetězce (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 086a4baecee9ee927b08d6da53d16324ef32e8a8
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140974"
---
# <a name="how-to-parse-a-string-c"></a>Postupy: Analýza řetězce (C#)

Toto téma ukazuje, jak analyzovat řetězec pro vytvoření stromu XML v C#.

## <a name="example"></a>Příklad

Následující C# kód ukazuje, jak analyzovat řetězec XML:

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

Uzel kořenového `Contacts` má dva uzly `Contact`. Chcete-li získat přístup k určitým datům v analyzovaném kódu XML, použijte metodu [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , která v tomto případě vrátí podřízené prvky kořenového uzlu `Contacts`. Následující příklad vytiskne první `Contact` uzel do konzoly:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Viz také:

- [Jak najít element s konkrétním atributem (C#)](how-to-find-an-element-with-a-specific-attribute.md)
