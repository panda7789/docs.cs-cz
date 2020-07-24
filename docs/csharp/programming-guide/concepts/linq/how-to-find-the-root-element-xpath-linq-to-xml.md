---
title: Jak najít kořenový element (XPath-LINQ to XML) (C#)
description: Tento příklad v jazyce C# porovnává XPath s LINQ to XML pro získání kořenového prvku pro ukázkový dokument XML.
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105188"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Jak najít kořenový element (XPath-LINQ to XML) (C#)
Toto téma ukazuje, jak získat kořenový prvek pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Výraz XPath je:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Příklad  
 Tento příklad najde kořenový element.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
Results are identical  
PurchaseOrders  
```  
