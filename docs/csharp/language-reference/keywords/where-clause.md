---
title: klauzule WHERE – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: aceda6cfd33a53388a5afb046359c4dcfddfd1f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602023"
---
# <a name="where-clause-c-reference"></a>where – klauzule (Referenční dokumentace jazyka C#)

`where` Klauzule je použita ve výrazu dotazu k určení, které prvky ze zdroje dat budou vráceny ve výrazu dotazu. Aplikuje logickou podmínku (*predikát*) na každý zdrojový element (odkazovaný proměnnou rozsahu) a vrátí hodnoty, pro které je zadaná podmínka pravdivá. Jeden výraz dotazu může obsahovat více `where` klauzulí a jedna klauzule může obsahovat více dílčích výrazů predikátu.

## <a name="example"></a>Příklad

V následujícím příkladu `where` klauzule filtruje všechna čísla kromě těch, které jsou méně než pět. Při odebrání `where` klauzule se vrátí všechna čísla ze zdroje dat. Výraz `num < 5` je predikát, který je použit pro každý prvek.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Příklad

V rámci jedné `where` klauzule můžete zadat libovolný počet predikátů podle potřeby [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) pomocí operátorů a [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) . V následujícím příkladu dotaz určuje dva predikáty, aby bylo možné vybrat pouze sudá čísla, která jsou menší než pět.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Příklad

`where` Klauzule může obsahovat jednu nebo více metod, které vracejí logické hodnoty. V následujícím příkladu `where` klauzule používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudá nebo lichá.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Poznámky

`where` Klauzule je filtrovací mechanismus. Může být umístěn skoro kdekoli ve výrazu dotazu, s výjimkou nemůže být první nebo poslední klauzule. Klauzule může být uvedena před nebo po klauzuli skupiny v závislosti na tom, zda je nutné filtrovat zdrojové prvky před nebo po seskupení. [](group-clause.md) `where`

Pokud zadaný predikát není platný pro prvky ve zdroji dat, bude výsledkem chyba při kompilaci. Toto je jedna z výhod silné kontroly typu, kterou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]poskytuje.

V době kompilace se `where` klíčové slovo převede na volání <xref:System.Linq.Enumerable.Where%2A> standardní metody operátoru dotazu.

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [select – klauzule](select-clause.md)
- [Filtrování dat](../../programming-guide/concepts/linq/filtering-data.md)
- [Výrazy dotazů LINQ](../../programming-guide/linq-query-expressions/index.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
