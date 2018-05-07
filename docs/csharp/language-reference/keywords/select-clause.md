---
title: select – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 6e7277b5d714e48059fe1ed7e8b85e46a14a840c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="select-clause-c-reference"></a>select – klauzule (Referenční dokumentace jazyka C#)
Ve výrazu dotazu `select` klauzuli Určuje typ hodnoty, které budou vytvořeny, když je proveden dotaz. Výsledkem je založena na vyhodnocení všechny předchozí klauzule a na všechny výrazy v `select` klauzule sám sebe. Výraz dotazu musí ukončit některým `select` klauzule nebo [skupiny](../../../csharp/language-reference/keywords/group-clause.md) klauzule.  
  
 Následující příklad ukazuje jednoduchý `select` klauzule ve výrazu dotazu.  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 Typ pořadí vyprodukované `select` klauzuli Určuje typ proměnné dotazu `queryHighScores`. V nejjednodušším případě `select` klauzule právě Určuje proměnnou rozsahu. To způsobí, že vrácený pořadí tak, aby obsahovala elementy stejného typu jako zdroj dat. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Ale `select` klauzule také poskytuje výkonný mechanismus pro transformaci (nebo *plánování*) zdroj dat do nové typy. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na různé způsoby, které `select` klauzule může trvat. V každém dotazu Poznámka: vztah mezi `select` klauzule a typ *proměnné dotazu* (`studentQuery1`, `studentQuery2`a tak dále).  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 Jak je znázorněno v `studentQuery8` v předchozím příkladu, v některých případech můžete elementy vrácený pořadí tak, aby obsahovala pouze podmnožinu vlastností zdrojové elementy. Udržováním vrácený pořadí co nejmenší může snížit požadavky na paměť a zvýšit rychlost zpracování dotazu. To můžete udělat tak, že vytvoříte instanci anonymního typu v `select` klauzule a pomocí inicializátoru objektu k chybě při inicializaci s příslušné vlastnosti ze zdroje elementu. Příklad toho, jak to provést, naleznete v části [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="remarks"></a>Poznámky  
 Při kompilaci `select` přeložen volání metody <xref:System.Linq.Enumerable.Select%2A> operátor standardní dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [from – klauzule](../../../csharp/language-reference/keywords/from-clause.md)  
 [partial (metoda) (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/partial-method.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
