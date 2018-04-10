---
title: '[] – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03664f5604bb7d7dce9e8ae2ff0ec045c6a203b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>[] – operátor (Referenční dokumentace jazyka C#)
Hranaté závorky (`[]`) se používají pro pole, indexery a atributy. Můžete také používají s ukazatele.  
  
## <a name="remarks"></a>Poznámky  
 Typ pole je typu, za nímž následuje `[]`:  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Pro přístup k elementu pole, je index požadovaný element uzavřený v závorkách:  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Pokud pole indexu je mimo rozsah, je vyvolána výjimka.  
  
 Pole indexu operátor nemohou být přetíženy; typy však můžete definovat, indexery a vlastnosti, které trvat jeden nebo více parametrů. Indexer parametry jsou uzavřeny do hranatých závorek, stejně jako indexy pole, ale indexer parametry lze deklarovat být jakéhokoli typu, na rozdíl od indexy pole, které musí být celočíselné.  
  
 Například definuje rozhraní .NET Framework `Hashtable` typ, který přidruží klíče a hodnoty libovolného typu:  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Hranaté závorky se také používají k určení [atributy](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Hranaté závorky můžete použít k indexu vypnout ukazatel:  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Žádné hranice, kontrola probíhá.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
