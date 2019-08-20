---
title: 'Postupy: Vytvoření stromu z objektu XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: f632bbdad7d52ea37e2587516792dfd13178d702
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593870"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Postupy: Vytvoření stromu z objektu XmlReader (C#)
Toto téma ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader>. Chcete-li <xref:System.Xml.Linq.XElement> vytvořit <xref:System.Xml.XmlReader>z <xref:System.Xml.XmlReader> , je nutné umístit na uzel elementu. Přeskočí komentáře a pokyny pro zpracování, ale <xref:System.Xml.XmlReader> Pokud je umístěn v textovém uzlu, bude vyvolána chyba. <xref:System.Xml.XmlReader> Chcete-li předejít těmto chybám <xref:System.Xml.XmlReader> , vždy umístěte element na prvek před vytvořením stromu XML <xref:System.Xml.XmlReader>z.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML](./sample-xml-file-books-linq-to-xml.md)).  
  
 Následující kód vytvoří `T:System.Xml.XmlReader` objekt a poté přečte uzly, dokud nenajde první uzel elementu. Poté načte <xref:System.Xml.Linq.XElement> objekt.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Analýza kódu XMLC#()](./parsing-xml.md)
