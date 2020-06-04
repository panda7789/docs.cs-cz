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
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="19de5-102">Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.</span><span class="sxs-lookup"><span data-stu-id="19de5-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>

<span data-ttu-id="19de5-103">V klauzuli jste nezadali `WithEvents` proměnnou `Handles` .</span><span class="sxs-lookup"><span data-stu-id="19de5-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="19de5-104">`Handles`Klíčové slovo na konci deklarace procedury způsobí, že zpracovává události vyvolané proměnnou objektu deklarované pomocí `WithEvents` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="19de5-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>

<span data-ttu-id="19de5-105">**ID chyby:** BC30506</span><span class="sxs-lookup"><span data-stu-id="19de5-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="19de5-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="19de5-106">To correct this error</span></span>

<span data-ttu-id="19de5-107">Zadejte potřebnou `WithEvents` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="19de5-107">Supply the necessary `WithEvents` variable.</span></span>

## <a name="example"></a><span data-ttu-id="19de5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="19de5-108">Example</span></span>

<span data-ttu-id="19de5-109">V následujícím příkladu Visual Basic generuje chybu kompilátoru, `BC30506` protože klíčové slovo [WithEvents](../modifiers/withevents.md) není v definici <xref:System.Timers.Timer?displayProperty=nameWithType> instance použito.</span><span class="sxs-lookup"><span data-stu-id="19de5-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

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

<span data-ttu-id="19de5-110">Následující příklad se úspěšně zkompiluje, protože `_timer1` proměnná je definována s `WithEvents` klíčovým slovem:</span><span class="sxs-lookup"><span data-stu-id="19de5-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="19de5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="19de5-111">See also</span></span>

- [<span data-ttu-id="19de5-112">Handles</span><span class="sxs-lookup"><span data-stu-id="19de5-112">Handles</span></span>](../statements/handles-clause.md)
