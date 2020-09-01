---
description: Select – klauzule – reference jazyka C#
title: Select – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136899"
---
# <a name="select-clause-c-reference"></a>select – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu `select` klauzule určuje typ hodnot, které budou vytvořeny při spuštění dotazu. Výsledek vychází z vyhodnocení všech předchozích klauzulí a na jakékoli výrazy v `select` klauzuli samotné. Výraz dotazu musí být ukončen `select` klauzulí klauzule nebo [Group](group-clause.md) .

Následující příklad ukazuje jednoduchou `select` klauzuli ve výrazu dotazu.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Typ sekvence vytvářené `select` klauzulí určuje typ proměnné dotazu `queryHighScores` . V nejjednodušším případě `select` klauzule pouze určuje proměnnou rozsahu. To způsobí, že vrácená sekvence bude obsahovat prvky stejného typu jako zdroj dat. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Nicméně `select` klauzule také poskytuje výkonný mechanizmus pro transformaci (nebo *projekci*) zdrojových dat do nových typů. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje všechny různé formuláře, které `select` klauzule může provést. V každém dotazu si poznamenejte vztah mezi `select` klauzulí a typem *proměnné dotazu* ( `studentQuery1` , `studentQuery2` a tak dále).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Jak je znázorněno v `studentQuery8` předchozím příkladu, někdy může být vhodné, aby prvky vrácené sekvence obsahovaly pouze podmnožinu vlastností zdrojových elementů. Udržováním vrácené sekvence co nejmenší je možné snížit nároky na paměť a zvýšit rychlost provádění dotazu. To lze provést tak, že vytvoříte anonymní typ v `select` klauzuli a pomocí inicializátoru objektu jej inicializujete s příslušnými vlastnostmi ze zdrojového elementu. Příklad, jak to provést, naleznete v tématu [Inicializátory objektů a kolekcí](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Poznámky

V době kompilace `select` je klauzule přeložena na volání metody <xref:System.Linq.Enumerable.Select%2A> standardního operátoru dotazu.

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [Partial (metoda) (Referenční dokumentace jazyka C#)](partial-method.md)
- [Anonymní typy](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ v jazyku C#](../../linq/index.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
