---
title: Delegate – operátor C# – reference
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 9a78faaccffa9e7d4bf2829d8dfa0fa62a788bba
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039045"
---
# <a name="delegate-operator-c-reference"></a>Delegate – operátorC# (Referenční dokumentace)

Operátor `delegate` vytvoří anonymní metodu, která může být převedena na typ delegáta:

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Počínaje C# 3 výrazy lambda poskytují výstižnější a výrazný způsob vytváření anonymní funkce. Použijte [operátor = >](lambda-operator.md) pro vytvoření výrazu lambda:
>
> [!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> Další informace o funkcích výrazů lambda, například zachycení vnějších proměnných, naleznete v tématu [lambda Expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Při použití operátoru `delegate` můžete vynechat seznam parametrů. Pokud to uděláte, můžete vytvořenou anonymní metodu převést na typ delegáta s libovolným seznamem parametrů, jak ukazuje následující příklad:

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

To je jediná funkce anonymních metod, které výrazy lambda nepodporují. Ve všech ostatních případech je výraz lambda upřednostňovaným způsobem, jak psát vložený kód.

Pomocí klíčového slova `delegate` také deklarujete [typ delegáta](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [= > – operátor](lambda-operator.md)
