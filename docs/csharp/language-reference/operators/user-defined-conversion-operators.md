---
title: Uživatelsky definované operátory převodu – reference jazyka C#
description: Naučte se definovat vlastní implicitní a explicitní převody typů v jazyce C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
- explicit
- implicit
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: a0eb11d55ad9e9cccde1704ba4c5ae8acb609989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916631"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Uživatelsky definované operátory převodu (Referenční dokumentace jazyka C#)

Uživatelsky definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.

Implicitní převody nevyžadují, aby se vyvolala speciální syntaxe, která může nastat v různých situacích, například v přiřazení a volání metod. Předdefinované implicitní převody jazyka C# jsou vždy úspěšné a nikdy nevyvolávají výjimku. Uživatelem definované implicitní převody by se měly chovat i tímto způsobem. Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.

Uživatelem definované převody nejsou považovány za operátory [is](type-testing-and-cast.md#is-operator) a [as](type-testing-and-cast.md#as-operator) . Použijte [výraz přetypování](type-testing-and-cast.md#cast-expression) k vyvolání uživatelem definovaného explicitního převodu.

Použijte `operator` `implicit` `explicit` klíčová slova a nebo pro definování implicitního nebo explicitního převodu v uvedeném pořadí. Typ, který definuje převod, musí být buď zdrojový typ, nebo cílový typ převodu. Převod mezi dvěma uživatelsky definovanými typy lze definovat v jednom ze dvou typů.

Následující příklad ukazuje, jak definovat implicitní a explicitní převod:

[!code-csharp[implicit an explicit conversions](snippets/shared/UserDefinedConversions.cs)]

Klíčové slovo lze použít také `operator` k přetížení předdefinovaného operátoru jazyka C#. Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Operátory převodu](~/_csharplang/spec/classes.md#conversion-operators)
- [Uživatelem definované převody](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Implicitní převody](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Přetěžování operátoru](operator-overloading.md)
- [Operátory pro testování typů a přetypování](type-testing-and-cast.md)
- [Přetypování a převod typu](../../programming-guide/types/casting-and-type-conversions.md)
- [Pokyny pro návrh – operátory převodu](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Zřetězené uživatelem definované explicitní převody v jazyce C #](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
