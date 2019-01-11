---
title: kde klauzule - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 182de6ebf9d22da644f1d19566e8cab0052e8521
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221684"
---
# <a name="where-clause-c-reference"></a>where – klauzule (Referenční dokumentace jazyka C#)

`where` Klauzule se používá ve výrazu dotazu k určení, které elementy ze zdroje dat se vrátí ve výrazu dotazu. Použije se logická podmínka (*predikátu*) pro každý prvek zdroje (odkazuje proměnnou rozsahu) a vrátí těch, u kterých je zadaná podmínka pravdivá. Výraz jeden dotaz může obsahovat více `where` klauzule a jedna klauzule může obsahovat několik dílčích výrazů predikátu.

## <a name="example"></a>Příklad

V následujícím příkladu `where` klauzule odfiltruje všechna čísla s výjimkou těch, které jsou méně než pět. Pokud odeberete `where` klauzule všechna čísla ve zdroji dat by vrátila. Výraz `num < 5` je predikát, který se použije na každý prvek.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Příklad

V jednom `where` klauzule, podle potřeby můžete zadat libovolný počet predikátů s použitím [ && ](../operators/conditional-and-operator.md) a [ &#124; &#124; ](../operators/conditional-or-operator.md) operátory. V následujícím příkladu dotaz určuje dva predikáty abyste mohli vybrat pouze sudá čísla, které jsou méně než pět.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Příklad

A `where` klauzule může obsahovat jednu nebo více metod, které vracejí logické hodnoty. V následujícím příkladu `where` klauzule používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudý, nebo lichý.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Poznámky

`where` Klauzule virtuálních sítí je mechanismus filtrování. To může být umístěné skoro kdekoli ve výrazu dotazu, s výjimkou nemůže být prvním nebo posledním klauzuli. A `where` klauzule může být buď před, nebo po [skupiny](group-clause.md) klauzule v závislosti na tom, zda je třeba k filtrování zdrojové prvky před nebo po jsou seskupené.

Pokud zadaný predikát není platná pro elementy ve zdroji dat, způsobí chybu kompilace. Toto je jednou z výhod silné kontroly typů poskytované [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].

V době kompilace `where` – klíčové slovo se převede na volání <xref:System.Linq.Enumerable.Where%2A> metody standardního operátoru dotazu.

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [select – klauzule](select-clause.md)
- [Filtrování dat](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)