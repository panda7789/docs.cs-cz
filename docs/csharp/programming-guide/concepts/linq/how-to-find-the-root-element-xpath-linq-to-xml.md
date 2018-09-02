---
title: 'Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a7c15c8eb688f70b2d1633fc5c094b02cc97031c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421019"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)
Toto téma ukazuje, jak získat kořenový element, jejichž výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Výraz XPath je:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá kořenový element.  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Viz také  
 [LINQ to XML pro uživatele jazyka XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
