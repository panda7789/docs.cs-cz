---
title: Jak najít kořenový element (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345952"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Jak najít kořenový element (XPath-LINQ to XML) (C#)
Toto téma ukazuje, jak získat kořenový prvek pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
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
