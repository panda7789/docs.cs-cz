---
title: Příklad odloženého provedení
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6ab8f6434bb24b7a66ca4afd1d082911481671f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354230"
---
# <a name="deferred-execution-example-visual-basic"></a>Příklad odloženého provedení (Visual Basic)

Toto téma ukazuje, jak odložené provádění a opožděné vyhodnocení ovlivní spuštění dotazů LINQ to XML.

## <a name="example"></a>Příklad

Následující příklad ukazuje pořadí spouštění při použití metody rozšíření, která používá odložené provádění. Příklad deklaruje pole tří řetězců. Poté provede iteraci kolekcí vrácenou `ConvertCollectionToUpperCase`.

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

Všimněte si, že při iteraci v kolekci vrácené `ConvertCollectionToUpperCase`je každá položka načtena ze zdrojového pole řetězce a převedena na velká písmena před načtením další položky ze zdrojového pole řetězce.

Můžete vidět, že celé pole řetězců není převedeno na velká písmena před tím, než se každá položka v vrácené kolekci zpracuje v `foreach` smyčce v `Main`.

## <a name="see-also"></a>Viz také:

- [Kurz: odložené provádění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
