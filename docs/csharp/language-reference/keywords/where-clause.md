---
title: klauzule WHERE – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 42932809d58c739afc165676c0b90c5a23f568de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712816"
---
# <a name="where-clause-c-reference"></a>where – klauzule (Referenční dokumentace jazyka C#)

Klauzule `where` se používá ve výrazu dotazu k určení, které prvky ze zdroje dat budou vráceny ve výrazu dotazu. Aplikuje logickou podmínku (*predikát*) na každý zdrojový element (odkazovaný proměnnou rozsahu) a vrátí hodnoty, pro které je zadaná podmínka pravdivá. Jeden výraz dotazu může obsahovat více klauzulí `where` a jedna klauzule může obsahovat více dílčích výrazů predikátu.

## <a name="example"></a>Příklad

V následujícím příkladu vyfiltruje klauzule `where` všechny počty kromě těch, které jsou méně než pět. Odeberete-li klauzuli `where`, bude vrácena veškerá čísla ze zdroje dat. Výraz `num < 5` je predikát, který je použit pro každý prvek.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Příklad

V rámci jedné klauzule `where` můžete zadat libovolný počet predikátů podle potřeby pomocí operátorů [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) a [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) . V následujícím příkladu dotaz určuje dva predikáty, aby bylo možné vybrat pouze sudá čísla, která jsou menší než pět.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Příklad

Klauzule `where` může obsahovat jednu nebo více metod, které vracejí logické hodnoty. V následujícím příkladu klauzule `where` používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudá nebo lichá.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Poznámky

Klauzule `where` je filtrovací mechanismus. Může být umístěn skoro kdekoli ve výrazu dotazu, s výjimkou nemůže být první nebo poslední klauzule. Klauzule `where` může být uvedena před nebo za klauzulí [Group](group-clause.md) v závislosti na tom, zda je nutné filtrovat zdrojové prvky před seskupením nebo po nich.

Pokud zadaný predikát není platný pro prvky ve zdroji dat, bude výsledkem chyba při kompilaci. Toto je jedna z výhod silné kontroly typu, kterou poskytuje LINQ.

V době kompilace je klíčové slovo `where` převedeno na volání metody operátoru dotazu <xref:System.Linq.Enumerable.Where%2A> Standard.

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [select – klauzule](select-clause.md)
- [Filtrování dat](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [Začínáme s dotazy LINQ v jazyce C#](/dotnet/csharp/programming-guide/concepts/linq/)
