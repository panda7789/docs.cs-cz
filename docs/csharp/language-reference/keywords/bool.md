---
title: BOOL – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: a274083ad2e518f8f29384e51d692bcf9a9cb61e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237243"
---
# <a name="bool-c-reference"></a>bool (Referenční dokumentace jazyka C#)

`bool` – Klíčové slovo je alias pro <xref:System.Boolean?displayProperty=nameWithType>. Se používá k deklaraci proměnné k ukládání logické hodnoty: [true](true-literal.md) a [false](false-literal.md).

> [!NOTE]
> Pokud požadujete logickou hodnotu, která může také obsahovat hodnotu `null`, použijte `bool?`. Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.

## <a name="literals"></a>Literály

Můžete přiřadit logickou hodnotu k `bool` proměnné. Můžete také přiřadit výraz, který se vyhodnotí `bool` k `bool` proměnné.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Výchozí hodnota `bool` proměnná je `false`. Výchozí hodnota `bool?` proměnná je `null`.

## <a name="conversions"></a>Převody

V jazyce C++ je hodnota typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` je ekvivalentní hodnotě nula a `true` odpovídá nenulové hodnoty. V jazyce C#, neexistuje žádný převod mezi `bool` typ a jiné typy. Například následující `if` příkaz není platný v jazyce C#:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

K otestování proměnné typu `int`, je nutné explicitně porovnejte ji s hodnotou, jako je nula, následujícím způsobem:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Příklad

V tomto příkladu zadejte znak z klávesnice a program kontroluje, jestli vstupní znak je písmeno. Pokud je písmeno, se zkontroluje, jestli malá nebo velká písmena. Tyto kontroly se provádějí s <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, jak které návratovou hodnotu `bool` typu:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  