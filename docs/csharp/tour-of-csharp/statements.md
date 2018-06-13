---
title: C# příkazy – přehled používání jazyka C#
description: Vytvoříte akce programu v C# pomocí příkazů
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351976"
---
# <a name="statements"></a>Příkazy

Akce programu jsou vyjádřeny pomocí *příkazy*. C# podporuje několik různých druhů příkazy, počet jsou definována v embedded příkazy.

A *bloku* umožňuje více příkazů, které má být zapsán v kontextu, kde je povoleno jeden příkaz. Blok sestává ze seznamu příkazů, které jsou zapsány mezi oddělovače `{` a `}`.

*Deklarační příkazy* se používá k deklaraci místní proměnné a konstanty.

*Příkazy výrazu* se používají k vyhodnocení výrazů. Výrazy, které lze použít jako příkazy zahrnují volání metod objektu přidělení pomocí `new` operátor, přiřazení pomocí `=` a složené operátory přiřazení, přírůstek a snížení operace pomocí `++`a `--` operátory a `await` výrazy.

*Příkazy výběru* slouží k výběru jedné počet možných příkazů pro spuštění na základě hodnoty některých výrazu. V této skupině se `if` a `switch` příkazy.

*Příkazy iterace* se používají k provedení příkazu embedded opakovaně. V této skupině se `while`, `do`, `for`, a `foreach` příkazy.

*Jump – příkazy* se používá k přenosu ovládacího prvku. V této skupině se `break`, `continue`, `goto`, `throw`, `return`, a `yield` příkazy.

`try`... `catch` příkaz se používá k zachycení výjimky, ke kterým došlo během provádění blok, a `try`... `finally` příkaz slouží k určení finalizace kód, který je spuštěn vždy, zda došlo k chybě, nebo ne.

`checked` a `unchecked` příkazy jsou používány k ovládání kontext kontrola Přetečení aritmetické operace integrální type a převody.

`lock` Se použije příkaz získat zámek vzájemné vyloučení pro daný objekt, provedení příkazu a pak uvolní zámek.

`using` Se použije příkaz získat prostředek, provedení příkazu a pak odstranění tohoto prostředku.

V následujícím seznamu uvedeny druhy příkazy, které lze použít a představuje příklad.

* Místní deklarace proměnné:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Místní deklarace konstanty:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Příkaz výrazu:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if` příkaz:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch` příkaz:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while` příkaz:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do` příkaz:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for` příkaz:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach` příkaz:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break` příkaz:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue` příkaz:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto` příkaz:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return` příkaz:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield` příkaz:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw` Příkazy a `try` příkazy:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked` a `unchecked` příkazy:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock` příkaz:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using` příkaz:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
[Předchozí](expressions.md)
[další](classes-and-objects.md)
