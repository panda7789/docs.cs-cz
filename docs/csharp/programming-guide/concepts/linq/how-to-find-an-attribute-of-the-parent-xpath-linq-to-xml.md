---
title: 'Postupy: vyhledat atribut nadřazeného (XPath-technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6f796bfb8f8b0051af4e31f6e82a503dbfbbc334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318796"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Postupy: vyhledat atribut nadřazeného (XPath-technologie LINQ to XML) (C#)
Toto téma ukazuje, jak vyhledat atribut ho a přejděte do nadřazeného elementu.  
  
 Výraz XPath je:  
  
 `../@id`  
  
## <a name="example"></a>Příklad  
 Tento příklad nejprve najde `Author` elementu. Poté vyhledá `id` atribut nadřazeného elementu.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: knihy (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML pro uživatele XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
