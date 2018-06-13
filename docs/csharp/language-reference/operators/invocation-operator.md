---
title: () – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 2ded01ef3192e0f34d586cd63d93b894b5347e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275022"
---
# <a name="-operator-c-reference"></a>() – operátor (Referenční dokumentace jazyka C#)
Kromě používají k určení pořadí operací ve výrazu, kulaté závorky lze provádět následující úlohy:  
  
1.  Zadejte přetypování a převody typu.  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Vyvolání metody nebo delegáti.  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Přetypování explicitně vyvolá operátor převodu z jednoho typu přetypování selže, pokud je definovaný žádný převod operátor. Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../../../csharp/language-reference/keywords/explicit.md) a [implicitní](../../../csharp/language-reference/keywords/implicit.md).  
  
 `()` Operátor nemohou být přetíženy.  
  
 Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Výraz cast může vést k nejednoznačný syntaxe. Například výraz `(x)–y` může být buď interpretovat jako výraz přetypování (přetypování y – typ x) nebo jako doplňkové výrazu kombinovat s výrazu v závorkách, která vypočítá hodnotu x – y.  
  
 Další informace o volání metody najdete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
