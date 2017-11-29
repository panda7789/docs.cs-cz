---
title: "Postupy: projektu anonymní typ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b383b0a7e0fc0aa22bdcc8ed87628947858986da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Postupy: projektu anonymní typ (Visual Basic)
V některých případech můžete chtít projektu dotaz pro nový typ, i když víte, že použijete tento typ se pouze na krátkou dobu. Je velké množství práce navíc k vytvoření nového typu jenom pro použití v projekci. V takovém případě má efektivnější přístup projekt anonymního typu. Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt třídy, bez nutnosti poskytnutí název třídy.  
  
 Anonymní typy jsou implementace C# matematickém koncept *řazené kolekce členů*. Matematický výraz řazené kolekce členů, pochází z pořadí jednoho, double, triple, čtyřikrát, pětkrát, n řazené kolekce členů. Odkazuje na konečné pořadí objektů, každý z konkrétního typu. To se někdy říká seznam dvojic název hodnota. Například obsah adresy [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) dokumentu XML může být vyjádřena takto:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Když vytvoříte instanci anonymního typu, je vhodné si ho představit jako vytváření pořadí n řazené kolekce členů. Pokud píšete dotaz, který vytvoří řazené kolekce členů v `Select` klauzule, dotaz vrátí `IEnumerable` řazené kolekce členů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Select` klauzule projekty anonymního typu. V příkladu se pak použije `Dim` vytvořit `IEnumerable` objektu. V rámci `For Each` smyčky, proměnné iterace stane instanci anonymního typu vytvořen ve výrazu dotazu.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Viz také  
 [Projekce a transformace (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
