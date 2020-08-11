---
title: Delegate – operátor – reference jazyka C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 33c438b88f1e993f4648786da9b20b91961b7ee1
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062987"
---
# <a name="delegate-operator-c-reference"></a>Delegate – operátor (Referenční dokumentace jazyka C#)

`delegate`Operátor vytvoří anonymní metodu, která může být převedena na typ delegáta:

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Počínaje jazykem C# 3 výrazy lambda poskytují výstižnější a výrazný způsob vytvoření anonymní funkce. Použijte [operátor =>](lambda-operator.md) pro vytvoření výrazu lambda:
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> Další informace o funkcích výrazů lambda, například zachycení vnějších proměnných, naleznete v tématu [lambda Expressions](lambda-expressions.md).

Při použití `delegate` operátoru můžete seznam parametrů vynechat. Pokud to uděláte, můžete vytvořenou anonymní metodu převést na typ delegáta s libovolným seznamem parametrů, jak ukazuje následující příklad:

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

To je jediná funkce anonymních metod, které výrazy lambda nepodporují. Ve všech ostatních případech je výraz lambda upřednostňovaným způsobem, jak psát vložený kód.

Pomocí `delegate` klíčového slova také deklarujete [typ delegáta](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [=> – operátor](lambda-operator.md)
