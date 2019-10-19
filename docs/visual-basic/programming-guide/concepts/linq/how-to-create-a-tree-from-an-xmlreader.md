---
title: 'Postupy: vytvoření stromu ze třídy XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: c90fbee29a380824cdc32dd62622e55ea40044fd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583030"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Postupy: vytvoření stromu ze třídy XmlReader (Visual Basic)

Toto téma ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader>. Chcete-li vytvořit <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, je nutné umístit <xref:System.Xml.XmlReader> na uzel elementu. @No__t_0 přeskočí komentáře a pokyny pro zpracování, ale pokud je <xref:System.Xml.XmlReader> umístěn v textovém uzlu, bude vyvolána chyba. Chcete-li se těmto chybám vyhnout, před vytvořením stromu XML z <xref:System.Xml.XmlReader> vždy umístěte <xref:System.Xml.XmlReader> na prvek.

## <a name="example"></a>Příklad

Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).

Následující kód vytvoří objekt `T:System.Xml.XmlReader` a pak přečte uzly, dokud nenajde první uzel elementu. Poté načte objekt <xref:System.Xml.Linq.XElement>.

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
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

- [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
