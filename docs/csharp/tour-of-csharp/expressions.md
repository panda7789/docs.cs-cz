---
title: C#Výrazy – připravuje C# jazyka
description: výrazy, operandy a operátory jsou stavební bloky C# jazyka
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: ffe800304a9125e11e20d96a84919936f1fee2c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753644"
---
# <a name="expressions"></a>Výrazy

*Výrazy* se vytvářejí na základě *operandy* a *operátory*. Operátory výrazu označují operace, které chcete použít pro operandy. Příklady operátorů `+`, `-`, `*`, `/`, a `new`. Příklady operandy: literály, pole, místní proměnné a výrazy.

Pokud výraz obsahuje více operátorů *prioritu* operátorů určuje pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány. Například výraz `x + y * z` se vyhodnotí jako `x + (y * z)` protože `*` má vyšší prioritu než operátor `+` operátor.

Dojde-li operand mezi dva operátory se stejnou prioritou, *asociativita* operátorů určuje pořadí, ve kterém jsou operace prováděny:

* S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádějí zleva doprava. Například `x + y + z` se vyhodnotí jako `(x + y) + z`.
* Operátory přiřazení a podmiňovací operátor (`?:`) jsou *asociativní zprava*, což znamená, že operace se provádějí zprava doleva. Například `x = y = z` se vyhodnotí jako `x = (y = z)`.

Přednost a asociativita operátorů lze ovládat pomocí závorek. Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidá výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a pak vynásobí výsledků `z`.

Většina operátory mohou být [ *přetížené*](../language-reference/keywords/operator.md). Přetížení operátoru umožňuje uživatelem definovaný operátor implementace pro operace, kde jeden nebo oba operandy jsou třídy nebo struktury typu uživatelem definované.

C#poskytuje několik operátorů sloužící k provedení [aritmetické](../language-reference/operators/arithmetic-operators.md), [logické](../language-reference/operators/boolean-logical-operators.md), [bitové a shift](../language-reference/operators/bitwise-and-shift-operators.md) operací a [rovnosti](../language-reference/operators/equality-operators.md) a [pořadí](../language-reference/operators/comparison-operators.md) porovnání.

Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Předchozí](types-and-variables.md)
> [další](statements.md)
