---
title: Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582829"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.

V klauzuli `Handles` jste nezadali `WithEvents` proměnnou. Klíčové slovo `Handles` na konci deklarace procedury způsobí, že má zpracovávat události vyvolané proměnnou objektu deklarovanou pomocí klíčového slova `WithEvents`.

**ID chyby:** BC30506

## <a name="to-correct-this-error"></a>Oprava této chyby

Zadejte potřebnou `WithEvents` proměnnou.

## <a name="example"></a>Příklad

V následujícím příkladu Visual Basic generuje chybu kompilátoru `BC30506` protože klíčové slovo [WithEvents](../modifiers/withevents.md) není v definici instance <xref:System.Timers.Timer?displayProperty=nameWithType> použito.

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

Následující příklad je úspěšně zkompilován, protože proměnná `_timer1` je definována pomocí klíčového slova `WithEvents`:

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
