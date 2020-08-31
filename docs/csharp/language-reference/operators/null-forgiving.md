---
description: '! (null-striktní) – operátor – reference jazyka C#'
title: '! (null-striktní) – operátor – reference jazyka C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 7ae35f4741e1ef377b73a15066dddd243c94d8fe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118218"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-striktní) – operátor (Referenční dokumentace jazyka C#)

K dispozici v C# 8,0 a novějším, unární `!` operátor přípony je operátor null-striktní. V povoleném [kontextu anotace s možnou hodnotou](../../nullable-references.md#nullable-annotation-context)null použijte operátor null-striktní k deklaraci, že výraz `x` typu odkazu není `null` : `x!` . Unární operátor prefix `!` je [logický operátor negace](boolean-logical-operators.md#logical-negation-operator-).

Operátor null-striktní nemá žádný vliv na dobu běhu. Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu. V době běhu se výraz `x!` vyhodnotí jako výsledek podkladového výrazu `x` .

> [!NOTE]
> V C# 8 operátor null-striktní ukončí seznam předchozích operací [s hodnotou null](member-access-operators.md#null-conditional-operators--and-) . Například výraz `x?.y!.z` je analyzován jako `(x?.y)!.z` . Z důvodu této interpretace `z` je vyhodnocena i `x` v případě, že je `null` , což může vést k <xref:System.NullReferenceException> .

Další informace o funkci typů odkazů s možnou hodnotou null naleznete v tématu [typy odkazů s možnou hodnotou null](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Příklady

Jedním z případů použití operátoru null-striktní je testování logiky ověřování argumentů. Zvažte například následující třídu:

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

Pomocí [testovacího rozhraní MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test logiky ověřování v konstruktoru:

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro předchozí kód: `Warning CS8625: Cannot convert null literal to non-nullable reference type` . Pomocí operátoru null-striktní informujte kompilátor, že předávání `null` je očekáváno, a neměl by se mu upozornit.

Operátor null-striktní můžete použít také v případě, že jednoznačně víte, že výraz nemůže být, `null` ale kompilátor nespravuje pro rozpoznání. V následujícím příkladu, pokud se `IsValid` Metoda vrátí `true` , její argument není `null` a můžete ho bezpečně odkázat:

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

Bez operátoru null-striktní generuje kompilátor následující upozornění pro `p.Name` kód: `Warning CS8602: Dereference of a possibly null reference` .

Pokud můžete upravit `IsValid` metodu, můžete použít atribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) k informování kompilátoru, že argument `IsValid` metody nemůže být, `null` když metoda vrátí `true` :

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

V předchozím příkladu nemusíte používat operátor null-striktní, protože kompilátor obsahuje dostatek informací, aby bylo možné zjistit, že `p` nemůže být `null` uvnitř `if` příkazu. Další informace o atributech, které umožňují zadat další informace o stavu null proměnné, naleznete v tématu [upgrade rozhraní API s atributy pro definování očekávání null](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátor null-striktní](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) v [konceptu specifikace typů odkazů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Kurz: návrh s použitím typů odkazů s možnou hodnotou null](../../tutorials/nullable-reference-types.md)
