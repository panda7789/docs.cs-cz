---
title: vybrat klauzuli – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: b4d25f80e4cdb08fbc28fa4db3cb1c790b1145e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713089"
---
# <a name="select-clause-c-reference"></a>select – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu určuje klauzule `select` typ hodnot, které budou vytvořeny při spuštění dotazu. Výsledek vychází z vyhodnocení všech předchozích klauzulí a na jakékoli výrazy v klauzuli `select` samotné. Výraz dotazu musí být ukončen buď klauzulí `select`, nebo klauzulí [Group](group-clause.md) .

Následující příklad ukazuje jednoduchou klauzuli `select` ve výrazu dotazu.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Typ sekvence, která je vytvořena klauzulí `select`, určuje typ proměnné dotazu `queryHighScores`. V nejjednodušším případě klauzule `select` pouze určuje proměnnou rozsahu. To způsobí, že vrácená sekvence bude obsahovat prvky stejného typu jako zdroj dat. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Klauzule `select` však také poskytuje výkonný mechanizmus pro transformaci (nebo *projekci*) zdrojových dat do nových typů. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje všechny různé formuláře, které může klauzule `select` trvat. V každém dotazu si poznamenejte vztah mezi klauzulí `select` a typem *proměnné dotazu* (`studentQuery1`, `studentQuery2`a tak dále).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Jak ukazuje `studentQuery8` v předchozím příkladu, někdy můžete chtít, aby prvky vrácené sekvence obsahovaly pouze podmnožinu vlastností zdrojových elementů. Udržováním vrácené sekvence co nejmenší je možné snížit nároky na paměť a zvýšit rychlost provádění dotazu. To lze provést tak, že vytvoříte anonymní typ v klauzuli `select` a pomocí inicializátoru objektu jej inicializujete s příslušnými vlastnostmi ze zdrojového elementu. Příklad, jak to provést, naleznete v tématu [Inicializátory objektů a kolekcí](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Poznámky

V době kompilace je klauzule `select` přeložena do volání metody standardní operátor dotazu <xref:System.Linq.Enumerable.Select%2A>.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [from – klauzule](from-clause.md)
- [Partial (metoda) (C# Referenční dokumentace)](partial-method.md)
- [Anonymní typy](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [Začínáme s dotazy LINQ v jazyce C#](/dotnet/csharp/programming-guide/concepts/linq/)
