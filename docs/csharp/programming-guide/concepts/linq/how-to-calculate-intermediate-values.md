---
title: Jak vypočítat mezilehlé hodnoty (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141445"
---
# <a name="how-to-calculate-intermediate-values-c"></a>Jak vypočítat mezilehlé hodnoty (C#)
Tento příklad ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběru.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Let` klauzuli.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Numerická data (LINQ to XML).](./sample-xml-file-numerical-data-linq-to-xml.md)  
  
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
 Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Numerická data v oboru názvů](./sample-xml-file-numerical-data-in-a-namespace.md).  
  
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
