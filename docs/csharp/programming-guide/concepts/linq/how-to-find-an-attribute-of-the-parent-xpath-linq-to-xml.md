---
title: 'Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: d6660e2bab074432f3dcd8f95825d76a6ff704a5
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487405"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)
Toto téma ukazuje, jak přejít do nadřazeného elementu a vyhledání atributu ho.  
  
 Výraz XPath je:  
  
 `../@id`  
  
## <a name="example"></a>Příklad  
 V tomto příkladu nejprve vyhledá `Author` elementu. Následně vyhledá `id` atributu nadřazeného elementu.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Knihy (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
id="bk101"  
```  
  
