---
title: "Odložené provedení příklad (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4d2146901d9282b0df706b483afef79f714f660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
