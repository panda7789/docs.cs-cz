---
title: Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512736"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.
V klauzuli jste nezadali `WithEvents`proměnnou `Handles` . Klíčové slovo na konci deklarace procedury způsobí, že zpracovává události vyvolané proměnnou objektu deklarované `WithEvents` pomocí klíčového slova. `Handles`
  
 **ID chyby:** BC30506

## <a name="to-correct-this-error"></a>Oprava této chyby
  
- Zadejte potřebnou `WithEvents` proměnnou.
  
## <a name="example"></a>Příklad

V následujícím příkladu Visual Basic generuje chybu `BC30506` kompilátoru, protože klíčové slovo [WithEvents](../modifiers/withevents.md) není v definici <xref:System.Timers.Timer?displayProperty=nameWithType> instance použito.

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}
    
    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

Následující příklad se úspěšně zkompiluje, protože `_timer1` proměnná je definována `WithEvents` s klíčovým slovem:

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a>Viz také:

- [Řeší](../../../visual-basic/language-reference/statements/handles-clause.md)
