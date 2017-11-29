---
title: "Postupy: načtení hodnoty atributu (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eed0c34f79a4a338dda7b26049f2c1510443736
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Postupy: načtení hodnoty atributu (technologie LINQ to XML) (Visual Basic)
Toto téma ukazuje, jak získat hodnotu atributů. Existují dva hlavní způsoby: může odevzdat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitní převod potom převede obsah elementu nebo atributu zadaného typu. Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost. Přetypování je ale obecně lepší přístup. Pokud jste přetypovat atribut typu s povolenou hodnotou Null, kód je jednodušší při načítání hodnoty atributu, který může nebo nemusí existovat zápis. Příklady tento postup najdete v tématu [postupy: načtení hodnoty elementu (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Vlastnost integrované atribut v jazyce Visual Basic slouží k načtení hodnoty atributu.  
  
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
 Vlastnost integrované atribut v jazyce Visual Basic slouží k nastavení hodnoty atributu. Dál platí Pokud použijete vlastnost integrované atribut nastavit hodnotu atributu, který ještě neexistuje, bude vytvořena atribut.  
  
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
 Následující příklad ukazuje, jak načíst hodnotu atributu kde atributu je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
```  
abcde  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
