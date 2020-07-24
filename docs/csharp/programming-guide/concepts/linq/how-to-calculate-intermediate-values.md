---
title: Jak vypočítat mezilehlé hodnoty (C#)
description: Tento LINQ to XML příklad v jazyce C# ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběr.
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103620"
---
# <a name="how-to-calculate-intermediate-values-c"></a>Jak vypočítat mezilehlé hodnoty (C#)
Tento příklad ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběr.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Let` klauzule.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data v oboru názvů](./sample-xml-file-numerical-data-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
