---
title: "() – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d62e6c93dcc69c892d4ca96ace3806cb1c8d989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
