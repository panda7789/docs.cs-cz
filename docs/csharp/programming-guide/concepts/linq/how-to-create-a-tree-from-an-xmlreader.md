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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="68958-104">Postup vytvoření stromu ze třídy XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="68958-104">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="68958-105">Toto téma ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="68958-105">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="68958-106">Chcete-li vytvořit <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader> , je nutné umístit <xref:System.Xml.XmlReader> na uzel elementu.</span><span class="sxs-lookup"><span data-stu-id="68958-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="68958-107"><xref:System.Xml.XmlReader>Přeskočí komentáře a pokyny pro zpracování, ale pokud <xref:System.Xml.XmlReader> je umístěn v textovém uzlu, bude vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="68958-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="68958-108">Chcete-li předejít těmto chybám, vždy umístěte <xref:System.Xml.XmlReader> element na prvek před vytvořením stromu XML z <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="68958-108">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68958-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="68958-109">Example</span></span>  
 <span data-ttu-id="68958-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="68958-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="68958-111">Následující kód vytvoří `T:System.Xml.XmlReader` objekt a poté přečte uzly, dokud nenajde první uzel elementu.</span><span class="sxs-lookup"><span data-stu-id="68958-111">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="68958-112">Poté načte <xref:System.Xml.Linq.XElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="68958-112">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="68958-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="68958-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68958-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68958-114">See also</span></span>

- [<span data-ttu-id="68958-115">Analýza XML (C#)</span><span class="sxs-lookup"><span data-stu-id="68958-115">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
