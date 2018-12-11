---
title: '[] – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 3e2ce5c4b74cbf79e00410791ffcc31368f78648
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243995"
---
# <a name="-operator-c-reference"></a>[] – operátor (Referenční dokumentace jazyka C#)
Hranaté závorky (`[]`) se používají pro pole, indexery a atributy. Můžete také používají s ukazateli.  
  
## <a name="remarks"></a>Poznámky  
 Typ pole je typu, za nímž následuje `[]`:  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 O přístup k prvku pole, index požadovaný element uzavřený v hranatých závorkách:  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Pokud pole indexu je mimo rozsah, je vyvolána výjimka.  
  
 Pole indexování operátor nelze přetížit; typy však můžete definovat indexerů, které provést jeden nebo více parametrů. Indexer parametry jsou uzavřeny do hranatých závorek, stejně jako indexy pole, ale mohou být deklarovány parametry indexer bude libovolný typ, na rozdíl od indexy pole, které musí být integrálního typu.  
  
 Například rozhraní .NET Framework definuje `Hashtable` typ, který přidruží klíče a hodnoty libovolného typu:  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Hranaté závorky se také používají k určení [atributy](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Hranaté závorky můžete použít k indexování vypnout ukazatel:  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Žádné kontroly hranic, se provádí.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Indexery](../../../csharp/programming-guide/indexers/index.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
