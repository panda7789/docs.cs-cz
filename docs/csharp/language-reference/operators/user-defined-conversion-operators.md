---
title: Uživatelem definovaný převod operators – C# odkaz
description: Další informace o definování vlastního typu implicitní a explicitní převody v C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67788498"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Uživatelem definovaný převod operátorů (C# odkaz)

Uživatelem definovaný typ, můžete definovat vlastní explicitní nebo implicitní převod z nebo do jiného typu.

Implicitní převody nevyžadují speciální syntaxe má být vyvolána a může dojít v různých situacích, například v přiřazení a metody volání. Předdefinované C# implicitních převodů vždy úspěšné a nikdy vyvolat výjimku nebo dojít ke ztrátě informací. Uživatelem definované implicitní převody by měla chovat i tímto způsobem. Pokud vlastní převod může vyvolat výjimku nebo dojít ke ztrátě informací, můžete jej definují jako explicitní převod.

Uživatelem definované převody nejsou považovány za podle [je](type-testing-and-conversion-operators.md#is-operator) a [jako](type-testing-and-conversion-operators.md#as-operator) operátory. Použití [přetypování () operátor](type-testing-and-conversion-operators.md#cast-operator-) vyvolat explicitní převod definovaný uživatelem.

Použití `operator` a `implicit` nebo `explicit` klíčová slova k definování implicitní nebo explicitní převod, v uvedeném pořadí. Typ, který definuje převod musí být typu zdrojový nebo cílový typ převodu. Převod mezi dvěma uživatelem definované typy lze definovat v některém ze dvou typů.

Následující příklad ukazuje, jak definovat implicitní a explicitní převod:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Můžete také použít `operator` – klíčové slovo přetížení i předdefinovanou C# operátor. Další informace najdete v tématu [přetížení operátoru](operator-overloading.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [operátory převodu](~/_csharplang/spec/classes.md#conversion-operators)
- [Uživatelem definované převody](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Implicitní převody](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Přetížení operátoru](operator-overloading.md)
- [Typové zkoušky a převod operátorů](type-testing-and-conversion-operators.md)
- [Přetypování a typ převodu](../../programming-guide/types/casting-and-type-conversions.md)
- [Zřetězit uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
