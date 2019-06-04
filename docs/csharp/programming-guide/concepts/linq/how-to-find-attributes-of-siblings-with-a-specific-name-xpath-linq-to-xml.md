---
title: 'Postupy: Vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0c62ecb7660a012af556515ba5e7de330d5ab5e7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486790"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Postupy: Vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)
Toto téma ukazuje, jak najít všechny atributy na stejné úrovni kontextu uzlu. Pouze atributy s konkrétním názvem jsou vráceny v kolekci.  
  
 Výraz XPath je:  
  
 `../Book/@id`  
  
## <a name="example"></a>Příklad  
 V tomto příkladu nejdříve vyhledá `Book` elementu a najde všechny prvky na stejné úrovni s názvem `Book`a následně vyhledá všechny atributy s názvem `id`. Výsledkem je kolekce atributů.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  