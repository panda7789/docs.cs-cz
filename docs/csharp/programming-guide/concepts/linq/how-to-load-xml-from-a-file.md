---
title: Jak načíst XML ze souboru (C#)
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: f57d7a8375d04d1d7eda6d09aef81f42dd3e4b51
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345828"
---
# <a name="how-to-load-xml-from-a-file-c"></a>Jak načíst XML ze souboru (C#)
Toto téma ukazuje, jak načíst XML z identifikátoru URI pomocí metody <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst dokument XML ze souboru. Následující příklad načte soubor Books. XML a vytvoří výstup stromu XML do konzoly.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<Catalog>  
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
</Catalog>  
```  
  