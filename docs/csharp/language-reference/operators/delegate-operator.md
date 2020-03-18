---
title: operátor delegáta – odkaz jazyka C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dd27fe5fdfdc1bc8a63e1298da00d252e800a72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847336"
---
# <a name="delegate-operator-c-reference"></a>operátor delegáta (odkaz C# )

Operátor `delegate` vytvoří anonymní metodu, kterou lze převést na typ delegáta:

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Počínaje C# 3, lambda výrazy poskytují stručnější a expresivní způsob, jak vytvořit anonymní funkce. Pomocí [operátoru =>](lambda-operator.md) vytvořte výraz lambda:
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> Další informace o funkcích výrazů lambda, například zachycení vnějších proměnných, naleznete v [tématu Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Při použití `delegate` operátoru můžete vynechat seznam parametrů. Pokud tak učiníte, vytvořená anonymní metoda může být převedena na typ delegáta s libovolným seznamem parametrů, jak ukazuje následující příklad:

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

To je jediná funkce anonymnímetody, která není podporována lambda výrazy. Ve všech ostatních případech lambda výraz je upřednostňovaný způsob, jak psát vřádkový kód.

Klíčové `delegate` slovo můžete také použít k deklarování [typu delegáta](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [= operátor>](lambda-operator.md)
