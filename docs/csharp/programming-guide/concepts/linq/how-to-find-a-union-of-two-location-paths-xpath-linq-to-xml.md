---
title: Jak najít sjednocení dvou cest umístění (XPath-LINQ to XML) (C#)
description: Naučte se najít sjednocení dvou cest k umístění XPath pomocí výrazu XPath. Zkontrolujte příklad kódu, který používá ukázkový soubor XML.
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 65b20fe25a0990fd82ce3bd08c3433499e728512
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303319"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Jak najít sjednocení dvou cest umístění (XPath-LINQ to XML) (C#)
XPath umožňuje najít sjednocení výsledků dvou cest umístění XPath.  
  
 Výraz XPath je:  
  
 `//Category|//Price`  
  
 Stejné výsledky můžete dosáhnout pomocí <xref:System.Linq.Enumerable.Concat%2A> standardního operátoru dotazu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou vyhledány všechny `Category` prvky a všechny `Price` prvky a zřetězeny do jedné kolekce. Všimněte si, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz volá <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> k řazení výsledků. Výsledky vyhodnocení výrazu XPath jsou také v pořadí dokumentů.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  