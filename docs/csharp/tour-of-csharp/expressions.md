---
title: C#Výrazy – prohlídka C# jazyka
description: Výrazy, operandy a operátory jsou stavební bloky C# jazyka.
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4866d12118518827c1f7032ac09933927f0f3c52
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395678"
---
# <a name="expressions"></a>Výrazy

*Výrazy* jsou vytvořené z *operandů* a *operátorů*. Operátory výrazu označují, které operace se mají použít u operandů. Mezi příklady operátorů patří `+`, `-`, `*`, `/` a `new`. Příklady operandů zahrnují literály, pole, místní proměnné a výrazy.

Pokud výraz obsahuje více operátorů, *Priorita* operátorů řídí pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány. Například výraz `x + y * z` je vyhodnocen jako `x + (y * z)`, protože operátor `*` má vyšší prioritu než operátor `+`.

Když dojde k operandu mezi dvěma operátory se stejnou prioritou, *asociativita* operátor řídí pořadí, ve kterém jsou operace prováděny:

* S výjimkou operátorů přiřazení a slučování s hodnotou null jsou všechny binární operátory *asociativní*, což znamená, že operace jsou prováděny zleva doprava. Například `x + y + z` se vyhodnotí jako `(x + y) + z`.
* Operátory přiřazení @no__t operátory null-0 a `??=` a podmíněný operátor `?:` jsou *asociativní zprava*, což znamená, že operace jsou prováděny zprava doleva. Například `x = y = z` se vyhodnotí jako `x = (y = z)`.

Priority a asociativita lze ovládat pomocí závorek. Například `x + y * z` nejprve vynásobí `y` hodnotou `z` a následně výsledek přidá do `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a pak výsledek vynásobí `z`.

Většina operátorů může být [*přetížená*](../language-reference/operators/operator-overloading.md). Přetížení operátoru umožňuje zadat uživatelsky definované implementace operátorů pro operace, u nichž jeden nebo oba operandy jsou uživatelsky definovaný typ třídy nebo struktury.

C#poskytuje několik operátorů pro provádění [aritmetických](../language-reference/operators/arithmetic-operators.md)operací, [logických](../language-reference/operators/boolean-logical-operators.md), [bitových a posunutých](../language-reference/operators/bitwise-and-shift-operators.md) a [rovnosti](../language-reference/operators/equality-operators.md) a porovnávání [objednávek](../language-reference/operators/comparison-operators.md) .

Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Předchozí](types-and-variables.md)
> [Další](statements.md)
