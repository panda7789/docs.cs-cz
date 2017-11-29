---
title: "Postupy: čtení a zápis kódovaného dokumentu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a08fa9404c92bd64b07059df2f419bff5f80da3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="f5d39-102">Postupy: čtení a zápis kódovaného dokumentu (C#)</span><span class="sxs-lookup"><span data-stu-id="f5d39-102">How to: Read and Write an Encoded Document (C#)</span></span>
<span data-ttu-id="f5d39-103">Chcete-li vytvořit dokument XML kódovaného, je přidat <xref:System.Xml.Linq.XDeclaration> do stromu XML nastavení kódování, které má název požadované kódu stránky.</span><span class="sxs-lookup"><span data-stu-id="f5d39-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="f5d39-104">Všechny hodnoty vrácené <xref:System.Text.Encoding.WebName%2A> platná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f5d39-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="f5d39-105">Pokud si přečíst dokument kódovaného <xref:System.Xml.Linq.XDeclaration.Encoding%2A> vlastnost bude nastavena na název stránky kód.</span><span class="sxs-lookup"><span data-stu-id="f5d39-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="f5d39-106">Pokud nastavíte <xref:System.Xml.Linq.XDeclaration.Encoding%2A> k názvu stránky platný kód [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bude serializovat s zadanému kódování.</span><span class="sxs-lookup"><span data-stu-id="f5d39-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d39-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5d39-107">Example</span></span>  
 <span data-ttu-id="f5d39-108">Následující příklad vytvoří dva dokumenty, jeden s kódováním utf-8 a jednu s kódování utf-16.</span><span class="sxs-lookup"><span data-stu-id="f5d39-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="f5d39-109">Potom načte dokumenty a vytiskne kódování ke konzole.</span><span class="sxs-lookup"><span data-stu-id="f5d39-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 <span data-ttu-id="f5d39-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f5d39-110">This example produces the following output:</span></span>  
  
```  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5d39-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5d39-111">See Also</span></span>  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f5d39-112">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="f5d39-112">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
