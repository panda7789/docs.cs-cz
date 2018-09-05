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
ms.openlocfilehash: 29097dc4aa0bf712b9b2beda4450820a66472ba7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671848"
---
# <a name="-operator-c-reference"></a>() – operátor (Referenční dokumentace jazyka C#)
Kromě používá k určení pořadí operací ve výrazu závorky slouží k provádění následujících úloh:  
  
1.  Zadejte přetypování a převody typů.  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Vyvolání metod a delegátů.  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Přetypování vyvolá explicitní operátor převodu z jednoho typu na jiný; přetypování selže, pokud není definován žádný převod operátor. Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../../../csharp/language-reference/keywords/explicit.md) a [implicitní](../../../csharp/language-reference/keywords/implicit.md).  
  
 `()` Operátor nelze přetížit.  
  
 Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Další informace o volání metody, naleznete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
