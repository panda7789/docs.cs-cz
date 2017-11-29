---
title: "Postupy: vytvoření dokumentu s obory názvů (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 038e2924603eba7250620bc2792ec87b8e978787
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Postupy: vytvoření dokumentu s obory názvů (technologie LINQ to XML) (Visual Basic)
Toto téma ukazuje, jak vytvořit dokument s obory názvů v jazyce Visual Basic.  
  
 Pokud používáte literálů XML v jazyce Visual Basic, uživatelé mohou definovat jeden globální výchozí obor názvů XML. Tento obor názvů je výchozí obor názvů pro literály XML a vlastnosti XML. Výchozí obor názvů XML lze definovat na úrovni projektu nebo úrovni souborů. Pokud je definován na úrovni souborů, přepíše výchozí obor názvů na úrovni projektu.  
  
 Můžete také definovat další obory názvů a zadejte předpony oboru názvů pro obory názvů.  
  
 Definovat výchozí obory názvů a obory názvů s předponou pomocí `Imports` – klíčové slovo.  
  
 Další informace najdete v tématu [Úvod do literálů XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Všimněte si, že výchozí obor názvů XML se vztahuje pouze na elementy a atributy. Atributy jsou ve výchozím nastavení vždy v žádné oboru názvů. Můžete však použít předponu oboru názvů uvést atribut v oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří dokument, který obsahuje obor názvů.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří dokument, který obsahuje dva obory názvů, z nichž jeden je výchozí obor názvů.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument, který obsahuje více oborů názvů, jak pomocí předpony oboru názvů.  
  
 Při serializaci strom XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vysílá deklarace oboru názvů podle potřeby tak, aby každý prvek v jeho určené oboru názvů.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
