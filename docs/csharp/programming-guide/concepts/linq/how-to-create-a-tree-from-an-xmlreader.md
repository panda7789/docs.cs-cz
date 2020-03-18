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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="70b0b-102">Jak vytvořit strom z XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="70b0b-102">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="70b0b-103">Toto téma ukazuje, jak vytvořit <xref:System.Xml.XmlReader>strom XML přímo z aplikace .</span><span class="sxs-lookup"><span data-stu-id="70b0b-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="70b0b-104">Chcete-li <xref:System.Xml.Linq.XElement> vytvořit <xref:System.Xml.XmlReader>z , <xref:System.Xml.XmlReader> musíte umístit na uzel prvku.</span><span class="sxs-lookup"><span data-stu-id="70b0b-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="70b0b-105">Přeskočí <xref:System.Xml.XmlReader> komentáře a pokyny pro <xref:System.Xml.XmlReader> zpracování, ale pokud je umístěn na textovém uzlu, bude vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="70b0b-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="70b0b-106">Chcete-li se těmto <xref:System.Xml.XmlReader> chybám vyhnout, vždy umístěte prvek <xref:System.Xml.XmlReader>před vytvořením stromu XML z .</span><span class="sxs-lookup"><span data-stu-id="70b0b-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b0b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="70b0b-107">Example</span></span>  
 <span data-ttu-id="70b0b-108">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML).](./sample-xml-file-books-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="70b0b-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="70b0b-109">Následující kód vytvoří `T:System.Xml.XmlReader` objekt a potom přečte uzly, dokud nenajde uzel prvního prvku.</span><span class="sxs-lookup"><span data-stu-id="70b0b-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="70b0b-110">Potom načte <xref:System.Xml.Linq.XElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="70b0b-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="70b0b-111">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70b0b-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70b0b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="70b0b-112">See also</span></span>

- [<span data-ttu-id="70b0b-113">Analýza XML (C#)</span><span class="sxs-lookup"><span data-stu-id="70b0b-113">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
