---
title: '! (null-odpouštějící) operátor - C# odkaz'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: a8b47e83ce9e999ea2afe94db0a21725abc2d327
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738577"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-odpouštějící) operátor (C# odkaz)

K dispozici v C# 8.0 a `!` novější unární přípona operátor je operátor null odpouštějící. V povoleném [kontextu poznámky s možnou hodnotou null](../../nullable-references.md#nullable-annotation-context)použijete `x` operátor null-odpouštějící k prohlášení, že výraz typu odkazu není `null`: `x!`. Operátor unární `!` předpony je [logický operátor negace](boolean-logical-operators.md#logical-negation-operator-).

Operátor null odpouštějící nemá žádný vliv v době běhu. Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu. Za běhu výraz `x!` vyhodnotí výsledek základní `x`výraz .

Další informace o funkci typů odkazů s možnou hodnotou null naleznete v [tématu Nullable reference types](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Příklady

Jedním z případů použití operátoru null odpouštějící je testování logiky ověřování argument. Zvažte například následující třídu:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

Pomocí [testovacího rámce MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test pro logiku ověření v konstruktoru:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Bez operátoru null-forgiving kompilátor vygeneruje následující upozornění `Warning CS8625: Cannot convert null literal to non-nullable reference type`pro předchozí kód: . Pomocí operátoru null odpouštějící, informujete kompilátor, že předávání `null` je očekáváno a nemělo by být upozorněno.

Můžete také použít operátor null odpouštějící, když určitě `null` víte, že výraz nemůže být, ale kompilátor nepodaří rozpoznat, že. V následujícím příkladu, `IsValid` pokud `true`metoda vrátí `null` , její argument není a můžete bezpečně dereference:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Bez operátoru null-forgiving kompilátor generuje následující `p.Name` upozornění `Warning CS8602: Dereference of a possibly null reference`pro kód: .

Pokud můžete změnit `IsValid` metodu, můžete použít [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atribut informovat kompilátor, že argument `IsValid` metody nemůže být, `null` když metoda vrátí `true`:

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

V předchozím příkladu není nutné použít operátor null odpouštějící, protože kompilátor má `p` dostatek `null` informací `if` k zjistíní, že nemůže být uvnitř příkazu. Další informace o atributech, které umožňují poskytnout další informace o stavu null proměnné, naleznete v [tématu Upgrade api s atributy definovat očekávání null](../../nullable-attributes.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [v části operátor odpouštějící nula](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) v [návrhu specifikace referenčních typů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Kurz: Návrh s typy odkazů s možnou hodnotou null](../../tutorials/nullable-reference-types.md)
