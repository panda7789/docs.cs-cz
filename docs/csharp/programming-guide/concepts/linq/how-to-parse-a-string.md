---
title: "Postupy: Analýza řetězců (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e09885b00830f319a829e900f33927498df0e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="0a494-102">Postupy: Analýza řetězců (C#)</span><span class="sxs-lookup"><span data-stu-id="0a494-102">How to: Parse a String (C#)</span></span>
<span data-ttu-id="0a494-103">Toto téma ukazuje, jak analyzovat řetězec k vytvoření strom XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="0a494-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a494-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a494-104">Example</span></span>  
 <span data-ttu-id="0a494-105">Následující kód C# ukazuje, jak analyzovat řetězec.</span><span class="sxs-lookup"><span data-stu-id="0a494-105">The following C# code shows how to parse a string.</span></span>  
  
```csharp  
XElement contacts = XElement.Parse(  
    @"<Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type=""home"">206-555-0144</Phone>  
            <Phone type=""work"">425-555-0145</Phone>  
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
  
## <a name="see-also"></a><span data-ttu-id="0a494-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a494-106">See Also</span></span>  
 [<span data-ttu-id="0a494-107">Analýza kódu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0a494-107">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
