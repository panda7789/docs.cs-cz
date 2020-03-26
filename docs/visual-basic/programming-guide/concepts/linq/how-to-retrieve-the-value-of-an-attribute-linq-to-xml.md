---
title: 'Postup: Načtení hodnoty atributu (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248944"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Postup: Načtení hodnoty atributu (LINQ do XML) (Visual Basic)
Toto téma ukazuje, jak získat hodnotu atributů. Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> Můžete přetypovat na požadovaný typ; explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ. Případně můžete využít <xref:System.Xml.Linq.XAttribute.Value%2A> ubytování. Nicméně, casting je obecně lepší přístup. Pokud přetypování atributu s hodnotou s možnou hodnotou null, kód je jednodušší psát při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky naleznete v tématu [How to: Retrieve the Value of a Element (LINQ to XML) (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)  
  
## <a name="example"></a>Příklad  
 V jazyce Visual Basic můžete použít vlastnost integrovaného atributu k načtení hodnoty atributu.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Příklad  
 V jazyce Visual Basic můžete použít vlastnost integrated attribute k nastavení hodnoty atributu. Dále pokud použijete vlastnost integrated attribute k nastavení hodnoty atributu, který neexistuje, bude atribut vytvořen.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (Visual Basic).](namespaces-overview-linq-to-xml.md)  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```console  
abcde  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
