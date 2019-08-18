---
title: Uživatelsky definované operátory převodu – C# referenční informace
description: Naučte se definovat vlastní implicitní a explicitní převody typu v C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 8788883a6c60032de2ffab658fcf2721654fc6f7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566674"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Uživatelsky definované operátory převodu (C# referenční)

Uživatelsky definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.

Implicitní převody nevyžadují, aby se vyvolala speciální syntaxe, která může nastat v různých situacích, například v přiřazení a volání metod. Předdefinované C# implicitní převody jsou vždy úspěšné a nikdy nevyvolávají výjimku nebo ztratí informace. Uživatelem definované implicitní převody by se měly chovat i tímto způsobem. Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.

Uživatelem definované převody nejsou považovány za operátory [is](type-testing-and-cast.md#is-operator) a [as](type-testing-and-cast.md#as-operator) . Použijte [operátor přetypování ()](type-testing-and-cast.md#cast-operator-) pro vyvolání uživatelem definovaného explicitního převodu.

Použijte klíčová `implicit` slova `explicit` a nebo pro definování implicitního nebo explicitního převodu v uvedeném pořadí. `operator` Typ, který definuje převod, musí být buď zdrojový typ, nebo cílový typ převodu. Převod mezi dvěma uživatelsky definovanými typy lze definovat v jednom ze dvou typů.

Následující příklad ukazuje, jak definovat implicitní a explicitní převod:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

`operator` Klíčové slovo lze použít také k přetížení předdefinovaného C# operátoru. Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Operátory převodu](~/_csharplang/spec/classes.md#conversion-operators)
- [Uživatelem definované převody](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Implicitní převody](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Přetížení operátoru](operator-overloading.md)
- [Operátory testování typů a přetypování](type-testing-and-cast.md)
- [Přetypování a převod typu](../../programming-guide/types/casting-and-type-conversions.md)
- [Zřetězené uživatelem definované explicitní převody vC#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
