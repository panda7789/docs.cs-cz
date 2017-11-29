---
title: "Postupy: načtení XML ze souboru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7babad6b08b2aa486c2ae92e7ad2485d62ac5d47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="0210a-102">Postupy: načtení XML ze souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0210a-102">How to: Load XML from a File (Visual Basic)</span></span>
<span data-ttu-id="0210a-103">Toto téma ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="0210a-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0210a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0210a-104">Example</span></span>  
 <span data-ttu-id="0210a-105">Následující příklad ukazuje, jak načíst dokument XML ze souboru.</span><span class="sxs-lookup"><span data-stu-id="0210a-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="0210a-106">Následující příklad načte books.xml a výstupy stromu XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0210a-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="0210a-107">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: knihy (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0210a-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim booksFromFile As XElement = XElement.Load("books.xml")  
Console.WriteLine(booksFromFile)  
```  
  
 <span data-ttu-id="0210a-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0210a-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0210a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="0210a-109">See Also</span></span>  
 [<span data-ttu-id="0210a-110">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0210a-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
