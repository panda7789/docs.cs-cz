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
ms.openlocfilehash: dcab29cdbe98b5e49463d9a2781d43d4b9ee9544
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467338"
---
# <a name="select-clause-c-reference"></a>select – klauzule (Referenční dokumentace jazyka C#)
Ve výrazu dotazu `select` klauzule určuje typ hodnoty, které se budou vytvářet při spuštění dotazu. Výsledkem je založeno na vyhodnocení všechny předchozí klauzule a na všechny výrazy v `select` klauzule samotný. Buď musí končit výrazu dotazu `select` klauzule nebo [skupiny](../../../csharp/language-reference/keywords/group-clause.md) klauzuli.  
  
 Následující příklad ukazuje jednoduchý `select` klauzule ve výrazu dotazu.  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 Typ pořadí vytvářených `select` klauzule určuje typ proměnné dotazu `queryHighScores`. V nejjednodušším případě `select` klauzule právě Určuje proměnnou rozsahu. To způsobí, že vrácená sekvence má obsahovat prvky stejného typu jako zdroj dat. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Ale `select` klauzule také poskytuje výkonný mechanismus pro transformaci (nebo *projekci*) zdroje dat do nové typy. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé formuláře, který `select` klauzule může trvat. V obou dotazech, mějte na paměti o vztah mezi `select` klauzule a typ *proměnné dotazu* (`studentQuery1`, `studentQuery2`, a tak dále).  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 Jak je znázorněno v `studentQuery8` v předchozím příkladu, můžete někdy chtít prvky vrácená sekvence má obsahovat pouze podmnožinu vlastností zdrojové elementy. Udržováním vrácené posloupnosti co nejmenší může snížit požadavky na paměť a zvýšit rychlost provádění dotazu. Můžete to udělat tak, že vytvoříte anonymního typu v `select` klauzule a pomocí inicializátoru objektu inicializovat s odpovídající vlastností ze zdrojového elementu. Příklad toho, jak to provést, najdete v části [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="remarks"></a>Poznámky  
 V době kompilace `select` přeložen na volání metody <xref:System.Linq.Enumerable.Select%2A> standardní operátor dotazu.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
- [from – klauzule](../../../csharp/language-reference/keywords/from-clause.md)  
- [partial (metoda) (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/partial-method.md)  
- [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
