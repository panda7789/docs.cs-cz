---
title: 'Postupy: Vytvoření stromu ze třídy XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: fb65c7b74bf3bd006fd4f545e4587efe9a392131
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496178"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="63ebb-102">Postupy: Vytvoření stromu ze třídy XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="63ebb-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="63ebb-103">Toto téma ukazuje, jak vytvořit stromu XML přímo ze <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="63ebb-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="63ebb-104">K vytvoření <xref:System.Xml.Linq.XElement> ze <xref:System.Xml.XmlReader>, je třeba umístit <xref:System.Xml.XmlReader> na uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="63ebb-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="63ebb-105"><xref:System.Xml.XmlReader> Komentáře se přeskočí a zpracování pokynů, ale pokud <xref:System.Xml.XmlReader> je umístěn na textový uzel, bude vyvolána k chybě.</span><span class="sxs-lookup"><span data-stu-id="63ebb-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="63ebb-106">Aby se zabránilo podobné chyby, vždy umístěte <xref:System.Xml.XmlReader> v elementu před vytvořením stromu XML ze <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="63ebb-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63ebb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="63ebb-107">Example</span></span>  
 <span data-ttu-id="63ebb-108">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="63ebb-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="63ebb-109">Následující kód vytvoří `T:System.Xml.XmlReader` objektu a čtení uzly, dokud nenajde prvního uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="63ebb-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="63ebb-110">Pak načte <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="63ebb-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="63ebb-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="63ebb-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63ebb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63ebb-112">See also</span></span>

- [<span data-ttu-id="63ebb-113">Analýza kódu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="63ebb-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
