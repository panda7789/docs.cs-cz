---
title: Příklad odloženého provedení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6d1f66cbe246b609f634989625688965dd4e5c93
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351802"
---
# <a name="deferred-execution-example-visual-basic"></a>Příklad odloženého provedení (Visual Basic)
Toto téma ukazuje, jak odložené provádění a opožděné vyhodnocení ovlivní spuštění dotazů LINQ to XML.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje pořadí spouštění při použití metody rozšíření, která používá odložené provádění. Příklad deklaruje pole tří řetězců. Pak provede iteraci kolekcí vrácenou `ConvertCollectionToUpperCase`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Všimněte si, že při iteraci v kolekci vrácené funkcí `ConvertCollectionToUpperCase` je každá položka načtena ze zdrojového pole řetězce a převedena na velká písmena před načtením další položky ze zdrojového pole řetězců.  
  
 Můžete vidět, že celé pole řetězců není převedeno na velká písmena před tím, než se každá položka v vrácené kolekci zpracuje v `Main` smyčka `foreach`.  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Odložené spuštění (Visual Basic) ](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
