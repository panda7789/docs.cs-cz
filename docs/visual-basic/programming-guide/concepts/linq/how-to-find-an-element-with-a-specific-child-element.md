---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405284"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Postupy: Vyhledání elementu s konkrétním podřízeným elementem (Visual Basic)
Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.  
  
## <a name="example"></a>Příklad  
 Příklad vyhledá `Test` prvek, který má `CommandLine` podřízený element s hodnotou "EXAMP2. exe".  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
0002  
0006  
```  
  
 Všimněte si, že v tomto příkladu je použita [vlastnost podřízená osa XML](../../../language-reference/xml-axis/xml-child-axis-property.md), [vlastnost osy atributu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)a [vlastnost hodnoty XML](../../../language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: konfigurace testu v oboru názvů](sample-xml-file-test-configuration-in-a-namespace.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Základní dotazy (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Operace projekce (Visual Basic)](projection-operations.md)
