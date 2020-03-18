---
title: select klauzule - C# Reference
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 68ea7ad6fc7cf5580dbdd0ae7f012f36566db0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173507"
---
# <a name="select-clause-c-reference"></a>select – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu `select` klauzule určuje typ hodnot, které budou vytvořeny při spuštění dotazu. Výsledek je založen na vyhodnocení všech předchozích klauzulí a `select` na všech výrazech v samotné klauzuli. Výraz dotazu musí být `select` ukončen klauzulí nebo [klauzulí skupiny.](group-clause.md)

Následující příklad ukazuje `select` jednoduchou klauzuli ve výrazu dotazu.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Typ sekvence vytvořené `select` klauzulí určuje typ proměnné `queryHighScores`dotazu . V nejjednodušším případě `select` klauzule pouze určuje proměnnou rozsahu. To způsobí, že vrácená sekvence obsahuje prvky stejného typu jako zdroj dat. Další informace naleznete [v tématu Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Klauzule `select` však také poskytuje výkonný mechanismus pro transformaci (nebo *promítání*) zdrojová data do nových typů. Další informace naleznete [v tématu Transformace dat s LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje všechny různé `select` formy, které klauzule může mít. V každém dotazu si `select` všimněte vztahu mezi klauzulí`studentQuery1` `studentQuery2`a typem *proměnné dotazu* ( , , a tak dále).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Jak je `studentQuery8` znázorněno v předchozím příkladu, někdy můžete chtít, aby prvky vrácené sekvence obsahovaly pouze podmnožinu vlastností zdrojových prvků. Udržováním vrácené sekvence co nejmenší můžete snížit požadavky na paměť a zvýšit rychlost provádění dotazu. Toho lze dosáhnout vytvořením anonymního `select` typu v klauzuli a použitím inicializačního zařízení objektu k jeho inicializaci s příslušnými vlastnostmi ze zdrojového prvku. Příklad, jak to provést, naleznete [v tématu Objekt a kolekce Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Poznámky

V době kompilace `select` klauzule je přeložen a <xref:System.Linq.Enumerable.Select%2A> volání metody operátoru standardní dotaz.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [částečné (metoda) (C# Reference)](partial-method.md)
- [Anonymní typy](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
