---
title: C# Prohlášení - prohlídka jazyka C#
description: Můžete vytvořit akce programu Jazyka C# pomocí příkazů
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159101"
---
# <a name="statements"></a>Příkazy

Akce programu jsou vyjádřeny pomocí *příkazů*. C# podporuje několik různých druhů příkazů, z nichž řada jsou definovány z hlediska vložené příkazy.

Blok *block* umožňuje více příkazů, které mají být zapsány v kontextech, kde je povolen jeden příkaz. Blok se skládá ze seznamu příkazů napsaných `{` `}`mezi oddělovači a .

*Příkazy deklarace* se používají k deklarování místních proměnných a konstant.

*Příkazy výrazů* se používají k vyhodnocení výrazů. Výrazy, které lze použít jako příkazy, zahrnují vyvolání metody, přidělení objektů pomocí `new` operátoru, přiřazení pomocí `=` a `++` operátory složeného přiřazení, operace přírůstku a snížení pomocí operátorů a `--` `await` výrazů a.

*Příkazy výběru* se používají k výběru jednoho z několika možných příkazů pro provedení na základě hodnoty některého výrazu. Tato skupina `if` obsahuje `switch` příkazy a.

*Iterace příkazy* se používají k provádění opakovaně vložený příkaz. Tato skupina `while`obsahuje `do` `for`příkazy `foreach` , , a.

*Příkazy skoku* se používají k přenosu řízení. Tato skupina `break`obsahuje `continue` `goto`příkazy , , `throw`, `return`, a. `yield`

V `try`... `catch` příkaz se používá k zachycení výjimky, ke kterým `try`dochází při provádění bloku a ... `finally` příkaz se používá k určení kódu finalizace, který je vždy proveden, bez ohledu na to, zda došlo k výjimce či nikoli.

`checked` Příkazy `unchecked` a se používají k řízení kontextu kontroly přetečení pro aritmetické operace a převody integrálního typu.

Příkaz `lock` se používá k získání vzájemné vyloučení zámek pro daný objekt, spusťte příkaz a potom uvolnit zámek.

Příkaz `using` se používá k získání prostředku, spuštění příkazu a následném vyřazení tohoto prostředku.

V následujícím seznamu jsou uvedeny druhy příkazů, které lze použít, a poskytuje příklad pro každý z nich.

* Deklarace místní proměnné:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Místní konstantní prohlášení:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Příkaz výrazu:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if`Prohlášení:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch`Prohlášení:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while`Prohlášení:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do`Prohlášení:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for`Prohlášení:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach`Prohlášení:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break`Prohlášení:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue`Prohlášení:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto`Prohlášení:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return`Prohlášení:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield`Prohlášení:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw`prohlášení `try` a prohlášení:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked`a `unchecked` prohlášení:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock`Prohlášení:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using`Prohlášení:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Předchozí](expressions.md)
>[další](classes-and-objects.md)
