---
title: Jak najít uzly na stejné úrovni (XPath-LINQ to XML) (C#)
description: Tento příklad jazyka C# porovnává XPath s LINQ to XML pro vyhledání všech položek na stejné úrovni uzlu, který má konkrétní název.
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 2936fc4ad088580a9644f79f1797e679fe877e00
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105211"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a>Jak najít uzly na stejné úrovni (XPath-LINQ to XML) (C#)
Možná budete chtít najít všechny uzly na stejné úrovni, které mají konkrétní název. Výsledná kolekce může zahrnovat kontextový uzel, pokud má uzel kontextu také konkrétní název.  
  
 Výraz XPath je:  
  
 `../Book`  
  
## <a name="example"></a>Příklad  
 Tento příklad nejprve vyhledá `Book` prvek a poté vyhledá všechny prvky na stejné úrovni s názvem `Book` . Výsledná kolekce obsahuje kontextový uzel.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
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
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>  
</Book>  
```  
