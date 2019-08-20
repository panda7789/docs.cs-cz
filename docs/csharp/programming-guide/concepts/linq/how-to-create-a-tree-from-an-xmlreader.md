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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="db2cf-102">Postupy: Vytvoření stromu z objektu XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="db2cf-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="db2cf-103">Toto téma ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="db2cf-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="db2cf-104">Chcete-li <xref:System.Xml.Linq.XElement> vytvořit <xref:System.Xml.XmlReader>z <xref:System.Xml.XmlReader> , je nutné umístit na uzel elementu.</span><span class="sxs-lookup"><span data-stu-id="db2cf-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="db2cf-105">Přeskočí komentáře a pokyny pro zpracování, ale <xref:System.Xml.XmlReader> Pokud je umístěn v textovém uzlu, bude vyvolána chyba. <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="db2cf-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="db2cf-106">Chcete-li předejít těmto chybám <xref:System.Xml.XmlReader> , vždy umístěte element na prvek před vytvořením stromu XML <xref:System.Xml.XmlReader>z.</span><span class="sxs-lookup"><span data-stu-id="db2cf-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db2cf-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="db2cf-107">Example</span></span>  
 <span data-ttu-id="db2cf-108">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML](./sample-xml-file-books-linq-to-xml.md)).</span><span class="sxs-lookup"><span data-stu-id="db2cf-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="db2cf-109">Následující kód vytvoří `T:System.Xml.XmlReader` objekt a poté přečte uzly, dokud nenajde první uzel elementu.</span><span class="sxs-lookup"><span data-stu-id="db2cf-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="db2cf-110">Poté načte <xref:System.Xml.Linq.XElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="db2cf-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="db2cf-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="db2cf-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db2cf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db2cf-112">See also</span></span>

- [<span data-ttu-id="db2cf-113">Analýza kódu XMLC#()</span><span class="sxs-lookup"><span data-stu-id="db2cf-113">Parsing XML (C#)</span></span>](./parsing-xml.md)
