---
title: Uživatelem definované operátory převodu – odkaz jazyka C#
description: Zjistěte, jak definovat vlastní implicitní a explicitní převody typů v c#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b6061492cc1a4f756196fb8a9050b68651431e38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847261"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Uživatelem definované operátory převodu (odkaz C#

Uživatelem definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.

Implicitní převody nevyžadují speciální syntaxi, která má být vyvolána a může dojít v různých situacích, například v přiřazení a volání metod. Předdefinované c# implicitní převody vždy úspěšné a nikdy vyvolat výjimku. Uživatelem definované implicitní převody by se měly chovat také tímto způsobem. Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.

Uživatelem definované převody nejsou považovány za [is](type-testing-and-cast.md#is-operator) a [jako](type-testing-and-cast.md#as-operator) operátory. Pomocí [operátoru přetypádka ()](type-testing-and-cast.md#cast-operator-) vyvoláte explicitní převod definovaný uživatelem.

Pomocí `operator` klíčových slov a `implicit` nebo `explicit` definujte implicitní nebo explicitní převod. Typ, který definuje převod, musí být typ zdroje nebo cílový typ tohoto převodu. Převod mezi dvěma uživatelem definovanými typy lze definovat v jednom z těchto dvou typů.

Následující příklad ukazuje, jak definovat implicitní a explicitní převod:

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

Můžete také `operator` použít klíčové slovo přetížení předdefinované c# operátor. Další informace naleznete v tématu [Operator přetížení](operator-overloading.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Operátory převodu](~/_csharplang/spec/classes.md#conversion-operators)
- [Uživatelem definované převody](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Implicitní převody](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Přetěžování operátoru](operator-overloading.md)
- [Operátory pro testování typů a přetypování](type-testing-and-cast.md)
- [Převod odlitků a typů](../../programming-guide/types/casting-and-type-conversions.md)
- [Pokyny pro návrh - Operátory konverzí](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Zřetězené uživatelem definované explicitní převody v C #](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
