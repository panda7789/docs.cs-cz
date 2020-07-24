---
title: Jak načíst XML ze souboru (C#)
description: Naučte se, jak načíst XML z identifikátoru URI pomocí metody XElement. Load v jazyce C#. Tento příklad načte soubor XML a vytiskne strom XML do konzoly.
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 29de914139d1e9abcda2097addca9219d44d2696
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104959"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="6b00a-104">Jak načíst XML ze souboru (C#)</span><span class="sxs-lookup"><span data-stu-id="6b00a-104">How to load XML from a file (C#)</span></span>
<span data-ttu-id="6b00a-105">Toto téma ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6b00a-105">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b00a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b00a-106">Example</span></span>  
 <span data-ttu-id="6b00a-107">Následující příklad ukazuje, jak načíst dokument XML ze souboru.</span><span class="sxs-lookup"><span data-stu-id="6b00a-107">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="6b00a-108">Následující příklad načte books.xml a vytvoří výstup stromu XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6b00a-108">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="6b00a-109">Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6b00a-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="6b00a-110">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6b00a-110">This code produces the following output:</span></span>  
  
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
  