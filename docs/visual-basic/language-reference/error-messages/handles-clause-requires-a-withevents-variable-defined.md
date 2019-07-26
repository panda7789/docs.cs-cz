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
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="860b1-102">Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.</span><span class="sxs-lookup"><span data-stu-id="860b1-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="860b1-103">V klauzuli jste nezadali `WithEvents`proměnnou `Handles` .</span><span class="sxs-lookup"><span data-stu-id="860b1-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="860b1-104">Klíčové slovo na konci deklarace procedury způsobí, že zpracovává události vyvolané proměnnou objektu deklarované `WithEvents` pomocí klíčového slova. `Handles`</span><span class="sxs-lookup"><span data-stu-id="860b1-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>
  
 <span data-ttu-id="860b1-105">**ID chyby:** BC30506</span><span class="sxs-lookup"><span data-stu-id="860b1-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="860b1-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="860b1-106">To correct this error</span></span>
  
- <span data-ttu-id="860b1-107">Zadejte potřebnou `WithEvents` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="860b1-107">Supply the necessary `WithEvents` variable.</span></span>
  
## <a name="example"></a><span data-ttu-id="860b1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="860b1-108">Example</span></span>

<span data-ttu-id="860b1-109">V následujícím příkladu Visual Basic generuje chybu `BC30506` kompilátoru, protože klíčové slovo [WithEvents](../modifiers/withevents.md) není v definici <xref:System.Timers.Timer?displayProperty=nameWithType> instance použito.</span><span class="sxs-lookup"><span data-stu-id="860b1-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

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

<span data-ttu-id="860b1-110">Následující příklad se úspěšně zkompiluje, protože `_timer1` proměnná je definována `WithEvents` s klíčovým slovem:</span><span class="sxs-lookup"><span data-stu-id="860b1-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="860b1-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="860b1-111">See also</span></span>

- [<span data-ttu-id="860b1-112">Řeší</span><span class="sxs-lookup"><span data-stu-id="860b1-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
