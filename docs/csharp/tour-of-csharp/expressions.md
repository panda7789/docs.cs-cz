---
title: Výrazy jazyka C# – prohlídka jazyka C#
description: Výrazy, operandy a operátory jsou stavebními kameny jazyka C#
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159153"
---
# <a name="expressions"></a>Výrazy

*Výrazy* jsou vytvořeny z *operandů* a *operátorů*. Operátory výrazu označují, které operace se mají u operandů použít. `+`Příklady operátorů: `-` `*`, `/`, `new`, a . Příklady operandů zahrnují literály, pole, místní proměnné a výrazy.

Pokud výraz obsahuje více operátorů, *priorita* operátorů řídí pořadí, ve kterém jsou vyhodnocovány jednotlivé operátory. Výraz `x + y * z` je například vyhodnocen jako `x + (y * z)` proto, že `*` operátor má vyšší prioritu `+` než operátor.

Pokud dojde k operandu mezi dvěma operátory se stejnou prioritou, *asociativity* operátorů řídí pořadí, ve kterém jsou operace prováděny:

* S výjimkou operátorů přiřazení a null-coalescing jsou všechny binární operátory *levostranné*, což znamená, že operace jsou prováděny zleva doprava. Například `x + y + z` je vyhodnocen jako `(x + y) + z`.
* Operátory přiřazení, `??` null-coalescing `??=` a operátory `?:` a podmíněný operátor jsou *pravostranné*, což znamená, že operace jsou prováděny zprava doleva. Například `x = y = z` je vyhodnocen jako `x = (y = z)`.

Prioritu a asociativitu lze ovládat pomocí závorek. `x + y * z` Například nejprve `y` vynásobí `z` a `x`potom `(x + y) * z` přidá `x` `y` výsledek do , ale `z`nejprve přidá a potom vynásobí výsledek .

Většina operátorů může být [*přetížena*](../language-reference/operators/operator-overloading.md). Přetížení operátoru umožňuje uživatelem definované implementace operátorů, které mají být určeny pro operace, kde jeden nebo oba operandy jsou uživatelem definované třídy nebo struktury typu.

C# poskytuje počet operátorů k provádění [aritmetické](../language-reference/operators/arithmetic-operators.md), [logické](../language-reference/operators/boolean-logical-operators.md), [bitové a shift](../language-reference/operators/bitwise-and-shift-operators.md) operace a rovnost [i](../language-reference/operators/equality-operators.md) [pořadí](../language-reference/operators/comparison-operators.md) porovnání.

Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v [tématu Operátory jazyka C#](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Předchozí](types-and-variables.md)
> [další](statements.md)
