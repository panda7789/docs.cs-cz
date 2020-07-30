---
title: Postup vytvoření stromu ze třídy XmlReader (C#)
description: Naučte se vytvořit strom XML přímo z objektu XmlReader. Podívejte se na příklad, který ukazuje, jak vytvořit objekt T:System.Xml.XmlReader.
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 3801177e664d142652d38748d44eaf3f274239dd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302656"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Postup vytvoření stromu ze třídy XmlReader (C#)
Toto téma ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader> . Chcete-li vytvořit <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader> , je nutné umístit <xref:System.Xml.XmlReader> na uzel elementu. <xref:System.Xml.XmlReader>Přeskočí komentáře a pokyny pro zpracování, ale pokud <xref:System.Xml.XmlReader> je umístěn v textovém uzlu, bude vyvolána chyba. Chcete-li předejít těmto chybám, vždy umístěte <xref:System.Xml.XmlReader> element na prvek před vytvořením stromu XML z <xref:System.Xml.XmlReader> .  
  
## <a name="example"></a>Příklad  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
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

- [Analýza XML (C#)](how-to-parse-a-string.md)
