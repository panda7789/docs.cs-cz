---
title: 'Postupy: Vyhledání atributu nadřazené položky (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: c4cb2f2e52aeaa42fd69b83c19c47fd205d48cbc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352961"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a>Postupy: Vyhledání atributu nadřazené položky (XPath-LINQ to XML) (Visual Basic)
Toto téma ukazuje, jak přejít na nadřazený prvek a najít atribut.  
  
 Výraz XPath je:  
  
 `../@id`  
  
## <a name="example"></a>Příklad  
 Tento příklad nejprve najde `Author` element. Pak najde atribut `id` nadřazeného elementu.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML pro uživatele XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
