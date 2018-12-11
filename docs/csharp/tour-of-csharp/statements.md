---
title: C#Příkazy – připravuje C# jazyka
description: Vytvoření akce C# programu pomocí příkazů
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 75f6c7bb29af7f9c809c5278c97d21683166a8e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154291"
---
# <a name="statements"></a>Příkazy

Akce programu jsou vyjádřeny pomocí *příkazy*. C# podporuje několik různých druhů příkazů, číslo, které jsou definovány z hlediska vložených příkazů.

A *bloku* povoluje více příkazů, které má být zapsán v kontextech, kde je povoleno jeden příkaz. Blok obsahuje seznam příkazů, které jsou napsané mezi oddělovači `{` a `}`.

*Příkazy deklarace* se používají k deklarování místní proměnné a konstanty.

*Příkazy výrazů* se používají k vyhodnocení výrazů. Volání metod, obsahovat výrazy, které lze použít jako příkazy přidělení pomocí objektu `new` operátora, přiřazení pomocí `=` a operátory složeného přiřazení, operace Inkrementace a dekrementace pomocí `++`a `--` operátory a `await` výrazy.

*Příkazy výběru* se používají k výběru jedním z možných příkazů pro spuštění na základě hodnoty některých výrazu. V této skupině jsou `if` a `switch` příkazy.

*Příkazy iterace* se používají ke spouštění opakovaně vloženým příkazem. V této skupině jsou `while`, `do`, `for`, a `foreach` příkazy.

*Jump – příkazy* slouží k předání řízení. V této skupině jsou `break`, `continue`, `goto`, `throw`, `return`, a `yield` příkazy.

`try`... `catch` prohlášení se používá k zachycení výjimek, ke kterým dochází při provádění bloku, a `try`... `finally` prohlášení se používá k určení dokončovacího kódu, který je vždy spuštěn, zda došlo k výjimce, nebo ne.

`checked` a `unchecked` příkazy se používají k řízení kontextu kontrol přetečení pro aritmetické operace s celými čísly a převody.

`lock` Prohlášení se používá k získání zámku vzájemné vyloučení pro daný objekt, provedení příkazu a uvolněte zámek.

`using` Prohlášení se používá k získání prostředku, provedení příkazu a potom tento prostředek.

Následuje seznam typy příkazů, které lze použít a poskytuje příklad pro každý.

* Deklarace lokální proměnné:

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
>[Předchozí](expressions.md)
>[další](classes-and-objects.md)