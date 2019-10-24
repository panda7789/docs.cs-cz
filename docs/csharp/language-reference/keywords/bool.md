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
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771851"
---
# <a name="bool-c-reference"></a>bool (Referenční dokumentace jazyka C#)

Klíčové slovo `bool` je aliasem <xref:System.Boolean?displayProperty=nameWithType>. Slouží k deklaraci proměnných pro uložení logických hodnot: [true](true-literal.md) a [false](false-literal.md).

> [!NOTE]
> @No__t_0 typ použijte, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují logický typ se třemi hodnotami. Pro operandy `bool?` jsou předdefinované operátory `&` a `|` podporovány v rámci logiky se třemi hodnotami. Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .

## <a name="literals"></a>Literály

Můžete přiřadit logickou hodnotu k proměnné `bool`. Můžete také přiřadit výraz, který se vyhodnotí jako `bool` na `bool` proměnnou.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Výchozí hodnota `bool` proměnné je `false`. Výchozí hodnota `bool?` proměnné je `null`.

## <a name="conversions"></a>Převody

V C++, hodnota typu `bool` může být převedena na hodnotu typu `int`; Jinými slovy, `false` je ekvivalentem nula a `true` je ekvivalentní nenulovým hodnotám. V C#neexistují žádné konverze mezi typem `bool` a dalšími typy. Například následující příkaz `if` je neplatný v C#:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Chcete-li otestovat proměnnou typu `int`, je nutné ji explicitně porovnat s hodnotou, jako je například nula, následovně:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Příklad

V tomto příkladu zadáte znak z klávesnice a program zkontroluje, jestli je vstupním znakem písmeno. Pokud se jedná o písmeno, zkontroluje, zda se jedná o malá nebo velká písmena. Tyto kontroly se provádějí s <xref:System.Char.IsLetter%2A> a <xref:System.Char.IsLower%2A>, jak vrátí `bool` typ:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka předdefinovaných typů](./built-in-types-table.md)
