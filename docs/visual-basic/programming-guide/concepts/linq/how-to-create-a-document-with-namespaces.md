---
title: 'Postupy: vytvoření dokumentu s názvovými prostory (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499923"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Postupy: vytvoření dokumentu s názvovými prostory (LINQ to XML) (Visual Basic)
Toto téma ukazuje, jak vytvořit dokument s obory názvů v jazyce Visual Basic.  
  
 Při použití literálů XML v jazyce Visual Basic, uživatelé mohou definovat jeden globální výchozí názvový prostor XML. Tento obor názvů je výchozí obor názvů pro literály XML a vlastnosti XML. Výchozí obor názvů XML lze definovat na úrovni projektu nebo na úrovni souboru. Pokud je definován na úrovni souboru, přepíše výchozí obor názvů na úrovni projektu.  
  
 Můžete také definovat další obory názvů a zadat předpony oboru názvů pro obory názvů.  
  
 Definovat výchozí obory názvů a obory názvů s předponou pomocí `Imports` – klíčové slovo.  
  
 Další informace najdete v tématu [Úvod k Literálům XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Všimněte si, že výchozí obor názvů XML se vztahuje pouze na prvky a atributy. Atributy jsou ve výchozím nastavení vždy bez oboru názvů. Ale můžete použít předponu oboru názvů do atribut v oboru názvů.  
  
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
 Následující příklad vytvoří dokument, který obsahuje více oborů názvů, jak u předpony oboru názvů.  
  
 Při serializaci stromu XML, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vysílá deklarace oboru názvů podle potřeby tak, aby každý prvek v jeho určený obor názvů.  
  
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
 [Práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
