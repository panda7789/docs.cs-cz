---
title: 'Postupy: Analýza řetězce (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: da1c9d2573ac09a9db7f87c619f67bf0b2fb23ba
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834181"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="3dd32-102">Postupy: Analýza řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="3dd32-102">How to: Parse a String (C#)</span></span>

<span data-ttu-id="3dd32-103">Toto téma ukazuje, jak analyzovat řetězec pro vytvoření stromu XML v C#.</span><span class="sxs-lookup"><span data-stu-id="3dd32-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="3dd32-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dd32-104">Example</span></span>

<span data-ttu-id="3dd32-105">Následující C# kód ukazuje, jak analyzovat řetězec XML:</span><span class="sxs-lookup"><span data-stu-id="3dd32-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="3dd32-106">Kořenový uzel `Contacts` má dva uzly `Contact`.</span><span class="sxs-lookup"><span data-stu-id="3dd32-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="3dd32-107">Chcete-li získat přístup k určitým datům v analyzovaném kódu XML, použijte metodu [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , která v tomto případě vrátí podřízené prvky uzlu root `Contacts`.</span><span class="sxs-lookup"><span data-stu-id="3dd32-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="3dd32-108">Následující příklad vytiskne první uzel `Contact` do konzoly:</span><span class="sxs-lookup"><span data-stu-id="3dd32-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```
