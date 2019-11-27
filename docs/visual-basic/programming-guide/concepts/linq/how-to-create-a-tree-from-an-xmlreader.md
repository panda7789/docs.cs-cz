---
title: 'Postupy: vytvoření stromu z objektu XmlReader'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 7d8d7f5b6389bef520e11fd2b7cc3e1c7e862e73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353088"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="8604f-102">Postupy: vytvoření stromu ze třídy XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8604f-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="8604f-103">Toto téma ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="8604f-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="8604f-104">Chcete-li vytvořit <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, je nutné umístit <xref:System.Xml.XmlReader> na uzel elementu.</span><span class="sxs-lookup"><span data-stu-id="8604f-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="8604f-105"><xref:System.Xml.XmlReader> přeskočí komentáře a pokyny pro zpracování, ale pokud je <xref:System.Xml.XmlReader> umístěn v textovém uzlu, bude vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="8604f-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="8604f-106">Chcete-li se těmto chybám vyhnout, před vytvořením stromu XML z <xref:System.Xml.XmlReader>vždy umístěte <xref:System.Xml.XmlReader> na prvek.</span><span class="sxs-lookup"><span data-stu-id="8604f-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="8604f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8604f-107">Example</span></span>

<span data-ttu-id="8604f-108">Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8604f-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="8604f-109">Následující kód vytvoří objekt `T:System.Xml.XmlReader` a pak přečte uzly, dokud nenajde první uzel elementu.</span><span class="sxs-lookup"><span data-stu-id="8604f-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="8604f-110">Poté načte objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8604f-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="8604f-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8604f-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8604f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8604f-112">See also</span></span>

- [<span data-ttu-id="8604f-113">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8604f-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
