---
title: Jak najít atributy na stejné úrovni s určitým názvem (XPath-LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 331e1a7f432f4d06b697180b1594106ec6842c9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169256"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Jak najít atributy na stejné úrovni s určitým názvem (XPath-LINQ na XML) (C#)
Toto téma ukazuje, jak najít všechny atributy na stejné úrovni kontextového uzlu. V kolekci jsou vráceny pouze atributy s určitým názvem.  
  
 Výraz XPath je:  
  
 `../Book/@id`  
  
## <a name="example"></a>Příklad  
 Tento příklad nejprve `Book` vyhledá prvek a potom `Book`vyhledá všechny prvky `id`na stejné úrovni s názvem a potom vyhledá všechny atributy s názvem . Výsledkem je kolekce atributů.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML).](./sample-xml-file-books-linq-to-xml.md)  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  