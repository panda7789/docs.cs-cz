---
title: BOOL – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d6b0cb91dd9b8159919b0d155bb2f9773e7ba534
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315105"
---
# <a name="bool-c-reference"></a>bool (Referenční dokumentace jazyka C#)

`bool` – Klíčové slovo je zástupce <xref:System.Boolean?displayProperty=nameWithType>. Se používá k deklaraci proměnné, které chcete uložit logické hodnoty [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md).

> [!NOTE]
> Pokud požadujete logická hodnota proměnné, která může mít hodnotu `null`, použijte `bool?`. Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).

## <a name="literals"></a>Literály

Můžete přiřadit logickou hodnotu k `bool` proměnné. Je také možné přiřadit výraz, který se vyhodnocuje `bool` k `bool` proměnné.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Výchozí hodnota `bool` proměnná `false`. Výchozí hodnota `bool?` proměnná `null`.

## <a name="conversions"></a>Převody

V jazyce C++ hodnotu typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` se rovná nule a `true` je ekvivalentní nenulové hodnoty. V jazyce C#, neexistuje žádný převod mezi `bool` typu a dalších typů. Například následující `if` příkaz je neplatný v jazyce C#:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

K testování proměnné typu `int`, budete muset explicitně porovnávají ho na hodnotu, jako je například nula, následujícím způsobem:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Příklad

V tomto příkladu zadejte znak z klávesnice a program ověří, zda vstupní znak je písmeno. Pokud je písmeno, zkontroluje, pokud je malá nebo velká písmena. Tyto kontroly se provádějí pomocí <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, obě které vrátit `bool` typ:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
[Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  