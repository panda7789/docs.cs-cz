---
title: Jak vytvořit strom z XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 9ead6352112d9e1b56bd70699c90133e432f96b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169269"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Jak vytvořit strom z XmlReader (C#)
Toto téma ukazuje, jak vytvořit <xref:System.Xml.XmlReader>strom XML přímo z aplikace . Chcete-li <xref:System.Xml.Linq.XElement> vytvořit <xref:System.Xml.XmlReader>z , <xref:System.Xml.XmlReader> musíte umístit na uzel prvku. Přeskočí <xref:System.Xml.XmlReader> komentáře a pokyny pro <xref:System.Xml.XmlReader> zpracování, ale pokud je umístěn na textovém uzlu, bude vyvolána chyba. Chcete-li se těmto <xref:System.Xml.XmlReader> chybám vyhnout, vždy umístěte prvek <xref:System.Xml.XmlReader>před vytvořením stromu XML z .  
  
## <a name="example"></a>Příklad  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML).](./sample-xml-file-books-linq-to-xml.md)  
  
 Následující kód vytvoří `T:System.Xml.XmlReader` objekt a potom přečte uzly, dokud nenajde uzel prvního prvku. Potom načte <xref:System.Xml.Linq.XElement> objekt.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 Tento příklad vytváří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také

- [Analýza XML (C#)](how-to-parse-a-string.md)
