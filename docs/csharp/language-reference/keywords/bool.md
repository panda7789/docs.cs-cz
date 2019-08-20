---
title: bool – klíčové C# slovo – Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 3e4e83b52cd6b275e68039693c774f6490f2b88f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606055"
---
# <a name="bool-c-reference"></a>bool (Referenční dokumentace jazyka C#)

Klíčové slovo je <xref:System.Boolean?displayProperty=nameWithType>alias. `bool` Slouží k deklaraci proměnných pro uložení logických hodnot: [true](true-literal.md) a [false](false-literal.md).

> [!NOTE]
> `bool?` Použijte typ, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují logický typ se třemi hodnotami. Pro operandy, předdefinované `&` a `|` operátory podporují logiku se třemi hodnotami. `bool?` Další informace naleznete v části s [možnou hodnotou null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) logických operátorů v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .

## <a name="literals"></a>Literály

`bool` Proměnné můžete přiřadit logickou hodnotu. Můžete také přiřadit výraz, který je vyhodnocen `bool` `bool` na proměnnou.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Výchozí hodnota `bool` proměnné je `false`. Výchozí hodnota `bool?` proměnné je `null`.

## <a name="conversions"></a>Převody

V C++ `bool` , hodnota typu může být převedena na hodnotu typu `int`; jinými slovy `false` je ekvivalentem nula a `true` je ekvivalentní nenulovým hodnotám. V C#neexistují žádné konverze mezi `bool` typem a jinými typy. Například následující `if` příkaz je neplatný v: C#

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Chcete-li otestovat proměnnou typu `int`, je nutné ji explicitně porovnat s hodnotou, jako je například nula, následovně:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Příklad

V tomto příkladu zadáte znak z klávesnice a program zkontroluje, jestli je vstupním znakem písmeno. Pokud se jedná o písmeno, zkontroluje, zda se jedná o malá nebo velká písmena. Tyto kontroly se provádějí s <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, `bool` jak vrátí typ:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka předdefinovaných typů](./built-in-types-table.md)
- [Tabulka implicitních číselných převodů](./implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](./explicit-numeric-conversions-table.md)
