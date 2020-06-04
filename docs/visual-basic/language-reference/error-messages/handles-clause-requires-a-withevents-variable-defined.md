---
title: Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 94c4229d4036382e344cffb09295e218642c55d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402898"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.

V klauzuli jste nezadali `WithEvents` proměnnou `Handles` . `Handles`Klíčové slovo na konci deklarace procedury způsobí, že zpracovává události vyvolané proměnnou objektu deklarované pomocí `WithEvents` klíčového slova.

**ID chyby:** BC30506

## <a name="to-correct-this-error"></a>Oprava této chyby

Zadejte potřebnou `WithEvents` proměnnou.

## <a name="example"></a>Příklad

V následujícím příkladu Visual Basic generuje chybu kompilátoru, `BC30506` protože klíčové slovo [WithEvents](../modifiers/withevents.md) není v definici <xref:System.Timers.Timer?displayProperty=nameWithType> instance použito.

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

Následující příklad se úspěšně zkompiluje, protože `_timer1` proměnná je definována s `WithEvents` klíčovým slovem:

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

## <a name="see-also"></a>Viz také

- [Handles](../statements/handles-clause.md)
