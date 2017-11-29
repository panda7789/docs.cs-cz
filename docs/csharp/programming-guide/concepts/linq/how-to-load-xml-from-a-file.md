---
title: "Postupy: načtení XML ze souboru (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7db51b4b0d6cebb443a9ff43ac8916d3004c1ea5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="866b7-102">Postupy: načtení XML ze souboru (C#)</span><span class="sxs-lookup"><span data-stu-id="866b7-102">How to: Load XML from a File (C#)</span></span>
<span data-ttu-id="866b7-103">Toto téma ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="866b7-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="866b7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="866b7-104">Example</span></span>  
 <span data-ttu-id="866b7-105">Následující příklad ukazuje, jak načíst dokument XML ze souboru.</span><span class="sxs-lookup"><span data-stu-id="866b7-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="866b7-106">Následující příklad načte books.xml a výstupy stromu XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="866b7-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="866b7-107">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: knihy (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="866b7-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="866b7-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="866b7-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="866b7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="866b7-109">See Also</span></span>  
 [<span data-ttu-id="866b7-110">Analýza kódu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="866b7-110">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
