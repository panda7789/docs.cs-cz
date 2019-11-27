---
title: 'Postupy: načtení hodnoty atributu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 693746c24488029415e68a7c954143a86b7dbb16
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352403"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Postupy: načtení hodnoty atributu (LINQ to XML) (Visual Basic)
V tomto tématu se dozvíte, jak získat hodnotu atributů. Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> můžete přetypovat na požadovaný typ; operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ. Alternativně můžete použít vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>. Přetypování je však všeobecně lepším přístupem. Pokud přetypování atributu na typ s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky naleznete v tématu [How to: načtení hodnoty elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 V Visual Basic můžete použít vlastnost integrovaného atributu k načtení hodnoty atributu.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Příklad  
 V Visual Basic můžete použít vlastnost integrovaného atributu k nastavení hodnoty atributu. Pokud použijete vlastnost integrovaného atributu k nastavení hodnoty atributu, který neexistuje, bude vytvořen atribut.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
abcde  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
