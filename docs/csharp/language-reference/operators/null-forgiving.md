---
title: '! (null – striktní) – odkaz C# na operátora'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 21bbf8e1253641317750b911e052ee5ff0a0d063
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036162"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null – striktní) – operátorC# (Referenční dokumentace)

K dispozici v C# 8,0 a novějším, unární přípona`!`operátor je operátor null-striktní. V povoleném [kontextu anotace s možnou hodnotou null](../../nullable-references.md#nullable-annotation-context)použijte operátor null-striktní k deklaraci, že výraz `x` typu odkazu není `null`: `x!`. Unární předpona `!` je operátor [logické negace](boolean-logical-operators.md#logical-negation-operator-).

Operátor null-striktní nemá žádný vliv na dobu běhu. Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu. V době běhu je výraz `x!` vyhodnocen jako výsledek podkladového výrazu `x`.

Další informace o funkci typů odkazů s možnou hodnotou null naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).

## <a name="examples"></a>Příklady

Jedním z případů použití operátoru null-striktní je testování logiky ověřování argumentů. Zvažte například následující třídu:

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

Pomocí [testovacího rozhraní MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test logiky ověřování v konstruktoru:

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro předchozí kód: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Pomocí operátoru null-striktní informujte kompilátor, který předává `null` je očekáván a neměl by se mu upozornit.

Operátor null-striktní můžete použít také v případě, že jednoznačně víte, že výraz nemůže být `null`, ale kompilátor nespravuje pro rozpoznání. V následujícím příkladu, pokud metoda `IsValid` vrátí `true`, jeho argument není `null` a můžete ho bezpečně odkázat:

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro kód `p.Name`: `Warning CS8602: Dereference of a possibly null reference`.

Pokud můžete upravit metodu `IsValid`, můžete použít atribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) k informování kompilátoru, že argument metody `IsValid` nemůže být `null`, pokud metoda vrátí `true`:

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

V předchozím příkladu nemusíte používat operátor null-striktní, protože kompilátor má dostatek informací, aby zjistil, že `p` nelze v příkazu `if` `null`. Další informace o atributech, které umožňují zadat další informace o stavu null proměnné, naleznete v tématu [upgrade rozhraní API s atributy pro definování očekávání null](../../nullable-attributes.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátor null-striktní](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) v [konceptu specifikace typů odkazů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Kurz: návrh s použitím typů odkazů s možnou hodnotou null](../../tutorials/nullable-reference-types.md)
