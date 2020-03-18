---
title: where klauzule - C# Reference
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173481"
---
# <a name="where-clause-c-reference"></a>where – klauzule (Referenční dokumentace jazyka C#)

Klauzule se `where` používá ve výrazu dotazu k určení, které prvky ze zdroje dat budou vráceny ve výrazu dotazu. Použije logickou podmínku *(predikát)* pro každý zdrojový prvek (odkazuje proměnná rozsahu) a vrátí ty, pro které je zadaná podmínka true. Jeden dotaz výraz může `where` obsahovat více klauzulí a jedna klauzule může obsahovat více podvýrazů predikátu.

## <a name="example"></a>Příklad

V následujícím příkladu `where` klauzule filtruje všechna čísla kromě těch, které jsou menší než pět. Pokud odeberete klauzuli, `where` budou vrácena všechna čísla ze zdroje dat. Výraz `num < 5` je predikát, který je použit pro každý prvek.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Příklad

V rámci `where` jedné klauzule můžete určit tolik predikáty [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) podle potřeby pomocí a [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operátory. V následujícím příkladu dotaz určuje dvě predikáty, aby bylo možné vybrat pouze sudá čísla, která jsou menší než pět.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Příklad

Klauzule `where` může obsahovat jednu nebo více metod, které vracejí logické hodnoty. V následujícím příkladu `where` klauzule používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudá nebo lichá.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Poznámky

Klauzule `where` je mechanismus filtrování. Může být umístěn téměř kdekoli ve výrazu dotazu, s výjimkou nemůže být první nebo poslední klauzule. Klauzule `where` se může zobrazit před nebo za [klauzule skupiny](group-clause.md) v závislosti na tom, zda je třeba filtrovat zdrojové prvky před nebo po jejich seskupení.

Pokud zadaný predikát není platný pro prvky ve zdroji dat, dojde k chybě v době kompilace. To je jedna z výhod silné kontroly typu poskytované LINQ.

V době `where` kompilace je klíčové slovo <xref:System.Linq.Enumerable.Where%2A> převedeno na volání metody Operátor standardního dotazu.

## <a name="see-also"></a>Viz také

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [select – klauzule](select-clause.md)
- [Filtrování dat](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
