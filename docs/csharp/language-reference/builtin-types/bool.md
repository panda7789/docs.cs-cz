---
title: bool – typ – reference jazyka C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 4623dc7d6c8c6c437c78aee45f0eeee8a92e3200
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854877"
---
# <a name="bool-c-reference"></a>bool (Referenční dokumentace jazyka C#)

`bool`Klíčové slovo Type je alias pro <xref:System.Boolean?displayProperty=nameWithType> typ struktury .NET, který představuje logickou hodnotu, která může být buď `true` nebo `false` .

K provádění logických operací s hodnotami `bool` typu použijte logické [logické](../operators/boolean-logical-operators.md) operátory. `bool`Typ je výsledný typ operátoru [porovnání](../operators/comparison-operators.md) a [rovnosti](../operators/equality-operators.md) . `bool`Výraz může být řídicí podmíněný výraz v příkazech [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněných operátorech `?:` ](../operators/conditional-operator.md).

Výchozí hodnota `bool` typu je `false` .

## <a name="literals"></a>Literály

`true`Literály a lze použít `false` k inicializaci `bool` proměnné nebo k předání `bool` hodnoty:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logická logika se třemi hodnotami

Typ s povolenou hodnotou null použijte `bool?` , pokud potřebujete podporovat logiku se třemi hodnotami, například když pracujete s databázemi, které podporují logický typ se třemi hodnotami. Pro `bool?` operandy, předdefinované `&` a `|` operátory podporují logiku se třemi hodnotami. Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .

Další informace o typech hodnot s možnou hodnotou null naleznete v tématu [typy hodnot s možnou hodnotou null](nullable-value-types.md).

## <a name="conversions"></a>Převody

Jazyk C# poskytuje pouze dva převody, které obsahují `bool` typ. Jedná se o implicitní převod na odpovídající typ s možnou hodnotou null `bool?` a explicitní převod z `bool?` typu. Nicméně rozhraní .NET poskytuje další metody, které lze použít pro převod na nebo z `bool` typu. Další informace naleznete v části [Převod do a z logických hodnot](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na <xref:System.Boolean?displayProperty=nameWithType> referenční stránce rozhraní API.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typ bool](~/_csharplang/spec/types.md#the-bool-type) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [true a false – operátory](../operators/true-false-operators.md)
