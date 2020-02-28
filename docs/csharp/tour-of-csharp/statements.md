---
title: C#Příkazy – prohlídka C# jazyka
description: Akce C# programu vytvoříte pomocí příkazů
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159101"
---
# <a name="statements"></a>Příkazy

Akce programu jsou vyjádřeny pomocí *příkazů*. C#podporuje několik různých druhů příkazů, jejichž počet je definován z podmínek vložených příkazů.

*Blok* povoluje zápis více příkazů v kontextech, kde je povolen jediný příkaz. Blok obsahuje seznam příkazů zapsaných mezi oddělovači `{` a `}`.

*Příkazy deklarace* slouží k deklaraci lokálních proměnných a konstant.

*Příkazy výrazů* se používají k vyhodnocení výrazů. Výrazy, které lze použít jako příkazy, zahrnují vyvolání metod, přidělení objektů pomocí operátoru `new`, přiřazení pomocí `=` a operátory složeného přiřazení, zvýšení a snížení provozu pomocí operátorů `++` a `--` a `await` výrazů.

*Příkazy výběru* se používají k výběru jednoho z několika možných příkazů pro spuštění na základě hodnoty nějakého výrazu. Tato skupina obsahuje příkazy `if` a `switch`.

*Příkazy iterace* se používají ke opakovanému provedení vloženého příkazu. Tato skupina obsahuje příkazy `while`, `do`, `for`a `foreach`.

*Příkazy skoku* slouží k přenosu ovládacího prvku. Tato skupina obsahuje příkazy `break`, `continue`, `goto`, `throw`, `return`a `yield`.

Příkaz `try`...`catch` slouží k zachycení výjimek, ke kterým dojde během provádění bloku, a příkaz `try`...`finally` slouží k určení finálního kódu, který je vždy spuštěn, bez ohledu na to, zda došlo k výjimce nebo nikoli.

Příkazy `checked` a `unchecked` slouží k řízení kontextu kontroly přetečení pro aritmetické operace a převody integrálního typu.

Příkaz `lock` slouží k získání zámku vzájemného vyloučení pro daný objekt, spuštění příkazu a uvolnění zámku.

Příkaz `using` slouží k získání prostředku, spuštění příkazu a následnému uvolnění tohoto prostředku.

Následující seznam uvádí typy příkazů, které lze použít, a poskytuje příklad pro každý z nich.

* Místní deklarace proměnné:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Deklarace místní konstanty:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Příkaz výrazu:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* příkaz `if`:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* příkaz `switch`:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* příkaz `while`:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* příkaz `do`:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* příkaz `for`:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* příkaz `foreach`:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* příkaz `break`:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* příkaz `continue`:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* příkaz `goto`:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* příkaz `return`:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* příkaz `yield`:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* příkazy `throw` a příkazy `try`:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* příkazy `checked` a `unchecked`:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* příkaz `lock`:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* příkaz `using`:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Předchozí](expressions.md)
>[Další](classes-and-objects.md)
