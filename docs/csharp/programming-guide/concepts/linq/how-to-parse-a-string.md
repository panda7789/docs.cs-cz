---
title: Jak analyzovat řetězec (C#)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345813"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="95a12-102">Jak analyzovat řetězec (C#)</span><span class="sxs-lookup"><span data-stu-id="95a12-102">How to parse a string (C#)</span></span>

<span data-ttu-id="95a12-103">Toto téma ukazuje, jak analyzovat řetězec k vytvoření stromu XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="95a12-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="95a12-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="95a12-104">Example</span></span>

<span data-ttu-id="95a12-105">Následující kód jazyka C# ukazuje, jak analyzovat řetězec XML:</span><span class="sxs-lookup"><span data-stu-id="95a12-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="95a12-106">Kořenový `Contacts` uzel má `Contact` dva uzly.</span><span class="sxs-lookup"><span data-stu-id="95a12-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="95a12-107">Chcete-li získat přístup k některým konkrétním datům v analyzovaném XML, použijte metodu [XElement.Elements(),](xref:System.Xml.Linq.XContainer.Elements) která v tomto případě vrátí podřízené prvky kořenového `Contacts` uzlu.</span><span class="sxs-lookup"><span data-stu-id="95a12-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="95a12-108">Následující příklad vytiskne první `Contact` uzel do konzoly:</span><span class="sxs-lookup"><span data-stu-id="95a12-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="95a12-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="95a12-109">See also</span></span>

- [<span data-ttu-id="95a12-110">Jak najít prvek s určitým atributem (C#)</span><span class="sxs-lookup"><span data-stu-id="95a12-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
