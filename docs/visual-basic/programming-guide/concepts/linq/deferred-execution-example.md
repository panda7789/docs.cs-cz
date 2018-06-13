---
title: Odložené provedení příklad (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642126"
---
# <a name="deferred-execution-example-visual-basic"></a>Odložené provedení příklad (Visual Basic)
Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení ovlivnit provádění vaší technologie LINQ to XML dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené provedení. V příkladu deklaruje pole tři řetězců. Ji pak iteruje kolekcí vrácený `ConvertCollectionToUpperCase`.  
  
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
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Všimněte si, že když iterace v rámci kolekce vrácené `ConvertCollectionToUpperCase`, každé položky se načítají z pole řetězců zdroje a převeden na velká písmena před další položky se načítají z pole řetězců zdroje.  
  
 Uvidíte, že celé pole řetězce není převeden na velká písmena, před každou položku v kolekci vrácený při zpracování ve `foreach` smyčky v `Main`.  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Odložený provádění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
